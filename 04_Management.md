# FHS
FHS為File Hierarchy Standard的縮寫，規範每個檔案應該存放的位置，了解這個檔案架構就能理解目錄的意義。  
依照FHS標準，指令存放位置分類如下:
1. **系統開機用**
  - /usr/bin , /usr/sbin
2. **自行編譯程式**
  - /usr/local/bin , /usr/local/sbin
3. **3rd Party Free軟體**
  - /usr/local/軟體/bin , /usr/local/軟體/sbin 
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
列出已安裝套件 : dpkg -l  
搜尋相關套件 : apt search 'python' ... 會連說明也搜尋
搜尋相關套件 : apt search --names-only 'python' ... 只搜尋套件名稱
套件移除 : apt purge xxx 
相依性套件移除 : apt autoremove
