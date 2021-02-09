---
title: HOW TO：使用工作流程設計工具中的搜尋
description: 瞭解如何在工作流程設計工具內搜尋，以依關鍵字尋找專案，讓您能夠更輕鬆地建立更大型、更複雜的工作流程。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6fb30d4846c24638f87989d2a7a716df06b0523b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894110"
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

1. 在工作流程設計工具開啟的情況下，按下 **Ctrl + F**，或選取 [**編輯**  >  **尋找並取代**  >  **快速尋找**]。

2. 在 [ **尋找目標** ] 文字方塊中輸入搜尋字詞，然後按一下 [ **找下一個]**。

3. 搜尋字詞位於目前的工作流程中。 下圖顯示在設計工具中找出的活動顯示名稱：

   ![Workflow Designer 中的搜尋結果](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>檔案中尋找

檔案中尋找會尋找工作流程檔案中的字串，包括 XAML 檔案。

### <a name="use-find-in-files"></a>使用檔案中尋找

1. 在 Visual Studio 中，按 **Ctrl** + **Shift** + **F**，或選取 [**編輯**  >  **尋找並取代** 檔案  >  **中尋找**]。

2. 在 [ **尋找目標** ] 文字方塊中輸入搜尋專案，然後按一下 [ **全部尋找**]。

3. 尋找結果會顯示在 [ **尋找結果** ] 視圖中。 按兩下結果專案，即可導覽至包含工作流程設計工具中相符專案的活動。