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
ms.openlocfilehash: 37963e1ee5b7eeb0d07c36e0abe42c98eb6436fe
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
1. 在**方案總管 中**，以滑鼠右鍵按一下專案節點，然後選取**發行**(Web form**發行 Web 應用程式**)。

2. 在**發行**對話方塊中，選取**資料夾**，按一下 **瀏覽**，並建立新的資料夾， **C:\Publish**。

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    Web Form 應用程式中，選擇 **自訂**在 發行 對話方塊中，輸入設定檔名稱，然後選擇 **確定**。

3. 按一下 [發行] 。

    Visual Studio 將專案發行至資料夾。 進度會顯示在 [輸出] 視窗中。

4. 在**發行**對話方塊中，按一下 [**設定**連結，然後再選取**設定**] 索引標籤。

5. 若要設定的設定**偵錯**，選取**刪除所有現有的檔案發行前**，然後按一下 **儲存**。

    > [!NOTE]
    > 如果您使用的發行組建，您停用偵錯的 web.config 檔案中，當您發行時。

6. 按一下 [發行] 。

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")
    
    應用程式會發佈**偵錯**到本機資料夾專案組態。

5. 從 Visual Studio 電腦複製 ASP.NET 專案目錄到 ASP.NET 應用程式設定的本機目錄 (在此範例中， **C:\Publish**) Windows Server 電腦上。 在本教學課程中，我們假設您要手動複製，但您可以使用其他工具，例如 PowerShell、 Xcopy 或 Robocopy。

    > [!CAUTION]
    >  如果您需要對程式碼或重建的變更，您必須重新發佈，並重複此步驟。 您複製到遠端電腦的可執行檔必須完全符合您的本機來源和符號。    如果您不要這樣將會收到`cannot find or open the PDB file`警告 Visual Studio 中，當您嘗試偵錯的處理序。

6. 在 Windows Server 中，確認可以執行應用程式在您的瀏覽器中開啟應用程式的正確。

    如果應用程式無法正確執行，請在您的伺服器和您的 Visual Studio 電腦上所安裝的 ASP.NET 版本之間可能有不相符，或可能有問題，您的 IIS 或網站設定。 重新檢查先前的步驟。
