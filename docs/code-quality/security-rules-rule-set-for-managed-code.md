---
title: 適用於 Managed 程式碼的安全性規則規則集
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 45c51a6c5496686ef84b17341c97f00680a80bdd
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59366038"
---
# <a name="security-rules-rule-set-for-managed-code"></a>適用於 Managed 程式碼的安全性規則規則集
您應該包含 Microsoft 安全性規則規則集以最大化所報告的潛在安全性問題數目。

|規則|描述|
|----------|-----------------|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|必須檢閱 SQL 查詢中是否有安全性弱點|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|必須使用一般處理常式攔截非 CLSCompliant 例外狀況|
|[CA2103](../code-quality/ca2103-review-imperative-security.md)|必須檢閱命令式安全性|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|不要宣告唯讀的可變動參考類型|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|陣列欄位不應該為唯讀|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|必須保護判斷提示|
|[CA2107](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|必須檢閱 Deny 和 Permit Only 的使用方式|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|必須檢閱實值類型上的宣告式安全性|
|[CA2109](../code-quality/ca2109-review-visible-event-handlers.md)|必須檢閱可見的事件處理常式|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|指標不應該為可見的|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|受保護類型不應該公開欄位|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|方法安全性應該是類型的超集|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|使用原生資源時必須呼叫 GC.KeepAlive|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA 方法應該只呼叫 APTCA 方法|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA 類型應該只擴充 APTCA 基底類型|
|[CA2118](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|檢閱 SuppressUnmanagedCodeSecurityAttribute 使用方法|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|密封方法以滿足私用介面的要求|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|必須保護序列化建構函式|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|靜態建構函式應該為私用的|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|不要間接公開具有連結要求的方法|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|覆寫連結要求應該與基底相同|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|必須將有弱點的 finally 子句包裝在外層 try 中|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|必須同時具有類型連結要求和繼承要求|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|安全性關鍵常數應該是透明的|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|安全性關鍵類型可能未參與類型等價|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|預設建構函式至少必須和基底類型的預設建構函式一樣關鍵|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|委派必須繫結至具有一致透明度的方法|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|覆寫基底方法時，方法必須保持一致的透明度|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|層級 2 組件不應該包含 LinkDemand|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|成員不應該具有衝突的透明度註釋|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|透明方法必須只包含可驗證的 IL|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|透明方法不可以使用 SuppressUnmanagedCodeSecurity 屬性呼叫方法|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|透明方法不能使用 HandleProcessCorruptingExceptions 屬性|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|透明程式碼不可以參考安全性關鍵項目|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|透明方法不可以滿足 Linkdemand|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|透明程式碼不可以使用 LinkDemand 加以保護|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|透明方法不可以使用安全性要求|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|透明程式碼不可以從位元組陣列載入組件|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|透明方法不可以使用 SuppressUnmanagedCodeSecurityAttribute 來裝飾|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|類型至少必須和基底類型與介面一樣關鍵|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|CA2147：透明方法不可以使用安全性判斷提示|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|透明方法不可以呼叫機器碼|
|[CA2210](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|組件應該具備有效的強式名稱|
|[CA2300](ca2300-do-not-use-insecure-deserializer-binaryformatter.md)|請勿使用不安全還原 BinaryFormatter 序列化程式|
|[CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)|如果沒有第一個設定 BinaryFormatter.Binder 不呼叫 BinaryFormatter.Deserialize|
|[CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)|請確定呼叫 BinaryFormatter.Deserialize 之前設定 BinaryFormatter.Binder|
|[CA3001](../code-quality/ca3001-review-code-for-sql-injection-vulnerabilities.md)|檢閱程式碼是否有 SQL 插入式攻擊弱點|
|[CA3002](../code-quality/ca3002-review-code-for-xss-vulnerabilities.md)|檢閱程式碼是否有 XSS 弱點|
|[CA3003](../code-quality/ca3003-review-code-for-file-path-injection-vulnerabilities.md)|檢閱程式碼是否有檔案路徑插入式攻擊弱點|
|[CA3004](../code-quality/ca3004-review-code-for-information-disclosure-vulnerabilities.md)|檢閱程式碼是否有資訊洩漏弱點|
|[CA3005](../code-quality/ca3005-review-code-for-ldap-injection-vulnerabilities.md)|檢閱程式碼是否有 LDAP 插入式攻擊弱點|
|[CA3006](../code-quality/ca3006-review-code-for-process-command-injection-vulnerabilities.md)|檢閱程式碼是否有處理序命令插入式攻擊弱點|
|[CA3007](../code-quality/ca3007-review-code-for-open-redirect-vulnerabilities.md)|檢閱程式碼是否有開放式重新導向弱點|
|[CA3008](../code-quality/ca3008-review-code-for-xpath-injection-vulnerabilities.md)|檢閱程式碼是否有 XPath 插入式攻擊弱點|
|[CA3009](../code-quality/ca3009-review-code-for-xml-injection-vulnerabilities.md)|檢閱程式碼是否有 XML 插入式攻擊弱點|
|[CA3010](../code-quality/ca3010-review-code-for-xaml-injection-vulnerabilities.md)|檢閱程式碼是否有 XAML 插入式攻擊弱點|
|[CA3011](../code-quality/ca3011-review-code-for-dll-injection-vulnerabilities.md)|檢閱程式碼是否有 DLL 插入式攻擊弱點|
|[CA3012](../code-quality/ca3012-review-code-for-regex-injection-vulnerabilities.md)|檢閱程式碼是否有 regex 插入式攻擊弱點|
