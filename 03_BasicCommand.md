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
- id : 顯示使用資訊(較詳細)，uid=0代表管理員;uid=1000代表login帳號
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
- pwd : 印出工作目錄
- cp -r /etc . : copy 整個etc目錄到指定位置(copy目錄要用-r；copy檔案不用)
- scp : secure copy，例如: scp user01@192.168.31.204:/home/user01/xxx.tar.gz
- mv : 移動檔案或者重新命名檔案，例如: mv etc myetc
- rm : 刪除所有資料的目錄(一般移除: rm -r myetc ; 強制移除: rm -rf m myetc) 
- cat : 列出指定檔案內容(資料量大請勿使用)，例如: cat /etc/os-release (查作業系統版本)；cat /etc/lsb-release (查Linux standard base e.g.水母jammy) 
- ls 
  > -a : 包含.開頭的檔案
  > -A : 不包含.開頭的檔案
  > -d : 只列出資料夾
  > -h : human readable
  > -i : 每個檔案顯示標號
  > -l : 結果以長形資料呈現(list)
  > -R : 遞迴列出
2014年以後發表的Linux大多使用systemd風格開機且只有login帳號能切管理員


