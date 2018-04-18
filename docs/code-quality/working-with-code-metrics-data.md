---
title: Visual Studio 中的程式碼度量結果視窗 |Microsoft 文件
ms.custom: ''
ms.date: 12/12/2017
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8663b2c8d0fe4de4fa4b2073827175e7bc65a91a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-code-metrics-results-window"></a>使用程式碼度量結果視窗

**程式碼度量結果**視窗會顯示所產生的程式碼度量分析的資料。 如需程式碼度量資料值的詳細資訊，請參閱[程式碼度量值](../code-quality/code-metrics-values.md)。

## <a name="displaying-code-metrics-results"></a>顯示程式碼度量結果

**程式碼度量結果**時產生程式碼度量結果視窗會自動顯示。 您也可以在任何時間，顯示視窗。

### <a name="to-display-the-code-metrics-results-window"></a>若要顯示程式碼度量結果視窗

- 在**分析**功能表上，選擇**Windows** > **程式碼度量結果**。

   \-或-

- 在**檢視**功能表上，選擇**其他視窗** > **程式碼度量結果**。

**程式碼度量結果**視窗隨即顯示，即使它包含沒有結果。

### <a name="to-view-code-metrics-details"></a>若要檢視程式碼度量詳細資料

如果已產生程式碼度量結果，展開樹狀目錄中的**階層**資料行。

## <a name="filtering-code-metrics-results"></a>篩選程式碼度量結果

您可以篩選會顯示在結果**程式碼度量結果**視窗使用頂端的工具列。 例如，您可以看到有 65 以下可維護性指數的結果。

**篩選**下拉式清單方塊包含的結果資料行的名稱。 當定義的篩選時，則會將其加入清單與縮排的底部。 清單可以包含已定義的最後十個篩選條件。

### <a name="to-filter-the-code-metrics-results"></a>若要篩選程式碼度量結果

1.  從**篩選**清單中，選取資料行名稱。

2.  在**Min**，輸入要顯示的最小值。

3.  在**Max**，輸入要顯示的最大值。

4.  按一下**套用篩選** 按鈕。

5.  若要查看結果詳細資料，請展開階層樹狀結構。

## <a name="adding-removing-and-rearranging-data-columns"></a>新增、 移除和重新排列資料行

您可以新增或移除結果中的資料行**程式碼度量結果**視窗。 此外，您可以重新排列結果資料行，使它們出現在您想要的順序。

### <a name="to-remove-a-column"></a>若要移除資料行

1. 按一下**新增/移除欄位** 按鈕。

     \- 或-以滑鼠右鍵按一下任何欄標題，然後按一下**新增/移除欄位**。

1. 在**新增/移除欄位**對話方塊中，清除核取方塊資料行，您想要移除，然後按一下 **確定**。

### <a name="to-add-a-previously-removed-column"></a>若要加入先前移除的資料行

1. 按一下**新增/移除欄位** 按鈕。

     \-或-

     以滑鼠右鍵按一下任何欄標題，然後按一下**新增/移除欄位**。

1. 在**新增/移除欄位**對話方塊方塊中，選取您想要加入，然後按一下 資料行的核取方塊**確定**。

### <a name="to-rearrange-columns"></a>若要重新排列資料行

1. 按一下**新增/移除欄位** 按鈕。

     \-或-

     以滑鼠右鍵按一下任何欄標題，然後按一下**新增/移除欄位**。

1. 在**新增/移除欄位**對話方塊方塊中，選取您想要移動，然後按一下向上鍵或向下箭號的資料行。

1. 當您想要的位置位於資料行時，按一下 **確定**。

## <a name="copying-data-to-the-clipboard-or-excel"></a>將資料複製到剪貼簿或 Excel

您可以選取，並為文字字串，其中包含一條線的名稱和每個資料行的值，將選取的資料列的程式碼度量資料複製到剪貼簿。 您也可以按一下**在 Microsoft Excel 中開啟選取項目**，將所有的程式碼度量結果匯出至 Excel 試算表。

## <a name="creating-a-work-item-based-on-code-metric-results"></a>建立工作項目，根據程式碼度量結果

您可以建立[Visual Studio Team Services (VSTS)](/vsts/index)為基礎的工作項目會導致**程式碼度量結果**視窗。 建立工作項目時，Visual Studio 會自動輸入中的標題**標題**底下的欄位和程式碼度量資料**記錄** 索引標籤。

如需有關 VSTS 工作項目，請參閱[工作項目 (VSTS)](/vsts/work/work-items/index)。

### <a name="to-create-a-work-item-based-on-a-result"></a>若要建立根據結果的工作項目

1.  以滑鼠右鍵按一下結果。

2.  指向**建立工作項目**，然後按一下您想要建立的工作項目類型 (**Bug**，**工作**，依此類推)。

3.  填入所有必要欄位，在完成工作項目表單。

4.  在**檔案**功能表上，按一下 **全部儲存**儲存工作項目。

### <a name="to-create-a-bug-based-on-a-result"></a>若要建立 bug，根據結果

1.  按一下以選取它的結果。

2.  按一下**建立工作項目** 按鈕。

3.  填入所有必要欄位，在完成工作項目表單。

4.  在**檔案**功能表上，按一下 **全部儲存**儲存工作項目。

## <a name="see-also"></a>另請參閱

- [程式碼度量值](../code-quality/code-metrics-values.md)
- [如何： 產生程式碼度量資料](../code-quality/how-to-generate-code-metrics-data.md)