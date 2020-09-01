---
title: 可靠性警告
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db99a9628992c40ef65699fee72d65b891ed1e24
ms.sourcegitcommit: 26178b116cbf7353fee6ca989b8d872114f7b405
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2020
ms.locfileid: "89219604"
---
# <a name="reliability-warnings"></a>可靠性警告

可靠性警告支援程式庫和應用程式可靠性，例如正確的記憶體和執行緒的使用。 可靠性規則包括：

|規則|說明|
|----------|-----------------|
|[CA2000:必須在超出範圍前處置物件](../code-quality/ca2000.md)|因為可能會發生例外事件以防止執行物件的完成項，所以應在物件的所有參考都超出範圍之前，明確處置物件。|
|[CA2001:避免呼叫有問題的方法](../code-quality/ca2001.md)|成員呼叫了可能有危險或問題的方法。|
|[CA2002:不要鎖定具有弱式識別的物件](../code-quality/ca2002.md)|可以跨應用程式定義域範圍直接存取的物件，即所謂具有弱式識別的物件。 嘗試取得具有弱式識別之物件鎖定的執行緒，可以被不同應用程式定義域中具有相同物件鎖定的第二個執行緒所封鎖。|
|[CA2003:不要將 Fiber 視為執行緒](../code-quality/ca2003.md)|Managed 執行緒被視為 Win32 執行緒。|
|[CA2004:必須移除對 GC.KeepAlive 的呼叫](../code-quality/ca2004.md)|如果您要轉換成 SafeHandle 使用方式，請移除所有對 GC 的呼叫。KeepAlive (物件) 。 在此情況下，類別應該不需要呼叫 GC。KeepAlive，假設它們沒有完成項，但依賴 SafeHandle 來完成它們的作業系統控制碼。|
|[CA2006:必須使用 SafeHandle 封裝原生資源](../code-quality/ca2006.md)|在 Managed 程式碼中使用 IntPtr，可能會有潛在的安全性和可靠性問題。 必須檢閱所有使用 IntPtr 的情況，判斷是否需要在該處使用 SafeHandle (或類似技術)。|
|[CA2007:不直接等候工作](../code-quality/ca2007.md)|非同步方法會[awaits](/dotnet/csharp/language-reference/keywords/await)直接等候 <xref:System.Threading.Tasks.Task> 。|
|[CA2008：不要在不傳遞 TaskScheduler 的情況下建立工作](../code-quality/ca2008.md)|工作建立或接續運算使用未指定參數的方法多載 <xref:System.Threading.Tasks.TaskScheduler> 。|
|[CA2009：請勿對 ImmutableCollection 值呼叫 TolmmutableCollection](../code-quality/ca2009.md)|`ToImmutable` 方法在命名空間的不可變集合上不必要地呼叫 <xref:System.Collections.Immutable> 。|
|[CA2011：請勿在屬性 setter 中指派屬性](../code-quality/ca2011.md) | 屬性在其本身的 [set 存取](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor)子中不小心指派了值。 |
|[CA2012：必須正確使用 ValueTasks](../code-quality/ca2012.md) | 從成員調用傳回的 ValueTasks 是要直接等待。  嘗試多次使用 ValueTask 或在已知完成之前直接存取一個結果可能會導致例外狀況或損毀。  忽略這類 ValueTask 可能表示功能錯誤，而且可能會降低效能。 |
|[CA2013：請勿使用具有值類型的 ReferenceEquals](../code-quality/ca2013.md) | 使用比較值時 <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> ，如果 objA 和 objB 是實值型別，則會在傳遞至方法之前先將它們裝箱 <xref:System.Object.ReferenceEquals%2A> 。 這表示即使 objA 和 objB 都代表實值型別的實例，方法仍會傳回 <xref:System.Object.ReferenceEquals%2A> false。 |
|[CA2014：不要在迴圈中使用 stackalloc。](../code-quality/ca2014.md) | Stackalloc 配置的堆疊空間只會在目前方法的調用結束時釋出。  在迴圈中使用它，可能會導致未系結的堆疊成長和最終的堆疊溢位狀況。 |
|[CA2015：請勿定義衍生自 MemoryManager T 之類型的完成項 &lt;&gt;](../code-quality/ca2015.md) | 將完成項加入至衍生自的型別 <xref:System.Buffers.MemoryManager%601> 時，可能會允許在記憶體仍在使用時釋放記憶體 <xref:System.Span%601> 。 |
|[CA2016：將 CancellationToken 參數傳遞給使用該參數的方法](ca2016.md) | 將 `CancellationToken` 參數轉寄至採用其中一個的方法，以確保作業取消通知會正確傳播，或明確地傳入 `CancellationToken.None` 以表示刻意不傳播權杖。 |
