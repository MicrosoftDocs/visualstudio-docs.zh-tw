---
title: DA0022-高比率的 Gen 2 垃圾收集 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0022
- vs.performance.rules.DA0022
- vs.performance.22
ms.assetid: f871a547-0e6f-4b11-b2d7-174d30fc2ed8
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 61fb953b1eae3ecfb0aa9c87e8b10a25099cb12a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967003"
---
# <a name="da0022-high-rate-of-gen-2-garbage-collections"></a>DA0022：高比率的 Gen 2 記憶體回收

|Item|值|
|-|-|
|規則 ID|DA0022|
|類別|.NET Framework 使用方式|
|程式碼剖析方法|全部|
|訊息|發生相當高比率的 Gen 2 記憶體回收。 如果您設計讓大部分程式的資料結構配置並持續一段很長的時間，這通常不是問題。 不過，如果這不是預期的行為，您的應用程式可能正鎖定物件。 如果您不確定，可以收集 .NET 記憶體配置資料和物件存留期資訊，了解應用程式所使用之記憶體配置的模式。|
|規則型別|警告|

 當您使用取樣、.NET 記憶體或資源爭用方法進行分析時，必須至少收集 10 個樣本才能觸發此規則。

## <a name="cause"></a>原因
 分析期間所收集的系統效能資料表示，相較於第 0 代和第 1 代的記憶體回收，大部分 .NET Framework 物件的記憶體是在記憶體回收的第 2 代回收。

## <a name="rule-description"></a>規則描述
 Microsoft .NET 通用語言執行平台 (CLR) 提供一種自動的記憶體管理機制，此機制使用一種記憶體回收行程回收應用程式不再使用之物件的記憶體。 記憶體回收行程假設許多配置的存留期都很短，因此是層代導向。 例如區域變數的存留期應該很短。 新建立的物件從第 0 代 (gen 0) 開始，然後在記憶體回收執行中留存時進展到第 1 代，如果應用程式一直使用這些物件，最後就會轉換到第 2 代。

 第 0 代中的物件通常會以頻繁且非常有效率的方式回收。 第 1 代中的物件則不會以太頻繁也不會太有效率的方式回收。 最後，在第 2 代中長時間執行的物件則不會太常回收。 第 2 代回收，是執行完整的記憶體回收，也是最耗費資源的作業。

 發生太高比例的第 2 代記憶體回收時，就會引發此規則。 正常運作的 .NET Framework 應用程式的第 1 代記憶體回收，會是第 2 代回收的 5 倍以上。 (10x 倍也可能很理想)。

## <a name="how-to-investigate-a-warning"></a>如何調查警告
 按兩下 [錯誤清單] 視窗中的訊息，瀏覽至分析資料的[標記檢視](../profiling/marks-view.md)。 尋找 **.NET CLR Memory\\# of Gen 0 Collections** 和 **.NET CLR Memory\\# of Gen 1 Collections** 欄。 判斷是否有特定的程式執行階段，當中的記憶體回收較頻繁發生。 比較這些值與 **% Time in GC** 欄，查看 Managed 記憶體配置的模式是否會造成過多的記憶體管理負擔。

 高比例的第 2 代記憶體回收並不一定是問題。 這可能是刻意的設計。 配置大型資料結構的應用程式如果在執行期間必須保持長時間作用中，就可能會觸發此規則。 當這類應用程式有記憶體不足的壓力時，可能會強制執行頻繁的記憶體回收。 如果成本較低的第 0 代和第 1 代記憶體回收都只能回收少量 Managed 記憶體，系統則會安排更頻繁的第 2 代記憶體回收。

 在 [標記檢視] 中有額外的 .NET CLR Memory 欄，可協助您找出記憶體回收問題。 **% Time in GC** 欄可協助您了解發生多少記憶體管理負擔。 如果您的應用程式通常使用非常少量大型但持久的物件，則頻繁的第 2 代回收應該不會耗用過多的 CPU 時間。 如果應用程式因為需要更多實體記憶體 (RAM) 而有記憶體不足的壓力，則也可能會引發評估 **Memory\Pages/sec** 欄值的相關規則。

 若要了解應用程式之 Managed 記憶體使用方式的模式，請執行 .NET 記憶體配置設定檔再次進行分析，並選取「物件存留期」分析選項。

 如需如何改善記憶體回收效能的詳細資訊，請參閱 Microsoft 網站上的[記憶體回收行程的基礎概念和效能提示 (英文)](/previous-versions/dotnet/articles/ms973837(v=msdn.10))。 如需有關自動記憶體回收之額外負荷的詳細資訊，請參閱[大型物件堆積的面目 (英文)](/archive/msdn-magazine/2008/june/clr-inside-out-large-object-heap-uncovered)。