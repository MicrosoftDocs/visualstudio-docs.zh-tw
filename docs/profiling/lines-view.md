---
title: 程式行檢視 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 25dbb0beb600f7f043ae006e09ac48b9b64d613b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "74773977"
---
# <a name="lines-view"></a>程式行檢視
[程式行] 檢視僅適用於使用取樣方法收集的分析工具資料。 此檢視不適用於使用檢測收集的資料。

 對於取樣程式碼剖析資料，[程式行] 檢視會識別收集取樣時直接執行之函式中的陳述式。 對於 .NET 記憶體資料，[程式行] 檢視會識別用於配置記憶體的陳述式。

 在任一原始程式檔中，任一陳述式在該原始程式檔中可以長達多行，而單一一行程式行也可能包含一個以上的陳述式。

 陳述式是由下列項目識別：

- 包含此函式陳述式的原始程式檔。

- 包含此陳述式的函式。

- 此陳述式在原始程式檔中開始的行位置。

- 此陳述式在原始程式檔中開始的字元。

- 此陳述式在原始程式檔中結束的行位置。

- 此陳述式在原始程式檔中結束的字元。

## <a name="see-also"></a>另請參閱
- [程式行檢視](../profiling/lines-view-sampling-data.md)
- [線條視圖-取樣](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [程式行檢視](../profiling/lines-view-contention-data.md)
