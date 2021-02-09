---
title: DA0017-高比率的使用中記憶體分頁到磁片 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.17
- vs.performance.rules.DA0017
- vs.performance.DA0017
ms.assetid: 01011eec-5930-43b3-980d-2cb01e2ca7f6
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5f66db4c727be1377b41da381b75609af6478c10
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916770"
---
# <a name="da0017-high-rates-of-paging-active-memory-to-disk"></a>DA0017：高比率的使用中記憶體分頁到磁碟

|Item|值|
|-|-|
|規則 ID|DA0017|
|類別|記憶體和分頁|
|程式碼剖析方法|全部|
|訊息|發生高比率的使用中記憶體分頁到磁碟。 您的應用程式可能是記憶體繫結。|
|規則型別|資訊|

 當您使用取樣、.NET 記憶體或資源爭用方法進行分析時，必須至少收集 10 個樣本才能觸發此規則。

## <a name="cause"></a>原因
 在分析執行中收集的系統效能資料表示在整個分析執行期間發生高比率的使用中記憶體分頁進出磁碟。 此程度的分頁比率通常會影響應用程式效能和回應性。 請考慮修改演算法減少記憶體配置。 您也必須考慮應用程式的記憶體需求。

## <a name="rule-description"></a>規則描述

> [!NOTE]
> 當使用中記憶體的分頁程度達到很高的量時，就會引發這個資訊性規則。 在發生極高的分頁程度時，則會引發警告規則 [DA0014︰極高比率的使用中記憶體分頁到磁碟](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)。

 過度分頁至磁碟可能是因為實體記憶體不足。 如果分頁作業控制使用分頁檔案所在的實體磁碟，則可能降低相同磁碟上其他應用程式導向之磁碟作業的速度。

 分頁經常以大量分頁作業從磁碟讀取或寫入磁碟。 例如，Pages Output/sec 數經常遠比 Page Writes/sec 數還大。 因為 Pages Output/sec 還包含系統檔案快取的變更資料頁。 不過，不一定可以輕鬆地判斷哪些處理序直接負責分頁或原因。

## <a name="how-to-fix-violations"></a>如何修正違規
 按兩下 [錯誤清單] 視窗中的訊息，流覽至 [ [標記](../profiling/marks-view.md) ] view。 尋找 **Memory\Pages/sec** 欄。 判斷是否有特定的程式執行階段，當中的分頁 IO 活動比其他階段更繁重。

 如果您在負載測試情節中收集 ASP.NET 應用程式的分析資料，請嘗試在設定額外實體記憶體 (或 RAM) 的機器上再次執行負載測試。

 請考慮修改演算法減少記憶體配置，以及避免需要大量記憶體的 API，例如 String.Concat 和 String.Substring。
