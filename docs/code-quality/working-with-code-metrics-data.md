---
title: 程式碼度量視窗
ms.date: 12/12/2017
ms.topic: reference
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8bcaa3688486831f83712dc0cf0ee3e4a17c4a22
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55918373"
---
# <a name="use-the-code-metrics-results-window"></a>使用程式碼度量結果視窗

**程式碼度量結果**視窗會顯示所產生的程式碼度量資訊分析的資料。 如需有關程式碼度量資料值的詳細資訊，請參閱[程式碼度量值](../code-quality/code-metrics-values.md)。

## <a name="display-code-metrics-results"></a>顯示程式碼度量結果

**程式碼度量結果**視窗會自動顯示，當您產生程式碼度量結果。 您也可以在任何時候顯示的視窗。

您可以顯示程式碼度量結果視窗中，使用下列功能表序列的其中一個：

- 在 **分析**功能表上，選擇**Windows** > **程式碼度量結果**。

- 在 **檢視**功能表上，選擇**其他 Windows** > **程式碼度量結果**。

**程式碼度量結果**視窗隨即開啟，即使它包含沒有任何結果。

### <a name="to-view-code-metrics-details"></a>若要檢視程式碼度量詳細資料

如果已產生程式碼度量結果，展開樹狀目錄中的**階層**資料行。

## <a name="filter-code-metrics-results"></a>篩選程式碼度量結果

您可以篩選會顯示在結果**程式碼度量結果**視窗使用頂端的工具列。 例如，您可能要查看具有可維護性指數 65 以下結果。

**篩選**下拉式清單方塊包含 結果資料行的名稱。 定義篩選時，會將它新增至與縮排清單的底部。 此清單可以包含最後 10 個已定義的篩選。

### <a name="to-filter-the-code-metrics-results"></a>若要篩選程式碼度量結果

1.  從**篩選**清單中，選取資料行名稱。

2.  在  **Min**，輸入要顯示的最小值。

3.  在  **Max**，輸入要顯示的最大值。

4.  按一下 [**套用篩選條件**] 按鈕。

5.  若要查看的結果詳細資料，請展開階層樹狀結構。

## <a name="add-remove-and-rearrange-data-columns"></a>新增、 移除和重新排列資料行

您可以新增或移除結果中的資料行**程式碼度量結果**視窗。 此外，您可以重新排列結果資料行，使其出現在您想要的順序。

### <a name="add-or-remove-a-column"></a>新增或移除資料行

1. 按一下 **新增/移除資料行**按鈕，或以滑鼠右鍵按一下任何欄標題，然後按一下**新增/移除欄位**。

1. 在 [**新增/移除資料行**] 對話方塊中，選取或清除核取方塊資料行，您想要新增或移除，然後選擇**確定**。

### <a name="rearrange-columns"></a>重新排列資料行

1. 按一下 [**新增/移除資料行**] 按鈕。

1. 在 **新增/移除資料行**對話方塊方塊中，選取您想要移動，然後選擇 向上鍵或向下箭號的資料行。

1. 當您想要的位置定位的資料行時，選擇**確定**。

## <a name="copy-data-to-the-clipboard-or-excel"></a>將資料複製到剪貼簿或 Excel

您可以選取，並將選取的資料列的程式碼計量資料複製到剪貼簿中，為文字字串，其中包含一條線的名稱和值的每個資料行。 您也可以按一下**在 Microsoft Excel 中開啟選取項目**，將所有的程式碼度量結果匯出至 Excel 試算表。

## <a name="create-a-work-item-based-on-code-metric-results"></a>建立工作項目，根據程式碼度量結果

您可以建立[Azure 面板](/azure/devops/boards/index?view=vsts)為基礎的工作項目導致**程式碼度量結果**視窗。 建立工作項目時，Visual Studio 會自動輸入其中一個職銜**標題**下方的欄位和程式碼度量資料**歷程記錄** 索引標籤。

如需有關 Azure 版工作項目，請參閱 <<c0> [ 的工作項目](/azure/devops/boards/work-items/index?view=vsts)。

### <a name="to-create-a-work-item-based-on-a-result"></a>若要建立根據結果的工作項目

1.  以滑鼠右鍵按一下結果。

2.  指向**建立工作項目**，然後按一下您想要建立的工作項目類型 (**Bug**，**工作**，依此類推)。

3.  填寫所有必要欄位，以完成工作項目表單。

4.  在 **檔案**功能表上，按一下**全部儲存**儲存工作項目。

### <a name="to-create-a-bug-based-on-a-result"></a>若要建立根據結果的 bug

1.  按一下以選取它的結果。

2.  按一下 [**建立工作項目**] 按鈕。

3.  填寫所有必要欄位，以完成工作項目表單。

4.  在 **檔案**功能表上，按一下**全部儲存**儲存工作項目。

## <a name="see-also"></a>另請參閱

- [程式碼度量值](../code-quality/code-metrics-values.md)
- [如何：產生程式碼度量資料](../code-quality/how-to-generate-code-metrics-data.md)