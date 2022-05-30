# VMWare
目前版本為VM16，下載位置: https://www.vmware.com/tw/products/workstation-player/workstation-player-evaluation.html  
依據個人電腦OS選擇下載版本，安裝過程可default進行，Keyboard Driver可不勾選(會占用一部分空間)  
通知更新等相關項目也可以不勾選(它會一直跳出通知直到你更新)  

# VMWare優點
1. 跨平台虛擬化
2. 支援Windows/Mac/Linux
3. 支援多guest系統
4. 提供NAT機制
  - 無外部網路ip位置，意思就是外面使用者無法連進來
  - 虛擬機透過DHCP server來取得一個私有ip
  - Host & Guest共享網段，便利性高(portable)

# Ubuntu Desktop
step1 : Google 搜尋 ubuntu iso mirror  
step2 : 尋找NCHC (國家安全網路中心)  
step3 : 找Mirror Location Information  
step4 : 找LTS(Long Term Solution)版本較穩健，進行下載。(據說是偶數年4月發布)  
step5 : 找最大容量的desktop-amd64.iso，即為安裝核心檔
step6 : 啟動VMWare
step7 : 建立虛擬機(+)
step8 : 點Linux，選擇64bit
step9 : 變更名稱(不要點到browse，不然要手動輸入)，指定存放在VMs資料夾內
step10: Max Memory Split : 500GB (這個數字並非硬體要給到500GB，而是有記憶體需求時，慢慢擴展上限)
step11: 點Finish
step12: Edit Virtual Machine Settings (點一下剛創好的虛擬機圖案，不要點兩下，點兩下會直接開啟)
step13: 根據電腦機體好壞決定設定值，這邊以我的MSI GL75筆電為例子:
  - 記憶體最大為16G，配置8G給Memory
  - Processors(核心)請查看主機資訊(Ctrl+Alt+Del)，點選"效能"，右下角的邏輯處理器即為可動用最大核心數(1 core = 2邏輯處理器)，我的電腦是12個，配置2/3過去，也就是8個
  - Display內必須勾選3D加速
  - Graphic欄位就是獨顯配置區，這裡的容量一半透過硬體支付；另一半則透過虛擬機，所以上面Memory配置的時候要記得留一點給圖像處理，我這邊是設定4GB
  - CD/DVD SATA選擇掛載先前下載的desktop-amd64.iso檔案(啟動+完成設定後記得要選上面的Use physical drive完成退片(模擬灌光碟的情境))
step14 : 啟動Ubuntu，開始安裝
step15 : 選擇Install Ubuntu
step16 : Keyboard Layout選擇 English - English(US)
step17 : 下一步Other Options勾選 Download updates while installing ubuntu
step18 : Installation Type - Advanced Settings選擇 Use LVM with the new Ubuntu installation
step19 : 點擊install now > continue開始安裝
step20 : 系統會定位所在地，如果沒定位到會顯示紐約，後面安裝很有可能會失敗
step21 : 輸入帳號名稱與使用者名稱，建議一致
step22 : 安裝完成後系統會提示說要重新啟動，點擊restart now並到 CD/DVD /SATA settings裡面完成退片(如果沒有磁碟機的，例如筆電，則在完成後續設定並關機後再退片) 

# Crucial Settings
1. 將Terminal加到左邊清單列
2. 切換管理員 sudo -i
3. 更新倉庫清單 apt update
4. 升級系統 apt upgrade
5. 重開機 reboot
6. 如果Terminal視窗無法最大化，需要做安裝 : apt install open-vm-tools-desktop
7. 重開機後繼續切換管理員 sudo -i
8. 安裝必要套件 : apt install dkms ; apt install build-essential
9. 檢查核心版本 uname -r
10. 安裝核心header-files (這些在安裝dkms的時候會連帶安裝)
11. 完成上一步後，沒有磁碟機的使用者可以關機，並執行退片

