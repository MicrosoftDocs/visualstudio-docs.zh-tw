---
title: 比較效能資料檔案 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, comparing profiling tools report files
- profiling tools reports, comparing
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 64842c5b4f622a1f76aa528360f79403ec92cb42
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777851"
---
# <a name="compare-performance-data-files"></a>比較效能資料檔案

分析工具資料檔案比較功能可讓您選取兩個報表檔案 (.*vsp* 或 .*vsps*) 檔案，然後產生報告以顯示一個分析工作階段到另一個之間發生的差異、效能回復和改善。

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 分析工具的資料檔案比較報表會比較一個分析資料檔案的分析結果和另一個資料檔案的基準分析結果。 必須使用相同的分析方法產生這兩個資料檔案。 分析的比較報表會儲存成 .*vsps* 檔。

比較報表檢視會以表格檢視的方式呈現變更資料。 表格會呈現相對於基準的差異或變更。 差異是透過判斷舊值、基準值和新分析中的結果值之間的差異計算而來。

分析工具資料的比較可以根據程式碼中的函式、應用程式中的模組、程式行、指令指標 (IP) 及型別。

適合比較的分析資料包括資料行中顯示的資訊。 如需這些資料行名稱的定義，請參閱[效能報告檢視](../profiling/performance-report-views.md)。

設定臨界值可減少雜訊，並以指定的數量篩選掉資料列的比較表格檢視中未變更的資料。

## <a name="in-this-section"></a>本節內容

[操作說明：比較效能資料檔案](../profiling/how-to-compare-performance-data-files.md)
