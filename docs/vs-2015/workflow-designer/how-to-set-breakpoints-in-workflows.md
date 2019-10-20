---
title: 如何：在工作流程中設定中斷點 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2d1bbb18a9015b52b3d65cb8f8fd02674693abc0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659144"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>HOW TO：在工作流程中設定中斷點
使用 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 時，您可以在圖形化工作流程上設定中斷點，就像利用 Visual Basic 或 C# 程式碼設定一樣。 如預期般，工作流程執行會在您設定的每個中斷點上停止。

 中斷點有三個狀態： [*擱置*]、[系結 *] 和 [* *錯誤*]。 設定中斷點時，狀態為「擱置」，由實心的紅色圖示表示。 如果執行階段已載入工作流程型別，中斷點就會變成「繫結」狀態。 如果您指定的中斷點格式不正確，例如活動名稱無效，就會出現錯誤視窗。 中斷點仍會新增至中斷點視窗，但以小的 "x" 記號標示。

> [!NOTE]
> 不支援在已叫用的工作流程上設定中斷點。
>
> [!WARNING]
> 請確定您在 debug 之前，從 [**工具**]、[**選項**]、[**調試**程式] 功能表選取 [**啟用 Just My Code （僅限 Managed）** ] 選項。 如果您有兩個序列位於另一個序列內，而且您在第一個內部序列上設定中斷點，則如果未選取 [<strong>啟用 Just My Code （僅限 Managed）</strong>] 選項，按**F11**將不會在第二個內部序列中進行 debug。
>
> [!WARNING]
> 如果 XAML 檔案屬性的完整路徑不正確，就不會取得工作流程中的中斷點。將專案/方案移至另一個資料夾或另一台機器之後，XAML 檔案的完整路徑即不正確。選取 Ctrl+S 以儲存並更新完整路徑屬性。

### <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>若要在設計檢視中的活動上設定中斷點

1. 選取您要偵錯工具中斷在哪一個活動上。

2. 在 [**調試**] 功能表上，選取 [**切換中斷點**]。 活動左邊的最上方會出現紅色圖示。

     或者，您也可以在選取活動之後按下快速鍵**F9**鍵，或以滑鼠右鍵按一下活動，然後選取 [**中斷點**]，然後從內容功能表中**插入中斷點**。

## <a name="see-also"></a>請參閱
 [如何：](../workflow-designer/how-to-invoke-the-workflow-debugger.md) [使用工作流程設計工具叫用](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)工作流程偵錯工具的偵錯工具工作流程[如何：使用工作流程設計工具進行 XAML 的 Debug](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)