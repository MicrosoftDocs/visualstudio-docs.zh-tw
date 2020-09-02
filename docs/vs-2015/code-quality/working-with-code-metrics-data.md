---
title: 使用程式碼計量資料 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c2460b4e8b9e0b9043178989fcf8825815471be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645698"
---
# <a name="working-with-code-metrics-data"></a>使用程式碼度量資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[程式 **代碼計量結果** ] 視窗會顯示程式碼計量分析所產生的資料。 如需程式碼計量資料值的詳細資訊，請參閱程式 [代碼度量值](../code-quality/code-metrics-values.md)。

 本主題包含下列幾節：

- [程式碼度量結果視窗](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)

- [顯示程式碼度量結果](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)

- [篩選程式代碼度量結果](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)

- [加入、移除及重新排列資料行](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)

- [將資料複製到剪貼簿或 Excel](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)

- [根據程式碼度量結果建立工作專案](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)

## <a name="code-metrics-results-window"></a><a name="BKMK_CodeMetricsResultsWindow"></a> Code Metrics Results Window
 程式 **代碼度量結果** 視窗的頂端有工具列，而資料行則顯示計算結果。

|資料行|描述|
|------------|-----------------|
|**階層**|[階層] **資料行包含** 程式碼階層的樹狀檢視，您可以展開或折迭以查看您想要的詳細程度。 其餘的資料行則顯示計算的結果。 您可以依需要隱藏或排列結果資料行。|
|**可維護性**|**維護**資料行除了數值結果之外，還包含一個圖示。 綠色圖示表示相對較高程度的可維護性。 黃色圖示表示適中程度的可維護性。 紅色圖示表示低維護性和潛在的問題點。 這些色彩指標對應至 FxCop 規則 AvoidUnmaintainableCode 所使用的嚴重性分類。 如果可維護性索引小於10，此規則就會引發錯誤，如果索引介於10和20之間，則會引發警告，而且如果索引大於20，則不會有錯誤或警告。 可維護性索引是三個計量的合成：迴圈複雜度、程式程式碼和計算複雜度。 其值不會以單位表示。|

## <a name="displaying-code-metrics-results"></a><a name="BKMK_DisplayingCodeMetricsResults"></a> 顯示程式碼度量結果
 當您產生程式碼度量結果時，會自動顯示 [程式碼度量結果] 視窗。 您也可以在任何時間顯示視窗。

#### <a name="to-display-the-code-metrics-results-window"></a>顯示程式碼度量結果視窗

- 在 [ **分析** ] 功能表上，按一下 [ **Windows** ]，然後按一下 [程式 **代碼度量結果**]。

     \- 或 -

- 在 [ **View** ] 功能表上，指向 [ **其他視窗** ]，然後按一下 [程式 **代碼度量結果**]。

     即使未包含任何結果，也會顯示 [程式碼計量結果] 視窗。

#### <a name="to-view-code-metrics-details"></a>若要查看程式碼計量詳細資料

- 如果已產生程式碼度量結果，請展開 [階層] 資料行中的樹狀 **結構** 。

## <a name="filtering-code-metrics-results"></a><a name="BKMK_FilteringCodeMetricsResults"></a> 篩選程式代碼度量結果
 您可以使用頂端的工具列，來篩選 [程式 **代碼度量結果** ] 視窗中顯示的結果。 例如，您可能只想要查看在65以下的可維護性索引的結果。

 [ **篩選** ] 下拉式清單方塊包含結果資料行的名稱。 定義篩選時，會將其加入至清單底部，以及縮排。 此清單可以包含最後十個已定義的篩選。

#### <a name="to-filter-the-code-metrics-results"></a>篩選程式代碼度量結果

1. 從 [ **篩選器** ] 清單中選取資料行名稱。

2. 在 [ **最**小值] 中，輸入要顯示的最小值。

3. 在 [ **最**大值] 中，輸入要顯示的最大值。

