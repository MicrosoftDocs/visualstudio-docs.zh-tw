---
title: 檢視使用 [平行堆疊] 視窗的往來文章 |Microsoft Docs
ms.custom: ''
ms.date: 04/25/2017
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d344cc8cd30d250c441788a7920d05086c38ca5f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940004"
---
# <a name="view-threads-and-tasks-using-the-parallel-stacks-window"></a>檢視往來文章和使用平行堆疊 視窗的工作
**平行堆疊**視窗會很有用，當您偵錯多執行緒應用程式。 其**執行緒檢視**顯示您的應用程式中的所有執行緒的呼叫堆疊資訊。 這個檢視可讓您巡覽執行緒和其上的堆疊框架。 在 managed 程式碼 **[工作] 檢視**顯示呼叫堆疊的<xref:System.Threading.Tasks.Task?displayProperty=fullName>物件。 原生程式碼，在 **[工作] 檢視**顯示呼叫堆疊[工作群組](/cpp/parallel/concrt/task-parallelism-concurrency-runtime)，[平行演算法](/cpp/parallel/concrt/parallel-algorithms)，[非同步代理程式](/cpp/parallel/concrt/asynchronous-agents)，以及[輕量型工作](/cpp/parallel/concrt/task-scheduler-concurrency-runtime)。  
  
## <a name="threads-view"></a>執行緒檢視  
 下圖顯示的執行緒是從「主要」流到 A 再流到 B，然後再流到某個外部程式碼。 其他兩個執行緒是從某個外部程式碼開始，然後再流到 A，但是其中一個執行緒繼續流到 B，然後流到某個外部程式碼，而另一個執行緒則繼續流到 C，然後流到某個 AnonymousMethod。  
  
 ![執行緒平行堆疊 視窗中的檢視](../debugger/media/parallel_stacksthread.png "Parallel_StacksThread")  
  
 在圖中，目前執行緒的呼叫路徑以藍色反白顯示，並在執行緒的目前位置 （作用中堆疊框架） 以黃色箭號。 您可以選取不同的方法中，以變更目前的堆疊框架**平行堆疊**視窗。 這可能也會導致切換目前執行緒，取決於您選取的方法已是目前執行緒的一部分還是另一個執行緒的一部分。 下表描述的主要特色**平行堆疊**視窗中，如圖所示。  
  
|圖說文字字母|元素名稱|描述|  
|-|-|-|  
|A|呼叫堆疊區段或節點|包含一系列的一個或多個執行緒的方法。 如果節點未連接任何帶箭號的線條，則表示它代表執行緒的整個呼叫路徑。|  
|B|藍色醒目提示|表示目前執行緒的呼叫路徑。|  
|C|帶箭號的線條|連接節點，以構成執行緒的整個呼叫路徑。|  
|D|節點標題的工具提示|顯示其呼叫路徑共用這個節點之每個執行緒的 ID 和由使用者定義的名稱。|  
|E|方法|表示相同方法中的一個或多個堆疊框架。|  
|F|在方法上的工具提示|在 [執行緒] 檢視中，它會顯示所有執行緒在資料表中類似**執行緒**視窗。 在 [工作] 檢視中，它會顯示所有工作資料表中類似**任務**視窗。|  
  
 此外，[平行堆疊] 視窗會顯示**鳥瞰檢視**圖形太大，無法納入視窗時，主要窗格中的圖示。 您可以按一下圖示，在視窗中查看整個圖形。  
  
## <a name="stack-frame-icons"></a>堆疊框架的圖示  
 下表所說明的圖示提供作用中和目前堆疊框架的詳細資訊：  
  
|圖示|描述|  
|-|-|  
|![平行堆疊 的黃色箭號](../debugger/media/icon_parallelyellowarrow.gif "Icon_ParallelYellowArrow")|表示方法，包含目前執行緒的目前位置 （作用中堆疊框架）。|  
|![平行堆疊 的執行緒圖示](../debugger/media/icon_parallelthreads.gif "Icon_ParallelThreads")|指出此方法包含非目前執行緒的目前位置 （作用中堆疊框架）。|  
|![平行堆疊 的綠色箭頭](../debugger/media/icon_parallelgreenarrow.gif "Icon_ParallelGreenArrow")|表示方法，包含目前的堆疊框架 （目前的偵錯工具內容）。 該方法名稱在其出現的所有節點中會顯示為粗體。|  
  
## <a name="toolbar-controls"></a>工具列控制項  
 下圖和下表說明 [平行堆疊] 工具列中可用的控制項。  
  
 ![在 [平行堆疊] 視窗的工具列](../debugger/media/parallel_stackstoolbar.png "Parallel_StacksToolbar")  
  
|圖說文字字母|控制項|描述|  
|-|-|-|  
|A|執行緒/工作下拉式方塊|切換執行緒呼叫堆疊檢閱和工作呼叫堆疊檢閱。 如需詳細資訊，請參閱＜工作檢閱＞和＜執行緒檢閱＞。|  
|B|僅顯示有旗標的項目|顯示呼叫堆疊，只針對這類標示其他偵錯視窗中中的執行緒**GPU 執行緒**視窗和**平行監看式**視窗。|  
|C|切換方法檢視|切換 [堆疊檢視] 和 [方法檢視]。 如需詳細資訊，請參閱＜方法檢視＞。|  
|D|自動捲動到目前堆疊框架|自動捲動圖表，讓目前堆疊框架出現在檢視中。 當您要從其他視窗變更目前堆疊框架，或是到達大型圖表中的新中斷點時，這項功能會很有用。|  
|E|切換縮放控制|顯示或隱藏縮放控制項。 您也可以放大按住 ctrl 鍵並轉動滑鼠滾輪，不論可見性的縮放控制項，或使用 CTRL + SHIFT + '+' 放大與 CTRL + SHIFT +'-' 縮小。按下 CTRL + f8 鍵會縮放以符合螢幕大小。|  
  
