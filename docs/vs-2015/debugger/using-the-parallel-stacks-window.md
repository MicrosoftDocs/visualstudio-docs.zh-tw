---
title: 使用平行堆疊視窗 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelstacks
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e89125c8e1dea25ab02fe64c21b8166e9d65194a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542216"
---
# <a name="using-the-parallel-stacks-window"></a>使用平行堆疊視窗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

當您正在對多執行緒應用程式進行偵錯工具時，[ **平行堆疊** ] 視窗相當有用。 其 **執行緒視圖** 會顯示您應用程式中所有線程的呼叫堆疊資訊。 這個檢視可讓您巡覽執行緒和其上的堆疊框架。 在 managed 程式碼中，[工作] **視圖** 會顯示物件的呼叫堆疊 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 。 在機器碼中，[工作] **視圖** 會顯示 [工作組](https://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077)、 [平行演算法](https://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473)、 [非同步代理](https://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a)程式和 [輕量](https://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90)工作的呼叫堆疊。  
  
## <a name="threads-view"></a>執行緒檢視  
 下圖顯示的執行緒是從「主要」流到 A 再流到 B，然後再流到某個外部程式碼。 其他兩個執行緒是從某個外部程式碼開始，然後再流到 A，但是其中一個執行緒繼續流到 B，然後流到某個外部程式碼，而另一個執行緒則繼續流到 C，然後流到某個 AnonymousMethod。  
  
 ![[平行堆疊] 視窗中的執行緒檢視](../debugger/media/parallel-stacksthread.png "Parallel_StacksThread")  
  
 在本圖中，是用藍色醒目提示目前執行緒的呼叫路徑，並用黃色箭號表示作用中堆疊框架。 您可以在 [ **平行堆疊** ] 視窗中選取不同的方法，以變更目前的堆疊框架。 這可能也會導致切換目前執行緒，取決於您選取的方法已是目前執行緒的一部分還是另一個執行緒的一部分。 下表描述 [ **平行堆疊** ] 視窗的主要功能，如圖所示。  
  
|圖說文字字母|元素名稱|描述|  
|--------------------|------------------|-----------------|  
|A|呼叫堆疊區段或節點|包含一個或多個執行緒的一系列方法內容。 如果節點未連接任何帶箭號的線條，則表示它代表執行緒的整個呼叫路徑。|  
|B|藍色醒目提示|表示目前執行緒的呼叫路徑。|  
|C|帶箭號的線條|連接節點，以構成執行緒的整個呼叫路徑。|  
|D|節點標題的工具提示|顯示其呼叫路徑共用這個節點之每個執行緒的 ID 和由使用者定義的名稱。|  
|E|方法內容|表示相同方法中的一個或多個堆疊框架。|  
|F|方法內容的工具提示|在 [執行緒] 視圖中，它會顯示資料表中的所有線程，類似于 [ **執行緒** ] 視窗。 在工作檢視中，它會顯示資料表中的所有工作，類似于 [ **平行** 工作] 視窗。|  
  
 此外，當圖形太大而無法放入視窗中時，[平行堆疊] 視窗會在主窗格中顯示 **鳥的眼睛** 圖示。 您可以按一下圖示，在視窗中查看整個圖形。  
  
## <a name="method-context-icons"></a>方法內容圖示  
 下表所說明的圖示提供作用中和目前堆疊框架的詳細資訊：  
  
|圖示|描述|  
|-|-|
|![[平行堆疊] 的黃色箭號](../debugger/media/icon-parallelyellowarrow.gif "Icon_ParallelYellowArrow")|表示方法內容包含目前執行緒的作用中堆疊框架。|  
|![[平行堆疊] 的執行緒圖示](../debugger/media/icon-parallelthreads.gif "Icon_ParallelThreads")|表示方法內容包含非目前執行緒的作用中堆疊框架。|  
|![[平行堆疊] 的綠色箭號](../debugger/media/icon-parallelgreenarrow.gif "Icon_ParallelGreenArrow")|表示方法內容包含目前堆疊框架。 該方法名稱在其出現的所有節點中會顯示為粗體。|  
  
## <a name="toolbar-controls"></a>工具列控制項  
 下圖和下表說明 [平行堆疊] 工具列中可用的控制項。  
  
 ![[平行堆疊] 視窗的中的工具列](../debugger/media/parallel-stackstoolbar.png "Parallel_StacksToolbar")  
  
|圖說文字字母|控制|描述|  
|--------------------|-------------|-----------------|  
|A|執行緒/工作下拉式方塊|切換執行緒呼叫堆疊檢閱和工作呼叫堆疊檢閱。 如需詳細資訊，請參閱＜工作檢視＞和＜執行緒檢視＞。|  
|B|僅顯示有旗標的項目|只針對在其他偵錯工具視窗（例如 [ **GPU 執行緒** ] 視窗和 [ **平行監看** 式] 視窗）中加上旗標的執行緒顯示呼叫堆疊。|  
|C|切換方法檢視|切換 [堆疊檢視] 和 [方法檢視]。 如需詳細資訊，請參閱＜方法檢視＞。|  
|D|自動捲動到目前堆疊框架|自動捲動圖表，讓目前堆疊框架出現在檢視中。 當您要從其他視窗變更目前堆疊框架，或是到達大型圖表中的新中斷點時，這項功能會很有用。|  
|E|切換縮放控制|顯示或隱藏縮放控制項。 您也可以按 CTRL 鍵，並開啟滑鼠滾輪（不論縮放控制項的可見度為何），或使用 **ctrl + shift + ' + '** 來放大和 **ctrl + shift + '-'** 以縮小。按下 **CTRL + F8** 將會縮放以符合螢幕。|  
  
### <a name="context-menu-items"></a>操作功能表項目  
 下圖和下表說明當您以滑鼠右鍵按一下 [執行緒檢閱] 或 [工作檢閱] 中的方法內容時，可用的捷徑功能表項目。 後六個項目是直接從 [呼叫堆疊] 視窗借用，並未引入新的行為。  
  
 ![[平行堆疊] 視窗中的捷徑功能表](../debugger/media/parallel-contmenu.png "Parallel_ContMenu")  
  
|功能表項目|描述|  
|---------------|-----------------|  
|旗標|將選取的項目加上旗標。|  
|取消旗標|取消所選取項目的旗標。|  
|凍結|將選取的項目凍結。|  
|解除凍結|將選取的項目解除凍結。|  
|移至工作 (執行緒)|執行的功能與工具列上的下拉式方塊相同，但是會持續醒目提示同一個堆疊框架。|  
|移至原始程式碼|巡覽至原始程式碼中的位置，而這個位置對應於使用者以滑鼠右鍵按一下的堆疊框架。|  
|切換至框架|與 [呼叫堆疊] 視窗上對應的功能表命令相同。 不過，使用 [平行堆疊] 時，多個框架可能會對應至一個方法內容。 因此，功能表項目會有子功能表，而每個子功能表都表示特定的堆疊框架。 如果其中一個堆疊框架是在目前執行緒上，則與該堆疊框架對應的功能表會呈現選取狀態。|  
|移至反組譯碼|巡覽至反組譯碼視窗中的位置，而這個位置對應於使用者以滑鼠右鍵按一下的堆疊框架。|  
|顯示外部程式碼|顯示或隱藏外部程式碼。|  
|十六進位顯示|切換十進位和十六進位顯示。|  
|符號載入資訊|顯示對應的對話方塊。|  
|符號設定|顯示對應的對話方塊。|  
  
## <a name="tasks-view"></a>工作檢閱  
 如果您的應用程式使用 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 物件 (managed 程式碼) 或 `task_handle` 物件 (機器碼) 以表示平行處理原則，您可以使用 [平行堆疊] 視窗工具列中的下拉式方塊來切換至工作 *視圖*。 [工作檢視] 會顯示工作 (而非執行緒) 的呼叫堆疊。 [工作檢閱] 有別於 [執行緒檢閱] 之處在於：  
  
- 如果執行緒沒有在執行工作，則不會顯示該執行緒的呼叫堆疊。  
  
- 如果執行緒目前正在執行工作，則會隱藏該執行緒之呼叫堆疊的頂端和底端，以顯示與工作最相關的框架。  
  
- 當有多個工作在同一個執行緒上時，這些工作的呼叫堆疊會分割成不同的節點。  
  
  下圖右邊顯示的是 [平行堆疊] 的 [工作檢視]，左邊顯示的是對應的 [執行緒檢視]。  
  
  ![[平行堆疊] 視窗中的工作檢閱](../debugger/media/parallel-tasksview.png "Parallel_TasksView")  
  
  若要查看整個呼叫堆疊，只要以滑鼠右鍵按一下堆疊框架，然後按一下 [ **移至執行緒**]，即可切換回執行緒的觀點。  
  
  如前表所述，將滑鼠游標停留在方法內容上，就可以看到其他資訊。 下圖為 [執行緒檢閱] 和 [工作檢閱] 的工具提示中所顯示的資訊。  
  
  ![[平行堆疊] 視窗中的工具提示](../debugger/media/parallel-stack-tooltips.png "Parallel_Stack_Tooltips")  
  
## <a name="method-view"></a>方法檢視  
 在 [執行緒檢閱] 或 [工作檢閱] 中，按一下工具列上的 [方法檢閱] 圖示，就可以切換至目前方法的圖形。 [方法檢視] 會顯示所有執行緒上所有呼叫目前方法或被目前方法呼叫的方法。 下圖顯示 [執行緒檢視]，以及相同的資訊在 [方法檢視] 中的樣子。  
  
 ![[平行堆疊] 視窗中的方法檢視](../debugger/media/parallel-methodview.png "Parallel_MethodView")  
  
 切換至新的堆疊框架，就可以將該方法變成目前的方法，並讓視窗顯示新方法的所有呼叫端和被呼叫端。 有些執行緒可能會因此顯示或不見，視該方法是否出現在這些執行緒的呼叫堆疊中。 若要回到 [堆疊檢視]，請再按一下 [方法檢視] 工具列按鈕。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：進行平行應用程式的偵錯工具](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [偵錯工具基本概念](../debugger/debugger-basics.md)   
 [Managed 程式碼的偵錯工具](../debugger/debugging-managed-code.md)   
 [平行程式設計](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [使用工作視窗](../debugger/using-the-tasks-window.md)   
 [逐步解說：進行平行應用程式的偵錯工具](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Task 類別](../extensibility/debugger/task-class-internal-members.md)
