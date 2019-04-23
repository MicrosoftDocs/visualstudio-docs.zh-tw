---
title: 針對即時 ASP.NET Azure 虛擬機器和 Azure 虛擬機器擴展集進行偵錯
description: 了解如何設定快照集，以及使用快照偵錯工具檢視快照集。
ms.custom: ''
ms.date: 02/06/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 2880b8bee25a79f5f182043ffed5c50c4512d033
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59663173"
---
# <a name="debug-live-aspnet-apps-on-azure-virtual-machines-and-azure-virtual-machine-scale-sets-using-the-snapshot-debugger"></a>使用快照偵錯工具針對 Azure 虛擬機器上的即時 ASP.NET 應用程式和 Azure 虛擬機器擴展集進行偵錯

[快照偵錯工具] 會在您感興趣的程式碼執行時，擷取實際執行應用程式的快照集。 若要指示偵錯工具擷取快照集，您可以在程式碼中設定快照點和記錄點。 偵錯工具可讓您清楚了解發生什麼問題，而不會影響實際執行應用程式的流量。 快照集偵錯工具可協助您大幅縮短為解決出現在生產環境之問題所花費的時間。

快照點和記錄點與中斷點很相似，但和中斷點不的是，快照點不會在叫用時停止應用程式。 一般而言，在快照點擷取快照集時需要 10 到 20 毫秒。

在本教學課程中，您將進行下列作業：

> [!div class="checklist"]
> * 啟動快照偵錯工具
> * 設定快照點及檢視快照
> * 設定記錄點

## <a name="prerequisites"></a>必要條件

* Azure 虛擬機器 (VM) 和 Azure 虛擬機器擴展集的快照集偵錯工具僅適用於 Visual Studio 2019 企業版或更高版本**Azure 開發工作負載**。 (您可以在 [個別元件] 索引標籤下的 [偵錯和測試] > [快照偵錯工具]底下找到它。)

    如果尚未安裝，安裝[Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/)。

* 快照集集合適用於下列的 Azure 虛擬 Machines\Virtual 機器擴展集 web 應用程式：
  * 執行 .NET Framework 4.6.1 或更新版本的 ASP.NET 應用程式。
  * 在 Windows 上執行 .NET Core 2.0 或更新版本的 ASP.NET Core 應用程式。

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>開啟專案並啟動快照偵錯工具

1. 開啟想要進行快照集偵錯的專案。

    > [!IMPORTANT]
    > 快照集偵錯，您需要開啟*相同版本的原始程式碼*發行到您 Azure 虛擬 Machine\Virtual 機器擴展集的服務。

