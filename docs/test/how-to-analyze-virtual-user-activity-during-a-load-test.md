---
title: 分析負載測試的虛擬使用者活動
description: 瞭解如何使用虛擬使用者活動圖來查看每個虛擬使用者在測試期間是否正在執行，以查看使用者活動模式和其他資訊。
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- virtual user activity chart, viewing
ms.assetid: 8bda19b3-91c1-4daf-b6c7-09108bddadff
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 353a38c17cdcd3358376547155750914e406f4be
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442387"
---
# <a name="how-to-analyze-what-virtual-users-are-doing-during-a-load-test-using-the-virtual-user-activity-chart"></a>如何：使用虛擬使用者活動圖表分析虛擬使用者在負載測試期間的行為

您可以使用「虛擬使用者活動圖」檢視與負載測試關聯的虛擬使用者活動。 圖表中的每一列都表示個別的虛擬使用者。 「虛擬使用者活動圖」會顯示每一個虛擬使用者在測試期間的行為。 您可以查看使用者活動的模式、負載模式、讓失敗或緩慢的測試產生關聯，以及查看其他虛擬使用者活動的要求。 「虛擬使用者活動圖」只有在負載測試完成執行之後才能使用。

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

下列程序會示範如何檢視「虛擬使用者活動圖」、如何調查特定使用者的活動，以及如何使用篩選。

## <a name="to-view-the-virtual-user-activity-chart-in-your-load-test-results"></a>若要在負載測試結果中檢視虛擬使用者活動圖

1. 若要檢視虛擬使用者資料，您必須先設定與負載測試關聯之 [計時詳細資料儲存區] 屬性的 [所有個別詳細資料] 設定。 然後再次執行負載測試。

2. 執行負載測試之後，測試結果摘要頁面隨即顯示。 選擇工具列上的 [使用者詳細資料] 按鈕。

     -或-

     選擇工具列上的 [圖形] 按鈕，開啟 [圖形] 檢視。 以滑鼠右鍵按一下圖形，然後選取 [移至使用者詳細資料]。

     如果您使用此選項，「虛擬使用者活動圖」會自動縮放至您以滑鼠右鍵按一下的測試部分。 例如，若指標位於大約 30 秒標記處，則詳細資料檢視會在「虛擬使用者活動圖」底部的 [縮放為時間週期] 工具中，大約 30 秒的標記處顯示出來。

     接著，可以調查「虛擬使用者活動圖」中特定的使用者活動詳細資訊。

## <a name="to-investigate-a-specific-users-activity-in-the-virtual-user-activity-chart"></a>在虛擬使用者活動圖中調查特定使用者活動

1. 使用「虛擬使用者活動圖」底部的 [縮放為時間週期] 工具，以選取圖表上的區域，您要在此區域中調查特定使用者的詳細資料。

2. 將指標移到圖形中的詳細資料上。 請注意，下列資訊會顯示在工具提示中。

   - **使用者識別碼**

   - **案例**

   - **測試**

   - **URL** (不會在測試或異動中顯示)

   - **結果**

   - **瀏覽** (不會在測試或異動中顯示)

   - **Network**

   - **Start Time**

   - **有效期間**

   - **代理程式**

   - **測試記錄檔** (連結至測試記錄)

     > [!NOTE]
     > 若要協助除錯應用程式，在選擇 [測試記錄] 連結時，與記錄關聯的 Web 測試結果或單元測試結果隨即開啟。

     接著，可以使用「虛擬使用者活動圖」中可用的篩選和反白顯示作業。

## <a name="to-use-filtering-options-in-the-virtual-user-activity-chart"></a>若要使用虛擬使用者活動圖中的篩選選項

1. 在 [ **詳細資料圖例**] 中，使用下拉式清單來選取 [ **測試**]、[ **頁面**] 或 [ **交易**]。

    **詳細資料圖例面板**

    ![詳細資料圖例面板](../test/media/ltest_detailslegend.png)

2. 選取或清除與負載測試關聯之錯誤、記錄、測試、搜尋和 ASPX 頁面的核取方塊。

    並會隨之更新「虛擬使用者活動圖」。

    「虛擬使用者活動圖」提供可根據不同準則篩選出測試、頁面和異動的功能。 您可以從檢視中移除特定測試、移除所有成功的測試，或移除因特定因素而失敗的測試。 您也可以移除不具有記錄的所有測試。

    例如，您可以選取 [(反白顯示錯誤)] 選項，該選項會顯示圖表中的所有錯誤，並以紅色標示。 您也可以選取 [(反白顯示有記錄檔的結果)] 選項，該選項會顯示圖表中有記錄檔的所有測試結果，並以綠色標示。

    **篩選結果面板**

    ![篩選結果面板](../test/media/ltest_filterresults.png)

3. 在 [篩選] 結果中，選取或清除下列篩選選項的核取方塊：

   - **只顯示有記錄檔的結果**：僅顯示具有關聯測試記錄檔的測試結果。

   - **顯示成功的結果**：顯示成功的結果。

   - **顯示有錯誤的結果**：顯示具有錯誤的結果，這些錯誤可協助偵錯。

     > [!NOTE]
     > 選擇 **Web 效能測試結果檢視器** 工具列中的 [**資料表]** 按鈕，即可進一步調查 [**顯示有錯誤的結果**] 節點底下列出的錯誤類型清單。 如需詳細資訊，請參閱在  [資料表視圖中分析負載測試結果和錯誤](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)。

     並會隨之更新「虛擬使用者活動圖」。

## <a name="see-also"></a>另請參閱

- [在詳細資料檢視中分析虛擬使用者活動](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [逐步解說：使用虛擬使用者活動圖來隔離問題](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)