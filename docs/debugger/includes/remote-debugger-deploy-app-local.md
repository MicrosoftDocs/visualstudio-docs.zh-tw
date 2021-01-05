---
title: 部署至本機資料夾
description: 將應用程式部署到本機資料夾
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 1d049bc8b74b83028e04fe92e7ce96f45907d042
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/24/2020
ms.locfileid: "97762592"
---
1. 在 [ **方案總管** 中，以滑鼠右鍵按一下專案節點，然後選取 [ **發佈** (以進行 Web Form、 **發佈 Web 應用程式**) 。

    如果您之前已設定任何發行設定檔，[發行] 窗格會隨即出現。 按一下 [ **新增設定檔**]。

1. 在 [ **發行** ] 對話方塊中，選取 [ **資料夾**]、按一下 **[流覽]**，然後建立新的資料夾 **C:\Publish**。

    ![[挑選發佈目標] 對話方塊的螢幕擷取畫面，其中已選取 [bin\Release\Publish Visual Studio] 資料夾做為發佈目標。](../media/remotedbg_publish_local.png)

    針對 Web Form 應用程式，請在 [發行] 對話方塊中選擇 [ **自訂** ]，輸入設定檔名稱，然後選擇 **[確定]**。

1. 按一下下拉式清單中的 [ **建立設定檔** ] (**發佈** 是) 的預設值。

1. 在 [ **發行** ] 對話方塊中，按一下 [ **設定** ] 連結，然後選取 [ **設定** ] 索引標籤。

1. 將設定設為 [ **Debug**]，選取 [ **發行前刪除所有現有** 的檔案]，然後按一下 [ **儲存**]。

    > [!NOTE]
    > 如果您使用發行組建，您可以在發行時停用 web.config 檔案中的調試。

1. 按一下 [發佈] 。

    ![[發行] 對話方塊中 [設定] 索引標籤的螢幕擷取畫面。 [設定] 設定為 [Debug]，並選取 [發行] 按鈕。](../media/remotedbg_publish_debug_config.png)

    應用程式會將專案的 **Debug** 設定發行至本機資料夾。 進度會顯示在 [輸出] 視窗中。

1. 將 ASP.NET 專案目錄從 Visual Studio 電腦複製到針對 ASP.NET 應用 (程式設定的本機目錄，在此範例中為 **C:\Publish**) （在 Windows Server 電腦上）。 在本教學課程中，我們假設您是手動複製，但您可以使用 PowerShell、Xcopy 或 Robocopy 等其他工具。

    > [!CAUTION]
    > 如果您需要變更程式碼或重建，則必須重新發佈並重複此步驟。 您複製到遠端電腦的可執行檔必須完全符合您的本機來源和符號。    如果您沒有這麼做， `cannot find or open the PDB file` 當您嘗試對處理常式進行偵錯工具時，將會在 Visual Studio 中收到警告。

1. 在 Windows Server 上，確認您可以在瀏覽器中開啟應用程式，以正確地執行應用程式。

    如果應用程式無法正確執行，則在您的伺服器上安裝的 ASP.NET 版本與 Visual Studio 電腦上可能會有不相符的情況，否則您的 IIS 或網站設定可能會有問題。 重新檢查先前的步驟。
