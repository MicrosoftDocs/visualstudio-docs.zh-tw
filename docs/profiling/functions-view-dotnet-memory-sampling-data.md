---
title: 函式檢視 - .NET 記憶體取樣資料 | Microsoft Docs
description: 取得使用取樣方法所收集之 .NET 記憶體配置分析資料的函數視圖相關資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 2c0bfd4c3355e6e4371fbec443ee38d7ba6e1da7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907331"
---
# <a name="functions-view---net-memory-sampling-data"></a>函式檢視 - .NET 記憶體取樣資料
使用取樣方法所收集之 .NET 記憶體配置分析資料的 [函式] 檢視，會列出已在分析回合期間配置記憶體的函式，並報告配置大小和數目。

|資料行|描述|
|------------|-----------------|
|**處理序識別碼**|分析執行的處理序 ID (PID)。|
|**進程名稱**|處理序的名稱。|
|**模組名稱**|包含該函式的模組名稱。|
|**模組路徑**|包含該函式的模組路徑。|
|**來源檔案**|含有這個函式定義的原始程式檔。|
|**函數名稱**|函式的完整格式名稱。|
|**函式行號**|原始程式檔中這個函式的開頭行號。|
|**函數位址**|函式的位址。|
|**內含配置**|此函式和其子函式中所配置的物件總數。|
|**內含配置 %**|在分析執行配置的所有物件中，屬於此函式的內含配置百分比。|
|**專有配置**|函式直接在呼叫堆疊最上方執行時所建立的物件數目。 此數目未包含子函式中所建立的物件。|
|**專有配置 %**|分析回合中配置的所有物件中，屬於此函式之專有配置的百分比。|
|**內含位元組**|此函式和其子函式所配置的記憶體位元組數目。|
|**內含位元組 %**|在分析執行中配置的所有記憶體位元組中，屬於此函式的內含位元組百分比。|
|**專有位元組**|此函式但非其子函式所配置的記憶體位元組數目。|
|**專有位元組 %**|在分析執行配置的所有記憶體位元組中，屬於此函式的專屬位元組百分比。|

## <a name="see-also"></a>另請參閱
- [函數視圖-檢測](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [函式檢視](../profiling/functions-view-sampling-data.md)
- [函式檢視](../profiling/functions-view-instrumentation-data.md)
