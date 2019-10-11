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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb39bb5f59373f52d77c7cc5d13d12544d4c0314
ms.sourcegitcommit: 3e94d9fb6dc56fa8b23fbacd5d11cf8d6e7e18f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252582"
---
# <a name="reliability-warnings"></a>可靠性警告

可靠性警告支援程式庫和應用程式可靠性，例如正確的記憶體和執行緒使用方式。 可靠性規則包括：

|規則|描述|
|----------|-----------------|
|[CA2000：在失去範圍 @ no__t 之前處置物件-0|因為可能會發生例外事件以防止執行物件的完成項，所以應在物件的所有參考都超出範圍之前，明確處置物件。|
|[CA2001：避免呼叫有問題的方法 @ no__t-0|成員呼叫了可能有危險或問題的方法。|
|[CA2002：不要鎖定具有弱式識別 @ no__t-0 的物件|可以跨應用程式定義域範圍直接存取的物件，即所謂具有弱式識別的物件。 嘗試取得具有弱式識別之物件鎖定的執行緒，可以被不同應用程式定義域中具有相同物件鎖定的第二個執行緒所封鎖。|
|[CA2003：不要將纖維視為執行緒 @ no__t-0|Managed 執行緒被視為 Win32 執行緒。|
|[CA2004：移除 GC 的呼叫。KeepAlive @ no__t-0|如果您要轉換成 SafeHandle 使用方式，請移除所有對 GC 的呼叫。KeepAlive （物件）。 在此情況下，類別應該不需要呼叫 GC。KeepAlive，假設它們沒有完成項，但依賴 SafeHandle 來完成作業系統控制碼。|
|[CA2006：使用 SafeHandle 封裝原生資源 @ no__t-0|在 Managed 程式碼中使用 IntPtr，可能會有潛在的安全性和可靠性問題。 必須檢閱所有使用 IntPtr 的情況，判斷是否需要在該處使用 SafeHandle (或類似技術)。|
|[CA2007：不要直接等待工作 @ no__t-0|非同步方法會 <xref:System.Threading.Tasks.Task>[直接等候](/dotnet/csharp/language-reference/keywords/await)。|
