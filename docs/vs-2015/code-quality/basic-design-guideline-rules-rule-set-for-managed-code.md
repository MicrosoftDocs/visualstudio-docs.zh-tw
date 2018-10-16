---
title: 基本設計方針規則規則集為 managed 程式碼 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7eb384f5-f961-400b-b151-115d92addc6a
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ed0728eb0daa5c1ff0f322db42f66373181f3e23
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49184713"
---
# <a name="basic-design-guideline-rules-rule-set-for-managed-code"></a>適用於 Managed 程式碼的基本設計方針規則規則集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 Microsoft 基本設計方針規則規則集將焦點放在讓您更輕鬆地了解和使用程式碼。 您應該包含這個規則集，如果您的專案包含程式庫程式碼，或如果您想要強制執行容易維護的程式碼的最佳作法。  
  
 基本設計方針規則納入 Microsoft 最小 Recommeded 規則規則集的所有規則。 如需最小規則的清單，請參閱 < [managed 程式碼的 Managed 建議規則規則集](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)。  
  
 下表描述所有 Microsoft 基本設計方針規則規則集內的規則。  
  
|規則|描述|  
|----------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|可處置欄位的類型應該是可處置的|  
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|必須正確宣告事件處理常式|  
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|組件必須標記 assemblyversionattribute|  
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|介面方法應該要可以由子類型呼叫|  
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|擁有原生資源的類型應該是可處置的|  
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|將 P/Invokes 移到 NativeMethods 類別|  
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|不要隱藏基底類別方法|  
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|必須正確實作 IDisposable|  
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|不會引發非預期的位置中的例外狀況|  
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|避免重複的快速鍵|  
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|P/Invoke 進入點應該要存在|  
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invokes 不應該為可見|  
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|自動配置類型不應該是 COM 可見|  
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|P/Invoke 之後立即呼叫 GetLastError|  
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|COM 可見類型的基底類型應該是 COM 可見|  
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|應該和 COM 註冊方法對應|  
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|P/Invokes 必須正確宣告|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|移除空的完成項|  
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|實值類型欄位應該為可移植的|  
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|P/Invoke 宣告應該為可移植的|  
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|不要鎖定具有弱式識別的物件|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|檢閱 SQL 查詢中的有安全性弱點|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|指定的 P/Invoke 字串引數封送處理|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|必須檢閱實值型別上的宣告式安全性|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|指標不應該為可見|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|受保護的類型不應該公開欄位|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|方法安全性應該是類型的超集|  
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA 方法應該只呼叫 APTCA 方法|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA 類型應該只擴充 APTCA 基底類型|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|不要間接公開具有連結要求的方法|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|覆寫連結要求應該與基底相同|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|易受攻擊的換行 finally 子句在外層 try 中|  
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|類型連結要求需要繼承要求|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|安全性關鍵類型可能未參與類型等價|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|預設建構函式必須至少與基底型別的預設建構函式一樣關鍵|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|必須將方法委派繫結具有一致透明度|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|覆寫基底方法時，方法必須保持一致的透明度|  
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|透明方法必須包含可驗證的 IL|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|透明方法不可以呼叫具有 SuppressUnmanagedCodeSecurity 屬性的方法|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|透明程式碼絕不能參考安全性關鍵項目|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|透明方法不可以滿足 Linkdemand|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|類型必須至少和基底類型與介面一樣關鍵|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|透明方法不可以使用安全性判斷提示|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|透明方法不可以呼叫原生程式碼|  
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|重新擲回以保存堆疊詳細資料|  
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|不要多次處置物件|  
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|初始化實值類型的靜態欄位內嵌|  
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|不要標記以 WebMethod 的 serviced 的元件|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|可處置的欄位應該受到處置|  
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|不要呼叫建構函式中的可覆寫方法|  
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|可處置類型應該宣告完成項|  
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|完成項應該呼叫基底類別完成項|  
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|實作序列化建構函式|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|多載覆寫 ValueType.Equals 的等號比較運算子|  
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|以 STAThread 標記 Windows Form 進入點|  
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|標記所有不可序列化的欄位|  
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|ISerializable 類型上呼叫基底類別方法|  
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Serializableattribute 標記 ISerializable 類型|  
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|正確實作序列化方法|  
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|必須正確實作 ISerializable|  
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|提供格式化方法的正確引數|  
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|正確測試 NaN|  
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|不要在泛型類型上宣告靜態成員|  
|[CA1002](../code-quality/ca1002-do-not-expose-generic-lists.md)|不要公開泛型清單|  
|[CA1003 必須](../code-quality/ca1003-use-generic-event-handler-instances.md)|使用一般事件處理常式執行個體|  
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|泛型方法應該提供型別參數|  
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|避免在泛型類型上的過多參數|  
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|無法建立巢狀成員簽章中的泛型型別|  
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|在適當時使用泛型|  
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|列舉應該使用零值|  
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|集合應該實作泛型介面|  
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|請考慮將基底類型當做參數傳遞|  
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|抽象類型不應該有建構函式|  
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|多載運算子等於多載加號和減號|  
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|組件必須標記 clscompliantattribute|  
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|組件必須標記 comvisibleattribute|  
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|以 AttributeUsageAttribute 標記屬性|  
|[CA1019 必須](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|定義存取子屬性引數|  
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|索引子不應該使用多維|  
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|在適當時使用屬性|  
|[CA1025 必須](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|以參數陣列取代重複的引數|  
|[CA1026](../code-quality/ca1026-default-parameters-should-not-be-used.md)|不應該使用預設參數|  
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|以 FlagsAttribute 標記列舉|  
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|列舉儲存區應該是 Int32|  
|[CA1030](../code-quality/ca1030-use-events-where-appropriate.md)|在適當時使用事件|  
|[CA1031](../code-quality/ca1031-do-not-catch-general-exception-types.md)|不要攔截一般例外狀況類型|  
|[CA1032 必須](../code-quality/ca1032-implement-standard-exception-constructors.md)|實作標準例外狀況建構函式|  
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|巢狀的類型不應該為可見|  
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|實作包含強類型成員|  
|[CA1036 必須](../code-quality/ca1036-override-methods-on-comparable-types.md)|覆寫在 comparable 類型的方法|  
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|應該是強類型列舉值|  
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|清單為強類型|  
|[CA1041](../code-quality/ca1041-provide-obsoleteattribute-message.md)|提供 ObsoleteAttribute 訊息|  
|[CA1043 必須](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|使用索引子的整數類或字串引數|  
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|屬性不應該為唯寫|  
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|不要多載參考類型上的等號比較運算子|  
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|不要宣告在密封類型中的受保護的成員|  
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|不要宣告在密封類型中的虛擬成員|  
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|宣告命名空間中的類型|  
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|不要宣告可見的執行個體欄位|  
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|靜態預留位置類型應該為密封|  
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|靜態預留位置類型不應該有建構函式|  
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|URI 參數不應該為字串|  
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|URI 會傳回值不應該為字串|  
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|URI 屬性不應該為字串|  
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|字串 URI 多載呼叫 System.Uri 多載|  
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|類型不應該擴充特定基底類型|  
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|成員不應該公開特定的具象類型|  
|[CA1064](../code-quality/ca1064-exceptions-should-be-public.md)|例外狀況必須是公用|  
|[CA1500](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|變數名稱不應該與欄位名稱相符|  
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|避免造成過度複雜|  
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|識別項應該不僅為大小寫不同|  
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|識別項不應該和關鍵字相符|  
|[CA1801 必須](../code-quality/ca1801-review-unused-parameters.md)|檢閱未使用的參數|  
|[CA1804 必須](../code-quality/ca1804-remove-unused-locals.md)|移除未使用的區域變數|  
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|避免過多區域變數|  
|[CA1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|初始化參考類型的靜態欄位內嵌|  
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|避免使用未呼叫的私用程式碼|  
|[CA1812](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|避免使用未執行個體化的內部類別|  
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|避免使用非密封的屬性|  
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|建議使用不規則陣列取代多維|  
|[CA1815](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|覆寫 equals 和實值型別上等號比較運算子|  
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|屬性不應該傳回陣列|  
|[CA1820 應該](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|測試使用字串長度的空字串|  
|[CA1822](../code-quality/ca1822-mark-members-as-static.md)|成員標記為 static|  
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|避免未使用的私用欄位|  
|[CA2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|不要引發保留的例外狀況類型|  
|[CA2205 必須](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|使用 Win32 API 的 managed 對等項目|  
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|正確執行個體化引數例外狀況|  
|[CA2211 非常數](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|非常數欄位不應該為可見|  
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|不以 FlagsAttribute 標記列舉|  
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|不會引發在 exception 子句中的例外狀況|  
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|完成項應該受到保護|  
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|不要降低繼承的成員的可視性|  
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|成員不應該由多個傳回的型別不同|  
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|覆寫等於多載等號比較運算子|  
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|運算子多載必須有具名的替代項目|  
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|運算子應該有對稱的多載|  
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|集合屬性應該為唯讀|  
|[CA2230 必須](../code-quality/ca2230-use-params-for-variable-arguments.md)|使用 params 做為變數引數|  
|[CA2234 必須](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|必須傳遞 System.Uri 物件而不是字串|  
|[CA2239 必須](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|提供選擇性欄位的還原序列化方法|



