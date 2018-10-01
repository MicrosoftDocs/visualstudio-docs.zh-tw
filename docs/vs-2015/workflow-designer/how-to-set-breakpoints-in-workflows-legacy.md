---
title: 如何： 在工作流程 （舊版） 中設定中斷點 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- breakpoints, setting in workflows
- debugging, setting breakpoints in workflows
- debugging workflows, setting breakpoints
- workflows, setting breakpoints
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: ac587b238d52e8955a4fe70cabc89444b39c712d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47488855"
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>HOW TO：在工作流程中設定中斷點 (舊版)
本主題描述如何在使用舊版 [!INCLUDE[wf](../includes/wf-md.md)] 建置的 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 應用程式中設定中斷點。 當您的 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 應用程式需要以 [!INCLUDE[wf2](../includes/wf2-md.md)] 或 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 為目標時，請使用舊版 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]。  
  
 當您在 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 中使用舊版 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 來建置 [!INCLUDE[wf2](../includes/wf2-md.md)] 應用程式時，您可以在 C# 和 Visual Basic 程式碼中設定中斷點，就像在 Visual Studio 中一樣。 如預期般，工作流程執行會在您設定的每個中斷點上停止。  
  
 中斷點有三種狀態：*暫止*，*繫結*，並*錯誤*。 設定中斷點時，狀態為「擱置」，由空心的紅色圖示表示。 執行階段已載入工作流程類型時，中斷點會變成「繫結」狀態，由實心的紅色圖示表示。 如果您指定錯誤的中斷點格式，且活動名稱無效，則會顯示錯誤視窗。 中斷點仍會新增至中斷點視窗，但以小的 "x" 記號標示。  
  
 在工作流程設計介面中，您可以使用以下方式在活動中設定中斷點：  
  
-   以滑鼠右鍵按一下活動，然後選取**中斷點 \ 插入中斷點**。  
  
-   選取該活動並按 F9。  
  
-   選取 **新增中斷點**從**偵錯**功能表。  
  
     當偵錯工具在中斷點處停止時，您也可以使用這個選項來設定偵錯時的新中斷點。  
  
    > [!NOTE]
    >  不支援在已叫用的工作流程上設定中斷點。  
  
### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>若要使用偵錯功能表上的新增中斷點選項設定中斷點  
  
1.  在 **偵錯**功能表上，選取**新中斷點**。  
  
2.  按一下 **在函式中斷**。  
  
     **新的中斷點**對話方塊隨即開啟。  
  
3.  指定的名稱中的活動**函式**文字方塊中，使用下列語法： `QualifiedActivityId[:[FullClassName][:InstanceId]]`。  
  
    > [!NOTE]
    >  （選擇性） 而非使用中的活動名稱**函式** 文字方塊中，您可以藉由指定的工作流程活動的絕對路徑設定中斷點。 例如，假設您擁有名為工作流程解決方案**WorkflowConsoleApplication1**和名為方案中的工作流程**Workflow1**使用的活動**Delay1**. 您可以使用活動名稱**Delay1** ，或指定為路徑**Delay1:WorkflowConsoleApplication1.Workflow1**或**Delay1:WorkflowConsoleApplication1.Workflow1: {6614886A-608E-412B-BF98-99FF1559DDDF}**。  
  
4.  選取 **使用 IntelliSense**核取方塊，以確認函式名稱。  
  
     如果未選取這個核取方塊，則不會執行中斷點名稱驗證。  
  
5.  選取 **工作流程**從**語言**清單。  
  
6.  按一下 [確定 **Deploying Office Solutions**]。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯舊版工作流程](../workflow-designer/debugging-legacy-workflows.md)   
 [叫用 Visual Studio Debugger for Windows Workflow Foundation (舊版)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)