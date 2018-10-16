---
title: 使用程式碼度量資料 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: 19
author: erickson-doug
ms.author: gewarren
manager: douge
ms.openlocfilehash: ae1ba68981b3ed462fc4f0f849226913c81ce1e8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49302207"
---
# <a name="working-with-code-metrics-data"></a>使用程式碼度量資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**程式碼度量結果**視窗會顯示所產生的程式碼度量資訊分析的資料。 如需有關程式碼度量資料值的詳細資訊，請參閱[程式碼度量值](../code-quality/code-metrics-values.md)。  
  
 此主題包括下列章節：  
  
-   [Code Metrics Results Window](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)  
  
-   [顯示程式碼度量結果](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)  
  
-   [篩選程式碼度量結果](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)  
  
-   [新增、 移除及重新排列資料行](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)  
  
-   [將資料複製到剪貼簿或 Excel](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)  
  
-   [建立工作項目，根據程式碼度量結果](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)  
  
##  <a name="BKMK_CodeMetricsResultsWindow"></a> Code Metrics Results Window  
 **程式碼度量結果**視窗有工具列則位於頂端和資料行，顯示計算的結果。  
  
|資料行|描述|  
|------------|-----------------|  
|**階層架構**|**階層**資料行包含的程式碼階層架構，您可以展開或摺疊來查看您想要的詳細層級的樹狀檢視。 其餘的資料行顯示計算的結果。 您可以隱藏，或視需要排列結果資料行。|  
|**可維護性**|**可維護性**資料行包含數值的結果除了的圖示。 綠色圖示表示可維護性相當高的程度。 黃色圖示表示可維護性中等程度。 紅色圖示表示低的可維護性和潛在的問題點。 這些色彩指示器會對應至所使用的 FxCop 規則 AvoidUnmaintainableCode 嚴重性分類。 如果可維護性指數小於 10，如果索引是介於 10 和 20，和不發生錯誤或警告，如果索引是 20 以上的警告，此規則就會引發錯誤。 可維護性指數是三個度量的合成： 循環複雜度、 程式碼和計算的複雜度。 其值不是以單位表示。|  
  
##  <a name="BKMK_DisplayingCodeMetricsResults"></a> 顯示程式碼度量結果  
 當您產生程式碼度量結果時，會自動顯示程式碼度量結果視窗。 您也可以在任何時候顯示的視窗。  
  
#### <a name="to-display-the-code-metrics-results-window"></a>若要顯示程式碼度量結果視窗  
  
-   在 **分析** 功能表中，按一下**Windows** ，然後按一下 **程式碼度量結果**。  
  
     \-或-  
  
-   在 **檢視**功能表上，指向**其他 Windows** ，然後按一下 **程式碼度量結果**。  
  
     即使在不含任何結果時，會顯示程式碼度量結果視窗。  
  
#### <a name="to-view-code-metrics-details"></a>若要檢視程式碼度量詳細資料  
  
-   如果已產生程式碼度量結果，展開樹狀目錄中的**階層**資料行。  
  
##  <a name="BKMK_FilteringCodeMetricsResults"></a> 篩選程式碼度量結果  
 您可以篩選會顯示在結果**程式碼度量結果**視窗使用頂端的工具列。 例如，您可能要查看具有可維護性指數 65 以下結果。  
  
 **篩選**下拉式清單方塊包含 結果資料行的名稱。 定義篩選時，會將它新增至與縮排清單的底部。 此清單可以包含最後十個已定義的篩選。  
  
#### <a name="to-filter-the-code-metrics-results"></a>若要篩選程式碼度量結果  
  
1.  從**篩選**清單中，選取資料行名稱。  
  
2.  在  **Min**，輸入要顯示的最小值。  
  
3.  在  **Max**，輸入要顯示的最大值。  
  
4.  按一下 [**套用篩選條件**] 按鈕。  
  
5.  若要查看的結果詳細資料，請展開階層樹狀結構。  
  
##  <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a> 新增、 移除及重新排列資料行  
 您可以新增或移除結果中的資料行**程式碼度量結果**視窗。 此外，您可以重新排列結果資料行，使其出現在您想要的順序。  
  
#### <a name="to-remove-a-column"></a>若要移除資料行  
  
1.  按一下 [**新增/移除資料行**] 按鈕。  
  
     \-或-  
  
     以滑鼠右鍵按一下任何欄標題，然後按一下**新增/移除欄位**。  
  
2.  在 [**新增/移除資料行**] 對話方塊中，清除核取方塊資料行，您想要移除，然後按一下**確定**。  
  
#### <a name="to-add-a-previously-removed-column"></a>若要加入先前移除的資料行  
  
1.  按一下 [**新增/移除資料行**] 按鈕。  
  
     \-或-  
  
     以滑鼠右鍵按一下任何欄標題，然後按一下**新增/移除欄位**。  
  
2.  在 **新增/移除資料行**對話方塊方塊中，選取您想要新增，然後按一下資料行的核取方塊**確定**。  
  
#### <a name="to-rearrange-columns"></a>若要重新排列資料行  
  
1.  按一下 [**新增/移除資料行**] 按鈕。  
  
     \-或-  
  
     以滑鼠右鍵按一下任何欄標題，然後按一下**新增/移除欄位**。  
  
2.  在 **新增/移除資料行**對話方塊方塊中，選取您想要移動，然後按一下 向上鍵或向下箭號的資料行。  
  
3.  當資料行位於您想要的位置時，按一下**確定**。  
  
##  <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a> 將資料複製到剪貼簿或 Excel  
 您可以選取，並將選取的資料列的程式碼計量資料複製到剪貼簿中，為文字字串，其中包含一條線的名稱和值的每個資料行。 您也可以按一下**在 Microsoft Excel 中開啟清單**，將所有的程式碼度量結果匯出至 Excel 試算表  
  
##  <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a> 建立工作項目，根據程式碼度量結果  
 您可以建立[!INCLUDE[esprfound](../includes/esprfound-md.md)]為基礎的工作項目會導致**程式碼度量結果**視窗。 建立工作項目時，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]會自動輸入其中一個職銜**Title**下的欄位和程式碼度量資料**歷程記錄** 索引標籤。  
  
 如需如何建立工作項目相關的詳細資訊，請參閱[建立工作項目&#91;重新導向&#93;](http://msdn.microsoft.com/en-us/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b)。  
  
#### <a name="to-create-a-work-item-based-on-a-result"></a>若要建立根據結果的工作項目  
  
1.  以滑鼠右鍵按一下結果。  
  
2.  指向**建立工作項目**，然後按一下您想要建立的工作項目類型 (**Bug**，**工作**，依此類推)。  
  
3.  填寫所有必要欄位，以完成工作項目表單。  
  
4.  在 **檔案**功能表上，按一下**全部儲存**儲存工作項目。  
  
#### <a name="to-create-a-bug-based-on-a-result"></a>若要建立根據結果的 bug  
  
1.  按一下以選取它的結果。  
  
2.  按一下 [**建立工作項目**] 按鈕。  
  
3.  填寫所有必要欄位，以完成工作項目表單。  
  
4.  在 **檔案**功能表上，按一下**全部儲存**儲存工作項目。  
  
## <a name="see-also"></a>另請參閱  
 [測量的複雜度與可維護性 Managed 程式碼](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)   
 [如何：產生程式碼度量資料](../code-quality/how-to-generate-code-metrics-data.md)



