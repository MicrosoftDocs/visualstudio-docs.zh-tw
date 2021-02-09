---
title: 在工作流程中設定中斷點
description: '瞭解如何使用工作流程設計工具在圖形化工作流程上設定中斷點，就像在 Visual Basic 或 c # 程式碼中所做的一樣。'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3fa7dc307dfef26bb8ab46f0df62f40bc0f4d5c2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894149"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>如何：在工作流程中設定中斷點

當您使用工作流程設計工具時，您可以在圖形化工作流程上設定中斷點，就像在 Visual Basic 或 c # 程式碼中所做的一樣。 如預期般，工作流程執行會在您設定的每個中斷點上停止。

中斷點有三種狀態：*暫* 止 *、已系結和**錯誤*。 設定中斷點時，狀態為「擱置」，由實心的紅色圖示表示。 如果執行階段已載入工作流程型別，中斷點就會變成「繫結」狀態。 如果您指定的中斷點格式不正確，例如活動名稱無效，就會出現錯誤視窗。 中斷點仍會新增至中斷點視窗，但以小的 "x" 記號標示。

> [!NOTE]
> 不支援在已叫用的工作流程上設定中斷點。

> [!NOTE]
> 在進行偵錯工具之前，請確定您已從 [**工具** 選項偵錯工具] 功能表中選取 [**啟用 Just My Code (僅限管理的)** ] 選項  >    >   。 如果未選取此選項，且您有兩個序列在另一個序列內，而且您在第一個內部序列上設定中斷點，則按 **F11** 鍵並不會在第二個內部序列中進行 debug。

> [!NOTE]
> 如果 XAML 檔案屬性的完整路徑不正確，則不會叫用工作流程中的中斷點。 將專案或方案移至另一個資料夾或另一部電腦之後，XAML 檔案的完整路徑是不正確的。 選取 **Ctrl** + **S** 以儲存並更新 [完整路徑] 屬性。

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>若要在設計檢視中的活動上設定中斷點

1. 選取您要偵錯工具中斷在哪一個活動上。

2. 在 [ **調試** ] 功能表上，選取 [ **切換中斷點**]。 活動左邊的最上方會出現紅色圖示。

   或者，您可以在選取活動之後按 **F9** ，也可以在活動上按一下滑鼠右鍵，然後  >  從快顯功能表中選取 [中斷點 **插入中斷點**]。

## <a name="see-also"></a>另請參閱

- [使用工作流程設計工具偵錯工作流程](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [HOW TO：使用工作流程設計工具偵測 XAML](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)
