---
title: 叫用 Windows Workflow Foundation 的偵錯工具（舊版） |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- stepping
- Step Over command
- stepping, commands
- debugging, using workflow debugger
- workflows, debugger
- workflow debugger, starting
- Step In command
- debugger, workflow
- Step Out command
- debugging workflows, starting the debugger
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bcceca362f3c2a891d36f8f4e8071d0e35c8f164
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658985"
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>叫用 Visual Studio Debugger for Windows Workflow Foundation (舊版)
本主題描述如何在舊版 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中使用 [!INCLUDE[wf](../includes/wf-md.md)] 偵錯工具來偵錯 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 應用程式。 當您需要以 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 或 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 為目標時，請使用舊版 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]。

 一般而言，偵錯舊版工作流程的方式就如同偵錯以其他 Visual Studio 程式語言撰寫的程式。 您可以使用下列方法啟動 [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] Debugger for Windows Workflow Foundation：

- 選取 [**調試**程式] 功能表上的 [**附加至進程**]，從可用的進程中選取執行中的工作流程實例。

- 按**F5**開始執行工作流程的實例，或在叫用中斷點後繼續執行。

## <a name="stepping-through-code"></a>逐步執行程式碼
 偵錯工具所支援最常見的偵錯程序之一為逐步執行：就是一次執行一行程式碼。 逐步執行程式碼的命令有三個：

- **逐步**執行：您可以使用**F11**逐步執行活動。 偵錯工具會逐步執行任何已定義的處理常式。 如果沒有定義處理常式，則不進入該活動；若為包含其他活動的複合活動，則逐步執行第一個執行中活動。 下列活動不支援從設計工具逐步執行程式碼處理常式： **IfElseActivity**、 **WhileActivity**、 **ConditionedActivityGroup**或**ReplicatorActivity**。 若要偵錯與這些活動相關聯的處理常式，您必須將明確的中斷點放入程式碼中。

- **跳出**：您可以使用**Shift-F11**跳出活動。 逐步跳出活動會將目前活動及其同層級活動執行到完成。 接著偵錯工具會在目前活動的父代上中斷。 從程式碼處理常式逐步跳出時，偵錯工具會在處理常式所關聯的活動上中斷。

- 不進入函式：您可以使用**F10** **跳過活動**。 不進入複合活動時。 偵錯工具會在複合活動的第一個可執行子系上中斷。 當不進入非複合的（例如**CodeActivity**活動）時，偵錯工具會執行活動及其相關聯的處理常式，並在下一個活動上中斷。 如果執行的活動是複合活動中最後一個子活動，則在執行後，偵錯工具會在父活動上中斷。

## <a name="attaching-to-a-process"></a>附加至處理序
 若要藉由附加至進程來進行工作流程的偵錯工具，請從 [**附加至進程**] 對話方塊的 [**可用的進程**] 清單方塊中選取可用的進程。 如果 [**自動：工作流程程式碼**] 未顯示在 [**附加至**] 文字方塊中，然後按一下 [**選取**]。 在 [**選取程式碼類型**] 對話方塊中，按一下 [**偵錯工具代碼類型**]，然後選取 [**工作流程**]。 然後按一下 **[確定]** ，再按一下 [**附加**]。

## <a name="debugging-with-f5"></a>以 F5 偵錯
 如果工作流程主應用程式和工作流程 DLL 位在不同的 Visual Studio 專案中（例如，當您使用工作流程活動程式庫時），您必須將工作流程 DLL 專案設定為 Visual Studio 方案啟始專案，以對工作流程進行 debug使用**F5**。 您也必須在工作流程 DLL 專案的 [**啟動外部程式**] 屬性中設定主應用程式的路徑。

 若要在方案總管中設定啟始專案，請以滑鼠右鍵按一下專案名稱，然後選取 [**設定為啟始專案**]。 若要在 [**啟動外部程式**] 屬性中設定主控制項的路徑，請在方案總管中按兩下工作流程專案的 [**屬性**] 節點，然後選取 [**調試**程式] 索引標籤。在 [**起始動作**] 底下，選取 [**啟動外部程式**]，並輸入裝載您想要進行偵錯工具之工作流程的 .exe 檔案路徑。

 如果主應用程式設為啟始專案，則只會叫用 Visual Studio 偵錯工具進行偵錯，不會叫用 [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] Debugger for Windows Workflow Foundation。 如果使用 Visual Studio 偵錯工具，則只會叫用 C# 或 Visual Basic 程式碼中斷點，不會叫用工作流程設計工具中設定的中斷點。 例如，如果使用 <xref:System.Workflow.Activities.ParallelActivity> Debugger for Windows Workflow Foundation，則會叫用您在設計工具中的 [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] 活動上設定的中斷點，但當您使用 Visual Studio 偵錯工具時不會叫用該中斷點。

## <a name="see-also"></a>請參閱
 [如何：在工作流程中設定中斷點（舊版）](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [調試舊版工作流程](../workflow-designer/debugging-legacy-workflows.md)