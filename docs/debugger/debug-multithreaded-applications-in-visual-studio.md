---
title: "偵錯 Visual Studio 中的多執行緒應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 09/05/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.gputthreads
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
caps.latest.revision: "25"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f8798616d9a39d46150f039ffe4340302439f31
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>在 Visual Studio 中偵錯多執行緒應用程式
執行緒是作業系統配置處理器時間的指令序列。 在作業系統中執行的每個處理序都包含至少一個執行緒。 具有一個以上執行緒的處理序就稱為多執行緒。  
  
具有多個處理器、多重核心處理器或超執行緒處理器的電腦，可以同時執行多個執行緒。 多個執行緒的平行處理可以大幅改進程式效能，但由於帶來了追蹤多個執行緒的需要，也可能會增加偵錯的困難度。  
  
除此之外，多執行緒也帶來一些新類型的潛在錯誤。 舉例來說，常常有兩個以上的執行緒必須存取相同資源，但同時間只有一個執行緒能夠安全存取該資源。 所以某些形式的互斥是必要的，才能確保同時間只有一個執行緒在存取該資源。 如果執行互斥的方式不正確，就可以建立*死結*沒有執行緒能夠在其中執行的條件。 在偵錯時死結可能會是個特別難處理的問題。

Visual Studio 會提供不同的工具，以用於偵錯多執行緒應用程式。

- 執行緒偵錯執行緒的主要工具是**執行緒**視窗中，來源視窗中的執行緒標記**平行堆疊**視窗中，**平行監看式**視窗中，並**偵錯位置**工具列。 若要了解**執行緒**視窗和**偵錯位置**工具列上，請參閱[逐步解說： 使用 [執行緒] 視窗進行偵錯](../debugger/how-to-use-the-threads-window.md)。 若要了解如何使用**平行堆疊**和**平行監看式**windows，請參閱[開始偵錯多執行緒應用程式](../debugger/get-started-debugging-multithreaded-apps.md)。 這兩個主題示範如何使用執行緒標記。
  
- 使用之程式碼[工作平行程式庫 (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)或[並行執行階段](/cpp/parallel/concrt/concurrency-runtime/)，偵錯的主要工具是**平行堆疊**視窗中， **平行監看式**視窗中，而**工作**視窗 (**工作**視窗也支援 JavaScript)。 若要開始使用，請參閱[逐步解說： 偵錯平行應用程式](../debugger/walkthrough-debugging-a-parallel-application.md)和[逐步解說： 偵錯 c + + AMP 應用程式](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)。 

- 主要工具是偵錯 gpu 執行緒， **GPU 執行緒**視窗。 請參閱[How to： 使用 GPU 執行緒視窗](../debugger/how-to-use-the-gpu-threads-window.md)。  

- 針對處理程序的主要工具是**附加至處理序**對話方塊中，**處理程序**視窗中，而**偵錯位置**工具列。  
  
Visual Studio 同樣提供強大的中斷點和追蹤點，這在您對多執行緒應用程式進行偵錯時非常實用。 您可以使用中斷點條件和篩選條件，將中斷點放置在個別執行緒上。 請參閱[使用中斷點](../debugger/using-breakpoints.md)。 
  
偵錯具有使用者介面的多執行緒應用程式可能會特別地困難。 在這種情況下，您可以考慮在第二部電腦上執行該應用程式，並使用遠端偵錯。 如需資訊，請參閱[遠端偵錯](../debugger/remote-debugging.md)。  
  
## <a name="in-this-section"></a>本章節內容
 [開始偵錯多執行緒應用程式](../debugger/get-started-debugging-multithreaded-apps.md)。  
 執行緒偵錯功能，並強調的功能的導覽**平行堆疊**視窗和**平行監看式**視窗。

 [執行緒和處理序偵錯工具](../debugger/debug-threads-and-processes.md)  
 列出的執行緒和處理序偵錯工具的功能。  
  
 [偵錯多重處理序](../debugger/debug-multiple-processes.md)  
 說明如何偵錯多重處理序

 [逐步解說： 偵錯使用執行緒視窗](../debugger/how-to-use-the-threads-window.md)。  
 逐步解說，示範如何使用**執行緒**視窗和**偵錯位置**工具列。 

 [逐步解說： 偵錯平行應用程式](../debugger/walkthrough-debugging-a-parallel-application.md)  
 逐步解說，示範如何使用**平行堆疊**和**工作**windows。  
  
 [如何：在偵錯時切換到另一個執行緒](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 切換偵錯內容到另一個執行緒的三種方式。  
  
 [如何：將執行緒加上旗標和取消旗標](../debugger/how-to-flag-and-unflag-threads.md)  
 將您要在偵錯時特別注意的執行緒加上標記或旗標。    
  
 [如何：偵錯高效能叢集](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 偵錯在高效能叢集上執行的應用程式的相關技巧。  

 [在機器碼中偵錯執行緒的秘訣](../debugger/tips-for-debugging-threads-in-native-code.md)  
 在偵錯原生執行緒時非常好用的簡單技巧。 

 [如何：在機器碼中設定執行緒名稱](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 為執行緒檢視中的名稱以方便**執行緒**視窗。  
  
 [如何：在 Managed 程式碼中設定執行緒名稱](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 為執行緒檢視中的名稱以方便**執行緒**視窗。 
  
## <a name="related-sections"></a>相關章節  
 [使用中斷點](../debugger/using-breakpoints.md)

 - 當您想要偵錯個別執行緒時，請使用中斷點條件或篩選。  
  
 - 追蹤點可以讓您追蹤程式的執行，而不會中斷程式。 在研究死結這類的問題時非常好用。  
  
 [執行緒處理](/dotnet/standard/threading/index)  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 程式設計中的執行緒概念，包括範例程式碼。  
  
 [元件中的多執行緒](http://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)  
 如何在 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 元件中使用多執行緒處理。  
  
 [舊版程式碼的多執行緒支援 (Visual C++)](/cpp/parallel/multithreading/multithreading-support-for-older-code-visual-cpp)  
 提供給使用 MFC 的 C++ 程式設計人員的執行緒概念和範例程式碼。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯執行緒和處理序](../debugger/debug-threads-and-processes.md)   
 [遠端偵錯](../debugger/remote-debugging.md)