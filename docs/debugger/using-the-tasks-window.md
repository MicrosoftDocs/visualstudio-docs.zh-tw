---
title: 使用工作視窗 |Microsoft Docs
ms.custom: ''
ms.date: 03/18/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6d22202e50c973c52bf2b47374b9eda583fb3fe8
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280879"
---
# <a name="using-the-tasks-window"></a>使用工作視窗

**任務**視窗類似於**執行緒**視窗中，差別在於前者顯示的資訊關於<xref:System.Threading.Tasks.Task?displayProperty=fullName>， [task_handle](/cpp/parallel/concrt/reference/task-group-class)，或[WinJS.Promise](/previous-versions/windows/apps/br211867(v=win.10))而不是每個執行緒的物件。 與執行緒一樣，工作代表可以並行執行的非同步作業，但是多項工作可能會在相同執行緒上執行。

在 managed 程式碼，您可以使用**工作**當您使用的視窗<xref:System.Threading.Tasks.Task?displayProperty=fullName>物件或使用**await**並**非同步**關鍵字 (**Await**並**非同步**在 visual Basic 中)。 如需在 managed 程式碼中的工作的詳細資訊，請參閱[平行程式設計](/dotnet/standard/parallel-programming/index)。

在原生程式碼，您可以使用**任務**視窗中，當您使用[工作群組](/cpp/parallel/concrt/task-parallelism-concurrency-runtime)，[平行演算法](/cpp/parallel/concrt/parallel-algorithms)，[非同步代理程式](/cpp/parallel/concrt/asynchronous-agents)，及[輕量型工作](/cpp/parallel/concrt/task-scheduler-concurrency-runtime)。 如需有關原生程式碼中的工作的詳細資訊，請參閱[並行執行階段](/cpp/parallel/concrt/concurrency-runtime)。

在 JavaScript 中，您可以使用 [工作] 視窗時您正在使用 promise`.then`程式碼。 請參閱[JavaScript (UWP app) 中的非同步程式設計](/previous-versions/windows/apps/hh700330(v=win.10))如需詳細資訊。

您可以使用**任務**只要您進入偵錯工具 視窗。 您可以在存取它**偵錯**功能表中的按一下**Windows** ，然後按一下**工作**。 如下圖所示**任務**視窗處於預設模式。

![工作視窗](../debugger/media/parallel_tasks_window.png "Parallel_Tasks_Window")

> [!NOTE]
> 在 managed 程式碼<xref:System.Threading.Tasks.Task>具有狀態[TaskStatus.Created](<xref:System.Threading.Tasks.TaskStatus.Created>)， [TaskStatus.WaitingForActivation](<xref:System.Threading.Tasks.TaskStatus.WaitingForActivation>)，或[TaskStatus.WaitingToRun](<xref:System.Threading.Tasks.TaskStatus.WaitingToRun>)可能不是顯示在**任務**當 managed 的執行緒處於睡眠或聯結狀態 視窗。

## <a name="tasks-column-information"></a>工作資料行資訊

中的資料行**任務**視窗會顯示下列資訊。

|資料行名稱|描述|
|-----------------|-----------------|
|**旗標**|顯示已加上旗標的工作，並可讓您為工作加上或取消旗標。|
|**圖示**|黃色箭號表示目前工作。 目前工作是目前執行緒上的最上方工作。<br /><br /> 白色箭號表示最新的工作，即叫用偵錯工具時的最新工作。<br /><br /> 暫停圖示表示已由使用者凍結的工作。 在清單中，於工作上按一下滑鼠右鍵，就可以凍結和解除凍結工作。|
|**ID**|由系統提供給工作的號碼。 在機器碼中，這是工作的位址。|
|**Status**|工作目前狀態 （已排程、 作用中、 已封鎖、 死結、 等待，或已完成）。 已排程工作是尚未執行的工作，因此，還沒有呼叫堆疊、指派的執行緒或相關資訊。<br /><br /> 使用中工作是在進入偵錯工具之前正在執行程式碼的工作。<br /><br /> 正在等待或封鎖的工作就是被封鎖，因為它正在等候事件收到訊號、 鎖定被釋放或另一個工作完成。<br /><br /> 死結工作是其執行緒與另一個執行緒產生死結的等待中工作。<br /><br /> 將滑鼠停留**狀態**死結或等待的工作，才能查看區塊的詳細資訊的儲存格。 **警告：** **工作**視窗會報告死結只針對遭到封鎖的工作，會使用支援的 Wait Chain Traversal (WCT) 同步處理原始物件。 例如，對於死結<xref:System.Threading.Tasks.Task>物件，使用了 WCT，偵錯工具會報告**正在等待中-死結**。 死結工作是由並行執行階段，不使用 WCT，偵錯工具會回報**等候**。 如需 WCT 的詳細資訊，請參閱[Wait Chain Traversal](/windows/desktop/Debug/wait-chain-traversal)。|
|**開始時間**|工作變成使用中的時間。|
|**持續期間**|工作已處於使用中狀態的秒數。|
|**完成時間**|工作已完成的時間。|
|**位置**|在工作之呼叫堆疊中的目前位置。 將滑鼠游標停留在這個儲存格上方，就可以查看整個工作的呼叫堆疊。 已排程工作的這個資料行沒有值。|
|**Task**|初始方法和任何在建立工作時未傳遞給工作的引數。|
|**AsyncState**|對於 Managed 程式碼來說，是指工作狀態。 根據預設，這個資料行是隱藏狀態。 若要顯示這個資料行，請開啟其中一個資料行標頭的操作功能表。 選擇**資料行**， **AsyncState**。|
|**父代**|建立這個工作之工作的 ID。 如果空白，表示工作沒有父代。 這只適用於 Managed 程式。|
|**執行緒指派**|正在執行工作之執行緒的 ID 和名稱。|
|**AppDomain**|針對 Managed 程式碼，是正在執行工作的應用程式定義域。|
|**task_group**|原生程式碼的地址[task_group](/cpp/parallel/concrt/reference/task-group-class)已排程工作的物件。 針對非同步代理程式和輕量型工作，此欄會設為 0。|
|**Process**|工作執行所在的處理序 ID。|

 在資料行標題上按一下滑鼠右鍵，然後選取想要的資料行，就可以將資料行加入至檢視  (清除選取範圍，就可以移除資料行)。您也可以將資料行向左或向右拖曳，以重新排列資料行。 下圖顯示資料行捷徑功能表。

 ![在 [工作] 視窗的捷徑檢閱功能表](../debugger/media/parallel_tasks_contextmenu.png "Parallel_Tasks_ContextMenu")

