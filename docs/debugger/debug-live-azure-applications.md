---
title: 偵錯即時 ASP.NET Azure 應用程式
description: 了解如何設定貼齊點與檢視快照集與快照集偵錯工具。
ms.custom: ''
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- azure
ms.openlocfilehash: f5f9b7e700ff21bac570cf8545207bb75fda820e
ms.sourcegitcommit: cdcbf254db737d42275e95de4ffc4f8c14e87e00
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57428735"
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>偵錯即時 ASP.NET Azure 應用程式使用快照集偵錯工具

您感興趣的程式碼執行時，快照集偵錯工具會在生產應用程式的快照集。 若要指示偵錯工具擷取快照集，您可以在程式碼中設定快照點和記錄點。 偵錯工具可讓您清楚了解發生什麼問題，而不會影響實際執行應用程式的流量。 快照集偵錯工具可協助您大幅縮短為解決出現在生產環境之問題所花費的時間。

貼齊點和記錄點類似於中斷點，但與中斷點不同，貼齊點未暫止應用程式叫用時。 一般而言，擷取快照時貼齊點需要 10 到 20 毫秒。

在本教學課程中，您將進行下列作業：

> [!div class="checklist"]
> * 啟動快照集偵錯工具
> * 設定貼齊點與檢視快照集
> * 設定記錄點

## <a name="prerequisites"></a>必要條件

* 快照偵錯工具僅適用於 Visual Studio 2017 Enterprise 15.5 版或更高版本**Azure 開發工作負載**。 (下**個別元件**索引標籤上，您會發現下**偵錯和測試** > **快照偵錯工具**。)

    如果尚未安裝，安裝[Visual Studio 2017 Enterprise 版本 15.5](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)或更新版本。 如果您從舊版的 Visual Studio 2017 安裝中更新，執行 Visual Studio 安裝程式，並簽入的快照集偵錯工具元件**ASP.NET 和 web 開發工作負載**。

* 基本或更高版本的 Azure App Service 方案。

* 快照集合適用於 Azure App Service 中執行的下列 Web 應用程式：
  * 執行 .NET Framework 4.6.1 或更新版本的 ASP.NET 應用程式。
  * 在 Windows 上執行 .NET Core 2.0 或更新版本的 ASP.NET Core 應用程式。

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>開啟您的專案，並啟動快照集偵錯工具

1. 開啟您想要的快照集偵錯的專案。

    > [!IMPORTANT]
    > 快照集偵錯，您需要開啟*相同版本的原始程式碼*發行至 Azure App Service。
::: moniker range="vs-2019"

2. 在 [雲端總管] (**檢視 > Cloud Explorer**)，以滑鼠右鍵按一下您的專案部署至 Azure App Service，然後選取**附加快照偵錯工具**。

   ![啟動快照集偵錯工具](../debugger/media/snapshot-launch.png)

    您選取的第一次**附加快照偵錯工具**，系統會提示您在 Azure App Service 上安裝快照偵錯工具網站延伸模組。 此安裝需要重新啟動您的 Azure App Service。

::: moniker-end
::: moniker range=">= vs-2019"
2. 附加快照偵錯工具。 您可以使用數種不同的方法之一：

    * 選擇**偵錯 > 附加快照偵錯工具...**.選取您的專案部署至 Azure App Service 和 Azure 儲存體帳戶，然後再按一下**附加**。

      ![啟動快照集偵錯工具偵錯 功能表](../debugger/media/snapshot-debug-menu-attach.png)

    * 以滑鼠右鍵按一下專案，然後選取**發佈**，然後在發佈頁面上，按一下**附加快照偵錯工具**。 選取您的專案部署至 Azure App Service 和 Azure 儲存體帳戶，然後再按一下**附加**。
    ![啟動快照集偵錯工具，從 [發行] 頁面](../debugger/media/snapshot-publish-attach.png)

    * 在偵錯目標下拉式選單選取**快照集偵錯工具**、 點擊**F5**然後視需要選取 如果您的專案部署至 Azure App Service 和 Azure 儲存體帳戶，然後再按一下**附加**。
    ![啟動快照集偵錯工具，從 [F5] 下拉式清單功能表](../debugger/media/snapshot-F5-dropdown-attach.png)

    * 使用 [雲端總管] (**檢視 > Cloud Explorer**)，以滑鼠右鍵按一下您的專案部署至 Azure App Service 和選取 Azure 儲存體帳戶，然後按一下**附加快照偵錯工具**。

      ![啟動快照集偵錯工具，從 [雲端總管]](../debugger/media/snapshot-launch.png)

    您選取的第一次**附加快照偵錯工具**，系統會提示您在 Azure App Service 上安裝快照偵錯工具網站延伸模組。 此安裝需要重新啟動您的 Azure App Service。
