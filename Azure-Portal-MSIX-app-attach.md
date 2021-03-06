# 在 Azure Portal 設定 MSIX 應用程式連接

- 在主機集區中新增 MSIX 套件，填入 MSIX 映像檔的路徑，註冊選擇隨需，並將狀態點選使用中，並儲存<br>
![GITHUB](https://github.com/BrianHsing/Azure-Virtual-Desktop/blob/master/MSIX/msix-app-attach.png "msix-app-attach")<br>
- 在應用程式群組中的完整桌面類型新增 MSIX 套件，輸入應用程式名稱後儲存<br>
![GITHUB](https://github.com/BrianHsing/Azure-Virtual-Desktop/blob/master/MSIX/applicationgroup-desktop-msix.png "applicationgroup-desktop-msix")<br>
- 在應用程式群組中的遠端應用程式類型新增 MSIX 套件，輸入應用程式名稱後儲存<br>
![GITHUB](https://github.com/BrianHsing/Azure-Virtual-Desktop/blob/master/MSIX/applicationgroup-remoteapp-msix.png "applicationgroup-remoteapp-msix")<br>
- 使用 Web / Client App 登入 AVD<br>
![GITHUB](https://github.com/BrianHsing/Azure-Virtual-Desktop/blob/master/MSIX/msrdc-msix.png "msrdc-msix")<br>
- 使用完整桌面開啟 Notepad++<br>
![GITHUB](https://github.com/BrianHsing/Azure-Virtual-Desktop/blob/master/MSIX/msrdc-desktop-notepad.png "msrdc-desktop-notepad")<br>
- 使用遠端應用程式開啟 Notepad++<br>
![GITHUB](https://github.com/BrianHsing/Azure-Virtual-Desktop/blob/master/MSIX/msrdc-remoteapp-notepad.png "msrdc-remoteapp-notepad")<br>

回到[Azure 虛擬桌面](https://github.com/BrianHsing/Azure-Virtual-Desktop)。<br>