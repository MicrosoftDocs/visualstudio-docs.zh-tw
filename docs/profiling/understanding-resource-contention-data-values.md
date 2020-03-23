---
title: 了解資源爭用資料值 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3f522d1854cae86d9dc6e757ef0c9a62f4511800
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779983"
---
# <a name="understand-resource-contention-data-values"></a>了解資源爭用資料值

資源爭用分析會在每次強迫應用程式中的競爭執行緒等候共用資源的存取權時，收集詳細的呼叫堆疊資訊。

資源爭用報表可顯示爭用總數，以及等候資源以用於發生等候的模組、函式、原始碼程式行及指示所花費的總時間。

- 內含值會顯示因資源爭用而強制函式等候爭用總數，以及該函式的總等候時間。  內含值中會包含由該函式所呼叫子函式造成的爭用情況。

- 專有值只顯示強制函式等候和由函式主體中的程式碼所造成的爭用數目。 不包括由子函式造成的爭用情況。 函式的專有時間也只包括函式主體中陳述式所造成的等候時間。

資源爭用報表檢視也會包含一個時間軸圖形，顯示一段時間內的個別爭用事件，以及顯示建立特定事件的呼叫堆疊。 如需詳細資訊，請參閱下列其中一個主題：

- [執行緒詳細資訊視圖](../profiling/thread-details-view-contention-data.md)

- [資源詳細資訊視圖](../profiling/resource-details-view-contention-data.md)

如需並行程式碼剖析第二個模式的詳細資訊，請參閱[並行視覺化檢視](../profiling/concurrency-visualizer.md)。
