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
ms.openlocfilehash: b6ceee76d8c24ccddb41e47c0865d96c79e6fc32
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249874"
---
1. 在 [ **方案 Explorer**] 中，以滑鼠右鍵按一下專案節點，然後選取 [ **發行** (的 Web 表單、 **發佈 web 應用程式**) 。

    如果您之前已設定任何發行設定檔，[發行] 窗格會隨即出現。 按一下 [ **新增設定檔**]。

1. 在 [ **發行** ] 對話方塊中，選取 [ **資料夾**]、按一下 **[流覽]**，然後建立新的資料夾 **C:\Publish**。

   ::: moniker range=">=vs-2019"

   :::image type="content" source="../media/vs-2019/remotedbg-publish-local.png" alt-text="Visual Studio 中 [挑選發佈目標] 對話方塊的螢幕擷取畫面，其中選取了 [C:\Publish] 資料夾做為發佈目標。":::

   按一下 **[完成]** 以儲存發行設定檔。
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![Visual Studio 中 [挑選發佈目標] 對話方塊的螢幕擷取畫面，其中選取了 [bin\Release\Publish] 資料夾做為發佈目標。](../media/remotedbg_publish_local.png)
   針對 Web Forms 應用程式，請在 [發行] 對話方塊中選擇 [ **自訂** ]，輸入設定檔名稱，然後選擇 **[確定]**。

   按一下下拉式清單中的 [ **建立設定檔** ] (**發佈** 是) 的預設值。
   ::: moniker-end

1. 切換至 debug 設定。

   ::: moniker range=">=vs-2019"
   選擇 [ **編輯** ] 以編輯設定檔，然後選擇 [ **設定**]。 選擇 [ **Debug** ] 設定，然後選擇 [檔案 **發行** 選項] 下的 [**移除目的地的其他** 檔案]。
   ::: moniker-end
   ::: moniker range="vs-2017"
   在 [**設定**] 對話方塊中，按一下 [**下一步]** 來啟用偵錯工具，選擇 **調試** 程式設定，然後選擇 [檔案 **發行** 選項] 下的 [**移除目的地的其他** 檔案]。
   ::: moniker-end

   > [!NOTE]
   > 如果您使用發行組建，您可以在發行時停用 *web.config* 檔案中的調試。

1. 按一下 [發佈] 。

    ![[發行] 對話方塊中 [設定] 索引標籤的螢幕擷取畫面。 [設定] 設定為 [Debug]，並選取 [發行] 按鈕。](../media/remotedbg_publish_debug_config.png)

    應用程式會將專案的 **Debug** 設定發行至本機資料夾。 進度會顯示在 [輸出] 視窗中。

1. 將 ASP.NET 專案目錄從 Visual Studio 電腦複製到為 ASP.NET 應用程式設定的本機目錄 (在此範例中，在 Windows Server 電腦上 **C:\Publish**) 。 在本教學課程中，我們假設您是手動複製，但您可以使用 PowerShell、Xcopy 或 Robocopy 等其他工具。

    > [!CAUTION]
    > 如果您需要變更程式碼或重建，則必須重新發佈並重複此步驟。 您複製到遠端電腦的可執行檔必須完全符合您的本機來源和符號。 如果您沒有這麼做， `cannot find or open the PDB file` 當您嘗試將程式進行偵錯工具時，將會在 Visual Studio 中收到警告。

1. 在 Windows Server 上，確認您可以在瀏覽器中開啟應用程式，以正確地執行應用程式。

    如果應用程式無法正確執行，則在您的伺服器上安裝的 ASP.NET 版本與您的 Visual Studio 電腦可能會有不相符的情況，或者您的 IIS 或網站設定可能有問題。 重新檢查先前的步驟。
