
1. 關閉並重新開啟 IIS 管理主控台，在 UI 中顯示更新的組態選項。

1. 在 IIS 中，以滑鼠右鍵按一下**Default Web Site**，選擇**部署** > **設定 Web 部署發行**。

    ![設定 Web Deploy 設定](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

1. 在**設定 Web 部署發行**對話方塊方塊中，檢查設定。

1. 按一下**安裝**。

    在**結果**面板中，輸出中顯示的存取權限授與指定的使用者，而且副檔名 *.publishsettings*已顯示於對話方塊中的位置中產生檔案的副檔名方塊。

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    根據您的 Windows Server 和 IIS 設定，您會看到不同的 XML 檔案中的值。 以下是一些詳細資料，您所看到的值：

    * *Msdeploy.axd*檔案中參考`publishUrl`屬性為動態產生的 HTTP 處理常式檔案 Web deploy。 (基於測試目的，`http://myhostname:8172`通常也運作。)
    * `publishUrl`連接埠設定為連接埠 8172，Web deploy 預設值。
    * `destinationAppUrl`連接埠設定為連接埠 80，此為 IIS 的預設值。
    * 如果無法連線至遠端主機使用的主機名稱 （在稍後步驟中） 的 Visual Studio 中，測試來取代主機名稱的 IP 位址。

    > [!NOTE]
    > 如果您要發行至 Azure VM 上執行之 IIS，您必須開啟網路安全性群組中的 Web Deploy 與 IIS 通訊埠。 如需詳細資訊，請參閱[安裝和執行的 IIS](/azure/virtual-machines/windows/quick-create-portal#open-port-80-for-web-traffic)。

1. 將這個檔案複製到執行 Visual Studio 的電腦。
