---
title: 工作流程設計工具-如何： 在工作流程 （舊版） 中設定中斷點
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- breakpoints, setting in workflows
- debugging, setting breakpoints in workflows
- debugging workflows, setting breakpoints
- workflows, setting breakpoints
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c0c70b630404830fa8c733a7310e4700da8f08b3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975191"
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>HOW TO：在工作流程中設定中斷點 (舊版)

本主題描述如何在 Windows Workflow Foundation (WF) 使用舊版的 Windows 工作流程設計工具建置的應用程式設定中斷點。 Windows Workflow Foundation 應用程式需要.NET Framework 3.5 版或 WinFX 為目標時，請使用舊版工作流程設計工具。

 當您使用 Visual Studio 2010 中的舊版工作流程設計工具來建置 Windows Workflow Foundation 應用程式時，您可以設定中斷點，在 C# 和 Visual Basic 程式碼在 Visual Studio 中一樣即可。 如預期般，工作流程執行會在您設定的每個中斷點上停止。

 中斷點有三種狀態：*暫止*，*繫結*，和*錯誤*。 設定中斷點時，狀態為「擱置」，由空心的紅色圖示表示。 執行階段已載入工作流程類型時，中斷點會變成「繫結」狀態，由實心的紅色圖示表示。 如果您指定錯誤的中斷點格式，且活動名稱無效，則會顯示錯誤視窗。 中斷點仍會新增至中斷點視窗，但以小的 "x" 記號標示。

 在工作流程設計介面中，您可以使用以下方式在活動中設定中斷點：

-   以滑鼠右鍵按一下活動，然後選取**中斷點 \ 插入中斷點**。

-   選取該活動並按 F9。

-   選取**新增中斷點**從**偵錯**功能表。

     當偵錯工具在中斷點處停止時，您也可以使用這個選項來設定偵錯時的新中斷點。

    > [!NOTE]
    > 不支援在已叫用的工作流程上設定中斷點。

### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>若要使用偵錯功能表上的新增中斷點選項設定中斷點

1.  在**偵錯**功能表上，選取**新增中斷點**。

2.  按一下**在函式中斷**。

     **新增中斷點**對話方塊隨即開啟。

3.  指定的名稱中的活動**函式**文字方塊中，使用此語法： `QualifiedActivityId[:[FullClassName][:InstanceId]]`。

    > [!NOTE]
    > （選擇性） 而非使用中的活動名稱**函式** 文字方塊中，您可以藉由指定的工作流程活動絕對路徑設定中斷點。 例如，假設您擁有名為工作流程解決方案**WorkflowConsoleApplication1**以及名為方案中的工作流程**Workflow1**使用活動呼叫**Delay1**. 您可以使用活動名稱**Delay1**或指定的路徑做為**Delay1:WorkflowConsoleApplication1.Workflow1**或**Delay1:WorkflowConsoleApplication1.Workflow1: {6614886A-608E-412B-BF98-99FF1559DDDF}**。

4.  選取**使用 IntelliSense**核取方塊，以確認函式名稱。

     如果未選取這個核取方塊，則不會執行中斷點名稱驗證。

5.  選取**工作流程**從**語言**清單。

6.  按一下 [確定 **Deploying Office Solutions**]。

## <a name="see-also"></a>另請參閱

- [偵錯舊版工作流程](../workflow-designer/debugging-legacy-workflows.md)
- [叫用 Visual Studio Debugger for Windows Workflow Foundation (舊版)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)