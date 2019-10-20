---
title: HOW TO：使用工作流程設計工具中的搜尋
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 12bda4af085b8ab41d3e11841f24cd5dfd389738
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650302"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>HOW TO：使用工作流程設計工具中的搜尋

為了方便建立更大型、更複雜的工作流程，您可以在工作流程設計工具內搜尋，以依關鍵字尋找專案。 請注意，設計工具不支援「取代」。

## <a name="quick-find"></a>快速尋找

[快速尋找] 會在設計工具中尋找下列內容：

- <xref:System.Activities.Activity> 物件、<xref:System.Activities.Statements.FlowNode> 物件、<xref:System.Activities.Statements.State> 物件、轉換及其他自訂流程控制項目的屬性。

- 變數

- 引數

- 運算式

### <a name="use-quick-find"></a>使用快速尋找

1. 在工作流程設計工具開啟時，按**Ctrl + F**，或選取 **編輯**  > **尋找並取代** > **快速尋找**。

2. 在 [**尋找目標**] 文字方塊中輸入搜尋字詞，然後按一下 **[尋找下一個]** 。

3. 搜尋字詞位於目前的工作流程中。 下圖顯示位於設計工具中的活動顯示名稱：

   ![Workflow Designer 中的搜尋結果](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>檔案中尋找

[檔案中尋找] 會尋找工作流程檔案中的字串，包括 XAML 檔案。

### <a name="use-find-in-files"></a>使用檔案中尋找

1. 在 Visual Studio 中，按**Ctrl** +**Shift** +**F**，或選取 **編輯**  > **尋找並取代** >  檔案**中尋找**。

2. 在 [**尋找目標**] 文字方塊中輸入搜尋專案，然後按一下 [**全部尋找**]。

3. 尋找結果會顯示在 [**尋找結果**] 視圖中。 按兩下結果專案，就會在工作流程設計工具中，流覽至包含符合專案的活動。