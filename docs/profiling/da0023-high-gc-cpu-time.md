---
title: DA0023-高 GC CPU 時間 |Microsoft 檔
description: 程式碼剖析期間收集的系統效能資料指出，相較於應用程式總處理時間，花費在記憶體回收的時間量極高。
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0023
- vs.performance.23
- vs.performance.rules.DA0023
ms.assetid: aba875fe-9cbc-418d-a2c4-6eb47519a5bb
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: eccf44528b18d43a97a5a9c202c72b59abbdf431
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466073"
---
# <a name="da0023-high-gc-cpu-time"></a>DA0023：高記憶體回收 CPU 時間

|Item|值|
|-|-|
|規則 ID|DA0023|
|類別|.NET Framework 使用方式|
|程式碼剖析方法|全部|
|訊息|% Time in GC 相當高。 這表示過多的記憶體回收負擔可能會影響應用程式的回應性。 您可以收集 .NET 記憶體配置資料和物件存留期資訊，更了解應用程式所使用之記憶體配置的模式。|
|規則型別|資訊|

 當您使用取樣、.NET 記憶體或資源爭用方法進行分析時，必須至少收集 10 個樣本才能觸發此規則。

## <a name="cause"></a>原因
 程式碼剖析期間收集的系統效能資料指出，相較於應用程式總處理時間，花費在記憶體回收的時間量極高。

## <a name="rule-description"></a>規則描述
 Microsoft .NET 通用語言執行平台 (CLR) 提供一種自動的記憶體管理機制，此機制使用一種記憶體回收行程回收應用程式不再使用之物件的記憶體。 記憶體回收行程假設許多配置的存留期都很短，因此是層代導向。 例如區域變數的存留期應該很短。 新建立的物件從第 0 代 (gen 0) 開始，然後在記憶體回收執行中留存時進展到第 1 代，如果應用程式一直使用這些物件，最後就會轉換到第 2 代。

 第 0 代中的物件會以頻繁且有效率的方式回收。 第 1 代中的物件則不會以太頻繁也不會太有效率的方式回收。 最後，在第 2 代中長時間執行的物件則不會太常回收。 第 2 代回收，是執行完整的記憶體回收，也是最耗費資源的作業。

 相較於應用程式總處理時間，當花費在記憶體回收的時間量極高時，就會引發此規則。

> [!NOTE]
> 相較於應用程式總處理時間，當有過高比例的時間花費在記憶體回收時，則會引發 [DA0024︰過多 GC CPU 時間](../profiling/da0024-excessive-gc-cpu-time.md)警告而不是此規則。

## <a name="how-to-investigate-a-warning"></a>如何調查警告
 按兩下 [錯誤清單] 視窗中的訊息，瀏覽至分析資料的[標記檢視](../profiling/marks-view.md)。 尋找 **.NET CLR Memory\\% Time in GC** 欄。 判斷是否有特定的程式執行階段，當中的 Managed 記憶體回收負荷比其他階段還繁重。 比較 % Time in GC 的值與在 **# of Gen 0 Collections**、**# of Gen 1 Collections**、**# of Gen 2 Collections** 值中報告的記憶體回收速率。

 % Time in GC 值會嘗試報告應用程式花費在執行記憶體回收的時間量與處理總量成比例的時間。 請注意，有時候 % Time in GC 值可能會報告很高的值，但不是因為有過多記憶體回收。 如需有關 [% Time in GC] 值的計算方式的詳細資訊，請參閱 MSDN 上的 **Maoni 的**[不同工具所報告的效能資料之間的差異-4](https://devblogs.microsoft.com/maoni/archive/difference-between-perf-data-reported-by-different-tools-4.aspx)專案。 如果發生分頁錯誤或應用程式在記憶體回收期間由電腦上其他較高優先順序的工作優先佔用，% Time in GC 計數器會反映這些額外的延遲。
