---
title: 執行時間 (執行緒檢視) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac0cf2a60fd194176b7cd9091f4e7dc7a758006f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62969910"
---
# <a name="execution-time-threads-view"></a>執行時間 (執行緒檢視)
當執行緒在系統的邏輯核心上主動執行工作時，[執行緒檢視] 時間表中的這些區段代表執行時間。

 執行緒狀態的變更是透過核心環境參數事件來偵測。 Windows 事件追蹤 (ETW) 每毫秒會擷取一次樣本堆疊。 在非常短的綠色區段中，則可能沒有取樣。 因此，一些簡短的執行區段可能不會顯示任何呼叫堆疊。

 當您按一下執行區段時，並行視覺化檢視會顯示最接近點擊位置的範例堆疊。 該樣本堆疊的位置會顯示為時間表上方的黑色箭號或插入號，樣本堆疊則出現在 [目前]**** 索引標籤中。

 若要在目前檢視中查看所有執行區段的傳統取樣分析，請在 [可見時間表分析] 中按一下 [執行]****。

## <a name="see-also"></a>另請參閱
- [執行分析報表](../profiling/execution-profile-report.md)
- [執行緒檢視](../profiling/threads-view-parallel-performance.md)