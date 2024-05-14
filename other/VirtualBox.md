# VirtualBox & ubuntu 安裝 & 設定

## 概述

為了方便模擬客戶環境 1 core/ram 2g/linux 等設定，來設置 VM 跑 

* 下載 VirtualBox 主程式與 ubuntu -22.04.4 映像檔

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

Terminal 叫不出來的話，先手動點 store 更新所有 software

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
$ sudo VBoxClient -–clipboard

====
<! 出問題的話，查一下指令有沒有變>
$ sudo VBoxClient -–help
```

## 參考
[在 VirtualBox 中安裝 Ubuntu 22.04：建立虛擬環境的步驟](https://ithelp.ithome.com.tw/articles/10314329)

[在虛擬機上下載 Ubuntu22.04](https://hackmd.io/@VlKF_DoARpms11MmypZ2lg/howard)

[解決VirtualBox無法雙向複製貼上](https://medium.com/%E8%8A%B1%E5%93%A5%E7%9A%84%E5%A5%87%E5%B9%BB%E6%97%85%E7%A8%8B/%E8%A7%A3%E6%B1%BAvirtualbox%E7%84%A1%E6%B3%95%E9%9B%99%E5%90%91%E8%A4%87%E8%A3%BD%E8%B2%BC%E4%B8%8A-1554d5a81da0)

[VirtualBox 安裝 Ubuntu 時的解析度問題以及設定雙向複製貼上](https://alexspot.tech/operating-system-virtualbox-display-copy-past-problem/#:~:text=%E9%9B%99%E5%90%91%E8%A4%87%E8%A3%BD%E8%B2%BC%E4%B8%8A%20%E6%89%80%E8%AC%82%E7%9A%84%E9%9B%99%E5%90%91%E8%A4%87%E8%A3%BD%E8%B2%BC%E4%B8%8A%EF%BC%8C%E4%B9%9F%E5%8F%AF%E4%BB%A5%E8%AA%AA%E6%98%AF%E5%85%B1%E7%94%A8%E5%89%AA%E8%B2%BC%E7%B0%BF%E3%80%82%20%E6%88%91%E5%80%91%E4%B9%8B%E6%89%80%E4%BB%A5%E6%9C%83%E9%96%8B%E8%99%9B%E6%93%AC%E6%A9%9F%EF%BC%8C%E9%80%9A%E5%B8%B8%E6%98%AF%E5%9C%A8%E4%B8%BB%E6%A9%9F%E9%96%8B%E7%99%BC%E7%9A%84%E6%9D%B1%E8%A5%BF%E6%83%B3%E6%8B%BF%E5%8E%BB%E8%99%9B%E6%93%AC%E6%A9%9F%E8%A9%A6%E3%80%82%20%E4%BD%86%E9%A0%90%E8%A8%AD%E6%98%AF%E6%B2%92%E6%9C%89%E8%BE%A6%E6%B3%95%E9%80%99%E8%A3%A1%E8%A4%87%E8%A3%BD%E9%82%A3%E8%A3%A1%E8%B2%BC%E4%B8%8A%E7%9A%84%EF%BC%8C%E5%9B%A0%E6%AD%A4%E6%88%91%E5%80%91%E8%A6%81%E5%85%88%E4%BE%86%E6%9B%B4%E6%94%B9%E8%83%BD%E5%A4%A0%E5%85%B1%E7%94%A8%E5%89%AA%E8%B2%BC%E7%B0%BF%E7%9A%84%E8%A8%AD%E5%AE%9A%E3%80%82,%E5%BE%9E%20Virtual%20Box%20%E8%A8%AD%E5%AE%9A%E6%9B%B4%E6%94%B9%20%E9%BB%9E%E6%8C%89%E8%99%9B%E6%93%AC%E6%A9%9F%E5%99%A8%E5%BE%8C%EF%BC%8C%E9%80%B2%E5%85%A5%E3%80%8C%E8%A8%AD%E5%AE%9A%E3%80%8D%E7%95%8C%E9%9D%A2%EF%BC%8C%E5%9C%A8%E3%80%8C%E4%B8%80%E8%88%AC%E3%80%8D%E7%9A%84%E8%A8%AD%E5%AE%9A%E4%B8%AD%EF%BC%8C%E6%9C%89%E5%80%8B%E3%80%8C%E9%80%B2%E9%9A%8E%E3%80%8D%E9%A0%81%E7%B1%A4%EF%BC%8C%E5%B0%87%E5%85%B1%E7%94%A8%E5%89%AA%E8%B2%BC%E7%B0%BF%E7%9A%84%E9%81%B8%E9%A0%85%E6%94%B9%E7%82%BA%E3%80%8C%E9%9B%99%E5%90%91%E3%80%8D%E3%80%82)
