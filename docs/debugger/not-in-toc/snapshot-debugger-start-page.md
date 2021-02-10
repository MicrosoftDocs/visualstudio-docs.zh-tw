---
title: 快照偵錯工具的起始頁
ms.date: 07/14/2018
robots: noindex, nofollow
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9f237f121d0bd0a5eaa57cd2b198024d22951622
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941992"
---
# <a name="getting-started-with-the-snapshot-debugger"></a>使用快照偵錯工具開始使用

Visual Studio 快照偵錯工具現在已連接至您的服務，您可以開始收集快照集以協助進行偵錯工具。

若要使用快照偵錯工具，請在您的程式碼中設定一些快照點，按一下按鈕開始收集快照集，然後執行您的案例。 當您已在其中設定快照點的程式碼執行時，會建立應用程式的快照集。 然後按一下 [診斷工具] 視窗中 Visual Studio 中的快照集來開啟快照集。 您現在可以從服務中的快照集來進行偵錯工具，就像是在本機一樣。 如需詳細指示，請繼續閱讀。

## <a name="collect-and-view-snapshots"></a>收集和查看快照集

快照偵錯工具會從您的應用程式收集快照集。 快照集就像您在某個時間點的 appication 圖片。 您可以藉由在程式碼中設定快照點，告訴您要收集快照集 Visual Studio 的時機和位置。 在快照點中，您可以設定任何需要的條件，以確保您取得正在調查之問題的快照。

### <a name="set-a-snappoint"></a>設定快照點

1. 在 [程式碼編輯器] 中，按一下您感興趣的程式程式碼旁邊的左邊裝訂邊來設定快照點。 請確定它是您知道將會執行的程式碼。

    ![在編輯器中設定快照點](../media/snapshot-startpage-set-snappoint.png)

    當您按一下左邊時，會出現紫色六邊形。

2. 按一下 [開始收集] 以開啟快照點。

### <a name="open-a-snapshot"></a>開啟快照集

1. 當達到快照點時，快照集會出現在右邊的診斷工具視窗中。 如果視窗未開啟，您可以選擇 [ **Debug**  >  **Windows**  >  **Show 診斷工具** 來開啟它。

    ![診斷工具視窗中的快照集](../media/snapshot-startpage-diagsession-window.png)

2. 按兩下快照集以開啟它。

### <a name="inspect-snapshot-data"></a>檢查快照集資料

您可以從這個檢視，將滑鼠移至變數上方以檢視 DataTips、使用 [區域]、[監看式]，以及 [呼叫堆疊] 視窗，也可以評估運算式。

網站本身是仍然是即時的且使用者不會受到影響。 依預設，每個快照點只會捕獲一個快照集。 也就是說，在捕捉快照集之後，快照點就會關閉。 如果想要在快照點擷取另一個快照集，可以按一下 [更新集合] 以重新開啟快照點。

### <a name="set-a-logpoint"></a>設定記錄點

1. 以滑鼠右鍵按一下快照點圖示 (紫色六邊形) ，然後選擇 [ **設定**]。

2. 在 [ **快照點設定** ] 視窗中，選取 [ **動作**]。

    ![快照點條件](../media/snapshot-startpage-logpoint.png)

3. 在 [ **訊息** ] 欄位中，輸入您想要記錄的記錄檔訊息。 也可以在記錄訊息中變數的前後加上大括號，以評估它們。

    如果您選擇 [ **傳送至] 輸出視窗**，當叫用記錄點時，訊息會出現在 [診斷工具] 視窗中。

    如果您選擇 [ **傳送至應用程式記錄** 檔]，則會出現訊息，您可以在叫用 `System.Diagnostics.Trace` 記錄點時查看來自 (或 `ILogger` .net Core) 的訊息，例如 App Insights。

## <a name="learn-more"></a>深入了解

您可以在 [檔] [頁面](../debug-live-azure-applications.md)找到快照偵錯工具的詳細資訊。 深入瞭解如何設定條件，讓您更輕鬆地找到 bug。

## <a name="dont-show-me-this-again"></a>不要再顯示此訊息

當您連接快照偵錯工具時，若不想再顯示快照偵錯工具起始頁，請在 [**工具** 選項] 快照偵錯工具的 [會話啟動] 選項中，變更 [**顯示 ' 開始使用 ' 頁面**]  >    >  ****。

![快照偵錯工具工具選項頁面](../media/snapshot-startpage-tools-options.png)
