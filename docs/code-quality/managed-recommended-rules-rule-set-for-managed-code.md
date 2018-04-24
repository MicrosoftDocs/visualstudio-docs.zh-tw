---
title: 適用於 Managed 程式碼的 Managed 建議規則規則集
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 1d1160f8-4e51-4e70-99cd-82ad10ee7b32
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3f15fc1859e0b7b8f3e3d7dc4bcf7fb315690734
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="managed-recommended-rules-rule-set-for-managed-code"></a>適用於 Managed 程式碼的 Managed 建議規則規則集
您可以使用 Microsoft Managed 建議規則規則集將焦點放在您的 managed 程式碼，包括潛在的安全性漏洞、 應用程式當機，以及其他重要邏輯和設計錯誤中最關鍵的問題。 您應該包含這個規則集在您建立專案的任何自訂規則集。

|規則|描述|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|應該處置可處置欄位的類型|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|事件處理常式必須正確宣告|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|以 AssemblyVersionAttribute 標記組件|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|介面方法應該要可以由子類型呼叫|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|原生資源的類型應該是可處置|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|將 P/Invokes 移到 NativeMethods 類別|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|不要隱藏基底類別方法|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|正確實作 IDisposable|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|不會引發例外狀況中的非預期的位置|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|避免重複的快速鍵|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|P/Invoke 進入點應該要存在|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invokes 不應該為可見|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|自動配置類型不應該是 COM 可見|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|在 P/Invoke 之後立即呼叫 GetLastError|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|COM 可見類型的基底類型應該是 COM 可見|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|應該符合 COM 註冊方法|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|P/Invokes 必須正確宣告|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|移除空的完成項|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|實值類型欄位應該為可移植|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|P/Invoke 宣告應該為可移植|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|請勿鎖定具有弱式識別的物件|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|檢閱 SQL 查詢有安全性弱點|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|指定 P/Invoke 字串引數的封送處理|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|檢閱實值類型的宣告式安全性|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|指標不應該為可見|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|受保護的類型不應該公開欄位|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|方法安全性應該是類型的超集|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA 方法應該只呼叫 APTCA 方法|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA 類型應該只擴充 APTCA 基底類型|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|不要間接公開具有連結要求方法|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|覆寫連結要求應該與基底相同|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Finally 子句包裝在外層 try|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|類型連結要求需要繼承要求|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|安全性關鍵類型可能未參與類型等價|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|預設建構函式必須為至少和基底類型的預設建構函式一樣關鍵|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|委派必須繫結至方法具有一致透明度|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|覆寫基底方法時，方法必須保持一致的透明度|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|透明方法必須包含可驗證的 IL|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|透明方法不可以呼叫使用 SuppressUnmanagedCodeSecurity 屬性的方法|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|透明程式碼不可以參考安全性關鍵項目|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|透明方法不可以滿足 Linkdemand|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|類型必須是至少及其基底類型與介面一樣關鍵|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|透明方法不能使用安全性判斷提示|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|透明方法不可以呼叫至原生程式碼|
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|重新擲回以保存堆疊詳細資料|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|不要多次處置物件|
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|初始化實值類型的靜態欄位內嵌|
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|不會標示以 WebMethod serviced 的元件|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|應該處置可處置的欄位|
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|不要呼叫建構函式中的可覆寫方法|
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|可處置類型應該宣告完成項|
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|完成項應該呼叫基底類別完成項|
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|實作序列化建構函式|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|多載覆寫 ValueType.Equals 的等號比較運算子|
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Stathread 標記 Windows Form 進入點|
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|標記所有不可序列化的欄位|
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|ISerializable 類型上呼叫基底類別方法|
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|ISerializable 類型必須標記 serializableattribute|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|正確實作序列化方法|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|正確實作 ISerializable|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|提供格式化方法的正確引數|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|正確測試 NaN|