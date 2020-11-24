---
title: 在負載測試結果的圖形上新增和刪除計數器
description: 瞭解如何使用 [計數器] 面板，將效能計數器加入至圖形以及取樣率屬性。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load test results graphs, adding counters
- load test results graph
- load test, results graph
- load test results, graphs
ms.assetid: 81536233-1962-40d9-9511-0b4633814d90
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82794efc8d3065c9b428602e50455cccd162bbd4
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442582"
---
# <a name="how-to-add-and-delete-counters-on-graphs-in-load-test-results"></a>如何：在負載測試結果的圖形上加入和刪除計數器

您可以使用 [計數器] 面板將效能計數器加入至圖形。

![已將計數器加入至圖形](../test/media/ltest_selectcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**效能計數器取樣間隔考慮**

請根據負載測試的長度，在負載測試回合設定中選擇 [採樣速率] 屬性的值。 較小的取樣率 (例如五秒的預設值) 會在負載測試結果資料庫中佔用較多空間。 若為較長的負載測試，增加取樣率會降低您所收集的資料量。 如需詳細資訊，請參閱[如何：指定採樣速率](../test/how-to-specify-the-sample-rate-for-a-load-test.md)。

下面是一些取樣率的方針：

|負載測試持續期間|建議取樣率|
|-|-----------------------------|
|\< 1 小時|5 秒|
|1 - 8 小時|15 秒|
|8 - 24 小時|30 秒|
|> 24 小時|60 秒|

**包含收集百分位數資料的計時詳細資料的考慮**

在 [負載測試編輯器] 的回合設定中，有一個名為 [計時詳細資料儲存區] 的屬性。 如果啟用 [計時詳細資料儲存區] 屬性，則在負載測試期間每個個別測試、異動和頁面的執行時間會儲存在負載測試結果儲存機制中。 這可以在 [負載測試分析器] 的 [測試]、[異動] 和 [頁面] 索引標籤中顯示第 90 和第 95 個百分位數資料。

在回合設定屬性中，有兩個用於啟用 [計時詳細資料儲存區] 屬性的選項，名為 [僅限統計資料] 和 [所有個別細節]。 不論選擇哪一種，所有的個別測試、頁面和異動都會計時，而且百分位數資料是從個別的計時資料計算出來的。 其差異在於，使用 [僅限統計資料] 選項時，一旦計算出百分位數資料之後，系統就會從存放庫中刪除個別的計時資料。 這樣做可減少使用計時詳細資料時儲存機制所需的空間量。 不過，進階使用者可能會想要使用 SQL 工具，以其他方式處理計時詳細資料。 如果是這種情況，您就應該使用 [所有個別細節] 選項，讓計時詳細資料可用於該項處理。 此外，如果您將此屬性設定為 [所有個別細節]，當負載測試執行完成之後，您就可以在 [負載測試分析器] 中使用「虛擬使用者活動」圖來分析虛擬使用者活動。 如需詳細資訊，請參閱[在詳細資料檢視中分析虛擬使用者活動](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)。

負載測試結果儲存機制用來儲存計時詳細資料所需的空間可能相當大，尤其是長時間執行的負載測試。 其次，在負載測試結束時，用來將這項資料儲存至負載測試結果儲存機制的時間會比較長，因為在負載測試執行完成之後，這項資料會儲存在負載測試代理程式上。 當負載測試完成時，資料就會儲存至儲存機制中。 預設會啟用 [計時詳細資料儲存區] 屬性。 如果您的測試環境發生這種問題，您可能會想要將 [計時詳細資料儲存區] 設定為 [無]。

如需詳細資訊，請參閱 [如何：指定計時詳細資料儲存區屬性](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)。

## <a name="to-display-a-particular-performance-counter-on-a-load-test-graph"></a>若要在負載測試圖形上顯示特定效能計數器

1. 在負載測試完成後，或當您載入測試結果之後，請在 [負載測試分析器] 的工具列中，選擇 [圖形]。

     [計數器] 面板隨即顯示在 [圖形] 檢視中。

    > [!NOTE]
    > 如果看不見 [計數器] 面板，請選擇工具列上的 [顯示計數器面板]。

2. 在 [計數器] 面板中，展開階層架構中的節點，直到找出您要以圖形顯示的效能計數器。

     例如，若要顯示執行測試所在電腦的可用記憶體，則依序展開 [電腦]、該電腦的節點及 [記憶體]。 您會看到 [Available MBytes] 計數器。

3. 選擇您要顯示效能計數器的圖形。

4. 以滑鼠右鍵按一下 [計數器] 面板中的效能計數器，並選取 [在圖形上顯示計數器]。

    > [!TIP]
    > 若要暫時停止在圖形上顯示效能計數器資料，請清除圖例中效能計數器的核取方塊。 這仍可讓您分析最小、最大和平均統計資料，而不檢視圖形上的趨勢線。 如果在您分析問題時，圖形包含數個重疊的效能計數器繪圖，這會非常有用。 如需詳細資訊，請參閱[使用圖形檢視圖例來分析負載測試](../test/use-the-graphs-view-legend-to-analyze-load-tests.md)。

5. 若要從圖形移除效能計數器資料，請以滑鼠右鍵按一下圖例的 [計數器] 欄位中的效能計數器，並選取 [刪除]。

     \- 或 -

     以滑鼠右鍵按一下圖形中的資料線，並選取 [刪除]。

     \- 或 -

     選擇圖例的 [計數器] 欄位中的效能計數器，或是圖形中的資料線，然後按 **Delete** 鍵。

    > [!NOTE]
    > 您也可以使用 [在圖例上新增計數器] 命令，選擇將效能計數器放在圖例，而不是圖形上。

## <a name="see-also"></a>另請參閱

- [在圖表檢視中分析負載測試結果](../test/analyze-load-test-results-in-the-graphs-view.md)
- [如何：建立自訂圖形](../test/how-to-create-custom-graphs-in-load-test-results.md)
