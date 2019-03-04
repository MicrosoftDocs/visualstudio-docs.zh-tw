---
title: 在 [平行堆疊] 視窗中檢視的往來文章 |Microsoft Docs
ms.date: 11/20/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelstacks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9728346bc4c6d805bb0febd3a0d5bef0ed809a5
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56712537"
---
# <a name="view-threads-and-tasks-in-the-parallel-stacks-window-c-visual-basic-c"></a>在 [平行堆疊] 視窗中檢視執行緒和工作 (C#，Visual Basic、 c + +)

**平行堆疊**視窗是用於偵錯多執行緒應用程式。 它有幾種檢視：

- [執行緒檢視](#threads-view)顯示應用程式中的所有執行緒呼叫堆疊資訊。 您可以巡覽執行緒和在這些執行緒的堆疊框架。

- [工作檢視](#tasks-view)顯示工作為主的呼叫堆疊資訊。
  - 在 managed 程式碼**任務**檢視會顯示呼叫堆疊<xref:System.Threading.Tasks.Task?displayProperty=fullName>物件。
  - 在機器碼**工作**檢視會顯示呼叫堆疊[工作群組](/cpp/parallel/concrt/task-parallelism-concurrency-runtime)，[平行演算法](/cpp/parallel/concrt/parallel-algorithms)，[非同步代理程式](/cpp/parallel/concrt/asynchronous-agents)，及[輕量型工作](/cpp/parallel/concrt/task-scheduler-concurrency-runtime)。

- [方法檢視](#method-view)之間進行切換選取的方法呼叫堆疊。

## <a name="use-the-parallel-stacks-window"></a>使用平行堆疊視窗

若要開啟 [**平行堆疊**] 視窗中，您必須在偵錯工作階段。 選取 **偵錯** > **Windows** > **平行堆疊**。

### <a name="toolbar-controls"></a>工具列控制項

**平行堆疊**視窗具有下列工具列上的控制項：

![在 [平行堆疊] 視窗的工具列](../debugger/media/parallel_stackstoolbar.png "平行堆疊 工具列")

|圖示|控制項|說明|
|-|-|-|
|![執行緒/工作下拉式方塊](media/parallel_toolbar1.png "執行緒/工作下拉式方塊")|**執行緒**/**工作**下拉式方塊|切換執行緒呼叫堆疊檢閱和工作呼叫堆疊檢閱。 如需詳細資訊，請參閱[工作檢視](#tasks-view)和[執行緒檢視](#threads-view)。|
|![顯示只加上旗標圖示](media/parallel_toolbar2.png "僅顯示已標幟的圖示")|僅顯示有旗標的項目|顯示呼叫堆疊，只針對這類標示其他偵錯工具視窗中，執行緒**GPU 執行緒**視窗和**平行監看式**視窗。|
|![切換方法檢視圖示](media/parallel_toolbar3.png "切換方法檢視圖示")|切換**方法檢視**|呼叫堆疊檢視之間切換以及**方法檢視**。 如需詳細資訊，請參閱[方法檢視](#method-view)。|
|![自動捲動到目前的圖示](media/parallel_toolbar4.png "自動捲動到目前的圖示")|自動捲動到目前堆疊框架|捲動圖形，讓目前堆疊框架是在檢視中。 當您從 其他視窗中，變更目前的堆疊框架，或當您到達大型圖表中的新中斷點時，此功能非常有用。|
|![切換 [顯示比例] 圖示](media/parallel_toolbar5.png "切換縮放圖示")|切換縮放控制|顯示或隱藏縮放控制項視窗的左邊。 <br /><br />不論縮放控制項的可見性，您也可以放大藉由按下**Ctrl**並轉動滑鼠滾輪，或藉由按下**Ctrl**+**Shift** +**+** 放大與**Ctrl**+**Shift** + **-** 若要縮小。 |

### <a name="stack-frame-icons"></a>堆疊框架的圖示
下列圖示會提供所有檢視中的作用中和目前的堆疊框架的相關資訊：

|圖示|說明|
|-|-|
|![黃色箭號](media/icon_parallelyellowarrow.gif)|表示目前執行緒的目前位置 （作用中堆疊框架）。|
|![執行緒圖示](media/icon_parallelthreads.gif)|表示非目前執行緒的目前位置 （作用中堆疊框架）。|
|![綠色箭號](media/icon_parallelgreenarrow.gif)|指出目前的堆疊框架 （目前的偵錯工具內容）。 方法名稱是粗體出現的任一處。|

### <a name="context-menu-items"></a>操作功能表項目
下列的快顯功能表項目時，可以使用中的方法上按一下滑鼠右鍵**執行緒**檢視或**工作**檢視。 過去六個項目是相同[呼叫堆疊 視窗](how-to-use-the-call-stack-window.md)。

![[平行堆疊] 視窗中的快顯功能表](../debugger/media/parallel_contmenu.png "平行堆疊 視窗中的快顯功能表")

|Menu item|說明|
|-|-|
|**旗標**|將選取的項目加上旗標。|
|**取消旗標**|取消所選取項目的旗標。|
|**凍結**|將選取的項目凍結。|
|**解除凍結**|將選取的項目解除凍結。|
|**切換至框架**|中的相同對應的功能表命令**呼叫堆疊**視窗。 不過，在**平行堆疊** 視窗中，在數個框架，可能是一種方法。 您可以在這個項目的子功能表中選取您想要的框架。 如果其中一個堆疊框架是在目前的執行緒上，子功能表中的預設會選取該範圍內。|
|**移至工作**或**移至執行緒**|會切換成**任務**或是**執行緒** 檢視中，並保留相同堆疊框架反白顯示。|
|**前往原始程式碼**|會移至原始程式碼視窗中的對應位置。 |
|**前往反組譯碼**|前往中對應的位置**反組譯碼**視窗。|
|**顯示外部程式碼**|顯示或隱藏外部程式碼。|
|**十六進位顯示**|切換十進位和十六進位顯示。|
|**在原始程式檔中顯示執行緒**|旗標的執行緒在原始程式碼視窗中的位置。 |
|**符號載入資訊**|會開啟**符號載入資訊** 對話方塊。|
|**符號設定**|會開啟**符號設定** 對話方塊。 |

## <a name="threads-view"></a>執行緒檢視

在 **執行緒**檢視的堆疊框架和目前執行緒的呼叫路徑會以藍色反白顯示。 執行緒的目前位置會顯示黃色箭號。

若要變更目前的堆疊框架，請按兩下不同的方法。 這也可能會切換目前的執行緒，根據您所選取的方法是在目前的執行緒或另一個執行緒的一部分。

當**執行緒**檢視圖形太大而無法納入視窗時，**鳥瞰檢視**控制項就會出現在視窗中。 您可以將畫面控制項瀏覽至圖形的不同部分中。

下圖顯示一個會從主要原生程式碼轉換為受控的執行緒。 六個執行緒會在目前的方法。 其中一個會繼續 Thread.Sleep，和另一個持續 Console.WriteLine，然後 SyncTextWriter.WriteLine。

 ![執行緒平行堆疊 視窗中的檢視](../debugger/media/parallel_stack1.png "執行緒平行堆疊 視窗中的檢視")

下表描述的主要特色**執行緒**檢視：

|圖說文字|元素名稱|說明|
|-|-|-|
|1|呼叫堆疊區段或節點|包含一系列的一個或多個執行緒的方法。 如果畫面不連線到它的箭號行，框架會顯示執行緒的整個呼叫路徑。|
|2|藍色醒目提示|表示目前執行緒的呼叫路徑。|
|3|帶箭號的線條|連接節點，以構成執行緒的整個呼叫路徑。|
|4|節點標題|顯示處理序和執行緒的節點數目。|
|5|方法|表示相同方法中的一個或多個堆疊框架。|
|6|在方法上的工具提示|當您將滑鼠停留方法會出現。 在 **執行緒**檢視中，工具提示會顯示所有執行緒，類似於資料表中**執行緒**視窗。 |

## <a name="tasks-view"></a>工作檢視
如果您的應用程式會使用<xref:System.Threading.Tasks.Task?displayProperty=fullName>物件 （managed 程式碼） 或`task_handle`物件 （機器碼） 表示平行處理原則，您可以使用**工作**檢視。 [工作] 檢視會顯示工作 (而非執行緒) 的呼叫堆疊。

在 **任務**檢視：

- 不會執行工作的執行緒的呼叫堆疊不會顯示。
- 目前正在執行工作的執行緒的呼叫堆疊會以視覺化方式修剪頂端和底部，以顯示工作最相關的框架。
- 在一個執行緒上數個工作時，這些工作的呼叫堆疊會顯示不同的節點。

若要查看整個呼叫堆疊，切換回**執行緒**檢視，以滑鼠右鍵按一下堆疊框架，然後選取**移至執行緒**。

如下圖所示**執行緒**檢視，在頂端，並對應**工作**底部的檢視。

![[執行緒] 和 [工作] 檢視](../debugger/media/parallel_threads-tasks.png "[執行緒] 和 [工作] 檢視")

暫留在顯示工具提示的其他資訊的方法。 在 **工作**檢視中，工具提示會顯示所有工作資料表中類似**工作**視窗。

下圖顯示的工具提示中的方法**執行緒**檢視的上方，並對應**工作**底部的檢視。

![執行緒和工作的工具提示](../debugger/media/parallel_threads-tasks-tooltips.png "執行緒和工作的工具提示")

## <a name="method-view"></a>方法檢視
從其中**執行緒**檢視或**工作** 檢視中，您可以藉由選取轉換目前方法的圖形**切換方法檢視**工具列上的圖示。 [方法檢視] 會顯示所有執行緒上所有呼叫目前方法，或由目前方法呼叫的方法。 下圖顯示相同的資訊中的外觀**執行緒**檢視的左邊，然後在**方法檢視**右邊。

![執行緒檢視和 方法檢視](../debugger/media/parallel_methodview.png "執行緒檢視和 方法檢視")

如果您切換到新的堆疊框架時，您將該方法變成目前的方法，並**方法檢視**顯示所有呼叫端和被呼叫端的新方法。 有些執行緒可能會因此顯示或不見，視該方法是否出現在這些執行緒的呼叫堆疊中。 若要傳回至呼叫堆疊檢視，請選取**方法檢視**再次工具列圖示。

## <a name="see-also"></a>另請參閱
- [開始偵錯多執行緒應用程式](../debugger/get-started-debugging-multithreaded-apps.md)
- [逐步解說：對平行應用程式進行偵錯](../debugger/walkthrough-debugging-a-parallel-application.md)
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)
- [對受控碼進行偵錯](../debugger/debugging-managed-code.md)
- [平行程式設計](/dotnet/standard/parallel-programming/index)
- [使用工作視窗](../debugger/using-the-tasks-window.md)
- [工作類別](../extensibility/debugger/task-class-internal-members.md)
