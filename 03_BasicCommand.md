# Format
Linux語法格式: command **[-options]** **[arguments]**  
options參數 目的為改變指令執行的方式
  -   Unix style : 單一dash字元，例如: ls -l /usr
  -   GNU style : 雙dash字元，例如: df --human-readable
  -   BSD style : 空格字元，例如: ps a (注意和ps -a不同)
  -   特殊 style : 例如: find / -name 'p*'

arguments參數 目的為改變指令處理的對象
  - ls -l /temp : 查看temp目錄的內容

第一提示字元(Primary Prompt):  
  - #代表系統管理員(root)
  - $代表一般使用者
第二提示字元(Secondary Prompt):
  - > 符號代表指令還沒打完

; 代表statement的結束，用來在同一列內使用不同指令
Linux內，綠色為執行檔；藍色為可執行捷徑；深藍色為目錄；紅色為壓縮檔

# Linux Manual(操作手冊)
輸入指令man可以查看各類指令用途與細節，左上角的數字為手冊分類:  
(1) 代表使用者可操作的指令
(2) 代表系統核心可呼叫的指令
(3) 代表常用的func.與library
(4) 代表裝置檔案的說明
(5) 代表設定檔格式
(6) 遊戲(Games)
(7) 雜項
(8) 系統管理相關指令

操作按鍵:  
1. 空白建 : 下一頁
2. Page Up/Down : 向上/下一頁
3. g / Home : 回到第一頁
4. G / End : 到最後一頁
5. / : 搜尋指定字串
6. n / N : 找上一個/下一個搜尋結果
7. q : 結束

# 基本指令
- cd : 前往指定路徑目錄
- pwd : 顯示目前路徑
- id : 顯示使用資訊(較詳細)，uid=0代表管理員;uid=1000代表login帳號
- uname -r : 查看核心版本
- ls -l /etc/os-release : 查看Linux版本
- whoami : 只顯示使用者名稱
- date : 顯示時間日期
- claer : 清空螢幕
- history : 顯示下過的指令(使用!<command number>來執行特定指令)
- exit : 登出
- sudo : 用來切換使用者為管理員，輸入後需要輸入密碼(非root密碼)，-i代表使用login shell
- shutdown -h : default 1分鐘後關機(只有ubuntu15.10後可以用login帳號關機)
- poweroff : 等價於shutdown now，立刻關機
- shutdown -r : 1分鐘後重新開機
- reboot : 等價於shutdown now，立刻關機
- ip route list : 查看所有ip
- ip addr show : 查看網路地址
- lsof -nPi : 查看TCP/IP socket
- df -h : 查看現有資源使用狀況
- du : 顯示目錄大小，例如: du -sh /* 顯示跟目錄下所有目錄容量
- pwd : 印出工作目錄
- cp -r /etc . : copy 整個etc目錄到指定位置(copy目錄要用-r；copy檔案不用)
- scp : secure copy，例如: scp user01@192.168.31.204:/home/user01/xxx.tar.gz
- mv : 移動檔案或者重新命名檔案，例如: mv etc myetc
- rm : 刪除所有資料的目錄(一般移除: rm -r myetc ; 強制移除: rm -rf m myetc) 
- mkdir/rmdir : 建立/移除空資料夾
- cat : 列出指定檔案內容(資料量大請勿使用)，例如: cat /etc/os-release (查作業系統版本)；cat /etc/lsb-release (查Linux standard base e.g.水母jammy) 3
- which/whereis : 找出指令全路徑(which只找執行檔)
- locate : 找出具備特定條件的檔名，例如: locate ABC
- find : 尋找路徑下符合條件的所有檔案，例如: find -name xxx.txt -typr d/f/l (d為目錄；f為檔案；l為捷徑)
- ls 
  > -a : 包含.開頭的檔案  
  > -A : 不包含.開頭的檔案  
  > -d : 只列出資料夾  
  > -h : human readable  
  > -i : 每個檔案顯示標號  
  > -l : 結果以長形資料呈現(list)  
  > -R : 遞迴列出  
- grep
  > -n : 顯示行號  
  > -i : 不分大小寫去搜尋  
  > -v : 反向搜尋，不包含的全部顯示  
  > -E : 判讀regexp  
  > 判斷 windows換行 : grep -m | $'\r'  

2014年以後發表的Linux大多使用systemd風格開機且只有login帳號能切管理員

# Redirection & Pipe
使用 > 將結果儲存到某個檔案，重複使用會overwrite原檔案；如果要不覆蓋原檔，需要用 >> 符號，例如: ls /usr > output.txt 或者 history > tmpCommands.txt  
使用 | 將結果丟入下一個運算式，例如: dpkg -l | grep '^python'  
e.g. cp -r /etc/xxx > err.txt (把error message丟到txt)
e.g. cp -r /etc > dev/null (直接丟掉不顯示在terminal的方法)

# Data Manipulation
除了上面的cat，常用的操作指令還有:
 - less : 檢視一部分的資料，用於當原始資料很多的時候，不能使用cat
 - head : 查看前幾筆資料，例如: head -1 xxx.csv | tr ';' '\n' | wc -l
 - tail : 查看後幾筆資料
 - wc : 看資料的domension，例如: wc -l/-w/-c計算# word rows/words/bytes
 - cut : 切資料，例如: head -1 xxx.csv | cut -d ';' '' -f 1 , 3-4 , 7-27
 - tr : 取代，例如: tr ';' '-'
 - 萬用字元 : *(符合所有字元) 與 ?(符合單一字元)
 - touch : touch file0{1,2,3} 將產生 file01 , file02 , file03 的空檔案 ...Brace Expansion

# 壓縮與解壓縮
以下指令可以獲得並處理壓縮檔:
  - wget : 從指定網址下載source code、tgz壓縮檔、package...etc
  - tar -tvf xxx.tar.gz : 查看 xxx 壓縮檔的內容
  - tar -xvf xxx.tar.gz : 解壓縮 xxx 壓縮檔
  - unzip -l xxx.zip : 查看 xxx 壓縮檔的內容
  - unzip xxx.zip : 解壓縮zip檔
