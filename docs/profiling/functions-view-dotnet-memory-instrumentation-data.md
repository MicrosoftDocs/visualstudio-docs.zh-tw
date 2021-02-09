---
title: 函式檢視 - .NET 記憶體檢測資料 | Microsoft Docs
description: 取得使用檢測方法所收集之 .NET 記憶體配置分析資料的函數視圖相關資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Functions view
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: a26ce757ade9428326e54d3c21050b7df8d9a620
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916572"
---
# <a name="functions-view---net-memory-instrumentation-data"></a>函式檢視 - .NET 記憶體檢測資料
使用檢測方法所收集之 .NET 記憶體配置分析資料的 [函式] 檢視，會列出已在執行分析期間配置記憶體的函式。 函式資料列會報告配置的大小和數量，以及函式的計時資料。

## <a name="general"></a>一般

|資料行|描述|
|------------|-----------------|
|**函數名稱**|函式的名稱。|
|**函數位址**|函式的位址。|
|**函式行號**|原始程式檔中這個函式的開頭行號。|
|**呼叫次數**|呼叫此函式的總次數。|
|**來源檔案**|包含此函式定義的原始程式檔。|
|**模組名稱**|包含該函式的模組名稱。|
|**模組路徑**|包含該函式的模組路徑。|
|**處理序識別碼**|分析執行的處理序 ID (PID)。|
|**進程名稱**|處理序的名稱。|
|**時間專有探查額外負荷**|檢測對此函式造成的時間額外負荷。 已經從所有專有時間減去探查額外負荷。|
|**時間內含探查額外負荷**|檢測對此函式及其子函式造成的時間額外負荷。 已經從所有內含時間減去探查額外負荷。|

## <a name="net-memory-values"></a>.NET 記憶體值
 函式的內含 .NET 記憶體值，表示函式及其子函式所建立物件的數目 (配置) 和大小 (位元組)。

 專有記憶體值表示由函式建立之物件的數量及大小，而不包含其子函式建立的物件。

|資料行|描述|
|------------|-----------------|
|**內含配置**|在此函式及此函式所呼叫函式中建立的物件總數。|
|**內含配置 %**|在分析執行配置的所有物件中，屬於此函式的內含配置百分比。|
|**專有配置**|當函式在函式主體中執行程式碼時所建立的物件總數。 此數量不包含此函式呼叫之函式建立的物件。|
|**專有配置 %**|在分析執行中建立的所有物件中，屬於此函式之專有配置的百分比。|
|**內含位元組**|在此函式及此函式所呼叫函式中配置的記憶體位元組數量。|
|**內含位元組 %**|在分析執行中配置的所有記憶體位元組中，屬於此函式的內含位元組百分比。|
|**專有位元組**|非由此函式所呼叫函式配置，而是由此函式配置的記憶體位元組數量。|
|**專有位元組 %**|在分析執行配置的所有記憶體位元組中，屬於此函式的專屬位元組百分比。|

## <a name="elapsed-inclusive-values"></a>功能內含耗用值
 功能內含耗用值表示函式在呼叫堆疊上的時間。 該時間包含在子函式中及呼叫作業系統所花費的時間，例如內容切換和輸入/輸出作業。

|資料行|描述|
|------------|-----------------|
|**功能內含耗用 (Elapsed Inclusive) 時間**|這個函式的所有呼叫的功能內含耗用 (Elapsed Inclusive) 時間總計。|
|**功能內含耗用 (Elapsed Inclusive) 時間 %**|在此函式的功能內含耗用時間內，花費在程式碼剖析執行的總功能內含耗用時間百分比。|
|**平均功能內含耗用 (Elapsed Inclusive) 時間**|呼叫這個函式的平功能內含耗用 (Elapsed Inclusive) 時間。|
|**最大功能內含耗用 (Elapsed Inclusive) 時間**|呼叫這個函式的最大功能內含耗用 (Elapsed Inclusive) 時間。|
|**最小功能內含耗用 (Elapsed Inclusive) 時間**|呼叫這個函式的最小功能內含耗用 (Elapsed Inclusive) 時間。|

