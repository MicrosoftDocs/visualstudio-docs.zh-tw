---
title: 適用於 Managed 程式碼的擴充正確性規則規則集
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e5781676bdcfe4af131926e2d3ed1a49414da4b1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965298"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>適用於 Managed 程式碼的擴充正確性規則規則集
Microsoft 擴充正確性規則規則集最大化的邏輯和 framework 使用錯誤報告的程式碼分析。 額外的重點會放在特定的案例，例如 COM 互通性和行動應用程式。 您應該考慮包含這個規則集如果任一這些案例適用於您的專案或您的專案中找出其他問題。

 Microsoft 擴充正確性規則規則集包含在 Microsoft 基本正確性規則規則集的規則。 基本正確性規則包括 Microsoft 最小建議規則規則中設定的規則。 如需詳細資訊，請參閱[managed 程式碼的基本正確性規則規則集](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)和[managed 程式碼的 Managed 建議規則規則集](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)

 下表描述所有的 Microsoft 擴充正確性規則規則集內的規則。

|規則|描述|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|具有可處置欄位的類型應該為可處置|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|事件處理常式必須正確宣告|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|組件必須標記 AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|介面方法應該要可以由子類型呼叫|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|具有原生資源的類型應該要可呼叫 Dispose 方法明確釋放資源|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|必須將 P/Invokes 移到 NativeMethods 類別|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|不要隱藏基底類別方法|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|必須正確實作 IDisposable|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|不要在非預期的位置中引發例外狀況|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|避免使用重複的快速鍵|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|P/Invoke 進入點應該要存在|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invokes 不應該為可見的|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|自動配置類型不應該是 COM 可見|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|必須在 P/Invoke 之後立即呼叫 GetLastError|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|COM 可見類型的基底類型應該是 COM 可見|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|應該和 COM 註冊方法對應|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|P/Invokes 必須正確宣告|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|必須移除空的完成項|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|實值類型欄位應該為可移植的|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|P/Invoke 宣告應該為可移植的|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|不要鎖定具有弱式識別的物件|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|必須檢閱 SQL 查詢中是否有安全性弱點|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|必須指定 P/Invoke 字串引數的封送處理|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|必須檢閱實值類型上的宣告式安全性|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|指標不應該為可見的|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|受保護類型不應該公開欄位|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|方法安全性應該是類型的超集|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA 方法應該只呼叫 APTCA 方法|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA 類型應該只擴充 APTCA 基底類型|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|不要間接公開具有連結要求的方法|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|覆寫連結要求應該與基底相同|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|必須將有弱點的 finally 子句包裝在外層 try 中|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|必須同時具有類型連結要求和繼承要求|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|安全性關鍵類型可能未參與類型等價|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|預設建構函式至少必須和基底類型的預設建構函式一樣關鍵|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|委派必須繫結至具有一致透明度的方法|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|覆寫基底方法時，方法必須保持一致的透明度|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|透明方法必須只包含可驗證的 IL|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|透明方法不可以使用 SuppressUnmanagedCodeSecurity 屬性呼叫方法|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|透明程式碼不可以參考安全性關鍵項目|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|透明方法不可以滿足 Linkdemand|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|類型至少必須和基底類型與介面一樣關鍵|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|CA2147：透明方法不可以使用安全性判斷提示|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|透明方法不可以呼叫機器碼|
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|必須重新擲回以保存堆疊詳細資料|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|不要多次處置物件的 Dispose 方法|
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|必須將實值類型的靜態欄位內嵌初始化|
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|不要以 WebMethod 標記 Serviced 元件|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|可處置的欄位應該受到處置|
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|不要呼叫建構函式中的可覆寫方法|
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|可處置的類型應該宣告完成項|
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|完成項應該呼叫基底類別完成項|
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|必須實作序列化建構函式|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|在覆寫 ValueType.Equals 上多載等號運算子|
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Windows Forms 進入點必須標記 STAThread|
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|必須標記所有不可序列化的欄位|
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|必須呼叫 ISerializable 類型上的基底類別方法|
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|ISerializable 類型必須標記 SerializableAttribute|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|必須正確實作序列化方法|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|必須正確實作 ISerializable|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|必須提供格式化方法的正確引數|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|必須正確測試 NaN|
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|列舉值中應該要有值為零的成員|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|多載加號和減號運算子時必須一併多載等號比較運算子|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|不要將常值當作已當地語系化的參數傳遞|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|必須將字串標準化為大寫字母|
|[CA1806](../code-quality/ca1806-do-not-ignore-method-results.md)|不要忽略方法的結果|
|[CA1816](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|正確呼叫 GC.SuppressFinalize|
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|屬性不應該傳回陣列|
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|應該使用字串長度測試空白字串|
|[CA1903](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|只使用來自目標架構的 API|
|[CA2004](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|必須移除對 GC.KeepAlive 的呼叫|
|[CA2006](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|必須使用 SafeHandle 封裝原生資源|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|必須使用一般處理常式攔截非 CLSCompliant 例外狀況|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|不要宣告唯讀的可變動參考類型|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|陣列欄位不應該為唯讀|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|必須保護判斷提示|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|使用原生資源時必須呼叫 GC.KeepAlive|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|密封方法以滿足私用介面的要求|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|必須保護序列化建構函式|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|靜態建構函式應該為私用的|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|安全性關鍵常數應該是透明的|
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|必須使用 Win32 API 的受控對應項|
|[CA2215](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Dispose 方法應該呼叫基底類別處置|
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Finalizer 方法應該為 protected|
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|不要降低繼承成員的可視性|
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|成員不應該只有在傳回類型上不同|
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|多載等號比較運算子時必須一併覆寫 Equals|
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|運算子應該有對稱的多載|
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|集合屬性應該為唯讀|
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|必須為選擇性欄位提供還原序列化方法|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|必須實作標準例外狀況建構函式|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|URI 參數不應該為字串|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|URI 傳回值不應該為字串|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|URI 屬性不應該為字串|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|字串 URI 多載呼叫 System.Uri 多載|
|[CA1402](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|避免在 COM 可見介面中多載|
|[CA1406](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|避免對 Visual Basic 6 用戶端使用 int64 引數|
|[CA1407](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|避免在 COM 可見類型中使用靜態成員|
|[CA1408](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|不要使用 AutoDual ClassInterfaceType|
|[CA1409](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Com 可見類型應該是可建立的|
|[CA1411](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|COM 註冊方法不應該為可見的|
|[CA1412](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|ComSource 介面必須標記為 IDispatch|
|[CA1413](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|避免在 COM 可見實值類型中使用非公用欄位|
|[CA1414](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|以 MarshalAs 標記布林 P/Invoke 引數|
|[CA1600](../code-quality/ca1600-do-not-use-idle-process-priority.md)|不要使用 Idle 處理序優先順序|
|[CA1601](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|不要使用會妨礙電源狀態變更的計時器|
|[CA1824](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md)|組件必須標記 NeutralResourcesLanguageAttribute|
|[CA2001](../code-quality/ca2001-avoid-calling-problematic-methods.md)|避免呼叫有問題的方法|
|[CA2003](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|不要將 Fiber 視為執行緒|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|層級 2 組件不應該包含 LinkDemand|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|成員不應該具有衝突的透明度註釋|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|透明方法不能使用 HandleProcessCorruptingExceptions 屬性|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|透明程式碼不可以使用 LinkDemand 加以保護|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|透明方法不可以使用安全性要求|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|透明程式碼不可以從位元組陣列載入組件|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|透明方法不可以使用 SuppressUnmanagedCodeSecurityAttribute 來裝飾|
|[CA2204](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|常值必須使用正確的拼字|
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|非常數欄位不應該為可見的|
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|不要以 FlagsAttribute 標記列舉|
|[CA2218](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|覆寫 Equals 時必須一併覆寫 GetHashCode|
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|不要在 exception 子句中引發例外狀況|
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|運算子多載必須有具名的替代方法|
|[CA2228](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md)|不要使用尚未發行版本所支援的格式建置資源|
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|必須使用 params 作為變數引數|
|[CA2233](../code-quality/ca2233-operations-should-not-overflow.md)|運算不應該發生溢位|
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|必須傳遞 System.Uri 物件而非字串|
|[CA2243](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|屬性字串常值必須正確剖析|