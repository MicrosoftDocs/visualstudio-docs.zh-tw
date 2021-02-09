---
title: 程式碼度量視窗
ms.date: 12/12/2017
description: 瞭解如何查看、篩選、重新排列和匯出 Visual Studio 程式碼計量分析資料。 瞭解如何根據程式碼度量結果來建立工作專案。
ms.custom: SEO-VS-2020
ms.topic: reference
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c02f5a3b5175be4517a51a6dc477d6e59b38a762
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859563"
---
# <a name="use-the-code-metrics-results-window"></a>使用程式碼度量結果視窗

[程式 **代碼計量結果** ] 視窗會顯示程式碼計量分析所產生的資料。 如需程式碼計量資料值的詳細資訊，請參閱程式 [代碼度量值](../code-quality/code-metrics-values.md)。

## <a name="display-code-metrics-results"></a>顯示程式碼度量結果

當您產生程式碼度量結果時，會自動顯示 [程式 **代碼度量結果** ] 視窗。 您也可以在任何時間顯示視窗。

您可以使用下列其中一個功能表順序來顯示 [程式碼計量結果] 視窗：

- 在 [**分析**] 功能表上，選擇 [ **Windows** 程式  >  **代碼度量結果**]。

- 在 [ **View** ] 功能表上，選擇 [**其他 Windows** 程式  >  **代碼度量結果**]。

即使未包含任何結果，程式 **代碼度量結果** 視窗也會開啟。

### <a name="to-view-code-metrics-details"></a>若要查看程式碼計量詳細資料

如果已產生程式碼度量結果，請展開 [階層] 資料行中的樹狀 **結構** 。

## <a name="filter-code-metrics-results"></a>篩選程式代碼度量結果

您可以使用頂端的工具列，來篩選 [程式 **代碼度量結果** ] 視窗中顯示的結果。 例如，您可能只想要查看在65以下的可維護性索引的結果。

[ **篩選** ] 下拉式清單方塊包含結果資料行的名稱。 定義篩選時，會將其加入至清單底部，以及縮排。 此清單可以包含最後10個已定義的篩選準則。

### <a name="to-filter-the-code-metrics-results"></a>篩選程式代碼度量結果

1. 從 [ **篩選器** ] 清單中選取資料行名稱。

2. 在 [ **最** 小值] 中，輸入要顯示的最小值。

3. 在 [ **最** 大值] 中，輸入要顯示的最大值。

4. 按一下 [套用 **篩選** ] 按鈕。

5. 若要查看結果詳細資料，請展開階層樹狀結構。

## <a name="add-remove-and-rearrange-data-columns"></a>新增、移除和重新排列資料行

您可以從程式 **代碼度量結果** 視窗新增或移除結果資料行。 此外，您可以重新排列結果資料行，使其按照您想要的順序出現。

### <a name="add-or-remove-a-column"></a>新增或移除資料行

1. 按一下 [ **新增/移除資料行** ] 按鈕，或以滑鼠右鍵按一下任何欄標題，然後按一下 [ **新增/移除資料行**]。

1. 在 [ **新增/移除資料行** ] 對話方塊中，選取或清除您要加入或移除之資料行的核取方塊，然後選擇 **[確定]**。

### <a name="rearrange-columns"></a>重新排列資料行

1. 按一下 [ **新增/移除資料行** ] 按鈕。

1. 在 [ **新增/移除資料行** ] 對話方塊中，選取您要移動的資料行，然後選擇向上箭號或向下箭號。

1. 當資料行位於您想要的位置時，請選擇 **[確定]**。

## <a name="copy-data-to-the-clipboard-or-excel"></a>將資料複製到剪貼簿或 Excel

您可以選取並將選取的程式碼計量資料列複製到剪貼簿，作為文字字串，其中包含每個資料行的名稱和值的一行。 您也可以按一下 [ **在 Microsoft Excel 中開啟選取範圍** ]，將所有的程式碼度量結果匯出至 Excel 試算表。

## <a name="create-a-work-item-based-on-code-metric-results"></a>根據程式碼度量結果建立工作專案

您可以根據 [程式 **代碼度量結果**] 視窗中的結果來建立 [Azure Boards](/azure/devops/boards/index?view=vsts&preserve-view=true)工作專案。 建立工作專案時，Visual Studio 會在 [**記錄**] 索引標籤下的 [**標題**] 欄位和 [程式碼度量] 資料中自動輸入標題。

如需 Azure Boards 工作專案的詳細資訊，請參閱 [工作專案](/azure/devops/boards/work-items/index?view=vsts&preserve-view=true)。

### <a name="to-create-a-work-item-based-on-a-result"></a>若要根據結果建立工作專案

1. 以滑鼠右鍵按一下結果。

2. 指向 [ **建立工作專案**]，然後按一下您要建立 (**Bug** **]、[** 工作]) 的工作專案類型。

3. 填寫所有必要欄位來完成工作專案表單。

4. **在 [檔案**] 功能表上，按一下 [**全部儲存**] 以儲存工作專案。

### <a name="to-create-a-bug-based-on-a-result"></a>若要根據結果建立 bug

1. 按一下以選取結果。

2. 按一下 [ **建立工作專案** ] 按鈕。

3. 填寫所有必要欄位來完成工作專案表單。

4. **在 [檔案**] 功能表上，按一下 [**全部儲存**] 以儲存工作專案。

## <a name="see-also"></a>另請參閱

- [程式碼度量值](../code-quality/code-metrics-values.md)
- [How to：產生程式碼度量資料](../code-quality/how-to-generate-code-metrics-data.md)
