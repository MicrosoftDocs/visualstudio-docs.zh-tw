---
ms.openlocfilehash: 69f4f4c2b55670d510652b44a203b9f0eafcc53a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "68143526"
---

1. 關閉並重新開啟 IIS 管理主控台，以在 UI 中顯示更新的組態選項。

2. 在 IIS 中，以滑鼠右鍵按一下 [預設的網站]****，然後選擇 [部署]**** > [設定 Web Deploy 發行]****。

    ![設定 Web Deploy 組態](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

3. 查看 [設定 Web Deploy 發行]**** 對話方塊中的設定。

4. 按一下 [設定]****。

    在 [結果]**** 面板中，輸出顯示會將存取權限授與指定的使用者，並已在對話方塊顯示的位置中產生副檔名為 *.publishsettings* 的檔案。

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

    根據您的 Windows Server 和 IIS 組態，您會在 XML 檔案中看到不同的值。 以下是您會看到有關這些值的一些詳細資料：

   * `publishUrl` 屬性中所參考的 *msdeploy.axd* 檔案是針對 Web Deploy 動態產生的 HTTP 處理常式檔案 (基於測試目的，`http://myhostname:8172` 通常也適用)。
   * `publishUrl` 連接埠設定為連接埠 8172，這是 Web Deploy 的預設值。
   * `destinationAppUrl` 連接埠設定為連接埠 80，這是 IIS 的預設值。
   * 如果您無法使用主機名稱連線到 Visual Studio 中的遠端主機 (在稍後步驟中)，請測試 IP 位址以取代主機名稱。

     > [!NOTE]
     > 如果您要發行至 Azure VM 上執行的 IIS，您必須開啟 Web Deploy 及網路安全性群組中的 IIS 連接埠。 如需詳細資訊，請參閱[安裝及執行 IIS](/azure/virtual-machines/windows/quick-create-portal#install-web-server)。

5. 將此檔案複製到您執行 Visual Studio 的電腦。
