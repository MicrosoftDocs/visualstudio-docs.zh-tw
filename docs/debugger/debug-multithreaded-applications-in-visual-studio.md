---
title: 偵錯多執行緒應用程式 |Microsoft Docs
ms.custom: seodec18
ms.date: 11/06/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8158444662b7e0b2f7eb90d4ec5919314489dfc1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54960593"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>在 Visual Studio 中對多執行緒應用程式進行偵錯
執行緒是一連串的指示，作業系統授與處理器時間。 在作業系統中執行的每個處理序都包含至少一個執行緒。 具有一個以上執行緒的處理序就稱為多執行緒。  
  
具有多個處理器、 多核心處理器或超執行緒處理器的電腦可以執行數個同時執行緒。 平行處理 使用多個執行緒可以大幅改善程式效能，但它可能也會使偵錯更加困難因為您正在追蹤的執行緒數目。  
  
多執行緒可以導入新類型的潛在錯誤。 例如，兩個或多個執行緒可能需要存取相同的資源，但一次只有一個執行緒可以安全地存取資源。 必須先確定只有一個執行緒存取的資源，在任何時候某種形式的互斥。 如果未正確實作互斥，它可以建立*死結*條件沒有任何執行緒執行的位置。 死結通常是偵錯困難的問題。

## <a name="tools-for-debugging-multithreaded-apps"></a>偵錯多執行緒應用程式的工具

Visual Studio 會提供不同的工具，以用於偵錯多執行緒應用程式。

- 偵錯執行緒的主要工具是以執行緒而言，**執行緒**視窗中，在來源視窗中的執行緒標記**平行堆疊**視窗中，**平行監看式**視窗中，而**偵錯位置**工具列。 若要了解**執行緒**視窗和**偵錯位置**工具列，請參閱[逐步解說：使用執行緒視窗進行偵錯](../debugger/how-to-use-the-threads-window.md)。 若要了解如何使用**平行堆疊**並**平行監看式**windows，請參閱[開始偵錯多執行緒應用程式](../debugger/get-started-debugging-multithreaded-apps.md)。 這兩個主題示範如何使用執行緒標記。
  
- 使用程式碼[Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)或[並行執行階段](/cpp/parallel/concrt/concurrency-runtime/)，偵錯的主要工具是**平行堆疊**視窗中， **平行監看式** 視窗中，而**工作** 視窗，它也支援 JavaScript。 若要開始，請參閱[逐步解說：偵錯平行應用程式](../debugger/walkthrough-debugging-a-parallel-application.md)和[逐步解說：C + + AMP 應用程式偵錯](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)。 

- 偵錯 GPU 上的執行緒的主要工具是**GPU 執行緒**視窗。 請參閱[如何：使用 GPU 執行緒視窗](../debugger/how-to-use-the-gpu-threads-window.md)。  

- 處理程序的主要工具是**附加至處理序** 對話方塊中，**處理程序**視窗中，而**偵錯位置**工具列。  
  
Visual Studio 也提供功能強大的中斷點和追蹤點，這有助於進行偵錯多執行緒應用程式。 若要將中斷點放在個別執行緒上，使用中斷點條件和篩選。 追蹤點讓您追蹤程式執行而不會中斷，來研究問題，例如死結 （deadlock）。 如需詳細資訊，請參閱 <<c0> [ 中斷點動作和追蹤點](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)。

偵錯具有使用者介面的多執行緒應用程式可能會特別地困難。 您可以考慮在第二部電腦上執行應用程式，並使用遠端偵錯。 如需詳細資訊，請參閱 <<c0> [ 遠端偵錯](../debugger/remote-debugging.md)。  
  
## <a name="articles-about-debugging-multithreaded-apps"></a>有關偵錯多執行緒應用程式的文件

 [開始偵錯多執行緒應用程式](../debugger/get-started-debugging-multithreaded-apps.md)   
 執行緒偵錯功能，強調中的功能的教學課程**平行堆疊**視窗和**平行監看式**視窗。

 [執行緒和處理序偵錯工具](../debugger/debug-threads-and-processes.md)  
 列出執行緒和處理序偵錯工具的功能。  
  
 [對多重處理序進行偵錯](../debugger/debug-multiple-processes.md)  
 說明如何偵錯多重處理序

 [逐步解說：使用執行緒視窗進行偵錯](../debugger/how-to-use-the-threads-window.md)。  
 逐步解說，示範如何使用**執行緒**視窗和**偵錯位置**工具列。 

 [逐步解說：對平行應用程式進行偵錯](../debugger/walkthrough-debugging-a-parallel-application.md)  
 逐步解說，示範如何使用**平行堆疊**並**工作**windows。  
  
 [如何：在偵錯時切換到另一個執行緒](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 若要切換到另一個執行緒的偵錯內容的數種方式。  
  
 [如何：將執行緒加上旗標和取消旗標](../debugger/how-to-flag-and-unflag-threads.md)  
 將您要在偵錯時特別注意的執行緒加上標記或旗標。    
  
 [如何：在高效能叢集上進行偵錯](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 偵錯在高效能叢集上執行的應用程式的相關技巧。  

 [在機器碼中對執行緒進行偵錯的祕訣](../debugger/tips-for-debugging-threads-in-native-code.md)  
 在偵錯原生執行緒時非常好用的簡單技巧。 

 [如何：在機器碼中設定執行緒名稱](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 為執行緒命名以方便在 [執行緒] 視窗中檢視。  
  
 [如何：在受控碼中設定執行緒名稱](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 為執行緒命名以方便在 [執行緒] 視窗中檢視。 
  
## <a name="see-also"></a>另請參閱  

[使用中斷點](../debugger/using-breakpoints.md)  
[執行緒處理](/dotnet/standard/threading/index)  
[元件中的多執行緒](https://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)  
[舊版程式碼的多執行緒支援 (Visual C++)](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)  
 [偵錯執行緒和處理序](../debugger/debug-threads-and-processes.md)   
 [遠端偵錯](../debugger/remote-debugging.md)