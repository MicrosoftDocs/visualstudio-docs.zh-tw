---
title: 即時 ASP.NET Azure 虛擬機器和擴展集
description: 了解如何設定快照集，以及使用快照偵錯工具檢視快照集。
ms.custom: ''
ms.date: 02/06/2019
ms.topic: how-to
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: d1e9248d3e70c885fa072e3bd4682a24f0bcfdd6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350611"
---
# <a name="debug-live-aspnet-apps-on-azure-virtual-machines-and-azure-virtual-machine-scale-sets-using-the-snapshot-debugger"></a>使用快照偵錯工具針對 Azure 虛擬機器上的即時 ASP.NET 應用程式和 Azure 虛擬機器擴展集進行偵錯

[快照偵錯工具] 會在您感興趣的程式碼執行時，擷取實際執行應用程式的快照集。 若要指示偵錯工具擷取快照集，您可以在程式碼中設定快照點和記錄點。 偵錯工具可讓您清楚了解發生什麼問題，而不會影響實際執行應用程式的流量。 快照集偵錯工具可協助您大幅縮短為解決出現在生產環境之問題所花費的時間。

快照點和記錄點與中斷點很相似，但和中斷點不的是，快照點不會在叫用時停止應用程式。 一般而言，在快照點擷取快照集時需要 10 到 20 毫秒。

在本教學課程中，您將：

> [!div class="checklist"]
> * 啟動快照偵錯工具
> * 設定快照點及檢視快照
> * 設定記錄點

## <a name="prerequisites"></a>先決條件

* 適用于 Azure 虛擬機器 (VM) 的快照偵錯工具和 Azure 虛擬機器擴展集僅適用于使用 **azure 開發工作負載**的 Visual Studio 2019 Enterprise 或更高版本。 (您可以在 [個別元件]**** 索引標籤下的 [偵錯和測試]**** > [快照偵錯工具]**** 底下找到它。)

    如果尚未安裝，請安裝 [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/)。

* 快照集集合適用于下列 Azure 虛擬 Machines\Virtual 機器擴展集 web apps：
  * 執行 .NET Framework 4.6.1 或更新版本的 ASP.NET 應用程式。
  * 在 Windows 上執行 .NET Core 2.0 或更新版本的 ASP.NET Core 應用程式。

  > [!NOTE]
  >  在32位的 Windows 上執行 Visual Studio Enterprise 將無法查看快照集。

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>開啟專案並啟動快照偵錯工具

1. 開啟想要行快照集偵錯的專案。

    > [!IMPORTANT]
    > 若要建立快照集的快照集，您必須開啟已發佈至 Azure Virtual Machine\Virtual 機器擴展集服務的 *相同原始程式碼版本* 。

