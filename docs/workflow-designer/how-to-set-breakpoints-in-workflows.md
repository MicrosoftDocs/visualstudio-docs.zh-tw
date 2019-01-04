---
title: 工作流程設計工具-如何：在工作流程中設定中斷點
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3bd6e10732c0248206810c9690910a8bd2f09ccf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53849628"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>HOW TO：在工作流程中設定中斷點

當您使用工作流程設計工具時，您可以設定中斷點，在您的圖形化工作流程和一樣在 Visual Basic 或 C# 程式碼中即可。 如預期般，工作流程執行會在您設定的每個中斷點上停止。

中斷點有三種狀態：*暫止*，*繫結*，以及*錯誤*。 設定中斷點時，狀態為「擱置」，由實心的紅色圖示表示。 如果執行階段已載入工作流程型別，中斷點就會變成「繫結」狀態。 如果您指定的中斷點格式不正確，例如活動名稱無效，就會出現錯誤視窗。 中斷點仍會新增至中斷點視窗，但以小的 "x" 記號標示。

> [!NOTE]
> 不支援在已叫用的工作流程上設定中斷點。

> [!NOTE]
> 請確定您選取的選項**啟用 Just My Code （僅限 Managed）** 從**工具** > **選項** > **偵錯**之前您偵錯 功能表。 如果未選取此選項，以及擁有巢狀在另一個序列中，兩個序列，您的第一個內部序列上設定中斷點，按下**F11**不偵錯到第二個內部序列。

> [!NOTE]
> 如果 XAML 檔案屬性的完整路徑不正確，不會叫用工作流程中的中斷點。 將專案或方案移到另一個資料夾或另一部電腦之後，不正確 XAML 檔案的完整路徑。 選取  **Ctrl**+**S**以儲存並更新完整路徑屬性。

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>若要在設計檢視中的活動上設定中斷點

1. 選取您要偵錯工具中斷在哪一個活動上。

2. 在 **偵錯**功能表上，選取**切換中斷點**。 活動左邊的最上方會出現紅色圖示。

   或者，您可以按**F9**選取活動，或者您可以在活動上按一下滑鼠右鍵並選取之後**中斷點** > **插入中斷點**從內容功能表。

## <a name="see-also"></a>另請參閱

- [使用工作流程設計工具偵錯工作流程](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [如何：偵錯 XAML 與工作流程設計工具](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)