---
title: 可靠性規則
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- rules, reliability
- reliability rules
- managed code analysis rules, reliability rules
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0a35b9c49f2eb5655eeb67721b0fafdbbe1e087
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808268"
---
# <a name="reliability-rules"></a>可靠性規則

可靠性規則支援程式庫和應用程式的可靠性，例如正確的記憶體和執行緒的使用。

|規則|描述|
|----------|-----------------|
|[CA2000:必須在超出範圍前處置物件](../code-quality/ca2000.md)|因為可能會發生例外事件以防止執行物件的完成項，所以應在物件的所有參考都超出範圍之前，明確處置物件。|
|[CA2002:不要鎖定具有弱式識別的物件](../code-quality/ca2002.md)|可以跨應用程式定義域範圍直接存取的物件，即所謂具有弱式識別的物件。 嘗試取得具有弱式識別之物件鎖定的執行緒，可以被不同應用程式定義域中具有相同物件鎖定的第二個執行緒所封鎖。|
|[CA2007:不直接等候工作](../code-quality/ca2007.md)|非同步方法會[awaits](/dotnet/csharp/language-reference/keywords/await)直接等候 <xref:System.Threading.Tasks.Task> 。|
|[CA2008：建立工作時請務必傳遞 TaskScheduler](../code-quality/ca2008.md)|工作建立或接續運算使用未指定參數的方法多載 <xref:System.Threading.Tasks.TaskScheduler> 。|
|[CA2009：請勿對 ImmutableCollection 值呼叫 TolmmutableCollection](../code-quality/ca2009.md)|`ToImmutable` 方法在命名空間的不可變集合上不必要地呼叫 <xref:System.Collections.Immutable> 。|
|[CA2011：請勿在屬性 setter 中指派屬性](../code-quality/ca2011.md) | 屬性在其本身的 [set 存取](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor)子中不小心指派了值。 |
|[CA2012：必須正確使用 ValueTasks](../code-quality/ca2012.md) | 從成員調用傳回的 ValueTasks 是要直接等待。  嘗試多次使用 ValueTask 或在已知完成之前直接存取一個結果可能會導致例外狀況或損毀。  忽略這類 ValueTask 可能表示功能錯誤，而且可能會降低效能。 |
|[CA2013：請勿使用具有值類型的 ReferenceEquals](../code-quality/ca2013.md) | 使用比較值時 <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> ，如果 objA 和 objB 是實值型別，則會在傳遞至方法之前先將它們裝箱 <xref:System.Object.ReferenceEquals%2A> 。 這表示即使 objA 和 objB 都代表實值型別的實例，方法仍會傳回 <xref:System.Object.ReferenceEquals%2A> false。 |
|[CA2014：不要在迴圈中使用 stackalloc。](../code-quality/ca2014.md) | Stackalloc 配置的堆疊空間只會在目前方法的調用結束時釋出。  在迴圈中使用它，可能會導致未系結的堆疊成長和最終的堆疊溢位狀況。 |
|[CA2015：請勿定義衍生自 MemoryManager T 之類型的完成項 &lt;&gt;](../code-quality/ca2015.md) | 將完成項加入至衍生自的型別 <xref:System.Buffers.MemoryManager%601> 時，可能會允許在記憶體仍在使用時釋放記憶體 <xref:System.Span%601> 。 |
|[CA2016：將 CancellationToken 參數傳遞給使用該參數的方法](ca2016.md) | 將 `CancellationToken` 參數轉寄至採用其中一個的方法，以確保作業取消通知會正確傳播，或明確地傳入 `CancellationToken.None` 以表示刻意不傳播權杖。 |
