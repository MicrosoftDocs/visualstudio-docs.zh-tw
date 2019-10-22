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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0824fe608ad1bac86ef904702bd1be907bc9ce7d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649000"
---
# <a name="use-the-code-metrics-results-window"></a>使用程式碼度量結果視窗

[程式**代碼計量結果**] 視窗會顯示程式碼計量分析所產生的資料。 如需程式碼度量資料值的詳細資訊，請參閱程式[代碼度量值](../code-quality/code-metrics-values.md)。

## <a name="display-code-metrics-results"></a>顯示程式碼度量結果

當您產生程式碼度量結果時，會自動顯示 [程式**代碼度量] 結果**視窗。 您也可以隨時顯示視窗。

您可以使用下列其中一個功能表順序來顯示 [程式碼計量結果] 視窗：

- 在 [**分析**] 功能表上，選擇 [ **Windows** >  程式**代碼計量結果**]。

- 在 [ **View** ] 功能表上，選擇 [**其他 Windows** >  程式**代碼計量結果**]。

[程式**代碼度量] 結果**視窗隨即開啟，即使它沒有包含任何結果。

### <a name="to-view-code-metrics-details"></a>若要查看程式碼計量詳細資料

如果已產生程式碼計量結果，請展開 [階層] 資料行中的樹狀**結構**。

## <a name="filter-code-metrics-results"></a>篩選程式代碼度量結果

您可以使用頂端的工具列，篩選 [程式**代碼度量] 結果**視窗中顯示的結果。 例如，您可能只想查看在65以下的可維護性索引的結果。

[**篩選**] 下拉式方塊包含 [結果] 資料行的名稱。 定義篩選時，會將它與縮排一併加入清單的底部。 清單可以包含最後10個已定義的篩選。

### <a name="to-filter-the-code-metrics-results"></a>篩選程式代碼度量結果

1. 從 [**篩選器**] 清單中，選取資料行名稱。

2. 在 [**最**小值] 中，輸入要顯示的最小值。

3. 在 [**最大**值] 中，輸入要顯示的最大值。

4. 按一下 [套用**篩選**] 按鈕。

5. 若要查看結果詳細資料，請展開階層樹狀結構。

## <a name="add-remove-and-rearrange-data-columns"></a>新增、移除和重新排列資料行

您可以從 [程式**代碼度量] 結果**視窗加入或移除 [結果] 資料行。 此外，您可以重新排列 [結果] 資料行，使其以您想要的順序顯示。

### <a name="add-or-remove-a-column"></a>加入或移除資料行

1. 按一下 [**新增/移除資料行**] 按鈕，或以滑鼠右鍵按一下任何資料行標題，然後按一下 [**新增/移除資料行**]。

1. 在 [**新增/移除資料行**] 對話方塊中，選取或清除您要新增或移除之資料行的核取方塊，然後選擇 **[確定]** 。

### <a name="rearrange-columns"></a>重新排列資料行

1. 按一下 [**新增/移除資料行**] 按鈕。

1. 在 [**新增/移除資料行**] 對話方塊中，選取您想要移動的資料行，然後選擇向上箭號或向下箭號。

1. 當資料行位於您想要的位置時，請選擇 **[確定]** 。

## <a name="copy-data-to-the-clipboard-or-excel"></a>將資料複製到剪貼簿或 Excel

您可以選取並將選取的程式碼計量資料列複製到剪貼簿做為文字字串，其中包含每個資料行之名稱和值的一行。 您也可以按一下 [**在 Microsoft Excel 中開啟選取專案**]，將所有的程式碼計量結果匯出至 Excel 試算表。

## <a name="create-a-work-item-based-on-code-metric-results"></a>根據程式碼度量結果建立工作專案

您可以根據 [程式**代碼度量] 結果**視窗中的結果，建立[Azure Boards](/azure/devops/boards/index?view=vsts)工作專案。 建立工作專案時，Visual Studio 會自動在 [**標題**] 欄位中輸入標題，並在 [歷程**記錄**] 索引標籤底下的 [程式碼計量] 資料。

如需 Azure Boards 工作專案的詳細資訊，請參閱[工作專案](/azure/devops/boards/work-items/index?view=vsts)。

### <a name="to-create-a-work-item-based-on-a-result"></a>若要根據結果建立工作專案

1. 以滑鼠右鍵按一下結果。

2. 指向 [**建立工作專案**]，然後按一下您想要建立的工作專案類型（[**Bug**] **、[工作] 等等）** 。

3. 填寫所有必要的欄位，完成工作專案表單。

4. **在 [檔案**] 功能表上，按一下 [**全部儲存**] 以儲存工作專案。

### <a name="to-create-a-bug-based-on-a-result"></a>若要根據結果建立 bug

1. 按一下結果以選取它。

2. 按一下 [**建立工作專案**] 按鈕。

3. 填寫所有必要的欄位，完成工作專案表單。

4. **在 [檔案**] 功能表上，按一下 [**全部儲存**] 以儲存工作專案。

## <a name="see-also"></a>請參閱

- [程式碼度量值](../code-quality/code-metrics-values.md)
- [如何：產生程式碼度量資料](../code-quality/how-to-generate-code-metrics-data.md)