### <a name="context-menu-items"></a>操作功能表項目  
 下圖和下表說明當您以滑鼠右鍵按一下 [執行緒檢閱] 或 [工作] 檢視中的方法的捷徑功能表項目。 後六個項目是直接從 [呼叫堆疊] 視窗借用，並未引入新的行為。  
  
 ![[平行堆疊] 視窗中的快顯功能表](../debugger/media/parallel_contmenu.png "Parallel_ContMenu")  
  
|功能表項目|描述|  
|-|-|  
|旗標|將選取的項目加上旗標。|  
|取消旗標|取消所選取項目的旗標。|  
|凍結|將選取的項目凍結。|  
|解除凍結|將選取的項目解除凍結。|  
|移至工作 (執行緒)|執行的功能與工具列上的下拉式方塊相同，但是會持續醒目提示同一個堆疊框架。|  
|移至原始程式碼|巡覽至原始程式碼中的位置，而這個位置對應於使用者以滑鼠右鍵按一下的堆疊框架。|  
|切換至框架|與 [呼叫堆疊] 視窗上對應的功能表命令相同。 不過，使用 平行堆疊，多個框架可能會對應到一種方法。 因此，功能表項目會有子功能表，而每個子功能表都表示特定的堆疊框架。 如果其中一個堆疊框架是在目前執行緒上，則與該堆疊框架對應的功能表會呈現選取狀態。|  
|移至反組譯碼|巡覽至反組譯碼視窗中的位置，而這個位置對應於使用者以滑鼠右鍵按一下的堆疊框架。|  
|顯示外部程式碼|顯示或隱藏外部程式碼。|  
|十六進位顯示|切換十進位和十六進位顯示。|  
|符號載入資訊|顯示對應的對話方塊。|  
|符號設定|顯示對應的對話方塊。|  
  
## <a name="tasks-view"></a>工作檢閱  
 如果您的應用程式使用<xref:System.Threading.Tasks.Task?displayProperty=fullName>物件 （managed 程式碼） 或`task_handle`表示平行處理原則物件 （原生程式碼），您可以使用 [平行堆疊] 視窗工具列中的下拉式方塊切換至 *[工作] 檢視*。 [工作檢閱] 會顯示工作 (而非執行緒) 的呼叫堆疊。 [工作檢視] 有別於 [執行緒檢視] 之處在於：  
  
- 如果執行緒沒有在執行工作，則不會顯示該執行緒的呼叫堆疊。  
  
- 如果執行緒目前正在執行工作，則會隱藏該執行緒之呼叫堆疊的頂端和底端，以顯示與工作最相關的框架。  
  
- 當有多個工作在同一個執行緒上時，這些工作的呼叫堆疊會分割成不同的節點。  
  
  下圖右邊顯示的是 [平行堆疊] 的 [工作檢閱]，左邊顯示的是對應的 [執行緒檢閱]。  
  
  ![工作平行堆疊 視窗中的檢視](../debugger/media/parallel_tasksview.png "Parallel_TasksView")  
  
  若要查看整個呼叫堆疊，只要切換回 執行緒檢視的堆疊框架上按一下滑鼠右鍵，然後按一下**移至執行緒**。  
  
  中所述較早的表格，停留在方法中，您可以看到其他資訊。 下圖為 [執行緒檢閱] 和 [工作檢閱] 的工具提示中所顯示的資訊。  
  
  ![平行堆疊 視窗中的工具提示](../debugger/media/parallel_stack_tooltips.png "Parallel_Stack_Tooltips")  
  
## <a name="method-view"></a>方法檢視  
 在 [執行緒檢視] 或 [工作檢視] 中，按一下工具列上的 [方法檢視] 圖示，就可以切換至目前方法的圖形。 [方法檢視] 會顯示所有執行緒上所有呼叫目前方法或被目前方法呼叫的方法。 下圖顯示 [執行緒檢視]，以及相同的資訊在 [方法檢視] 中的樣子。  
  
 ![[平行堆疊] 視窗中的 [方法檢視]](../debugger/media/parallel_methodview.png "Parallel_MethodView")  
  
 切換至新的堆疊框架，就可以將該方法變成目前的方法，並讓視窗顯示新方法的所有呼叫端和被呼叫端。 有些執行緒可能會因此顯示或不見，視該方法是否出現在這些執行緒的呼叫堆疊中。 若要回到 [堆疊檢視]，請再按一下 [方法檢視] 工具列按鈕。  
  
## <a name="see-also"></a>另請參閱  
 [開始偵錯多執行緒應用程式](../debugger/get-started-debugging-multithreaded-apps.md)   
 [逐步解說： 偵錯平行應用程式](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [偵錯工具基礎](../debugger/getting-started-with-the-debugger.md)   
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)   
 [平行程式設計](/dotnet/standard/parallel-programming/index)   
 [使用工作視窗](../debugger/using-the-tasks-window.md)   
 [Task 類別](../extensibility/debugger/task-class-internal-members.md)
