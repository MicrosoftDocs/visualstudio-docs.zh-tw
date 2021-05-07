---
title: Azure VM 上的時間移動即時偵測即時 ASP.NET
description: 瞭解如何使用快照偵錯工具在 Azure 虛擬機器上記錄和重新執行即時 ASP.NET 應用程式。
ms.custom: SEO-VS-2020
ms.date: 04/11/2019
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
ms.openlocfilehash: f8aabb109de02a1beec326407472a841fe16425a
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798449"
---
# <a name="record-and-replay-live-aspnet-apps-on-azure-virtual-machines-using-the-snapshot-debugger"></a>使用快照偵錯工具在 Azure 虛擬機器上記錄和重新播放即時 ASP.NET 應用程式

在 Visual Studio Enterprise 中 (TTD) preview 的時間移動偵錯工具，可讓您將在 Azure 虛擬機器上執行的 Web 應用程式記錄 (VM) ，然後精確地重建並重新執行執行路徑。 TTD 與快照偵錯工具整合，可讓您將每一行程式碼倒轉並重新執行任意數目的次數，協助您找出並找出可能只會在生產環境中發生的問題。

捕捉 TTD 錄製不會終止應用程式。 不過，TDD 記錄會增加執行中進程的大量負荷，並根據包含進程大小和使用中線程數目的因素，使其變慢。

這項功能處於預覽階段，可讓您使用 go live 授權發行 Visual Studio 2019。

在本教學課程中，您將：

> [!div class="checklist"]
> * 啟動已啟用時間移動調試的快照偵錯工具
> * 設定快照點並收集時間移動記錄
> * 開始進行時間移動記錄的調試

## <a name="prerequisites"></a>必要條件

* Azure 虛擬機器 (VM) 的時間移動偵錯工具，僅適用于使用 **azure 開發工作負載** 的 Visual Studio 2019 Enterprise 或更高版本。 (您可以在 [個別元件] 索引標籤下的 [偵錯和測試] > [快照偵錯工具]底下找到它。)

    如果尚未安裝，請安裝 [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/)。

* 時間移動偵錯工具適用于下列 Azure VM web apps：
  * ASP.NET 應用程式 (AMD64) 在 .NET Framework 4.8 或更新版本上執行。

## <a name="start-the-snapshot-debugger-with-time-travel-debugging-enabled"></a>啟動已啟用時間移動調試的快照偵錯工具

1. 開啟您想要收集時間移動錄製的專案。

    > [!IMPORTANT]
    > 若要開始 TTD，您必須開啟已發佈至 Azure VM 服務的 *相同原始程式碼版本* 。

1. 選擇 **Debug > 附加快照偵錯工具**.。。選取您的 web 應用程式部署所在的 Azure VM 和 Azure 儲存體帳戶。 選取 [ **啟用時間移動調試** 預覽] 選項，然後按一下 [ **附加**]。

      ![選取 Azure 資源](../debugger/media/time-travel-debugging-select-azure-resource-vm.png)

    > [!IMPORTANT]
    > 第一次為 VM 選取 [附加快照偵錯工具] 時，IIS 會自動重新啟動。

    **模組** 的中繼資料一開始不會啟用。 流覽至 web 應用程式，[ **開始收集** ] 按鈕就會變成作用中狀態。 Visual Studio 現在已經處於快照集偵錯模式。

   ![快照集偵錯模式](../debugger/media/snapshot-message.png)

    > [!NOTE]
    > Application Insights 網站延伸模組也支援快照集偵錯。 如果遇到「網站延伸模組過期」錯誤訊息，請參閱[快照集偵錯的疑難排解祕訣與已知問題](../debugger/debug-live-azure-apps-troubleshooting.md)了解升級詳細資料。

   當您為 Azure VM 載入所有模組時，[ **模組** ] 視窗會向您顯示 (選擇 [ **Debug] > Windows > 模組** 開啟此視窗) 。

   ![檢查 [模組] 視窗](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint-and-collect-a-time-travel-recording"></a>設定快照點並收集時間移動記錄

1. 在 [程式碼編輯器] 中，按一下您感興趣之方法中的左邊裝訂邊，以設定快照點。 確定這是您將執行的程式碼。

   ![設定快照點](../debugger/media/time-travel-debugging-set-snappoint-settings.png)

1. 以滑鼠右鍵按一下快照點圖示 (空心球) ，然後選擇 [ **動作**]。 在 [ **快照集設定** ] 視窗中，按一下 [ **動作** ] 核取方塊。 然後按一下 [將 **時間移動追蹤收集到此方法的結尾** ] 核取方塊。

   ![收集時間移動追蹤至方法的結尾](../debugger/media/time-travel-debugging-set-snappoint-action.png)

1. 按一下 [開始收集] 以開啟快照點。

   ![開啟快照點](../debugger/media/snapshot-start-collection.png)

## <a name="take-a-snapshot"></a>擷取快照集

當快照點開啟時，每當放置快照點的程式程式碼執行時，它就會捕捉快照集。 這項執行可能是因為伺服器上的實際要求所造成。 若要強制叫用快照點，請移至網站的瀏覽器檢視，並採取可使得系統叫用快照點的任何必要動作。

## <a name="start-debugging-a-time-travel-recording"></a>開始進行時間移動記錄的調試

1. 叫用快照點時，[診斷工具] 視窗中會顯示快照點。 若要開啟此視窗，請選擇 [偵錯] > [Windows] > [顯示診斷工具]。

   ![開啟快照點](../debugger/media/snapshot-diagsession-window.png)

1. 按一下 [視圖快照] 連結，以在程式碼編輯器中開啟時間移動記錄。
  
   您可以使用 [ **繼續** ] 和 [ **反向繼續** ] 按鈕，執行 TTD 所記錄的每一行程式碼。 此外，**調試** 的工具列還可以用來 **顯示下一個語句**、**逐步** 執行、不進入 **、跳** 過 **、逐步執行、逐步****執行、****跳** 回。 

   ![[偵錯]](../debugger/media/time-travel-debugging-step-commands.png)

   您也可以使用 [**區域變數**]、[監看式] 和 [**呼叫堆疊** **]** 視窗，也可以評估運算式。

   ![檢查快照集資料](../debugger/media/time-travel-debugging-start-debugging.png)

    網站本身仍在上線，且使用者不會受到任何後續 TTD 活動的影響。 每個快照點預設只會擷取一個快照集：擷取快照集之後，快照點就會關閉。 如果想要在快照點擷取另一個快照集，可以按一下 [更新集合] 以重新開啟快照點。

**需要協助嗎？** 請參閱[疑難排解和已知問題](../debugger/debug-live-azure-apps-troubleshooting.md)與[快照集偵錯的常見問題集](../debugger/debug-live-azure-apps-faq.yml)頁面。

## <a name="set-a-conditional-snappoint"></a>設定條件式快照點

如果很難在應用程式中重新建立特定狀態，請考量使用條件式快照點是否能有所幫助。 條件式快照點可協助您避免在應用程式進入所需狀態之前收集時間移動記錄，例如，當變數有您想要檢查的特定值時。 [您可以使用運算式、篩選或計數來設定條件](../debugger/debug-live-azure-apps-troubleshooting.md)。

## <a name="next-steps"></a>下一步

在本教學課程中，您已瞭解如何收集 Azure 虛擬機器的時間移動記錄。 您可能想要閱讀更多有關快照偵錯工具的詳細資料。

> [!div class="nextstepaction"]
> [快照集偵錯的常見問題集](../debugger/debug-live-azure-apps-faq.yml)