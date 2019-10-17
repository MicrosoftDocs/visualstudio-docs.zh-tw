---
title: Debug 多執行緒應用程式 |Microsoft Docs
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
ms.openlocfilehash: 668e95c340348eeb1fa509622aa44d99b65b6efc
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72431801"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>在 Visual Studio 中對多執行緒應用程式進行偵錯
執行緒是作業系統授與處理器時間的一系列指令。 在作業系統中執行的每個處理序都包含至少一個執行緒。 具有一個以上執行緒的處理序就稱為多執行緒。

具有多個處理器、多核心處理器或超執行緒進程的電腦，可以執行數個同時執行緒。 使用多個執行緒的平行處理可以大幅提升程式效能，但可能會因為您追蹤許多執行緒而使調試更難以進行。

多執行緒可能會引進新類型的潛在 bug。 例如，兩個或多個執行緒可能需要存取相同的資源，但一次只能有一個執行緒可以安全地存取資源。 需要某種形式的互斥，以確保每次只有一個執行緒存取資源。 如果相互排除未正確執行，它可以建立不會執行任何執行緒的*鎖死*狀況。 鎖死通常是很難進行的調試問題。

## <a name="tools-for-debugging-multithreaded-apps"></a>用於調試多執行緒應用程式的工具

Visual Studio 提供不同的工具，讓您用來進行多執行緒應用程式的調試。

- 針對執行緒，用於偵錯工具的主要工具是 [**執行緒**] 視窗、[來源] 視窗中的執行緒標記、[**平行堆疊**] 視窗、[**平行監看**式] 視窗和 [**偵錯工具位置**] 工具列。 若要瞭解 [**執行緒**] 視窗和 [**調試位置**] 工具列，請參閱[逐步解說：使用執行緒視窗進行 debug](../debugger/how-to-use-the-threads-window.md)。 若要瞭解如何使用 [**平行堆疊**] 和 [**平行監看式]** 視窗，請參閱[開始進行多執行緒應用程式的偵錯工具](../debugger/get-started-debugging-multithreaded-apps.md)。 這兩個主題會示範如何使用執行緒標記。

- 針對使用工作平行連結[庫（TPL）](/dotnet/standard/parallel-programming/task-parallel-library-tpl)或[並行執行階段](/cpp/parallel/concrt/concurrency-runtime/)的程式碼，用於進行偵錯工具的主要工具是 [**平行堆疊**] 視窗、[**平行監看**式 **] 視窗和 [工作] 視窗**，這也支援JavaScript. 若要開始使用，請參閱[逐步解說：調試平行應用程式](../debugger/walkthrough-debugging-a-parallel-application.md)和[逐步C++解說：對 AMP 應用程式進行偵錯工具](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)。

- 若要在 GPU 上偵錯工具執行緒，主要工具是 [ **Gpu 執行緒**] 視窗。 請參閱[如何：使用 GPU 執行緒視窗](../debugger/how-to-use-the-gpu-threads-window.md)。

- 針對進程，主要工具是 [**附加至進程**] 對話方塊、[**進程**] 視窗和 [**偵錯工具位置**] 工具列。

Visual Studio 也提供強大的中斷點和追蹤點，這在您進行多執行緒應用程式的調試時非常有用。 使用中斷點條件和篩選器，將中斷點放在個別執行緒上。 追蹤點可讓您在不中斷的情況下追蹤程式的執行，以研究鎖死之類的問題。 如需詳細資訊，請參閱[中斷點動作和追蹤點](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)。

偵錯具有使用者介面的多執行緒應用程式可能會特別地困難。 您可以考慮在第二部電腦上執行應用程式，並使用遠端偵錯程式。 如需詳細資訊，請參閱[遠端偵錯](../debugger/remote-debugging.md)程式。

## <a name="articles-about-debugging-multithreaded-apps"></a>有關調試多執行緒應用程式的文章

 [開始調試多執行緒應用程式](../debugger/get-started-debugging-multithreaded-apps.md)

執行緒調試功能的導覽，強調 [**平行堆疊**] 視窗和 [**平行監看**式] 視窗中的功能。

 [用於偵錯工具和進程的工具](../debugger/debug-threads-and-processes.md)

列出用於偵錯工具執行緒和進程的工具功能。

 [對多重處理序進行偵錯](../debugger/debug-multiple-processes.md)

說明如何偵錯多重處理序

 [Walkthrough: Debug using the Threads window](../debugger/how-to-use-the-threads-window.md)(逐步解說：使用 [執行緒] 視窗進行偵錯)。

說明如何使用 [**執行緒**] 視窗和 [偵錯工具**位置**] 工具列的逐步解說。

 [逐步解說：對平行應用程式進行偵錯](../debugger/walkthrough-debugging-a-parallel-application.md)

說明如何使用 [**平行堆疊**] 和 [工作 **] 視窗的**逐步解說。

 [如何：在偵錯時切換到另一個執行緒](../debugger/how-to-switch-to-another-thread-while-debugging.md)

有數種方式可以將調試內容切換到另一個執行緒。

 [如何：將執行緒加上旗標和取消旗標](../debugger/how-to-flag-and-unflag-threads.md)

將您要在偵錯時特別注意的執行緒加上標記或旗標。

 [How to: Debug on a high-performance cluster](../debugger/how-to-debug-on-a-high-performance-cluster.md) (如何：對高效能叢集進行偵錯)。

偵錯在高效能叢集上執行的應用程式的相關技巧。

 [在機器碼中對執行緒進行偵錯的祕訣](../debugger/tips-for-debugging-threads-in-native-code.md)

在偵錯原生執行緒時非常好用的簡單技巧。

 [如何：在機器碼中設定執行緒名稱](../debugger/how-to-set-a-thread-name-in-native-code.md)

為執行緒命名以方便在 [執行緒] 視窗中檢視。

 [如何：在 Managed 程式碼中設定執行緒名稱](../debugger/how-to-set-a-thread-name-in-managed-code.md)

為執行緒命名以方便在 [執行緒] 視窗中檢視。

## <a name="see-also"></a>請參閱

- [使用中斷點](../debugger/using-breakpoints.md)
- [執行緒處理](/dotnet/standard/threading/index)
- [元件中的多執行緒](https://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)
- [舊版程式碼的多執行緒支援](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)
- [Debug threads and processes](../debugger/debug-threads-and-processes.md) (對執行緒和處理序進行偵錯)
- [遠端偵錯](../debugger/remote-debugging.md)