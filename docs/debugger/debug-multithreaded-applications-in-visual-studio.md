---
title: Debug 多執行緒應用程式 |Microsoft Docs
description: 在 Visual Studio 中調試多執行緒應用程式。 檢查多執行緒應用程式的相關工具和其他文章。
ms.custom: SEO-VS-2020, seodec18
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
ms.openlocfilehash: 4fed6580219964ab71f5a5010060c1af193375df
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727134"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>在 Visual Studio 中對多執行緒應用程式進行偵錯
執行緒是作業系統授權處理器時間的一連串指令。 在作業系統中執行的每個處理序都包含至少一個執行緒。 具有一個以上執行緒的處理序就稱為多執行緒。

具有多個處理器、多核心處理器或超執行緒進程的電腦可以執行數個同時執行緒。 使用許多執行緒進行平行處理可大幅提升程式效能，但因為您正在追蹤許多執行緒，所以可能也會讓偵錯工具更困難。

多執行緒可能會引進新類型的潛在錯誤。 例如，兩個或多個執行緒可能需要存取相同的資源，但是一次只能有一個執行緒可以安全地存取資源。 需要某種形式的互斥，以確保每次只有一個執行緒存取資源。 如果相互排除未正確執行，它可以建立不會執行任何執行緒的 *鎖死* 條件。 鎖死通常是難以進行調試的問題。

## <a name="tools-for-debugging-multithreaded-apps"></a>用於調試多執行緒應用程式的工具

Visual Studio 提供不同的工具，可用於調試多執行緒應用程式。

- 針對執行緒，偵測執行緒的主要工具是 [ **執行緒** ] 視窗、來源視窗中的執行緒標記、[ **平行堆疊** ] 視窗、[ **平行監看** 式] 視窗和 [ **偵錯工具位置** ] 工具列。 若要瞭解 [ **執行緒** ] 視窗和 [ **調試位置** ] 工具列，請參閱 [逐步解說：使用執行緒視窗進行 debug](../debugger/how-to-use-the-threads-window.md)。 若要瞭解如何使用 [ **平行堆疊** ] 和 [ **平行監看式]** 視窗，請參閱 [開始對多執行緒應用程式進行偵錯工具](../debugger/get-started-debugging-multithreaded-apps.md)。 這兩個主題都會示範如何使用執行緒標記。

- 針對使用工作平行連結 [庫 (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)或 [並行執行階段](/cpp/parallel/concrt/concurrency-runtime/)的程式碼，偵錯工具的主要工具是 [**平行堆疊**] 視窗、[**平行監看****式] 視窗和 [工作]** 視窗，也支援 JavaScript。 若要開始使用，請參閱 [逐步解說：進行平行應用程式的偵錯工具](../debugger/walkthrough-debugging-a-parallel-application.md) 和 [逐步解說： C++ AMP 應用程式的偵錯工具](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)。

- 若要在 GPU 上進行執行緒的偵錯工具，主要工具是 [ **GPU 執行緒** ] 視窗。 請參閱 [如何：使用 GPU 執行緒視窗](../debugger/how-to-use-the-gpu-threads-window.md)。

- 針對進程，主要工具是 [ **附加至進程** ] 對話方塊、[ **進程** ] 視窗和 [ **偵錯工具位置** ] 工具列。

Visual Studio 也提供功能強大的中斷點和追蹤點，當您在調試多執行緒應用程式時，這會很有用。 使用中斷點條件和篩選器，將中斷點放置在個別執行緒上。 追蹤點可讓您在不中斷的情況下追蹤程式的執行，以研究鎖死之類的問題。 如需詳細資訊，請參閱 [中斷點動作和追蹤點](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)。

偵錯具有使用者介面的多執行緒應用程式可能會特別地困難。 您可以考慮在第二部電腦上執行應用程式，以及使用遠端偵錯程式。 如需詳細資訊，請參閱 [遠端偵錯](../debugger/remote-debugging.md)程式。

## <a name="articles-about-debugging-multithreaded-apps"></a>有關多執行緒應用程式的偵錯工具文章

 [開始對多執行緒應用程式進行偵錯工具](../debugger/get-started-debugging-multithreaded-apps.md)

執行緒偵錯工具功能的導覽，強調 [ **平行堆疊** ] 視窗和 [ **平行監看** 式] 視窗中的功能。

 [用於偵測執行緒和進程的工具](../debugger/debug-threads-and-processes.md)

列出用來偵測執行緒和進程之工具的功能。

 [對多重處理序進行偵錯](../debugger/debug-multiple-processes.md)

說明如何偵錯多重處理序

 [逐步解說：使用執行緒視窗進行 Debug](../debugger/how-to-use-the-threads-window.md)。

說明如何使用 [ **執行緒** ] 視窗和 [偵錯工具 **位置** ] 工具列的逐步解說。

 [逐步解說：對平行應用程式進行偵錯](../debugger/walkthrough-debugging-a-parallel-application.md)

說明如何使用 [ **平行堆疊** **] 和 [** 工作] 視窗的逐步解說。

 [如何：在偵錯時切換到另一個執行緒](../debugger/how-to-switch-to-another-thread-while-debugging.md)

有數種方式可將調試內容切換至另一個執行緒。

 [如何：將執行緒加上旗標和取消旗標](../debugger/how-to-flag-and-unflag-threads.md)

將您要在偵錯時特別注意的執行緒加上標記或旗標。

 [如何：在高效能叢集上進行調試](../debugger/how-to-debug-on-a-high-performance-cluster.md)

偵錯在高效能叢集上執行的應用程式的相關技巧。

 [在機器碼中對執行緒進行偵錯的祕訣](../debugger/tips-for-debugging-threads-in-native-code.md)

在偵錯原生執行緒時非常好用的簡單技巧。

 [如何：在機器碼中設定執行緒名稱](../debugger/how-to-set-a-thread-name-in-native-code.md)

為執行緒命名以方便在 [執行緒] 視窗中檢視。

 [如何：在 Managed 程式碼中設定執行緒名稱](../debugger/how-to-set-a-thread-name-in-managed-code.md)

為執行緒命名以方便在 [執行緒] 視窗中檢視。

## <a name="see-also"></a>請參閱

- [使用中斷點](../debugger/using-breakpoints.md)
- [執行緒](/dotnet/standard/threading/index)
- [元件中的多執行緒](/previous-versions/3es4b6yy(v=vs.140))
- [舊版程式碼的多執行緒支援](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)
- [對執行緒和處理序進行偵錯](../debugger/debug-threads-and-processes.md)
- [遠端偵錯](../debugger/remote-debugging.md)