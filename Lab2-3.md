# Lab2 - 使用 Azure VM ADDS 搭配 Azure Files 建立 WVD
## Lab2-3.建立 Azure Files 並啟用 Active Directory 驗證

 - 到 Azure 入口網站中，在搜尋列搜尋儲存體帳戶，並點選<br>
   ![GITHUB](https://github.com/BrianHsing/Azure-Windows-Virtual-Desktop/blob/master/Lab1/storage1.png "storage1")<br>
 - 點選「新增」<br>
   ![GITHUB](https://github.com/BrianHsing/Azure-Windows-Virtual-Desktop/blob/master/Lab1/storage2.png "storage2")<br>
 - 基本的頁籤中，選擇與 Azure AD Domain Services 同樣的訂用帳戶與資源群組，輸入自定義的儲存體帳戶名稱，請注意，請使用小寫與數字且不能重複的名稱。此範例區域選擇東亞，此儲存體是要作為儲存體的容器，所以效能選擇進階，帳戶種類選擇 FileStorage，複寫可以依照情境需求選擇。<br>
   ![GITHUB](https://github.com/BrianHsing/Azure-Windows-Virtual-Desktop/blob/master/Lab1/storage3.png "storage3")<br>
 - 網路的頁籤中，選擇公用端點(所有網路)。如果您有比較嚴謹的存取控管，您可以選擇公用端點，只允許您指定的虛擬網路中的流量存取。這一步，請直接點選下方「檢閱+建立」，完成儲存體帳戶的建立<br>
   ![GITHUB](https://github.com/BrianHsing/Azure-Windows-Virtual-Desktop/blob/master/Lab1/storage4.png "storage4")<br>
 - 開啟 IE 瀏覽器，輸入 https://github.com/Azure-Samples/azure-files-samples/releases 後下載最新版本 AzFilesHybrid.zip，下載後解壓縮<br>
 - 重新回到虛擬機器的頁面，開啟 Powershell ISE<br>
 - 輸入`Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Scope Currentuser`，跳出確認視窗，請選擇 「Yes to All」<br>
 - Powershell ISE 中的路徑移動至完成解壓縮的 AzFilesHybrid 資料夾路徑<br>
   ![GITHUB](https://github.com/BrianHsing/Azure-Windows-Virtual-Desktop/blob/master/Lab2/ada1.png "ada1")<br>
 - 輸入以下指令後，後續跳出的視窗請依序按下「Run once」、「Run once」、「Yes to All」<br>
	```
	.\CopyToPSPath.ps1
	Import-Module -name AzFilesHybrid
	``` 
 - 完成後會提示您重新啟動 Powershell ISE，請關閉後重新啟動，開啟後需要重複做一次一樣的動作<br>
   ![GITHUB](https://github.com/BrianHsing/Azure-Windows-Virtual-Desktop/blob/master/Lab2/ada2.png "ada2")<br>
 - Powershell ISE 中的路徑移動至完成解壓縮的 AzFilesHybrid 資料夾路徑<br>
 - 輸入以下指令後，後續跳出的視窗請依序按下「Run once」、「Run once」、「Yes to All」<br>
	```
	.\CopyToPSPath.ps1
	Import-Module -name AzFilesHybrid
	``` 
 - 完成後請輸入`Connect-AzAccount`，輸入您具有 Azure AD Global admin 權限的管理者帳號密碼<br>
 - 請輸入以下指令，其中 resourceGroup、OU、StorageAccountName，會替換成您實際使用的名稱<br>
   	```
	$resourceGroup = '資源群組名稱'
	$OU = 'WVD'
	$StorageAccountName = '儲存體帳戶名稱'

	join-AzStorageAccountForAuth -ResourceGroupName $resourceGroup `
                             -Name $StorageAccountName `
                             -DomainAccountType "ComputerAccount" `
                             -OrganizationalUnitName $OU
	``` 
 - 完成後 Powershell ISE 會顯示如下<br>
   ![GITHUB](https://github.com/BrianHsing/Azure-Windows-Virtual-Desktop/blob/master/Lab2/ada3.png "ada3")<br>
 - 您也可以在 Azure 入口網站選擇剛建立好的儲存體帳戶，在左邊欄位的設定類別中選擇組態，並檢查 Active Directory 網域服務 (AD DS) 為「已啟用」<br>
   ![GITHUB](https://github.com/BrianHsing/Azure-Windows-Virtual-Desktop/blob/master/Lab2/ada4.png "ada4")<br>
 - 在左邊欄位的檔案服務類別中選擇檔案共用，並新增檔案共用，輸入您的檔案共用名稱與容量，容量介於 100 GiB 到 102,400 GiB。點選建立。<br>
   ![GITHUB](https://github.com/BrianHsing/Azure-Windows-Virtual-Desktop/blob/master/Lab1/storage6.png "storage6")<br>
 - 點選剛建立的檔案共用，選擇左欄存取控制(IAM)後，選擇新增，指派儲存體檔案資料 SMB 共同參與者角色，並選取 Lab1-2 所建立的使用者，儲存。<br>
   ![GITHUB](https://github.com/BrianHsing/Azure-Windows-Virtual-Desktop/blob/master/Lab1/storage7.png "storage7")<br>
 - 點選左欄設定類別中的屬性，查看檔案共用路徑，此範例的路徑為「//stor1013.file.core.windows.net/userprofile」，在 Lab 會使用到此路徑，其中stor1013、userprofile 應該會依照您實際輸入的名稱顯示。<br>
   ![GITHUB](https://github.com/BrianHsing/Azure-Windows-Virtual-Desktop/blob/master/Lab1/storage8.png "storage8")<br>
 完成後，請[前往 Lab5](https://github.com/BrianHsing/Azure-Windows-Virtual-Desktop/blob/master/Lab5.md)。<br>