::: moniker-end

   Visual Studio 現在是在快照集偵錯模式中。

  > [!NOTE]
  > Application Insights 網站延伸模組也支援快照集偵錯。 如果您遇到 「 網站過時的延伸模組 」 的錯誤訊息，請參閱[疑難排解秘訣和已知的問題的快照集偵錯](../debugger/debug-live-azure-apps-troubleshooting.md)升級詳細資料。

   ![快照集偵錯模式](../debugger/media/snapshot-message.png)

   **模組**視窗會顯示您的 Azure App Service 的所有模組已都載入時 (選擇**偵錯 > Windows > 模組**若要開啟此視窗)。

   ![核取 [模組] 視窗](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>設定貼齊點

1. 在程式碼編輯器中，按一下您感興趣設定貼齊點的程式碼行旁的左裝訂邊。 請確定它是您知道將會執行的程式碼。

   ![設定貼齊點](../debugger/media/snapshot-set-snappoint.png)

2. 按一下 **開始收集**開啟貼齊點。

   ![開啟貼齊點](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > 您無法逐步檢視快照集時，但您可以將多個貼齊點放在您的程式碼，遵循在不同的幾行程式碼執行。 如果您有多個貼齊點在您的程式碼時，快照集偵錯工具確保對應的快照集是從相同的使用者工作階段。 快照集偵錯工具這樣即使有許多使用者達到您的應用程式。

## <a name="take-a-snapshot"></a>建立快照集

當開啟貼齊點時，它會擷取快照集，每當貼齊點所在的程式碼行執行。 這項執行可能因您的伺服器上的實際要求。 若要強制您的貼齊點按、 移至您的網站瀏覽器檢視，並採取任何動作所需，會導致您叫用的貼齊點。

## <a name="inspect-snapshot-data"></a>檢查快照集的資料

1. 當叫用的貼齊點時，快照集會出現在 [診斷工具] 視窗中。 若要開啟此視窗，選擇**偵錯 > Windows > 顯示診斷工具**。

   ![開啟貼齊點](../debugger/media/snapshot-diagsession-window.png)

1. 按兩下以開啟 程式碼編輯器中的 快照集的貼齊點。

   ![檢查快照集的資料](../debugger/media/snapshot-inspect-data.png)

   從這個檢視中，您可以將滑鼠移至變數，以檢視資料提示方塊中，使用**區域變數**，**監看式**，並**呼叫堆疊**windows，並同時評估運算式。

    在網站本身是仍然即時和終端使用者不會受到影響。 只有一個快照集時，會擷取每個貼齊點上，依預設： 貼齊點在擷取快照集之後會關閉。 如果您想要擷取的貼齊點在另一個快照集，您可以開啟貼齊點上一步，即可**更新集合**。

您也可以將更多的貼齊點新增至您的應用程式，並將其開啟與**更新集合** 按鈕。

**需要協助嗎？** 請參閱[疑難排解和已知的問題](../debugger/debug-live-azure-apps-troubleshooting.md)並[快照集偵錯的常見問題集](../debugger/debug-live-azure-apps-faq.md)頁面。

## <a name="set-a-conditional-snappoint"></a>設定條件式的貼齊點

如果很難重新建立您的應用程式中的特定狀態，請考慮使用條件式的貼齊點是否可以協助。 條件式貼齊點可協助您避免建立快照集，直到應用程式進入所需的狀態，例如當變數只有您想要檢查的特定值。 您可以設定使用運算式，篩選條件，或叫用次數。

#### <a name="to-create-a-conditional-snappoint"></a>若要建立條件式的貼齊點

1. 以滑鼠右鍵按一下 貼齊點圖示 （空心的球），然後選擇 **設定**。

   ![選擇設定](../debugger/media/snapshot-snappoint-settings.png)

1. 在 [貼齊點設定] 視窗中，輸入運算式。

   ![輸入運算式](../debugger/media/snapshot-snappoint-conditions.png)

   在上圖中，只擷取快照的貼齊點時`visitor.FirstName == "Dan"`。

## <a name="set-a-logpoint"></a>設定記錄點

除了貼齊點叫用時，請建立快照集，您也可以設定將訊息記錄的貼齊點 （也就是建立記錄點）。 您可以設定記錄點，而不必重新部署您的應用程式。 記錄點幾乎執行，並不造成任何影響或副作用，您執行的應用程式。

#### <a name="to-create-a-logpoint"></a>若要建立記錄點

1. 以滑鼠右鍵按一下 貼齊點圖示 （藍色六邊形），然後選擇 **設定**。

1. 在 [貼齊點設定] 視窗中，選取**動作**。

    ![建立記錄點](../debugger/media/snapshot-logpoint.png)

1. 在 [**訊息**] 欄位中，您可以輸入您想要記錄的新記錄檔訊息。 您也可以將它們放在大括號內，來評估您的記錄檔訊息中的變數。

    如果您選擇**傳送到輸出視窗**，當到達記錄點時，訊息會出現在 [診斷工具] 視窗。

    ![Diagsession 視窗中的記錄點資料](../debugger/media/snapshot-logpoint-output.png)

    如果您選擇**傳送至應用程式記錄檔**，當叫用的記錄點，則訊息會出現任何位置，您可以看到來自`System.Diagnostics.Trace`(或`ILogger`.NET Core 中)，例如[App Insights](/azure/application-insights/app-insights-asp-net-trace-logs)。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已了解如何使用 App service 的快照集偵錯工具。 若要閱讀有關這項功能的更多詳細資料。

> [!div class="nextstepaction"]
> [快照集偵錯的常見問題集](../debugger/debug-live-azure-apps-faq.md)