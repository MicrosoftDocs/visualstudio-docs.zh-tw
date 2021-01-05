---
title: 效能不良之多執行緒應用程式的常見模式
description: 瞭解 Visual Studio 平行存取視覺化檢視中所含效能不良之多執行緒應用程式的常見模式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.tools.gallery
helpviewer_keywords:
- Concurrency Visualizer, common patterns for poorly-behaved multithreaded applications
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36e14640da4d66134ca961607f66f6a355f6b9d9
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815785"
---
# <a name="common-patterns-for-poorly-behaved-multithreaded-applications"></a>行為錯誤之多執行緒應用程式的一般模式

「並行視覺化檢視」可協助開發人員以視覺化方式檢視多執行緒應用程式的行為。 此工具包含行為錯誤之多執行緒應用程式的一般模式陳列庫。 陳列庫包含許多透過工具顯示出，典型而可辨識的視覺模式，以及每個模式所代表的行為說明、該行為的可能結果，以及解決的最常見方法。

## <a name="lock-contention-and-serialized-execution"></a>鎖定爭用和序列化執行

![鎖定爭用導致序列化執行](../profiling/media/lockcontention_serialized.png "LockContention_Serialized")

有時候平行化應用程式即時有數個執行緒，而且電腦有足夠數量的邏輯核心數，還是會固定地循序執行。 第一個徵兆是多執行緒的效能不佳，甚至比序列實作還慢。 在 [執行緒檢視] 中，您不會看到多個執行緒以平行方式執行；相反地，無論何時您都只會看到一個執行緒在執行。 此時，如果您按一下執行緒中的同步處理區段，可以看到已封鎖執行緒 (封鎖的呼叫堆疊)，和移除封鎖狀態之執行緒 (解除封鎖的呼叫堆疊) 的呼叫堆疊。 此外，如果您要分析的處理序發生解除封鎖的呼叫堆疊，就會顯示執行緒就緒的連接器。 您可以從這裡開始瀏覽從封鎖到解除封鎖之呼叫堆疊的程式碼，調查更多序列化的原因。

如下圖所示，並行視覺化檢視也可以在 [CPU 使用率檢視] 中顯示出這個徵兆，檢視中雖然有多個執行緒，但是應用程式還是只使用一個邏輯核心。

如需詳細資訊，請參閱 MSDN Magazine 文章 [Thread Performance - Resource Contention Concurrency Profiling in Visual Studio 2010](/archive/msdn-magazine/2010/june/msdn-magazine-thread-performance-resource-contention-concurrency-profiling-in-visual-studio-2010) (執行緒效能 - Visual Studio 2010 中的資源爭用並行分析) 中的 "Start with the Problem" 一節。

![鎖定爭用](../profiling/media/lockcontention_2.png "LockContention_2")

## <a name="uneven-workload-distribution"></a>工作負載分佈不均

![並行視覺化中平行線程的工作負載圖形螢幕擷取畫面。 執行緒會在不同的時間結束，顯示階梯模式。](../profiling/media/unevenworkload_1.png)

當應用程式中數個平行執行緒之間出現不規則的工作分佈時，隨著每個執行緒完成其工作，便會顯示典型的階梯模式，如上圖所示。 並行視覺化檢視所顯示每個並行執行緒的開始時間通常非常接近。 不過，這些執行緒通常會以不規則的方式，而不是同時結束的方式結束。 此模式表示一組平行執行緒之間的工作分佈不規則，而這可能會導致效能降低。 這類問題的最佳方法是重新評估演算法如何在平行執行緒之間分割工作。

如下圖所示，並行視覺化檢視也可以在 [CPU 使用率檢視] 中逐步降低的 CPU 使用率顯示出此徵兆。

![並行視覺化程式中 CPU 使用率視圖的螢幕擷取畫面，其中顯示 CPU 使用率圖形結尾的階梯模式。](../profiling/media/unevenworkload_2.png)

## <a name="oversubscription"></a>過度訂閱

![並行視覺化中所有使用中線程的工作負載圖形螢幕擷取畫面。 圖例會顯示花費在執行和搶佔的時間量。](../profiling/media/oversubscription.png)

在過度訂閱的案例中，處理序中的作用中執行緒數目大於系統上可用的邏輯核心數目。 上圖顯示過度訂閱的結果，在所有作用中的執行緒中都有顯著的先佔級區。 此外，圖例顯示大部分的時間都花費在先佔 (在本例中為 84%)。 這可能表示處理序正要求系統執行比邏輯核心數還多的並行執行緒。 不過，這也可能表示系統上的其他處理序正使用認定為此處理序可用的資源。

當您評估此問題時，應該考慮下列事項：

- 整體系統可能過度訂閱。 考慮系統上的其他處理序可能先佔住了您的執行緒。 當您在執行緒檢視中暫停在先佔區段上方時，工具提示會識別執行緒和先佔執行緒的處理序。 此處理序不一定是您的處理序被先佔時整個期間執行的處理序，但提供對您的處理序造成先佔壓力的相關提示。

- 評估您的處理序如何判斷在此工作階段期間執行的適當執行緒數目。 如果您的處理序直接計算作用中的平行執行緒數目，請考慮修改該演算法，能夠更正確地計算系統上可用的邏輯核心數目。 如果您使用並行執行階段、工作平行程式庫或 PLINQ，這些程式庫會執行計算執行緒數目的工作。

## <a name="inefficient-io"></a>無效率 I/O

![無效率的 I&#47;O](../profiling/media/inefficient_io.png "Inefficient_IO")

過度使用或濫用 I/O 是應用程式缺乏效率的常見原因。 請參考上圖。 可見時間軸分析顯示 I/O 使用了 44% 的可見執行緒時間。 時間軸顯示大量 I/O，表示分析的應用程式經常會被 I/O 所阻塞。 若要查看 I/O 種類和阻塞程式位置的詳細資料，請放大有問題的區域、檢查可見時間軸分析，然後按一下特定的 I/O 區塊以查看目前的呼叫堆疊。

## <a name="lock-convoys"></a>鎖定護送

![鎖定群組](../profiling/media/lock_convoys.png "Lock_Convoys")

當應用程式以先到先服務的順序取得鎖定時，以及當鎖定的抵達速率高於取得速率時，就會發生鎖定護送。 這兩項條件的組合會導致鎖定的要求開始堵塞。 解決這個問題的一個方法是使用「不公平」的鎖定，或使用能提供第一個執行緒存取權以找出處於未鎖定狀態之鎖定的鎖定。 上圖顯示這個護送行為。 若要解決這個問題，請嘗試減少同步處理物件的爭用，並嘗試使用不公平的鎖定。

## <a name="see-also"></a>請參閱

[執行緒檢視](../profiling/threads-view-parallel-performance.md)