---
title: "在 Visual Studio 中偵錯多執行緒應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.gputthreads"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "偵錯 [Visual Studio], 高效能運算"
  - "偵錯 [Visual Studio], 多執行緒"
  - "高效能偵錯"
  - "多執行緒偵錯"
  - "執行緒處理 [Visual Studio], 偵錯"
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 在 Visual Studio 中偵錯多執行緒應用程式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

執行緒是作業系統配置處理器時間的指令序列。  在作業系統中執行的每個處理序都包含至少一個執行緒。  具有一個以上執行緒的處理序就稱為多執行緒。  
  
 具有多個處理器、多重核心處理器或超執行緒處理器的電腦，可以同時執行多個執行緒。  多個執行緒的平行處理可以大幅改進程式效能，但由於帶來了追蹤多個執行緒的需要，也可能會增加偵錯的困難度。  
  
 除此之外，多執行緒也帶來一些新類型的潛在錯誤。  舉例來說，常常有兩個以上的執行緒必須存取相同資源，但同時間只有一個執行緒能夠安全存取該資源。  所以某些形式的互斥是必要的，才能確保同時間只有一個執行緒在存取該資源。  如果執行互斥的方式不正確，就可能產生「*死結*」\(Deadlock\) 的情況，造成沒有執行緒能夠執行。  在偵錯時死結可能會是個特別難處理的問題。  
  
 Visual Studio 提供 \[執行緒\] 視窗、\[GPU 執行緒\] 視窗、\[平行監看式\] 視窗和其他功能，讓多執行緒偵錯更容易。 了解執行緒功能最好的方式，就是執行逐步解說。  請參閱[逐步解說：偵錯多執行緒應用程式](../debugger/walkthrough-debugging-a-multithreaded-application.md)和[逐步解說：偵錯 C\+\+ AMP 應用程式](../Topic/Walkthrough:%20Debugging%20a%20C++%20AMP%20Application.md)。  
  
 Visual Studio 同樣提供強大的中斷點和追蹤點，這在您對多執行緒應用程式進行偵錯時非常實用。  您可以使用中斷點篩選條件，將中斷點放置在個別執行緒上。  請參閱[使用中斷點](../debugger/using-breakpoints.md)  
  
 偵錯具有使用者介面的多執行緒應用程式可能會特別地困難。  在這種情況下，您可以考慮在第二部電腦上執行該應用程式，並使用遠端偵錯。  如需詳細資訊，請參閱[遠端偵錯](../debugger/remote-debugging.md)。  
  
## 在本節中  
 [偵錯執行緒和處理序](../debugger/debug-threads-and-processes.md)  
 說明偵錯執行緒和處理序的基本概念。  
  
 [偵錯處理序](../debugger/debug-multiple-processes.md)  
 說明如何偵錯多重處理序  
  
 [如何：使用執行緒視窗](../debugger/how-to-use-the-threads-window.md)  
 使用 \[**執行緒**\] 視窗偵錯執行緒的好用程序。  
  
 [如何：在偵錯時切換到另一個執行緒](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 切換偵錯內容到另一個執行緒的三種方式。  
  
 [如何：將執行緒加上旗標和取消旗標](../Topic/How%20to:%20Flag%20and%20Unflag%20Threads.md)  
 將您要在偵錯時特別注意的執行緒加上標記或旗標。  
  
 [如何：在機器碼中設定執行緒名稱](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 為執行緒命名以方便在 \[**執行緒**\] 視窗中檢視。  
  
 [如何：在 Managed 程式碼中設定執行緒名稱](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 為執行緒命名以方便在 \[**執行緒**\] 視窗中檢視。  
  
 [逐步解說：偵錯多執行緒應用程式](../debugger/walkthrough-debugging-a-multithreaded-application.md)。  
 執行緒偵錯功能的導覽，並強調說明 [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] 的功能。  
  
 [如何：偵錯高效能叢集](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 偵錯在高效能叢集上執行的應用程式的相關技巧。  
  
 [在機器碼中偵錯執行緒的秘訣](../debugger/tips-for-debugging-threads-in-native-code.md)  
 在偵錯原生執行緒時非常好用的簡單技巧。  
  
 [使用工作視窗](../debugger/using-the-tasks-window.md)  
 顯示所有 Managed 或原生工作物件，包括其狀態和其他有用的資訊。  
  
 [使用平行堆疊視窗](../debugger/using-the-parallel-stacks-window.md)  
 以單一檢視顯示多個執行緒 \(或工作\) 的呼叫堆疊，並且聯合執行緒 \(或工作\) 共有的堆疊區段。  
  
 [逐步解說：偵錯平行應用程式](../debugger/walkthrough-debugging-a-parallel-application.md)  
 顯示如何使用 \[平行工作\] 和 \[平行堆疊\] 視窗的逐步解說。  
  
 [如何：使用平行監看式視窗](../debugger/how-to-use-the-parallel-watch-window.md)  
 跨多個執行緒檢查值和運算式。  
  
 [如何：使用 GPU 執行緒視窗](../Topic/How%20to:%20Use%20the%20GPU%20Threads%20Window.md)  
 在偵錯期間檢查並使用 GPU 上執行的執行緒。  
  
## 相關章節  
 [使用中斷點](../debugger/using-breakpoints.md)  
 -   在您要將中斷點放置在個別執行緒上時，可以使用的中斷點篩選條件。  
  
-   追蹤點可以讓您追蹤程式的執行，而不會中斷程式。  在研究死結這類的問題時非常好用。  
  
 [Threading](../Topic/Managed%20Threading.md)  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 程式設計中的執行緒概念，包括範例程式碼。  
  
 [元件中的多執行緒](../Topic/Multithreading%20in%20Components.md)  
 如何在 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 元件中使用多執行緒處理。  
  
 [舊版程式碼的多執行緒支援 \(Visual C\+\+\)](/visual-cpp/parallel/multithreading/multithreading-support-for-older-code-visual-cpp)  
 提供給使用 MFC 的 C\+\+ 程式設計人員的執行緒概念和範例程式碼。  
  
## 請參閱  
 [偵錯執行緒和處理序](../debugger/debug-threads-and-processes.md)   
 [遠端偵錯](../debugger/remote-debugging.md)