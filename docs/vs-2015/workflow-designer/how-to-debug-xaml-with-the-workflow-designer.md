---
title: 如何：使用工作流程設計工具 Debug XAML |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a696123551c24fd0d14fecde67826cf14f88826f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668653"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>HOW TO：使用工作流程設計工具偵測 XAML
工作流程是根據 XAML 所定義的。 工作流程的 UI 呈現方式，乃是建立在定義該工作流程的 XAML 樹狀結構上。 偵錯的體驗類似 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 中的工作流程偵錯。 例如，為 XAML 偵錯時，其區域變數、監看及執行緒視窗的運作方式，就像在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 中偵錯一樣。 此外，在 XAML 偵錯期間的呼叫堆疊檢視，也是工作流程執行流程的逐行階層架構檢視。

> [!NOTE]
> 如果為工作流程的 XAML 與活動位於同一個組件中，則不會包含類別名稱中的組件部分。 沒有類別 (活動) 名稱的這個部分，就不能在執行階段載入 XAML。 不建議在與主要專案的同一個命名空間中定義活動，否則，XAML 在設計工具中編輯之後必須手動編輯。

### <a name="to-debug-workflow-xaml"></a>若要進行工作流程 XAML 偵錯

1. 在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中開啟工作流程或活動專案。

2. 如[如何：在工作流程中設定中斷點中](../workflow-designer/how-to-set-breakpoints-in-workflows.md)所述，在您想要進行 debug 的活動或活動上設定中斷點。

3. 以滑鼠右鍵按一下包含您工作流程定義的 .xaml 檔案，然後選取 [ **View Code**]。 在設計檢視中設定中斷點的活動之後，您會看到該活動 XAML 項目宣告的同一行上顯示中斷點。

4. 如[如何：叫用工作流程偵錯工具](../workflow-designer/how-to-invoke-the-workflow-debugger.md)中所述，叫用偵錯工具。

5. 當程式碼執行到您的其中一個中斷點時，該中斷點關聯的 XAML 項目會出現醒目顯示。 若要移到下一個中斷點，請使用**F10**或**F11**鍵。

## <a name="see-also"></a>請參閱
 [如何：在工作流程中設定中斷點](../workflow-designer/how-to-set-breakpoints-in-workflows.md)[如何：叫用工作流程偵錯工具](../workflow-designer/how-to-invoke-the-workflow-debugger.md)