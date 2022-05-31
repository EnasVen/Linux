# Format
Linux語法格式: command **[-options]** **[arguments]**  
第一提示字元(Primary Prompt):  
  - #代表系統管理員(root)
  - $代表一般使用者
第二提示字元(Secondary Prompt):
  - > 符號代表指令還沒打完

; 代表statement的結束，用來在同一列內使用不同指令

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
- id : 顯示使用資訊(較詳細)
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