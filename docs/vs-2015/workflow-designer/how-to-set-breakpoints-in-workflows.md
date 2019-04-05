---
title: HOW TO：在工作流程中設定中斷點 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2aaf61ada4167f29f1c6d4754ced7c9757054a88
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945834"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>HOW TO：在工作流程中設定中斷點
使用 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 時，您可以在圖形化工作流程上設定中斷點，就像利用 Visual Basic 或 C# 程式碼設定一樣。 如預期般，工作流程執行會在您設定的每個中斷點上停止。  
  
 中斷點有三種狀態：*暫止*，*繫結*，以及*錯誤*。 設定中斷點時，狀態為「擱置」，由實心的紅色圖示表示。 如果執行階段已載入工作流程型別，中斷點就會變成「繫結」狀態。 如果您指定的中斷點格式不正確，例如活動名稱無效，就會出現錯誤視窗。 中斷點仍會新增至中斷點視窗，但以小的 "x" 記號標示。  
  
> [!NOTE]
>  不支援在已叫用的工作流程上設定中斷點。  
> 
> [!WARNING]
>  請確定您選取的選項**啟用 Just My Code （僅限 Managed）** 從**工具**，**選項**，**偵錯**功能表之前偵錯。 如果您有兩個巢狀於另一個序列的序列，而且您在第一個內部序列上設定中斷點，按下**F11**將不進行偵錯到第二個內部序列<strong>啟用 Just My Code （僅限 Managed）</strong>未選取選項。  
> 
> [!WARNING]
>  如果 XAML 檔案屬性的完整路徑不正確，就不會取得工作流程中的中斷點。將專案/方案移至另一個資料夾或另一台機器之後，XAML 檔案的完整路徑即不正確。選取 Ctrl+S 以儲存並更新完整路徑屬性。  
  
### <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>若要在設計檢視中的活動上設定中斷點  
  
1.  選取您要偵錯工具中斷在哪一個活動上。  
  
2.  在 **偵錯**功能表上，選取**切換中斷點**。 活動左邊的最上方會出現紅色圖示。  
  
     或者，您也可以按快速鍵**F9**金鑰後選取的活動，或您可以以滑鼠右鍵按一下活動，並選取**中斷點**然後**插入中斷點**從內容功能表。  
  
## <a name="see-also"></a>另請參閱  
 [如何：叫用工作流程偵錯工具](../workflow-designer/how-to-invoke-the-workflow-debugger.md)   
 [偵錯工作流程與工作流程設計工具](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)   
 [如何：使用工作流程設計工具對 XAML 進行偵錯](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)