1. 選擇 **Debug > 附加快照偵錯工具**.。。選取您的 web 應用程式部署所在的 Azure 虛擬 Machine\Virtual 機器擴展集和 Azure 儲存體帳戶，然後按一下 [ **附加**]。 快照偵錯工具也支援 [Azure Kubernetes Service](debug-live-azure-kubernetes.md) 和 [Azure App Service](debug-live-azure-applications.md)。

    ![從 [偵錯] 功能表啟動快照偵錯工具](../debugger/media/snapshot-debug-menu-attach.png)

    ![選取 Azure 資源](../debugger/media/snapshot-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > 第一次為 VM 選取 [附加快照偵錯工具]**** 時，IIS 會自動重新啟動。
    > 當您第一次選取虛擬機器擴展集的 [ **附加快照偵錯工具** 時，需要手動升級每個虛擬機器擴展集實例。

    > [!NOTE]
    >  (Visual Studio 2019 16.2 版和更新版本) 快照偵錯工具已啟用 Azure 雲端支援。 請確定您選取的 Azure 資源和 Azure 儲存體帳戶都是來自相同的雲端。 如果您對企業的 [azure 合規性](https://azure.microsoft.com/overview/trusted-cloud/) 設定有任何問題，請洽詢您的 azure 系統管理員。

    **模組**的中繼資料一開始不會啟用，請流覽至 web 應用程式，[**開始收集**] 按鈕將會變成作用中狀態。 Visual Studio 現在已經處於快照集偵錯模式。

    ![快照集偵錯模式](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > 若為 VMSS，使用者必須在第一次連接快照偵錯工具之後，手動升級其虛擬機器擴展集中的實例。

    [ **模組** ] 視窗會顯示 Azure 虛擬 Machine\Virtual 機器擴展集的所有模組都已載入， (選擇 [ **Debug > Windows > 模組** ] 來開啟此視窗) 。

    ![檢查 [模組] 視窗](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>設定快照點

1. 在 [程式碼編輯器] 中，按一下您感興趣的程式程式碼旁邊的左邊裝訂邊來設定快照點。 請確定它是您知道將會執行的程式碼。

    ![設定快照點](../debugger/media/snapshot-set-snappoint.png)

1. 按一下 [開始收集]**** 以開啟快照點。

    ![開啟快照點](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > 檢視快照點時，您無法逐步檢視，但可以在程式碼中置入多個快照點，隨著不同行的程式碼執行。 如果程式碼中有多個快照點，快照偵錯工具會確定相對應的快照集是來自相同的使用者工作階段。 就算有許多使用者叫用您的應用程式，快照偵錯工具也會這樣做。

## <a name="take-a-snapshot"></a>擷取快照集

設定快照點之後，您可以手動產生快照集，方法是前往網站的瀏覽器視圖，並執行標示或等候使用者從網站使用方式產生的程式程式碼。

## <a name="inspect-snapshot-data"></a>檢查快照集資料

1. 叫用快照點時，[診斷工具] 視窗中會顯示快照點。 若要開啟此視窗，請選擇 [偵錯] > [Windows] > [顯示診斷工具]****。

    ![開啟快照點](../debugger/media/snapshot-diagsession-window.png)

1. 按兩下快照點以在程式碼編輯器中開啟快照點。

    ![檢查快照集資料](../debugger/media/snapshot-inspect-data.png)

    您可以從這個檢視，將滑鼠移至變數上方以檢視 DataTips、使用 [區域]****、[監看式]****，以及 [呼叫堆疊]**** 視窗，也可以評估運算式。

    網站本身仍在運作中，使用者也不會受到影響。 每個快照點預設只會擷取一個快照集：擷取快照集之後，快照點就會關閉。 如果想要在快照點擷取另一個快照集，可以按一下 [更新集合]**** 以重新開啟快照點。

您也可以將更多快照點新增至應用程式，並使用 [更新集合]**** 按鈕將它們開啟。

**需要協助嗎？** 請參閱[疑難排解和已知問題](../debugger/debug-live-azure-apps-troubleshooting.md)與[快照集偵錯的常見問題集](../debugger/debug-live-azure-apps-faq.md)頁面。

## <a name="set-a-conditional-snappoint"></a>設定條件式快照點

如果很難在您的應用程式中重新建立特定狀態，請考慮使用條件式快照點。 條件式快照點可協助您控制快照集的時間，例如當變數包含您想要檢查的特定值時。 您可以使用運算式、篩選或叫用次數設定條件。

#### <a name="to-create-a-conditional-snappoint"></a>建立條件式快照點

1. 以滑鼠右鍵按一下快照點圖示 (空心球) 並選擇 [設定]****。

   ![選擇設定](../debugger/media/snapshot-snappoint-settings.png)

1. 在快照點設定視窗中輸入運算式。

   ![輸入運算式](../debugger/media/snapshot-snappoint-conditions.png)

   在上圖中，只會在 `visitor.FirstName == "Dan"` 時才會建立快照點的快照集。

## <a name="set-a-logpoint"></a>設定記錄點

除了在叫用快照點時建立快照集之外，您也可以設定快照點記錄訊息 (也就是建立記錄點)。 您可以在不需要重新部署應用程式的情況下設定記錄點。 記錄點會以虛擬方式執行，而且不會對執行中的應用程式造成任何影響或副作用。

#### <a name="to-create-a-logpoint"></a>建立記錄點

1. 以滑鼠右鍵按一下快照點圖示 (藍色六邊形) 並選擇 [設定]****。

1. 在快照點設定視窗中選取 [動作]****。

    ![建立記錄點](../debugger/media/snapshot-logpoint.png)

1. 您可以在 [訊息]**** 欄位中輸入想要記錄的新記錄訊息。 也可以在記錄訊息中變數的前後加上大括號，以評估它們。

    如果您選擇 [傳送到輸出視窗]****，當叫用記錄點時，訊息會出現在 [診斷工具] 視窗中。

    ![[診斷工具] 視窗中的記錄點資料](../debugger/media/snapshot-logpoint-output.png)

    如果您選擇 [傳送到應用程式記錄檔]****，當叫用記錄點時，只要可以看到來自 `System.Diagnostics.Trace` (或在 .NET Core 中為 `ILogger`) (例如[應用程式深入解析](/azure/application-insights/app-insights-asp-net-trace-logs)) 之訊息的位置，就會顯示訊息。

## <a name="next-steps"></a>後續步驟

您已經在此教學課程中學到如何針對 Azure 虛擬機器和 Azure 虛擬機器擴展集使用快照偵錯工具。 您可以閱讀和此功能有關的更多詳細資料。

> [!div class="nextstepaction"]
> [快照集偵錯的常見問題集](../debugger/debug-live-azure-apps-faq.md)
