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
ms.openlocfilehash: c4b888dbbe7a26e5ff333ec39aa0fdfcec90b429
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586207"
---
# <a name="reliability-warnings"></a>可靠性警告

可靠性警告支援程式庫和應用程式可靠性，例如正確的記憶體和執行緒使用方式。 可靠性規則包括：

|規則|描述|
|----------|-----------------|
|[CA2000:必須在超出範圍前處置物件](../code-quality/ca2000.md)|因為可能會發生例外事件以防止執行物件的完成項，所以應在物件的所有參考都超出範圍之前，明確處置物件。|
|[CA2001:避免呼叫有問題的方法](../code-quality/ca2001.md)|成員呼叫了可能有危險或問題的方法。|
|[CA2002:不要鎖定具有弱式識別的物件](../code-quality/ca2002.md)|可以跨應用程式定義域範圍直接存取的物件，即所謂具有弱式識別的物件。 嘗試取得具有弱式識別之物件鎖定的執行緒，可以被不同應用程式定義域中具有相同物件鎖定的第二個執行緒所封鎖。|
|[CA2003:不要將 Fiber 視為執行緒](../code-quality/ca2003.md)|Managed 執行緒被視為 Win32 執行緒。|
|[CA2004:必須移除對 GC.KeepAlive 的呼叫](../code-quality/ca2004.md)|如果您要轉換成 SafeHandle 使用方式，請移除所有對 GC 的呼叫。KeepAlive （物件）。 在此情況下，類別應該不需要呼叫 GC。KeepAlive，假設它們沒有完成項，但依賴 SafeHandle 來完成作業系統控制碼。|
|[CA2006:必須使用 SafeHandle 封裝原生資源](../code-quality/ca2006.md)|在 Managed 程式碼中使用 IntPtr，可能會有潛在的安全性和可靠性問題。 必須檢閱所有使用 IntPtr 的情況，判斷是否需要在該處使用 SafeHandle (或類似技術)。|
|[CA2007:不直接等候工作](../code-quality/ca2007.md)|非同步方法會[awaits](/dotnet/csharp/language-reference/keywords/await) <xref:System.Threading.Tasks.Task>直接等候。|
|[CA2009：不要在 ImmutableCollection 值上呼叫 Tolmmutablecollection](../code-quality/ca2009.md)|`ToImmutable`不必要地在<xref:System.Collections.Immutable>命名空間的不可變集合上呼叫方法。|
