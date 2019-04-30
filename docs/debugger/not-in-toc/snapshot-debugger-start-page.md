---
title: 快照集偵錯工具的 [開始] 頁面
ms.date: 07/14/2018
robots: noindex, nofollow
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf2aba33089623dc98a90c23166291bb2d6e7123
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905240"
---
# <a name="getting-started-with-the-snapshot-debugger"></a>快照集偵錯工具使用者入門

Visual Studio 快照集偵錯工具現在會連接到您的服務，您可以開始收集快照集，以協助偵錯。

若要使用快照集偵錯工具，設定一些貼齊點在程式碼中，按一下按鈕以開始收集快照集，然後再執行您的案例。 程式碼時執行您在其中已設定貼齊點，擷取您的應用程式的快照集。 在 Visual Studio 診斷工具 視窗中按一下，然後開啟快照集。 您可以現在偵錯快照集從您的服務就像它是本機。 如需詳細指示，繼續閱讀。

## <a name="collect-and-view-snapshots"></a>收集及檢視快照集

快照集偵錯工具會從您的應用程式收集快照集。 快照集是類似的某一點您 appication 圖片的時間。 何時及如何收集程式碼中設定貼齊點的快照集，您會告訴 Visual Studio。 在貼齊點，您可以將任何您必須先確定您取得您要調查的問題的快照集的條件。

### <a name="set-a-snappoint"></a>設定貼齊點

1. 在程式碼編輯器中，按一下您感興趣設定貼齊點的程式碼行旁的左裝訂邊。 請確定它是您知道將會執行的程式碼。

    ![在編輯器中設定貼齊點](../media/snapshot-startpage-set-snappoint.png)

    紫色六邊形會出現在您按一下左側的位置。

2. 按一下 [開始收集] 以開啟快照點。

### <a name="open-a-snapshot"></a>開啟快照集

1. 當叫用的貼齊點時，快照集會出現在右邊的 [診斷工具] 視窗中。 如果視窗未開啟，您可以選擇其開啟**偵錯** > **Windows** > **顯示診斷工具**。

    ![在 [診斷工具] 視窗中的快照集](../media/snapshot-startpage-diagsession-window.png)

2. 按兩下以開啟它的快照集。

### <a name="inspect-snapshot-data"></a>檢查快照集的資料

從這個檢視中，您可以將滑鼠移至變數，以檢視資料提示方塊中，使用的區域變數、 監看式和呼叫堆疊視窗，並同時評估運算式。

網站本身是仍然是即時的且使用者不會受到影響。 根據預設，只有一個快照會擷取每個貼齊點。 也就是在擷取快照集之後，請貼齊點會關閉。 如果想要在快照點擷取另一個快照集，可以按一下 [更新集合] 以重新開啟快照點。

### <a name="set-a-logpoint"></a>設定記錄點

1. 以滑鼠右鍵按一下 貼齊點圖示 （紫色六邊形），然後選擇 **設定**。

2. 在 **貼齊點設定**視窗中，選取**動作**。

    ![貼齊點條件](../media/snapshot-startpage-logpoint.png)

3. 在 **訊息**欄位中，輸入您想要記錄的記錄訊息。 也可以在記錄訊息中變數的前後加上大括號，以評估它們。

    如果您選擇**傳送到輸出視窗**，訊息會出現在 [診斷工具] 視窗，當叫用的記錄點時。

    如果您選擇**傳送至應用程式記錄檔**，則訊息會出現任何位置，您可以看到來自`System.Diagnostics.Trace`(或`ILogger`.NET core)，例如 App Insights 記錄點叫用時。

## <a name="learn-more"></a>進一步了解

您可以找到快照集偵錯工具的詳細資訊，在[docs 頁面](../debug-live-azure-applications.md)。 深入了解設定條件，可讓您更輕鬆地找出 bug。

## <a name="dont-show-me-this-again"></a>不要再顯示此訊息

若要永遠不會在您連線的快照集偵錯工具時，再次顯示快照集偵錯工具起始頁，請變更**顯示 [Getting Started] 頁面上的工作階段開始**選項**工具** >  **選項** > **快照集偵錯工具**。

![快照集偵錯工具 工具選項頁面](../media/snapshot-startpage-tools-options.png)
