---
title: HOW TO：使用工作流程設計工具中的搜尋
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: b8a7a58e51706b5bd4d353595487984dd137c361
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55043373"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>HOW TO：使用工作流程設計工具中的搜尋

為了方便建立更大型且更複雜的工作流程，您可以搜尋關鍵字所尋找的項目在工作流程設計工具內。 請注意，設計工具不支援「取代」。

## <a name="quick-find"></a>快速尋找

快速尋找在設計工具中尋找下列：

-   <xref:System.Activities.Activity> 物件、<xref:System.Activities.Statements.FlowNode> 物件、<xref:System.Activities.Statements.State> 物件、轉換及其他自訂流程控制項目的屬性。

-   變數

-   引數

-   運算式

### <a name="use-quick-find"></a>使用快速尋找

1. 工作流程設計工具中開啟，然後按**Ctrl + F**，或選取**編輯** > **尋找和取代** > **快速尋找**.

2. 輸入搜尋詞彙**Find what**文字方塊中，按一下 **尋找下一個**。

3. 搜尋字詞位於目前的工作流程。 下圖顯示位於設計工具中的活動顯示名稱：

   ![Workflow Designer 中的搜尋結果](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>檔案中尋找

在檔案中的尋找會在工作流程檔案，包括 XAML 檔案中，找出字串。

### <a name="use-find-in-files"></a>使用 檔案中尋找

1.  在 Visual Studio 中按**Ctrl**+**Shift**+**F**，或選取**編輯** >  **尋找和取代** > **檔案中尋找**。

2.  輸入搜尋項目插入**Find what**文字方塊中，按一下 **全部尋找**。

3.  尋找結果所示**尋找結果**檢視。 按兩下結果項目會巡覽至工作流程設計工具中包含相符的活動。