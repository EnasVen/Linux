# FHS
FHS為File Hierarchy Standard的縮寫，規範每個檔案應該存放的位置，了解這個檔案架構就能理解目錄的意義。  
依照FHS標準，指令存放位置分類如下:
1. **系統開機用**
  - /bin , /sbin
2. **系統正常運作用**
  - /usr/bin , /usr/sbin
3. **自行編譯程式 or 3rd Party Free軟體**
  - /usr/local/[軟體]/bin , /usr/local/[軟體]/sbin 
4. **Vende相關軟體(廠商付費軟體/版權軟體)**
  - /opt/廠商名稱/軟體名稱/bin ,  /opt/廠商名稱/軟體名稱/sbin

1和2的指令可以透過apt install獲取;3可由make或cmake指令獲取(ex:pip3)

# 禁止儲存
以下4個位置不可存放資料:
1. /tmp : 暫存區重開機後會自動清空
2. /run , /proc / sys : 虛擬目錄存在RAM內

# 路徑
1. 絕對路徑: 從根目錄 / 開始
2. 相對路徑: 
  - . : 目前目錄
  - .. : 上一層目錄
  - ~ : 家目錄(使用者為/home/帳號名稱；管理員為 /root)

# 檔案系統
> Windows :  NTFS , fat32  
> RedHat : xfs  
> Debian : ext2,3,4 (有lost + found 目錄)  
> Docker : overlay2  

# 資料傳輸
下列兩種方法可以將資料上傳到Ubuntu:
1. 由windows上傳
  - step1 : 打開cmd
  - step2 : 到putty路徑
  - step3 : C:\Users\...\putty.exe pscp C:\shared\AIEN18\Data\xxx.tgz ubuntu@ip位置:/home/ubuntu
2. 由FileZilla上傳(安裝openssh套件後，只要有sftp服務就能用FileZilla!)
  - 主機ip : 虛擬機ip
  - 使用者名稱 : ubuntu
  - port : 22

# Debian Package
Debian套件名稱由3部分組成: 套件名稱、版本編號、核心型號 : 主版本.次版本.修補-套件release
套件的下載位置稱為倉庫，在系統的位置是:  
1. /etc/apt/sources.list
2. /etc/apt/sources.list.d/*.list

apt 為新版輕量級的套件管理指令，傳統套件管理指令為 apt-get , apt-cache , ...   
更新套件清單 : apt udate  
套件升級 : apt upgrade  
dpkg 套件管理指令:
  - dpkg -l : 列出所有安裝的套件
  - dpkg -S : 尋找指定套件
  - dpkg -L : 列出套件內所有檔案

搜尋相關套件 : apt search 'python' ... 會連說明也搜尋
搜尋相關套件 : apt search --names-only 'python' ... 只搜尋套件名稱
套件移除 : apt purge xxx 
相依性套件移除 : apt autoremove

# 檔案權限
ls -l可查看有權限觀測檔案
Linux會以一列數字+符號呈現特定檔案的權限:  
[檔案類型][存取權限][SE Linux Context][Links][Owner][Group][Size][tstamp][file Name]
e.g. -rw-r--r--.1 root root 70868 Nov 13 12:54 install.log

檔案類型如下:
  - -: 一般檔案
  - d: 目錄
  - l: symbolic links
  - b: block special files 
  - c: character special files

存取權限如下(以三個符號為一組):
  - User - Group - OtherUser
  - rwx為 read write execute

三種行動的定義如下:
  - 檔案 :
    > Read : 可 ll  
    > Write : 可 nano / vim  
    > Execute : 可執行  
  - 目錄 :
    > Read : 可 ll  
    > Write : 可 nano / vim  
    > Execute : 可 cd  
 

# 權限變更
常用權限變更指令包含chmod、chown以及chgrp (使用管理員進行變更)
指令語法 : [chmod/chmod/chown] [u/g/o/a][+/-][r/w/x] 檔案
其中:
  - u為使用者，g為group，o為others，a為all全部角色
  - 加號和減號為新增或刪除功能符號
  - r/w/x即read/write/excute權限，可複選!

chown 帳號:群組 資料  
e.g. chown -R  hadoop:ABC hadoop-3.1.0/  => 一次性變更目錄內所有檔案的擁有者  

gpasswd 可新增使用者到特定群組，例如: gpasswd -a ubuntu docker  
passwd 帳號名稱 : 可變更該帳號密碼
cat /etc/passwd : 放置所有帳號資訊的地方
cat /etc/shadow : 密碼放置的地方

加入使用者到群組內: 
  - adduse hadoop
  - usermod -G G1,G2,G3 peter : 把peter加到G1,G2,G3群組內
  - groups 使用者 : 顯示使用者屬於哪些群組

切換使用者 : su - xxx

# 啟動相關
開機方式: BSD style > Sysv style > Upstart style(Redhat) > Systemd style(Ubuntu)
runlevel : 查看上一次 & 當前的runlevel(沒有則顯示N)
  - 0 : system halt
  - 1 : single user mode
  - 3(24) : 已完整開機(非圖形介面)
  - 5 : 已完整開機(圖形介面)
  - 6 : 系統重啟

# 網路維護
ip addr show : 只看到有網卡的ip
ip link show : 可看到所有網卡
ip route list :
lsof -nPi : 查詢網路服務

網路設定檔位置:
1. server : /etc/netplan/50-cloud-init.yaml
2. Desktop : /etc/netplan/01-network-manager-all.yaml

控制網路的檔案(用 systemctl list-unit-files | grep -i 'networkd'):
1. server : networkmanager
2. Desktop : networkd

# 變更主機名稱
到 /etc/cloud/cloud.cfg nano這個檔案，找到preserve_hostname改為 true/false  
hostname -i : show ip  
hostname -f : show "正規fgdn"主機名稱  