## <a name="elapsed-exclusive-values"></a>功能專屬耗用值
 功能專屬耗用值表示函式直接在呼叫堆疊最上方執行的時間。 該時間包含呼叫作業系統所花費的時間，例如內容切換和輸入/輸出作業，但不包含在子函式中花費的時間。

|資料行|描述|
|------------|-----------------|
|**功能專屬耗用 (Elapsed Exclusive) 時間**|這個函式的所有呼叫的功能專屬耗用 (Elapsed Exclusive) 時間總計。|
|**功能專屬耗用 (Elapsed Exclusive) 時間 %**|在此函式的總功能專屬耗用時間內，花費在分析執行的總功能專屬耗用時間百分比。|
|**平均功能專屬耗用 (Elapsed Exclusive) 時間**|呼叫這個函式的平均功能專屬耗用 (Elapsed Exclusive) 時間。|
|**最大功能專屬耗用 (Elapsed Exclusive) 時間**|呼叫這個函式的最大功能專屬耗用 (Elapsed Exclusive) 時間。|
|**最小功能專屬耗用 (Elapsed Exclusive) 時間**|呼叫這個函式的最小功能專屬耗用 (Elapsed Exclusive) 時間。|

## <a name="application-inclusive-values"></a>應用程式內含值
 應用程式內含值表示函式在呼叫堆疊上的時間。 該時間不包含呼叫作業系統所花費的時間，例如內容切換和輸入/輸出作業，但包含在子函式中花費的時間。

|資料行|描述|
|------------|-----------------|
|**應用程式內含 (Application Inclusive) 時間**|這個函式所有呼叫的總應用程式內含 (Application Inclusive) 時間。|
|**應用程式內含 (Application Inclusive) 時間 %**|此函式的總應用程式內含時間內，花費在分析執行的總功能內含耗用時間百分比。|
|**平均應用程式內含 (Application Inclusive) 時間**|呼叫此函數的平均應用程式內含 (Application Inclusive) 時間。|
|**最大應用程式內含 (Application Inclusive) 時間**|呼叫此函式的最大應用程式內含 (Application Inclusive) 時間。|
|**最小應用程式內含 (Application Inclusive) 時間**|呼叫此函式的最小應用程式內含 (Application Inclusive) 時間。|

## <a name="application-exclusive-values"></a>應用程式專屬值
 應用程式專屬值表示函數直接在呼叫堆疊最上方執行的時間。 該時間不包含呼叫作業系統所花費的時間，例如內容切換和輸入/輸出作業，也不包含在子函式中花費的時間。

|資料行|描述|
|------------|-----------------|
|**應用程式專屬 (Application Exclusive) 時間**|這個函式所有呼叫的總應用程式專屬 (Application Inclusive) 時間。|
|**應用程式專屬 (Application Exclusive) 時間 %**|此函式的總應用程式專屬時間內，花費在分析執行的總功能專屬耗用時間百分比。|
|**平均應用程式專屬 (Application Exclusive) 時間**|呼叫此函式的平均應用程式專屬 (Application Exclusive) 時間。|
|**最大應用程式專屬 (Application Exclusive) 時間**|呼叫此函式的最大應用程式專屬 (Application Exclusive) 時間。|
|**最小應用程式專屬 (Application Exclusive) 時間**|呼叫此函式的最小應用程式專屬 (Application Exclusive) 時間。|

## <a name="see-also"></a>另請參閱
- [如何：自訂報表檢視資料行](../profiling/how-to-customize-report-view-columns.md)
- [函數視圖-取樣](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [函式檢視](../profiling/functions-view-instrumentation-data.md)
- [函式檢視](../profiling/functions-view-sampling-data.md)
