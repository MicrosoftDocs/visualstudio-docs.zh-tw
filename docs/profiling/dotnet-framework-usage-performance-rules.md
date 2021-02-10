---
title: .NET Framework 使用效能規則 | Microsoft Docs
description: 瞭解 .NET Framework 使用方式類別中的效能規則。 識別可優化的特定方法，並識別更多一般使用模式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ab573755-6370-48aa-853d-a7321c424c79
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f8ec2756353ac56b3b5d44e2a50c4d4f5b1c7ebf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955381"
---
# <a name="net-framework-usage-performance-rules"></a>.NET Framework 使用效能規則
.Net Framework 使用類別中的效能規則會識別可最佳化的特定方法，也會識別較一般的使用模式 (例如記憶體回收和鎖定爭用)，以用於效能問題調查。

|規則|Description|
|-|-|
|[DA0001：使用 StringBuilder 進行串連](../profiling/da0001-use-stringbuilder-for-concatenations.md)|呼叫 <xref:System.String.Concat(System.String,System.String)?displayProperty=fullName> 佔分析資料的絕大部分。 請考慮使用 <xref:System.Text.StringBuilder> 類別，從多個區段建構字串。|
|[DA0005：常見的 GC2 集合](../profiling/da0005-frequent-gc2-collections.md)|數量相對高的 .NET 記憶體物件正在層代 2 記憶體回收中收回。 如果有太多短期物件存留在層代 1 回收中，記憶體管理的成本很容易變得過高。|
|[DA0006：覆寫實值型別的 Equals()](../profiling/da0006-override-equals-parens-for-value-types.md)|呼叫 `Equals` 方法或公用實值型別的等號比較運算子，是程式碼剖析資料的重要部分。 請考慮實作更有效率的方法。|
|[DA0007：避免使用例外狀況進行控制流程](../profiling/da0007-avoid-using-exceptions-for-control-flow.md)|在分析資料中呼叫高比率的 .NET Framework 例外處理常式。 請考慮使用其他控制流程邏輯，以減少擲回的例外狀況數量。|
|[DA0010：GetHashCode 高度耗費資源](../profiling/da0010-expensive-gethashcode.md)|呼叫型別的 `GetHashCode` 方法是程式碼剖析資料的重要部分，或 `GetHashCode` 方法會配置記憶體。 降低方法的複雜性。|
|[DA0011：CompareTo 高度耗費資源](../profiling/da0011-expensive-compareto.md)|型別的 `CompareTo` 方法高度耗費資源，或方法會配置記憶體。 降低 `CompareTo`方法的複雜性。|
|[DA0012：大量的反射](../profiling/da0012-significant-amount-of-reflection.md)|呼叫 <xref:System.Reflection?displayProperty=fullName> 方法 (如 <xref:System.Reflection.IReflect.InvokeMember%2A> 和 <xref:System.Reflection.IReflect.GetMember%2A>) 或 Type 方法 (如 <xref:System.Type.InvokeMember%2A>) 佔分析資料的絕大部分。 可能的話，請考慮將這些方法取代為相依組件方法的早期繫結。|
|[DA0013：String.Split 或 String.Substring 的高用量](../profiling/da0013-high-usage-of-string-split-or-string-substring.md)|呼叫 <xref:System.String.Split%2A?displayProperty=fullName> 或 <xref:System.String.Substring%2A> 方法佔分析資料的絕大部分。 請考慮使用 <xref:System.String.IndexOf%2A> 或 <xref:System.String.IndexOfAny%2A>，如果您要測試字串中是否存在子字串。|
|[DA0018：執行 32 位元的應用程式時，處理序的記憶體限制會受到管理](../profiling/da0018-32-bit-application-running-at-process-managed-memory-limits.md)|程式碼剖析執行期間收集的系統資料指出，.NET Framework 記憶體堆積已接近 Managed 堆積在 32 位元處理序中可以到達的大小上限。 請考慮使用 .NET 記憶體分析方法再次進行分析，並最佳化應用程式使用的 Managed 資源。|
|[DA0021：高比率的 Gen 1 記憶體回收](../profiling/da0021-high-rate-of-gen-1-garbage-collections.md)|數量相對高的 .NET 記憶體物件正在層代 1 記憶體回收中收回。 如果有太多短期物件存留在層代 0 回收中，記憶體管理的成本很容易變得過高。|
|[DA0022：高比率的 Gen 2 記憶體回收](../profiling/da0022-high-rate-of-gen-2-garbage-collections.md)|數量高的 .NET 記憶體物件正在層代 2 記憶體回收中收回。 如果有太多短期物件存留在層代 1 回收中，記憶體管理的成本很容易變得過高。 鎖定爭用率超過規則 DA0005 的上限臨界值時，就會引發此規則。|
|[DA0023：高記憶體回收 CPU 時間](../profiling/da0023-high-gc-cpu-time.md)|程式碼剖析期間收集的系統效能資料指出，相較於應用程式總處理時間，花費在記憶體回收的時間量極高。|
|[DA0024：過度的垃圾收集 CPU 時間](../profiling/da0024-excessive-gc-cpu-time.md)|程式碼剖析期間收集的系統效能資料指出，相較於應用程式總處理時間，花費在記憶體回收的時間量過高。 當記憶體回收所花費的時間量超過規則 DA0023 的上限臨界值時，就會引發此規則。|
|[DA0038：高比率的鎖定爭用](../profiling/da0038-high-rate-of-lock-contentions.md)|分析資料收集的系統效能資料指出，應用程式執行期間發生極高的鎖定爭用率。 請考慮使用並行分析方法再次進行分析，以尋找爭用的原因。|
|[DA0039：極高比率的鎖定爭用](../profiling/da0039-very-high-rate-of-lock-contentions.md)|分析資料收集的系統效能資料指出，應用程式執行期間發生過高的鎖定爭用率。 請考慮使用並行分析方法再次進行分析，以尋找爭用的原因。 鎖定爭用率超過規則 DA0038 的上限臨界值時，就會引發此規則。|