1. 選擇 [偵錯] > [附加快照偵錯工具]。選取 Azure 虛擬 Machine\Virtual 機器擴展集部署至您的 web 應用程式和 Azure 儲存體帳戶，然後再按一下**附加**。

      ![從 [偵錯] 功能表啟動快照偵錯工具](../debugger/media/snapshot-debug-menu-attach.png)

      ![選取 Azure 資源](../debugger/media/snapshot-select-azure-resource-vm.png) 

    > [!IMPORTANT]
    > 第一次為 VM 選取 [附加快照偵錯工具] 時，IIS 會自動重新啟動。
    > 您選取的第一次**附加快照偵錯工具**虛擬機器擴展集，需要手動升級每個虛擬機器擴展集執行個體。

    **模組**的中繼資料將不會一開始就啟動，請瀏覽至 Web 應用程式，[開始收集] 按鈕會變成作用中。 Visual Studio 現在已經處於快照集偵錯模式。

   ![快照集偵錯模式](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > Application Insights 網站延伸模組也支援快照集偵錯。 如果遇到「網站延伸模組過期」錯誤訊息，請參閱[快照集偵錯的疑難排解祕訣與已知問題](../debugger/debug-live-azure-apps-troubleshooting.md)了解升級詳細資料。
    > VMSS 的使用者，才能手動升級之後第一次附加快照偵錯工具的 執行個體都在其虛擬機器擴展集的。

   **模組**視窗會顯示您的 Azure 虛擬 Machine\Virtual 機器擴展集的所有模組已都載入時 (選擇**偵錯 > Windows > 模組**若要開啟此視窗)。

   ![檢查 [模組] 視窗](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>設定快照點

1. 在程式碼編輯器中，按一下所需程式碼行左側的裝訂邊以設定快照點。 確定這是您將執行的程式碼。

   ![設定快照點](../debugger/media/snapshot-set-snappoint.png)

1. 按一下 [開始收集] 以開啟快照點。

   ![開啟快照點](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > 檢視快照點時，您無法逐步檢視，但可以在程式碼中置入多個快照點，隨著不同行的程式碼執行。 如果程式碼中有多個快照點，快照偵錯工具會確定相對應的快照集是來自相同的使用者工作階段。 就算有許多使用者叫用您的應用程式，快照偵錯工具也會這樣做。

## <a name="take-a-snapshot"></a>建立快照集

開啟快照點時，只要執行到包含快照點的程式碼行時，就會擷取快照點。 這可透過伺服器上的實際要求來執行。 若要強制叫用快照點，請移至網站的瀏覽器檢視，並採取可使得系統叫用快照點的任何必要動作。

## <a name="inspect-snapshot-data"></a>檢查快照集資料

1. 叫用快照點時，[診斷工具] 視窗中會顯示快照點。 若要開啟此視窗，請選擇 [偵錯] > [Windows] > [顯示診斷工具]。

   ![開啟快照點](../debugger/media/snapshot-diagsession-window.png)

1. 按兩下快照點以在程式碼編輯器中開啟快照點。

   ![檢查快照集資料](../debugger/media/snapshot-inspect-data.png)

   您可以從這個檢視，將滑鼠移至變數上方以檢視 DataTips、使用 [區域]、[監看式]，以及 [呼叫堆疊] 視窗，也可以評估運算式。

    網站本身是仍然是即時的且使用者不會受到影響。 每個快照點預設只會擷取一個快照集：擷取快照集之後，快照點就會關閉。 如果想要在快照點擷取另一個快照集，可以按一下 [更新集合] 以重新開啟快照點。

您也可以將更多快照點新增至應用程式，並使用 [更新集合] 按鈕將它們開啟。

**需要協助嗎？** 請參閱[疑難排解和已知問題](../debugger/debug-live-azure-apps-troubleshooting.md)與[快照集偵錯的常見問題集](../debugger/debug-live-azure-apps-faq.md)頁面。

## <a name="set-a-conditional-snappoint"></a>設定條件式快照點

如果很難在應用程式中重新建立特定狀態，請考量使用條件式快照點是否能有所幫助。 條件式快照點可協助您避免在應用程式進入所需狀態 (例如當變數有您想要檢查的特定值) 之前建立快照集。 您可以使用運算式、篩選或叫用次數設定條件。

#### <a name="to-create-a-conditional-snappoint"></a>建立條件式快照點

1. 以滑鼠右鍵按一下快照點圖示 (空心球) 並選擇 [設定]。

   ![選擇設定](../debugger/media/snapshot-snappoint-settings.png)

1. 在快照點設定視窗中輸入運算式。

   ![輸入運算式](../debugger/media/snapshot-snappoint-conditions.png)

   在上圖中，只會在 `visitor.FirstName == "Dan"` 時才會建立快照點的快照集。

## <a name="set-a-logpoint"></a>設定記錄點

除了在叫用快照點時建立快照集之外，您也可以設定快照點記錄訊息 (也就是建立記錄點)。 您可以在不需要重新部署應用程式的情況下設定記錄點。 記錄點會以虛擬方式執行，而且不會對執行中的應用程式造成任何影響或副作用。

#### <a name="to-create-a-logpoint"></a>建立記錄點

1. 以滑鼠右鍵按一下快照點圖示 (藍色六邊形) 並選擇 [設定]。

1. 在快照點設定視窗中選取 [動作]。

    ![建立記錄點](../debugger/media/snapshot-logpoint.png)

1. 您可以在 [訊息] 欄位中輸入想要記錄的新記錄訊息。 也可以在記錄訊息中變數的前後加上大括號，以評估它們。

    如果您選擇 [傳送到輸出視窗]，當叫用記錄點時，訊息會出現在 [診斷工具] 視窗中。

    ![[診斷工具] 視窗中的記錄點資料](../debugger/media/snapshot-logpoint-output.png)

    如果您選擇 [傳送到應用程式記錄檔]，當叫用記錄點時，只要可以看到來自 `System.Diagnostics.Trace` (或在 .NET Core 中為 `ILogger`) (例如[應用程式深入解析](/azure/application-insights/app-insights-asp-net-trace-logs)) 之訊息的位置，就會顯示訊息。

## <a name="next-steps"></a>後續步驟

您已經在此教學課程中學到如何針對 Azure 虛擬機器和 Azure 虛擬機器擴展集使用快照偵錯工具。 您可以閱讀和此功能有關的更多詳細資料。

> [!div class="nextstepaction"]
> [快照集偵錯的常見問題集](../debugger/debug-live-azure-apps-faq.md)