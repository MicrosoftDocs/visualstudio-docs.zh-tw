---
title: "如何： 在工作流程中設定中斷點 |Microsoft 文件"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 66ed757fab518d9cfe23b26186e6bded06eafe1e
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-set-breakpoints-in-workflows"></a>HOW TO：在工作流程中設定中斷點
當您使用 Windows 工作流程設計工具時，您可以設定中斷點，圖形化工作流程上與您會在 Visual Basic 或 C# 程式碼即可。 如預期般，工作流程執行會在您設定的每個中斷點上停止。

 中斷點有三種狀態：*暫止*，*繫結*，和*錯誤*。 設定中斷點時，狀態為「擱置」，由實心的紅色圖示表示。 如果執行階段已載入工作流程型別，中斷點就會變成「繫結」狀態。 如果您指定的中斷點格式不正確，例如活動名稱無效，就會出現錯誤視窗。 中斷點仍會新增至中斷點視窗，但以小的 "x" 記號標示。

> [!NOTE]
> 不支援在已叫用的工作流程上設定中斷點。

> [!WARNING]
> 請確定您選取選項**啟用 Just My Code （僅限 Managed）**從**工具**，**選項**，**偵錯**功能表之前偵錯。 如果您有兩個巢狀方式置於另一個序列的序列，而且您在第一個內部序列上設定中斷點，請按**F11**將不進行偵錯個第二個內部序列**啟用 Just My Code （僅限 Managed）**選項並未選取。

> [!WARNING]
> 如果 XAML 檔案屬性的完整路徑不正確，就不會取得工作流程中的中斷點。將專案/方案移至另一個資料夾或另一台機器之後，XAML 檔案的完整路徑即不正確。選取 Ctrl+S 以儲存並更新完整路徑屬性。

### <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>若要在設計檢視中的活動上設定中斷點

1.  選取您要偵錯工具中斷在哪一個活動上。

2.  在**偵錯**功能表上，選取**切換中斷點**。 活動左邊的最上方會出現紅色圖示。

     或者，您也可以按快速鍵**F9**之後選取的活動，或您可以在活動上按一下滑鼠右鍵並選取**中斷點**然後**插入中斷點**從內容功能表。

## <a name="see-also"></a>另請參閱

- [如何：叫用工作流程偵錯工具](../workflow-designer/how-to-invoke-the-workflow-debugger.md)
- [使用工作流程設計工具偵錯工作流程](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [如何：使用工作流程設計工具對 XAML 進行偵錯](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)