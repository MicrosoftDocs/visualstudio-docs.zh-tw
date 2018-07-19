---
title: 將部署到本機資料夾
description: 將應用程式部署至本機資料夾
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: bd477fec033eb75f626401586abfd10c798601ef
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809435"
---
1. 中**方案總管**，以滑鼠右鍵按一下專案節點，然後選取**發佈**(Web form**發佈的 Web 應用程式**)。

    如果您先前已設定任何發行的設定檔**發佈**窗格隨即出現。 按一下 **新的設定檔**。

1. 在 **發行**對話方塊方塊中，選取**資料夾**，按一下**瀏覽**，並建立新的資料夾， **C:\Publish**。

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    Web Form 應用程式中，選擇**自訂**在 [發佈] 對話方塊中，輸入設定檔名稱，然後選擇**確定**。

1. 按一下 **建立設定檔**下拉式清單中 (**發佈**做為預設值)。

1. 在 **發佈** 對話方塊中，按一下**設定**連結，然後再選取**設定** 索引標籤。

1. 若要將組態設定**偵錯**，選取**刪除所有現有的檔案發行前**，然後按一下**儲存**。

    > [!NOTE]
    > 如果您使用的發行組建時，您停用在發行時，偵錯 web.config 檔案中。

1. 按一下 [發行] 。

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")
    
    應用程式發佈**偵錯**的本機資料夾之專案的組態。 進度會顯示在 [輸出] 視窗中。

1. 從 Visual Studio 電腦複製 ASP.NET 專案目錄，設定 ASP.NET 應用程式的本機目錄 (在此範例中， **C:\Publish**) Windows Server 電腦上。 在本教學課程中，我們假設您要手動複製，但您可以使用其他工具，像是 PowerShell、 Xcopy 或 Robocopy。

    > [!CAUTION]
    >  如果您需要對程式碼或重建的變更，您必須重新發行，並重複此步驟。 您複製到遠端電腦的可執行檔必須完全符合您的本機來源和符號。    如果您不這麼做將會收到`cannot find or open the PDB file`警告在 Visual Studio 中，當您嘗試將偵錯的處理序。

1. 在 Windows 伺服器上，確認可以執行應用程式的瀏覽器中開啟應用程式的正確。

    如果應用程式無法正確執行，請安裝在您的伺服器和您的 Visual Studio 電腦上的 ASP.NET 版本之間可能有不相符，或您可能與您的 IIS 或網站設定發生問題。 重新檢查先前的步驟。