4. 按一下 [套用 **篩選** ] 按鈕。

5. 若要查看結果詳細資料，請展開階層樹狀結構。

## <a name="adding-removing-and-rearranging-data-columns"></a><a name="BKMK_AddingRemovingandRearrangingDataColumns"></a> 加入、移除及重新排列資料行
 您可以從程式 **代碼度量結果** 視窗新增或移除結果資料行。 此外，您可以重新排列結果資料行，使其按照您想要的順序出現。

#### <a name="to-remove-a-column"></a>移除資料行

1. 按一下 [ **新增/移除資料行** ] 按鈕。

     \- 或 -

     以滑鼠右鍵按一下任何欄標題，然後按一下 [ **新增/移除資料行**]。

2. 在 [ **新增/移除資料行** ] 對話方塊中，清除您要移除之資料行的核取方塊，然後按一下 **[確定]**。

#### <a name="to-add-a-previously-removed-column"></a>若要加入先前移除的資料行

1. 按一下 [ **新增/移除資料行** ] 按鈕。

     \- 或 -

     以滑鼠右鍵按一下任何欄標題，然後按一下 [ **新增/移除資料行**]。

2. 在 [ **新增/移除資料行** ] 對話方塊中，選取您要加入之資料行的核取方塊，然後按一下 **[確定]**。

#### <a name="to-rearrange-columns"></a>重新排列資料行

1. 按一下 [ **新增/移除資料行** ] 按鈕。

     \- 或 -

     以滑鼠右鍵按一下任何欄標題，然後按一下 [ **新增/移除資料行**]。

2. 在 [ **新增/移除資料行** ] 對話方塊中，選取您要移動的資料行，然後按一下向上箭號或向下箭號。

3. 當資料行位於您想要的位置時，請按一下 **[確定]**。

## <a name="copying-data-to-the-clipboard-or-excel"></a><a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a> 將資料複製到剪貼簿或 Excel
 您可以選取並將選取的程式碼計量資料列複製到剪貼簿，作為文字字串，其中包含每個資料行的名稱和值的一行。 您也可以按一下 [ **在 Microsoft Excel 中開啟清單** ]，將所有的程式碼度量結果匯出至 Excel 試算表

## <a name="creating-a-work-item-based-on-code-metric-results"></a><a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a> 根據程式碼度量結果建立工作專案
 您可以 [!INCLUDE[esprfound](../includes/esprfound-md.md)] 根據 [程式 **代碼度量結果** ] 視窗中的結果來建立工作專案。 建立工作專案時， [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會自動在 [ **標題** ] 欄位中輸入標題，並在 [歷程 **記錄** ] 索引標籤底下輸入程式碼計量資料。

 如需如何建立工作專案的詳細資訊，請參閱 [建立工作專案 &#91;重新導向&#93;](https://msdn.microsoft.com/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b)。

#### <a name="to-create-a-work-item-based-on-a-result"></a>若要根據結果建立工作專案

1. 以滑鼠右鍵按一下結果。

2. 指向 [ **建立工作專案**]，然後按一下您要建立 (**Bug** **]、[** 工作]) 的工作專案類型。

3. 填寫所有必要欄位來完成工作專案表單。

4. **在 [檔案**] 功能表上，按一下 [**全部儲存**] 以儲存工作專案。

#### <a name="to-create-a-bug-based-on-a-result"></a>若要根據結果建立 bug

1. 按一下以選取結果。

2. 按一下 [ **建立工作專案** ] 按鈕。

3. 填寫所有必要欄位來完成工作專案表單。

4. **在 [檔案**] 功能表上，按一下 [**全部儲存**] 以儲存工作專案。

## <a name="see-also"></a>另請參閱
 [測量 Managed 程式碼的複雜性和可維護性](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)[如何：產生程式碼度量資料](../code-quality/how-to-generate-code-metrics-data.md)
