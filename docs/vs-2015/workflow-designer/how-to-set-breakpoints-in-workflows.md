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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659144"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>HOW TO：在工作流程中設定中斷點
使用 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 時，您可以在圖形化工作流程上設定中斷點，就像利用 Visual Basic 或 C# 程式碼設定一樣。 如預期般，工作流程執行會在您設定的每個中斷點上停止。

 中斷點有三種狀態：*暫*止 *、已系結和**錯誤*。 設定中斷點時，狀態為「擱置」，由實心的紅色圖示表示。 如果執行階段已載入工作流程型別，中斷點就會變成「繫結」狀態。 如果您指定的中斷點格式不正確，例如活動名稱無效，就會出現錯誤視窗。 中斷點仍會新增至中斷點視窗，但以小的 "x" 記號標示。

> [!NOTE]
> 不支援在已叫用的工作流程上設定中斷點。
>
> [!WARNING]
> 在進行偵錯工具之前，請確定您已從 [**工具**]、[**選項**]、[**調試**程式] 功能表中選取 [**啟用 Just My Code () 管理**] 選項。 如果您有兩個序列在另一個序列內，並在第一個內部序列上設定中斷點，則如果未選取 [<strong>啟用 Just My Code (僅限 Managed]) </strong>選項，按**F11**鍵將不會在第二個內部序列中進行偵錯工具。
>
> [!WARNING]
> 如果 XAML 檔案屬性的完整路徑不正確，就不會取得工作流程中的中斷點。將專案/方案移至另一個資料夾或另一台機器之後，XAML 檔案的完整路徑即不正確。選取 Ctrl+S 以儲存並更新完整路徑屬性。

### <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>若要在設計檢視中的活動上設定中斷點

1. 選取您要偵錯工具中斷在哪一個活動上。

2. 在 [ **調試** ] 功能表上，選取 [ **切換中斷點**]。 活動左邊的最上方會出現紅色圖示。

     或者，您也可以在選取活動之後按下快速鍵 **F9** 鍵，也可以在活動上按一下滑鼠右鍵，然後從操作功能表中選取 [ **中斷點** ]，然後 **插入中斷點** 。

## <a name="see-also"></a>另請參閱
 如何：使用工作流程設計工具的 how [to：使用工作流程設計工具來對 XAML 進行調試](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)程式，以叫用[工作流程偵錯工具](../workflow-designer/how-to-invoke-the-workflow-debugger.md)[調試](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)程式