---
title: "可靠性警告 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 336548a51b6ee388f81602abca5a1d0421864c18
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="reliability-warnings"></a>可靠性警告
可靠性警告支援程式庫和應用程式的可靠性，例如記憶體和執行緒的正確用法。  
  
## <a name="in-this-section"></a>本節內容  
  
|規則|描述|  
|----------|-----------------|  
|[CA2000：必須在超出範圍前處置物件](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|因為可能會發生例外事件以防止執行物件的完成項，所以應在物件的所有參考都超出範圍之前，明確處置物件。|  
|[CA2001：避免呼叫有問題的方法](../code-quality/ca2001-avoid-calling-problematic-methods.md)|成員呼叫了可能有危險或問題的方法。|  
|[CA2002：不要鎖定具有弱式識別的物件](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|可以跨應用程式定義域範圍直接存取的物件，即所謂具有弱式識別的物件。 嘗試取得具有弱式識別之物件鎖定的執行緒，可以被不同應用程式定義域中具有相同物件鎖定的第二個執行緒所封鎖。|  
|[CA2003：不要將 Fiber 視為執行緒](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Managed 的執行緒會被視為 Win32 執行緒。|  
|[CA2004：必須移除對 GC.KeepAlive 的呼叫](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|如果您正在轉換為 SafeHandle 使用方式，移除所有對 GC。KeepAlive （物件）。 在此情況下，類別應該不需要呼叫 GC。KeepAlive，假設它們沒有完成項，但依賴 SafeHandle 最終處理 OS 處理它們。|  
|[CA2006：必須使用 SafeHandle 封裝原生資源](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|在 Managed 程式碼中使用 IntPtr，可能會有潛在的安全性和可靠性問題。 必須檢閱所有使用 IntPtr 的情況，判斷是否需要在該處使用 SafeHandle (或類似技術)。|