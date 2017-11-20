---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 27cff46f5a68ef28f247aa159a2b8be5db56b0fe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
如果您安裝 Web Deploy 使用 Web Platform Installer，您可以部署應用程式直接從 Visual Studio。

1. 啟動 Visual Studio 系統管理員權限，並重新開啟專案。

    使用 Web Deploy 部署應用程式，需要系統管理員權限。

2. 在 [方案總管] ，以滑鼠右鍵按一下專案節點，然後選取 [發行] 。

3. 如**選取發行目標**，選取**IIS，FTP 等**按一下**發行**。

    ![RemoteDBG_Publish_IISl](../media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

4. 輸入您的 IIS 設定更正組態參數。

    ![RemoteDBG_Publish_WebDeployl](../media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    如果未解析主機名稱，當您嘗試驗證中的下一個步驟**伺服器**文字方塊中，IP 位址再試一次。 包含`http://`中的前置詞為**伺服器**欄位。  請確定您在使用中的連接埠 80**伺服器**文字 方塊中，並確定已在防火牆中開啟連接埠 80。

6. 按一下**下一步**，選擇**偵錯**組態，然後選擇 **移除目的端的其他檔案**下**檔案發行**選項。

    > [!NOTE]
    > 如果您選擇發行組態，您停用偵錯的 web.config 檔案中，當您發行時。

5. 按一下**Prev**，然後選擇 **驗證**。 如果驗證的連接設定，您可以嘗試發行。

6. 按一下**發行**發行應用程式。

    [輸出] 索引標籤會顯示您是否已成功，發佈，並且您的瀏覽器，然後開啟應用程式。

    如果您收到錯誤 Web Deploy 一提，重新檢查的 Web Deploy 的安裝步驟，並確定正確的通訊埠已開啟 （Web Deploy 也需要連接埠 8172 開啟伺服器上）。

    如果應用程式部署成功，但無法正確地執行，可能是您的 IIS 設定、 ASP.NET 安裝或您的網站設定發生問題。 在 Windows Server 中，開啟更具體的錯誤訊息，請從 IIS 網站，然後重新檢查先前的步驟。