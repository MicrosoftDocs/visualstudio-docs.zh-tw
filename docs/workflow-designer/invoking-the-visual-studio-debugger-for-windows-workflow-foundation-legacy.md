---
title: "叫用 Visual Studio Debugger for Windows Workflow Foundation （舊版） |Microsoft 文件"
ms.date: 11/04/2016
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e3d1b00cc3f838de8d70310e56f6cdb3476cf742
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>叫用 Visual Studio Debugger for Windows Workflow Foundation (舊版)
本主題描述如何使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]偵錯工具偵錯[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]舊版的 Windows 工作流程設計工具中的應用程式。 當您需要以 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 或 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 為目標時，請使用舊版 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]。

 一般而言，偵錯舊版工作流程的方式就如同偵錯以其他 Visual Studio 程式語言撰寫的程式。 您可以使用下列方法啟動 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for Windows Workflow Foundation：

-   選取**附加至處理序**上**偵錯**功能表來選取從可用的處理序執行的工作流程執行個體。

-   按**F5**開始執行的工作流程執行個體，或叫用中斷點後繼續執行。

## <a name="stepping-through-code"></a>逐步執行程式碼
 偵錯工具所支援最常見的偵錯程序之一為逐步執行：就是一次執行一行程式碼。 逐步執行程式碼的命令有三個：

-   **逐步進入**： 您可以逐步執行的活動使用**F11**。 偵錯工具會逐步執行任何已定義的處理常式。 如果沒有定義處理常式，則不進入該活動；若為包含其他活動的複合活動，則逐步執行第一個執行中活動。 以下活動不支援從設計工具逐步進入程式碼處理常式： **IfElseActivity**， **WhileActivity**， **ConditionedActivityGroup**，或**ReplicatorActivity**。 若要偵錯與這些活動相關聯的處理常式，您必須將明確的中斷點放入程式碼中。

-   **跳離函式**： 逐步跳出活動使用**shift-f11**。 逐步跳出活動會將目前活動及其同層級活動執行到完成。 接著偵錯工具會在目前活動的父代上中斷。 從程式碼處理常式逐步跳出時，偵錯工具會在處理常式所關聯的活動上中斷。

-   **不進入函式**： 您可以不進入活動使用**F10**。 不進入複合活動時。 偵錯工具會在複合活動的第一個可執行子系上中斷。 不進入非複合，例如當**CodeActivity**偵錯工具的活動，在下一個活動上執行活動及其相關聯的處理常式和符號。 如果執行的活動是複合活動中最後一個子活動，則在執行後，偵錯工具會在父活動上中斷。

## <a name="attaching-to-a-process"></a>附加至處理序
 若要偵錯工作流程，藉由附加至處理程序，選取 [從可用的處理序**可用的處理序**清單方塊中的**附加至處理序**] 對話方塊。 如果**自動： 工作流程程式碼**不會顯示在**附加至**文字，然後按一下**選取**。 在**選取程式碼類型**對話方塊中，按一下 **偵錯這些程式碼類型**選取**工作流程**。 然後按一下 **確定**按一下**附加**。

## <a name="debugging-with-f5"></a>以 F5 偵錯
 如果工作流程主應用程式和工作流程 DLL 位在不同的 Visual Studio 專案中，例如，當您使用工作流程活動程式庫中，您必須為 Visual Studio 解決方案啟始專案，偵錯工作流程設定工作流程 DLL 專案使用**F5**。 您也必須在主應用程式在工作流程 DLL 專案的設定路徑**啟動外部程式**屬性。

 若要在 [方案總管] 中設定啟始專案，以滑鼠右鍵按一下專案名稱，然後選取**設定為啟始專案**。 若要將路徑設定中的主機**啟動外部程式**屬性中，按兩下工作流程專案的**屬性**節點在 [方案總管]，然後選取**偵錯**索引標籤。在下**起始動作**，選取**啟動外部程式**並輸入裝載您要偵錯工作的流程的.exe 檔案的路徑。

 如果主應用程式設為啟始專案，則只會叫用 Visual Studio 偵錯工具進行偵錯，不會叫用 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Debugger for Windows Workflow Foundation。 如果使用 Visual Studio 偵錯工具，則只會叫用 C# 或 Visual Basic 程式碼中斷點，不會叫用工作流程設計工具中設定的中斷點。 例如，如果使用 <xref:System.Workflow.Activities.ParallelActivity> Debugger for Windows Workflow Foundation，則會叫用您在設計工具中的 [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] 活動上設定的中斷點，但當您使用 Visual Studio 偵錯工具時不會叫用該中斷點。

## <a name="see-also"></a>另請參閱

- [如何：在工作流程中設定中斷點 (舊版)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)
- [偵錯舊版工作流程](../workflow-designer/debugging-legacy-workflows.md)