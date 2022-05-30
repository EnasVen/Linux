# 登入與登出
1. 圖形模式
  - 本機桌面登入，當前使用的desktop版
  - 遠端桌面登入(XDMCP)，但效能較差
2. 文字模式
  - 主控台(console)登入，輸入Ctrl+Alt+F3~F6 (RedHat才有到F7)，進去後的tty3其實就是指Ctrl+Alt+F3；使用Ctrl+Alt+F2或F1回原桌面/開機登入介面
  - 遠端終端機(Terminal)登入，使用SSH連線
  - 使用終端機模擬軟體，例如: Putty、MobaXterm、ConEmu或cmder
  - 使用exit或ctrl+d登出，千萬不要按叉叉(x)登出

# 安裝openssh服務
切管理員後輸入 apt install openssh-server
