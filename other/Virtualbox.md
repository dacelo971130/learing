# VirtualBox & ubuntu 安裝 & 設定

* 官網下載 virtualBox & ubuntu -22.04.4

## 建立虛擬機

打開介面選擇新增，選擇專家模式，安裝 ubuntu 並選擇映像檔路徑
  
* 名稱 : ubuntu_VM or 
* 虛擬記憶體 2G 以上

## 設定虛擬硬碟

* 選擇 "VDI (VirtualBox Disk Image)" 作為硬碟類型。
* 選擇 "Dynamically allocated" 以節省磁碟空間。
* 設定硬碟的大小，建議至少 20GB。
* cpu要兩顆以上

## 其他

Terminal 叫不出來的話，先手動點 store 更新

調整視窗

```
$ xrandr -s 1920x1080
```

下載最新套件

```
$ sudo apt-get update
```

解決雙向複製問題

```
$ sudo apt install dkms build-essential linux-headers-generic
```

裝置>插入Guest Additions CD映像

```
$ sudo apt install virtualbox-guest-x11 
$ sudo VBoxClient –clipboard 
```

## 參考
[在 VirtualBox 中安裝 Ubuntu 22.04：建立虛擬環境的步驟](https://ithelp.ithome.com.tw/articles/10314329)

[在虛擬機上下載 Ubuntu22.04](https://hackmd.io/@VlKF_DoARpms11MmypZ2lg/howard)

[解決VirtualBox無法雙向複製貼上](https://medium.com/%E8%8A%B1%E5%93%A5%E7%9A%84%E5%A5%87%E5%B9%BB%E6%97%85%E7%A8%8B/%E8%A7%A3%E6%B1%BAvirtualbox%E7%84%A1%E6%B3%95%E9%9B%99%E5%90%91%E8%A4%87%E8%A3%BD%E8%B2%BC%E4%B8%8A-1554d5a81da0)
