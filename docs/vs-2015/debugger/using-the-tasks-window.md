---
title: 使用工作視窗 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 267a04e0d717bde311423aae7f35fba07ca6f39b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684042"
---
# <a name="using-the-tasks-window"></a>使用工作視窗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[工作]**** 視窗與 [執行緒]**** 視窗類似，差別在於前者顯示的是 <xref:System.Threading.Tasks.Task?displayProperty=fullName>、[task_handle](https://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7) 或 [WinJS.Promise](https://msdn.microsoft.com/library/windows/apps/br211867.aspx) 物件的詳細資訊，而非每個執行緒的詳細資訊。 與執行緒一樣，工作代表可以並行執行的非同步作業，但是多項工作可能會在相同執行緒上執行。 如需詳細資訊，請參閱 [JavaScript 中的非同步程式設計 (Windows Store 應用程式) ](https://msdn.microsoft.com/library/windows/apps/hh700330.aspx) 。  
  
 在 Managed 程式碼中，當您使用 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 物件或使用 **await** 和 **async** 關鍵字 (在 Visual Basic 中為 **Await** 和 **Async**) 時，可以使用 [工作]**** 視窗。 如需 managed 程式碼中工作的詳細資訊，請參閱  [平行程式設計](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)。  
  
 在機器碼中，您可以在操作[工作群組](https://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077)、[平行演算法](https://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473)、[非同步代理程式](https://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a)及[輕量型工作](https://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90)時使用 [工作]**** 視窗。 如需機器碼格式之工作的詳細資訊，請參閱[並行執行階段](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)。  
  
 在 JavaScript 中，您可以在使用 promise .then 程式碼時使用 [工作] 視窗。  
  
 只要您進入偵錯工具，就可以使用 [工作]**** 視窗。 存取方式是按一下 [偵錯]**** 功能表上的 [視窗]****，然後按一下 [工作]****。 下圖顯示處於預設模式的 [工作]**** 視窗。  
  
 ![[平行工作] 視窗](../debugger/media/parallel-tasks-window.png "Parallel_Tasks_Window")  
  
> [!NOTE]
> 在 Managed 程式碼中，如果 Managed 執行緒處於睡眠或聯結狀態，則狀態為 <xref:System.Threading.Tasks.Task>、<xref:System.Threading.Tasks.TaskStatus> 或 <xref:System.Threading.Tasks.TaskStatus> 的 <xref:System.Threading.Tasks.TaskStatus> 可能不會在 [工作] 視窗中顯示。  
  
## <a name="tasks-column-information"></a>工作資料行資訊  
 [工作]**** 視窗中的資料行會顯示下列資訊。  
  
|資料行名稱|描述|  
|-----------------|-----------------|  
|**旗標**|顯示已加上旗標的工作，並可讓您為工作加上或取消旗標。|  
|**圖示**|黃色箭號表示目前工作。 目前工作是目前執行緒上的最上方工作。<br /><br /> 白色箭號表示最新的工作，即叫用偵錯工具時的最新工作。<br /><br /> 暫停圖示表示已由使用者凍結的工作。 在清單中，於工作上按一下滑鼠右鍵，就可以凍結和解除凍結工作。|  
|**識別碼**|由系統提供給工作的號碼。 在機器碼中，這是工作的位址。|  
|**狀態**|工作的目前狀態 (已排程、使用中、死結、等待中或已完成)。 已排程工作是尚未執行的工作，因此，還沒有呼叫堆疊、指派的執行緒或相關資訊。<br /><br /> 使用中工作是在進入偵錯工具之前正在執行程式碼的工作。<br /><br /> 等待中工作是因等待事件發出信號、釋放鎖定或另一個工作完成而遭封鎖的工作。<br /><br /> 死結工作是其執行緒與另一個執行緒產生死結的等待中工作。<br /><br /> 將滑鼠停留在鎖死或等候工作的 **狀態** 資料格上方，以查看有關區塊的詳細資訊。 **警告：**  [ **工作** ] 視窗只會針對已封鎖的工作報告鎖死，而該工作會使用等候鏈進行 (WCT) 所支援的同步處理原始物件。 例如，如果是使用 WCT 的鎖死 <xref:System.Threading.Tasks.Task> 物件，則偵錯工具會 **報告等待-鎖死**。 如果發生死結的工作是由「並行執行階段」管理 (即不使用 WCT)，偵錯工具會報告 [等待中]****。 如需 WCT 的詳細資訊，請參閱[等待鏈結周遊](https://msdn.microsoft.com/library/ms681622\(VS.85\).aspx)。|  
|**Start Time**|工作變成使用中的時間。|  
|**有效期間**|工作已處於使用中狀態的秒數。|  
|**完成時間**|工作完成的時間。|  
|**位置**|在工作之呼叫堆疊中的目前位置。 將滑鼠游標停留在這個儲存格上方，就可以查看整個工作的呼叫堆疊。 已排程工作的這個資料行沒有值。|  
|**Task**|初始方法和任何在建立工作時未傳遞給工作的引數。|  
|**父系**|建立這個工作之工作的 ID。 如果空白，表示工作沒有父代。 這只適用於 Managed 程式。|  
|**執行緒指派**|正在執行工作之執行緒的 ID 和名稱。|  
|**傳回狀態**|工作完成時的狀態。 傳回狀態值為 **成功**、已 **取消**和 **錯誤**。|  
|**AppDomain**|針對 Managed 程式碼，是正在執行工作的應用程式定義域。|  
|**task_group**|針對機器碼，是已排程工作之 [task_group](https://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7) 物件的位址。 針對非同步代理程式和輕量型工作，此欄會設為 0。|  
|程序|工作執行所在的處理序 ID。|  
|非同步狀態|對於 Managed 程式碼來說，是指工作狀態。 根據預設，這個資料行是隱藏狀態。 若要顯示這個資料行，請開啟其中一個資料行標頭的內容功能表。 選擇 [資料行]****、[AsyncState]****。|  
  
 在資料行標題上按一下滑鼠右鍵，然後選取想要的資料行，就可以將資料行加入至檢視   (藉由清除選取專案來移除資料行。 ) 您也可以將資料行向左或向右拖曳，以重新排序資料行。 下圖顯示資料行捷徑功能表。  
  
 ![[平行工作] 視窗中的捷徑檢視功能表](../debugger/media/parallel-tasks-contextmenu.png "Parallel_Tasks_CoNtextMenu")  
  
## <a name="sorting-tasks"></a>排序工作  
 若要依據資料行準則排序工作，請按一下資料行標頭。 例如，按一下 [ **ID** ] 資料行標頭，即可依工作識別碼排序工作：1、2、3、4、5等等。 若要反轉排序次序，請再按一下資料行標頭。 目前排序資料行和排序次序是透過資料行上的箭號來表示。  
  
## <a name="grouping-tasks"></a>群組工作  
 您可以根據清單檢閱中的任何資料行，來群組工作。 例如，以滑鼠右鍵按一下 [ **狀態** ] 資料行標頭，然後按一下 [ **依狀態群組**]，就可以將所有具有相同狀態的工作分組。 例如，您可以快速查看等待中工作，以將焦點放在它們遭到封鎖的原因。 您也可以摺疊偵錯工作階段期間不感興趣的群組。 同樣地，您也可以依據其他資料行來進行群組。 只要按一下群組標頭旁邊的按鈕，就可以為群組加上 (取消) 旗標。 下圖顯示處於群組模式的 [工作]**** 視窗。  
  
 ![[平行工作] 視窗中的已分組模式](../debugger/media/parallel-tasks-groupedmode.png "Parallel_Tasks_GroupedMode")  
  
## <a name="parent-child-view"></a>父子式檢視  
  (此視圖僅適用于 managed 程式碼。 ) 以滑鼠右鍵按一下資料行標題，然後按一下 [ **父子**式]，就可以將工作清單變更為階層式視圖，其中，每個子工作都是可以在其父系下顯示或隱藏的子節點。 下圖顯示父子式檢閱中的工作。  
  
 ![[平行工作] 視窗中的父&#45;子視圖](../debugger/media/parallel-tasks-parentchildview.png "Parallel_Tasks_ParentChildView")  
  
## <a name="flagging-tasks"></a>為工作加上旗標  
 您可以藉由選取 [工作清單] 專案，然後從內容功能表選擇 [ **旗** 標]，或是按一下第一個資料行中的旗標圖示，以旗標執行緒正在執行工作的工作。 如果您為多項工作加上旗標，則可以依據旗標資料行進行排序，以將所有加上旗標的工作帶至頂端，讓您可以只將焦點放在這些資料行。 您也可以使用 [平行堆疊]**** 視窗，只檢閱加上旗標的工作。 這可讓您篩選出不想要進行偵錯的工作。 在偵錯工作階段之間不會持續保留旗標。  
  
## <a name="freezing-and-thawing-tasks"></a>凍結和解除凍結工作  
 您可以凍結正在執行工作的執行緒，方法是在工作清單項目上按一下滑鼠右鍵，然後按一下 [凍結指派的執行緒]****。  (如果工作已經凍結，則命令會解除凍結 **指派的執行緒**。 ) 當您凍結執行緒時，當您在目前的中斷點之後逐步執行程式碼時，該執行緒將不會執行。 **凍結所有線程，但此**命令會凍結所有線程，但正在執行工作清單專案的執行緒除外。  
  
 下圖顯示每個工作的其他功能表項目。  
  
 ![[平行工作] 視窗中的捷徑執行緒功能表](../debugger/media/parallel-tasks-contextmenu2.png "Parallel_Tasks_CoNtextMenu2")  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具基本概念](../debugger/debugger-basics.md)   
 [Managed 程式碼的偵錯工具](../debugger/debugging-managed-code.md)   
 [平行程式設計](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [並行執行階段](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)   
 [使用平行堆疊視窗](../debugger/using-the-parallel-stacks-window.md)   
 [逐步解說：偵錯平行應用程式](../debugger/walkthrough-debugging-a-parallel-application.md)
