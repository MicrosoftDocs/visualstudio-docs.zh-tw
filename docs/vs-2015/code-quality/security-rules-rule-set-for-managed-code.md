---
title: 安全性規則規則集為 managed 程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0657f7f450a8dd4261e53c0c6c601ba8067a22ab
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489944"
---
# <a name="security-rules-rule-set-for-managed-code"></a>適用於 Managed 程式碼的安全性規則規則集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[managed 程式碼的安全性規則規則集](https://docs.microsoft.com/visualstudio/code-quality/security-rules-rule-set-for-managed-code)。  
  
您應該包含 Microsoft 安全性規則規則集以最大化所報告的潛在安全性問題數目。  
  
|規則|描述|  
|----------|-----------------|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|檢閱 SQL 查詢中的有安全性弱點|  
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|一般處理常式攔截非 CLSCompliant 例外狀況|  
|[CA2103 必須](../code-quality/ca2103-review-imperative-security.md)|必須檢閱命令式安全性|  
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|不要宣告唯讀的可變動參考類型|  
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|陣列欄位不應該為唯讀|  
|[CA2106 必須](../code-quality/ca2106-secure-asserts.md)|必須保護判斷提示|  
|[CA2107 必須](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|檢視 deny 和 permit only 的使用方式|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|必須檢閱實值型別上的宣告式安全性|  
|[CA2109 必須](../code-quality/ca2109-review-visible-event-handlers.md)|檢閱顯示的事件處理常式|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|指標不應該為可見|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|受保護的類型不應該公開欄位|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|方法安全性應該是類型的超集|  
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|呼叫 GC。KeepAlive 時使用原生資源|  
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA 方法應該只呼叫 APTCA 方法|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA 類型應該只擴充 APTCA 基底類型|  
|[CA2118](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|檢閱 SuppressUnmanagedCodeSecurityAttribute 使用方法|  
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|密封方法以滿足私用介面|  
|[CA2120 必須](../code-quality/ca2120-secure-serialization-constructors.md)|保護序列化建構函式|  
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|靜態建構函式應為私用|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|不要間接公開具有連結要求的方法|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|覆寫連結要求應該與基底相同|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|易受攻擊的換行 finally 子句在外層 try 中|  
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|類型連結要求需要繼承要求|  
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|安全性關鍵常數應該是透明的|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|安全性關鍵類型可能未參與類型等價|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|預設建構函式必須至少與基底型別的預設建構函式一樣關鍵|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|必須將方法委派繫結具有一致透明度|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|覆寫基底方法時，方法必須保持一致的透明度|  
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|層級 2 組件不應該包含 Linkdemand|  
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|成員不應該具有衝突的透明度註釋|  
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|透明方法必須包含可驗證的 IL|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|透明方法不可以呼叫具有 SuppressUnmanagedCodeSecurity 屬性的方法|  
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|透明方法不能使用 HandleProcessCorruptingExceptions 屬性|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|透明程式碼絕不能參考安全性關鍵項目|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|透明方法不可以滿足 Linkdemand|  
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|透明程式碼不應該使用 Linkdemand 加以保護|  
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|透明方法不應該使用安全性要求|  
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|透明程式碼不應該從位元組陣列載入組件|  
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|透明方法不可以使用 SuppressUnmanagedCodeSecurityAttribute 來裝飾|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|類型必須至少和基底類型與介面一樣關鍵|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|透明方法不可以使用安全性判斷提示|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|透明方法不可以呼叫原生程式碼|  
|[CA2210](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|組件應該具備有效的強式名稱|



