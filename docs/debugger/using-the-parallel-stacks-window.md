---
title: 在 [平行堆疊] 視窗中查看執行緒 |Microsoft Docs
description: 使用平行堆疊來協助您進行多執行緒應用程式的偵錯工具。 您可以查看所有線程的堆疊資訊，以及以工作為中心的呼叫堆疊資訊。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 55a004e65a39f4a2b7bbf972cec36d689bf88d97
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150167"
---
# <a name="view-threads-and-tasks-in-the-parallel-stacks-window-c-visual-basic-c"></a>在 [平行堆疊] 視窗中查看執行緒和工作 (c #、Visual Basic、c + +) 

[ **平行堆疊** ] 視窗適用于多執行緒應用程式的偵錯工具。 它有數個觀點：

- [[執行緒] 視圖](#threads-view)會顯示應用程式中所有線程的呼叫堆疊資訊。 您可以線上程和這些執行緒上的堆疊框架之間流覽。

- [工作][視圖](#tasks-view)會顯示以工作為中心的呼叫堆疊資訊。
  - 在 managed 程式碼 **中，** [工作] 視圖會顯示物件的呼叫堆疊 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 。
  - 在機器碼中，[工作 **] 視圖會** 顯示 [工作組](/cpp/parallel/concrt/task-parallelism-concurrency-runtime)、 [平行演算法](/cpp/parallel/concrt/parallel-algorithms)、 [非同步代理](/cpp/parallel/concrt/asynchronous-agents)程式和 [輕量](/cpp/parallel/concrt/task-scheduler-concurrency-runtime)工作的呼叫堆疊。

- [[方法視圖](#method-view)] 會將所選方法的呼叫堆疊進行透視。

## <a name="use-the-parallel-stacks-window"></a>使用平行堆疊視窗

若要開啟 [ **平行堆疊** ] 視窗，您必須在調試會話中。 選取 [ **Debug**  >  **Windows**  >  **平行堆疊**]。

### <a name="toolbar-controls"></a>工具列控制項

[ **平行堆疊** ] 視窗具有下列工具列控制項：

![[平行堆疊] 視窗的中的工具列](../debugger/media/parallel_stackstoolbar.png "平行堆疊工具列")

|圖示|控制|描述|
|-|-|-|
|![執行緒/工作下拉式方塊](media/parallel_toolbar1.png "執行緒/工作下拉式方塊")|**執行緒** /工作 **下拉式方塊**|切換執行緒呼叫堆疊檢閱和工作呼叫堆疊檢閱。 如需詳細資訊，請參閱[工作檢視](#tasks-view)和[執行緒檢視](#threads-view)。|
|![僅顯示已加上旗標的圖示](media/parallel_toolbar2.png "僅顯示已加上旗標的圖示")|僅顯示有旗標的項目|只顯示在其他偵錯工具視窗（例如 [ **GPU 執行緒** ] 視窗和 [ **平行監看** 式] 視窗）中加上旗標之執行緒的呼叫堆疊。|
|![切換方法視圖圖示](media/parallel_toolbar3.png "切換方法視圖圖示")|切換 **方法檢視**|在呼叫堆疊視圖和 **方法視圖** 之間切換。 如需詳細資訊，請參閱[方法檢視](#method-view)。|
|![自動滾動至目前的圖示](media/parallel_toolbar4.png "自動滾動至目前的圖示")|自動捲動到目前堆疊框架|自動捲動圖形，讓目前的堆疊框架處於視野中。 當您從其他視窗變更目前的堆疊框架，或當您在大型圖形中叫用新的中斷點時，這項功能就很有用。|
|![切換縮放圖示](media/parallel_toolbar5.png "切換縮放圖示")|切換縮放控制|顯示或隱藏視窗左邊的縮放控制項。 <br /><br />無論縮放控制項的可見度是否可見，您也可以按 **ctrl** 鍵並開啟滑鼠滾輪，或按 **ctrl** + **shift** 鍵放大 + **+** 和 **ctrl** + **shift** + **-** 以縮小。 |

### <a name="stack-frame-icons"></a>堆疊框架圖示
下列圖示提供所有視圖中作用中和目前堆疊框架的相關資訊：

|圖示|描述|
|-|-|
|![黃色箭號](media/icon_parallelyellowarrow.gif)|指出目前的位置 (現用堆疊框架) 目前的執行緒。|
|![執行緒圖示](media/icon_parallelthreads.gif)|指出目前位置 (非目前線程的作用中堆疊框架) 。|
|![綠色箭頭](media/icon_parallelgreenarrow.gif)|指出目前的堆疊框架 (目前的偵錯工具內容) 。 方法名稱會以粗體顯示。|

### <a name="context-menu-items"></a>操作功能表項目
當您以滑鼠右鍵按一下 [ **執行緒** ] **視圖或 [** 工作] 視圖中的方法時，可以使用下列快速鍵功能表項目。 最後六個專案和 [ [呼叫堆疊] 視窗](how-to-use-the-call-stack-window.md)中的專案相同。

![[平行堆疊] 視窗中的捷徑功能表](../debugger/media/parallel_contmenu.png "[平行堆疊] 視窗中的捷徑功能表")

|功能表項目|描述|
|-|-|
|**旗標**|將選取的項目加上旗標。|
|**取消旗標**|取消所選取項目的旗標。|
|**凍結**|將選取的項目凍結。|
|**解凍**|將選取的項目解除凍結。|
|**切換至框架**|與 [ **呼叫堆疊** ] 視窗中對應的功能表命令相同。 不過，在 [ **平行堆疊** ] 視窗中，其中一個方法可能會在數個框架中。 您可以在此專案的子功能表中，選取想要的畫面格。 如果其中一個堆疊框架是在目前的執行緒上，則預設會在子功能表中選取該框架。|
|**移至**[工作] 或 [**移至執行緒**]|切換至 [工作] **或 [** **執行緒** ] 視圖，並將相同的堆疊框架保持反白顯示。|
|**移至原始程式碼**|移至原始程式碼視窗中的對應位置。 |
|**前往反組譯碼**|移至 [反組 **解碼] 視窗中的對應** 位置。|
|**顯示外部程式碼**|顯示或隱藏外部程式碼。|
|**十六進位顯示**|切換十進位和十六進位顯示。|
|**在原始程式檔中顯示執行緒**|在原始程式碼視窗中標示執行緒的位置。 |
|**符號載入資訊**|開啟 [ **符號載入資訊** ] 對話方塊。|
|**符號設定**|開啟 [ **符號設定** ] 對話方塊。 |

## <a name="threads-view"></a>執行緒檢視

在 [ **執行緒** ] 視圖中，目前線程的堆疊框架和呼叫路徑會以藍色反白顯示。 執行緒的目前位置會以黃色箭號顯示。

若要變更目前的堆疊框架，請按兩下另一個方法。 這也可能會根據您選取的方法是目前線程或另一個執行緒的一部分，來切換目前的執行緒。

當 **執行緒** 視圖圖形太大而無法放入視窗中時，會在視窗中顯示 **鳥的眼睛** 控制項。 您可以移動控制項中的框架，以流覽至圖表的不同部分。

下圖顯示從 Main 移至 Managed to 機器碼轉換的一個執行緒。 目前的方法中有六個執行緒。 其中一個會繼續進入執行緒。睡眠，另一個則繼續進行主控台. WriteLine，然後 SyncTextWriter WriteLine。

 ![[平行堆疊] 視窗中的執行緒檢視](../debugger/media/parallel_stack1.png "[平行堆疊] 視窗中的執行緒檢視")

下表描述 [ **執行緒** ] 視圖的主要功能：

|圖說文字|元素名稱|描述|
|-|-|-|
|1|呼叫堆疊區段或節點|包含一或多個執行緒的一系列方法。 如果框架沒有連接的箭號線，框架會顯示執行緒 (的整個呼叫路徑) 。|
|2|藍色醒目提示|表示目前執行緒的呼叫路徑。|
|3|帶箭號的線條|連接節點，以構成執行緒的整個呼叫路徑。|
|4|節點標頭|顯示節點的進程和執行緒數目。|
|5|方法|表示相同方法中的一個或多個堆疊框架。|
|6|方法上的工具提示|當您將滑鼠停留在方法上時顯示。 在 [ **執行緒** ] 視圖中，工具提示會在類似于 [ **執行緒** ] 視窗的資料表中顯示所有線程。 |

## <a name="tasks-view"></a>工作檢視
如果您的應用程式使用 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 物件 (managed 程式碼) 或 `task_handle` 物件 (機器碼) 以表示平行處理原則 ，您可以使用 [工作視圖]。 [工作] 檢視會顯示工作 (而非執行緒) 的呼叫堆疊。

在 **[** 工作] 視圖中：

- 不會顯示未執行工作之執行緒的呼叫堆疊。
- 正在執行工作之執行緒的呼叫堆疊會在頂端和底部以視覺化方式修剪，以顯示工作最相關的畫面格。
- 當有數個工作在一個執行緒上時，這些工作的呼叫堆疊會顯示在不同的節點中。

若要查看整個呼叫堆疊，請以滑鼠右鍵按一下堆疊框架，然後選取 [**移至執行緒**]，切換回 **執行緒** 的觀點。

下圖顯示頂端的 [ **執行緒** ] 視圖，以及底部的 **對應工作** 視圖。

![執行緒和工作視圖](../debugger/media/parallel_threads-tasks.png "執行緒和工作視圖")

將滑鼠停留在方法上，以顯示具有其他資訊的工具提示。 在 [工作 **] 視圖中** ，工具提示會顯示資料表 **中的所有** 工作，類似于 [工作] 視窗。

下圖顯示 [ **執行緒** ] 視圖中的方法工具提示，以及底部 **的對應工作** 視圖。

![執行緒和工作工具提示](../debugger/media/parallel_threads-tasks-tooltips.png "執行緒和工作工具提示")

## <a name="method-view"></a>方法檢視
從 [ **執行緒** **] 或 [** 工作] 視圖中，您可以選取工具列上的 [ **切換方法視圖** ] 圖示，以在目前的方法上旋轉圖表。 [方法檢視] 會顯示所有執行緒上所有呼叫目前方法，或由目前方法呼叫的方法。 下圖顯示相同資訊在右側的 [ **執行緒** ] 和 [ **方法] 視圖** 中的外觀。

![執行緒視圖和方法視圖](../debugger/media/parallel_methodview.png "執行緒視圖和方法視圖")

如果您切換至新的堆疊框架，則會將該方法設為目前的方法，而 [ **方法視圖** ] 會顯示新方法的所有呼叫端和被呼叫端。 有些執行緒可能會因此顯示或不見，視該方法是否出現在這些執行緒的呼叫堆疊中。 若要返回 [呼叫堆疊] 視圖，請再次選取 [ **方法視圖** ] 工具列圖示。

## <a name="see-also"></a>另請參閱
- [開始對多執行緒應用程式進行偵錯工具](../debugger/get-started-debugging-multithreaded-apps.md)
- [逐步解說：對平行應用程式進行偵錯](../debugger/walkthrough-debugging-a-parallel-application.md)
- [偵錯工具簡介](../debugger/debugger-feature-tour.md)
- [Managed 程式碼的偵錯工具](../debugger/debugging-managed-code.md)
- [平行程式設計](/dotnet/standard/parallel-programming/index)
- [使用工作視窗](../debugger/using-the-tasks-window.md)
- [Task 類別](../extensibility/debugger/task-class-internal-members.md)
