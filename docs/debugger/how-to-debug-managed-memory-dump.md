---
title: 使用 .NET 診斷分析器來對 managed 記憶體傾印進行 Debug |Microsoft Docs
description: 瞭解如何使用 Visual Studio 的 .NET 診斷分析器來分析受控記憶體傾印
ms.custom: SEO-VS-2021
ms.date: 04/21/2021
ms.topic: how-to
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- analyzers
- dump debugging
- debugging managed memory dump
- debugging [Visual Studio]
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 083095ad534aa6b9131ba103178313cb1cdc4b7c
ms.sourcegitcommit: 925db7adb9cb554b081c7e727d09680d4863feed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2021
ms.locfileid: "107952891"
---
# <a name="how-to-debug-a-managed-memory-dump-with-net-diagnostic-analyzers"></a>如何使用 .NET 診斷分析器來對 managed 記憶體傾印進行偵錯工具



在本教學課程中，您將：

> [!div class="checklist"]
> * 開啟記憶體傾印
> * 針對傾印選取並執行分析器
> * 檢查分析器的結果
> * 流覽至有問題的程式碼


在本文所述的範例中，問題是您的應用程式不會及時回應要求。 


## <a name="opening-a-memory-dump-in-visual-studio"></a>在 Visual Studio 中開啟記憶體傾印

1. 在 Visual Studio 中開啟記憶體傾印，方法是使用 [檔案] **> 開啟 >** 檔案] 功能表命令，然後選取您的記憶體傾印。

1. 請注意，在記憶體傾印摘要頁面上，有一個稱為「**執行診斷分析**」的新 **動作**。

   ![動作-診斷分析](../debugger/media/diagnostic-analyzer-dump-summary-actions.png)

1. 選取此動作以啟動偵錯工具，並開啟新的 **診斷分析** 頁面，其中包含可用分析器選項的清單，並依基礎徵兆進行整理。


## <a name="select-and-execute-analyzers-against-the-dump"></a>針對傾印選取並執行分析器

若要調查這些徵兆，最佳選項可在 **處理常式回應** 性下使用，因為它最符合此範例中的問題。

   ![選取診斷分析器](../debugger/media/diagnostic-analyzer-diagnostics-analysis-window.png)

1. 按一下 [ **分析** ] 按鈕以開始調查流程 

1. 分析器會根據記憶體傾印中所捕捉的進程資訊和 CLR 資料的組合來呈現結果。
 
## <a name="review-the-results-of-the-analyzers"></a>檢查分析器的結果

1. 在此情況下，分析器發現兩個錯誤。 選取分析器結果以查看 **分析摘要** 和建議的 **補救**。

   ![診斷分析器結果](../debugger/media/diagnostic-analyzer-diagnostics-analysis-results.png)

1. **分析摘要** 指出「CLR 執行緒集區遇到過了」。 這項資訊會建議 CLR 目前已使用所有可用的執行緒集區執行緒，這表示在釋放執行緒之前，您的服務無法回應任何新的要求。

    > [!NOTE] 
    > 這種情況下的 **補救** 方式是「不同步等候監視、事件、工作或可能封鎖您的執行緒的任何其他物件。 請看看您是否可以將方法更新為非同步。」。

## <a name="navigating-to-the-problematic-code"></a>流覽至有問題的程式碼

我的下一項工作是找出有問題的程式碼。

1. 按一下 [ **顯示呼叫堆疊** ] 連結 Visual Studio 將會立即切換至出現這種行為的執行緒。

1. [ **呼叫堆疊** ] 視窗會顯示可能會在程式碼 (SyncOverAsyncExmple 之間快速區分的方法。*從 Framework 程式碼 (系統) 。*) 。

   ![診斷分析器連結至呼叫堆疊](../debugger/media/diagnostic-analyzer-call-stack.png)

1. 每個呼叫堆疊框架都會對應到一個方法，然後按兩下堆疊框架 Visual Studio 會流覽至在此執行緒上直接導向此案例的程式碼。

1. 在此範例中，沒有符號或程式碼，但是在 [ **未載入符號** ] 頁面上，您可以選取 [ **[反編譯原始程式碼](../debugger/decompilation.md)** ] 選項。

   ![反向組譯](../debugger/media/diagnostic-analyzer-decompilation.png)

1. 在下方的反向組譯來源中， (ConsumeThreadPoolThread) 的非同步工作很明顯地呼叫同步封鎖函式。

    > [!NOTE]  
    > 包含 WaitHandle WaitOne 方法的 ">dosomething () " 方法，它會封鎖目前的執行緒集區執行緒，直到收到信號為止。

   若要改善應用程式的回應性，請務必移除所有非同步內容中的封鎖同步程式碼。

   ![分析反向組譯程式碼](../debugger/media/diagnostic-analyzer-decompiled-code.png)


## <a name="see-also"></a>另請參閱

* [在偵錯工具中使用傾印檔案](../debugger/using-dump-files.md)
* [在偵錯工具時，從 .NET 元件產生原始程式碼](../debugger/decompilation.md)
* [指定符號 ( .pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