## <a name="sorting-tasks"></a>排序工作
 若要依據資料行準則排序工作，請按一下資料行標頭。 例如，依序按一下**識別碼**資料行標頭，您可以排序依工作識別碼的工作： id:1,2,3,4,5 等。 若要反轉排序次序，請再按一下資料行標頭。 目前排序資料行和排序次序是透過資料行上的箭號來表示。

## <a name="grouping-tasks"></a>群組工作
 您可以根據清單檢閱中的任何資料行，來群組工作。 例如，以滑鼠右鍵按一下**狀態**資料行的標頭，然後按一下**分組** > **[*狀態*]**，您可以群組具有相同狀態的所有工作。 例如，您可以快速查看正在等候工作，以便您專注於封鎖的原因。 您也可以摺疊偵錯工作階段期間不感興趣的群組。 同樣地，您也可以依據其他資料行來進行群組。 只要按一下群組標頭旁邊的按鈕，就可以為群組加上 (取消) 旗標。 如下圖所示**任務**處於群組模式的視窗。

 ![在 [工作] 視窗中的分組的模式](../debugger/media/parallel_tasks_groupedmode.png "Parallel_Tasks_GroupedMode")

## <a name="parent-child-view"></a>父子式檢視
 (此檢視僅適用於 Managed 程式碼)。以滑鼠右鍵按一下**狀態**資料行標頭，然後按一下**分組** > **父**，您可以為階層式檢閱，以變更工作清單每項子工作是可以顯示或隱藏其父系下的子節點。

## <a name="flagging-tasks"></a>為工作加上旗標
 您可以加上旗標的執行緒選取工作執行工作所在的工作清單項目，然後選擇**旗標指派給執行緒**從操作功能表中，或按一下第一個資料行中的旗標圖示。 如果您為多項工作加上旗標，則可以依據旗標資料行進行排序，以將所有加上旗標的工作帶至頂端，讓您可以只將焦點放在這些資料行。 您也可以使用**平行堆疊**僅視窗來檢視已標幟的工作。 這可讓您篩選出不想要進行偵錯的工作。 在偵錯工作階段之間不會持續保留旗標。

## <a name="freezing-and-thawing-tasks"></a>凍結和解除凍結工作
 您可以凍結一項工作執行的工作清單項目上按一下滑鼠右鍵，然後按一下所在的執行緒**凍結指派的執行緒**。 (如果工作已遭凍結，則命令是**解除凍結指派的執行緒**。)當您凍結執行緒時，就不會在逐步執行目前中斷點後面的程式碼時執行該執行緒。 **凍結所有執行緒，但此一**命令則會凍結正在執行的工作清單項目以外的所有執行緒。

 下圖顯示每個工作的其他功能表項目。

 ![在 [工作] 視窗的捷徑執行緒功能表](../debugger/media/parallel_tasks_contextmenu2.png "Parallel_Tasks_ContextMenu2")

## <a name="switching-the-active-task-or-frame"></a>切換框架的使用中工作

**切換至工作**命令會將目前的工作使用中工作。 **切換至框架**命令會將所選的堆疊框架的作用中堆疊框架。 偵錯工具內容會切換成目前的工作或所選的堆疊框架。

## <a name="see-also"></a>另請參閱

- [偵錯工具基礎](../debugger/getting-started-with-the-debugger.md)
- [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)
- [平行程式設計](/dotnet/standard/parallel-programming/index)
- [並行執行階段](/cpp/parallel/concrt/concurrency-runtime)
- [使用平行堆疊視窗](../debugger/using-the-parallel-stacks-window.md)
- [逐步解說：偵錯平行應用程式](../debugger/walkthrough-debugging-a-parallel-application.md)