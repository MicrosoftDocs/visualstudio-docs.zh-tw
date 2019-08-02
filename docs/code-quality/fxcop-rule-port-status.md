---
title: FxCop 規則埠狀態
ms.date: 05/21/2019
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- fxcop analyzers, ported rules
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2e635f2cbbeda67c4fbed760eb7e57dfcf140d15
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2019
ms.locfileid: "68604876"
---
# <a name="fxcop-rule-port-status"></a>Fxcop 規則埠狀態

如果您先前已在舊版的 Visual Studio 中使用靜態程式碼分析, 您可能會想知道哪些規則在目前的實作為[FxCop 分析器](install-fxcop-analyzers.md)中可供使用。 此頁面會列出已移植的規則, 以及尚未移植的規則, 以及是否有計劃要進行埠的通訊。

## <a name="ported-rules"></a>移植的規則

Roslyn 分析器存放庫中自動產生的[檔頁面](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md), 具有已移植到 FxCop 分析器的最新規則清單。 該頁面也有其他資訊, 例如規則是否預設為啟用, 以及是否有相關聯的*程式碼修正*。 ([程式碼修正](../ide/quick-actions.md)是 Visual Studio 的燈泡圖示功能表中, 可使用的單鍵修正)。

從這個頁面的日期開始, 已移植到[fxcop 分析器](install-fxcop-analyzers.md)的 FxCop 規則清單包含:

規則識別碼 | 標題
--------|---------
[CA1000](ca1000-do-not-declare-static-members-on-generic-types.md) | 不要在泛型類型上宣告靜態成員
[CA1001](ca1001-types-that-own-disposable-fields-should-be-disposable.md) | 具有可處置欄位的類型應該為可處置
[CA1003](ca1003-use-generic-event-handler-instances.md) | 使用一般事件處理常式執行個體
[CA1008](ca1008-enums-should-have-zero-value.md) | 列舉值中應該要有值為零的成員
[CA1010](ca1010-collections-should-implement-generic-interface.md) | 集合應該實作泛型介面
[CA1012](ca1012-abstract-types-should-not-have-constructors.md) | 抽象類型不應該有建構函式
[CA1014](ca1014-mark-assemblies-with-clscompliantattribute.md) | 以 CLSCompliant 標記元件
[CA1016](ca1016-mark-assemblies-with-assemblyversionattribute.md) | 以元件版本戳記元件
[CA1017](ca1017-mark-assemblies-with-comvisibleattribute.md) | 以 ComVisible 標記元件
[CA1018](ca1018-mark-attributes-with-attributeusageattribute.md) | 必須以 AttributeUsageAttribute 標記屬性
[CA1019](ca1019-define-accessors-for-attribute-arguments.md) | 定義屬性引數的存取子
[CA1024](ca1024-use-properties-where-appropriate.md) | 建議在適當時使用屬性
[CA1027](ca1027-mark-enums-with-flagsattribute.md) | 必須以 FlagsAttribute 標記列舉
[CA1028](ca1028-enum-storage-should-be-int32.md) | 列舉儲存區應該是 Int32
[CA1030](ca1030-use-events-where-appropriate.md) | 建議在適當時使用事件
[CA1031](ca1031-do-not-catch-general-exception-types.md) | 不要攔截一般例外狀況類型
[CA1032](ca1032-implement-standard-exception-constructors.md) | 必須實作標準例外狀況建構函式
[CA1033](ca1033-interface-methods-should-be-callable-by-child-types.md) | 介面方法應該要可以由子類型呼叫
[CA1034](ca1034-nested-types-should-not-be-visible.md) | 巢狀類型不應該為可見的
[CA1036](ca1036-override-methods-on-comparable-types.md) | 必須在 Comparable 類型中覆寫方法
[CA1040](ca1040-avoid-empty-interfaces.md) | 避免使用空的介面
[CA1041](ca1041-provide-obsoleteattribute-message.md) | 必須提供 ObsoleteAttribute 訊息
[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md) | 針對索引子使用整數或字串引數
[CA1044](ca1044-properties-should-not-be-write-only.md) | 屬性不應該為唯寫的
[CA1050](ca1050-declare-types-in-namespaces.md) | 類型必須在命名空間中宣告
[CA1051](ca1051-do-not-declare-visible-instance-fields.md) | 不要宣告可見的執行個體欄位
[CA1052](ca1052-static-holder-types-should-be-sealed.md) | 靜態預留位置類型應為靜態或 NotInheritable
[CA1053](ca1053-static-holder-types-should-not-have-constructors.md) | 靜態預留位置類型不應該有任何函式 (CA1053 是 FxCop 分析器的[CA1052](ca1052-static-holder-types-should-be-sealed.md)的一部分)
[CA1054](ca1054-uri-parameters-should-not-be-strings.md) | Uri 參數不應為字串
[CA1055](ca1055-uri-return-values-should-not-be-strings.md) | Uri 傳回值不應為字串
[CA1056](ca1056-uri-properties-should-not-be-strings.md) | Uri 屬性不應為字串
[CA1058](ca1058-types-should-not-extend-certain-base-types.md) | 類型不應該擴充特定基底類型
[CA1060](ca1060-move-p-invokes-to-nativemethods-class.md) | 將 pinvoke 移至原生方法類別
[CA1061](ca1061-do-not-hide-base-class-methods.md) | 不要隱藏基底類別方法
[CA1062](ca1062-validate-arguments-of-public-methods.md) | 必須驗證公用方法的引數
[CA1063](ca1063-implement-idisposable-correctly.md) | 正確地執行 IDisposable
[CA1064](ca1064-exceptions-should-be-public.md) | 例外狀況必須是公用
[CA1065](ca1065-do-not-raise-exceptions-in-unexpected-locations.md) | 不要在非預期的位置中引發例外狀況
CA1066 | 類型{0}應執行 IEquatable\<T >, 因為它會覆寫 Equals
CA1067 | 在執行 IEquatable\<T 時覆寫 object.equals (object) >
CA1068 | CancellationToken 參數必須是最後的
CA1200 | 避免使用具有前置詞的 cref 標記
[CA1303](ca1303-do-not-pass-literals-as-localized-parameters.md) | 不要將常值當作已當地語系化的參數傳遞
[CA1304](ca1304-specify-cultureinfo.md) | 必須指定 CultureInfo
[CA1305](ca1305-specify-iformatprovider.md) | 必須指定 IFormatProvider
[CA1307](ca1307-specify-stringcomparison.md) | 必須指定 StringComparison
[CA1308](ca1308-normalize-strings-to-uppercase.md) | 必須將字串標準化為大寫字母
[CA1309](ca1309-use-ordinal-stringcomparison.md) | 使用序數位符串比較
[CA1401](ca1401-p-invokes-should-not-be-visible.md) | P/Invokes 不應該為可見的
[CA1501](ca1501-avoid-excessive-inheritance.md) | 避免在物件間過度繼承
[CA1502](ca1502-avoid-excessive-complexity.md) | 避免造成過度複雜的方法
[CA1505](ca1505-avoid-unmaintainable-code.md) | 應避免撰寫無法維護的程式碼
[CA1506](ca1506-avoid-excessive-class-coupling.md) | 應避免使用結合過度的類別
[CA1507](ca1507.md) | 使用 nameof 來表達符號名稱
CA1508 | 避免失效的條件式程式碼
CA1509 | 程式碼度量規則規格檔案中的專案無效
[CA1707](ca1707-identifiers-should-not-contain-underscores.md) | 識別項名稱不應該包含底線
[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md) | 識別項名稱不應該只靠大小寫區別
[CA1710](ca1710-identifiers-should-have-correct-suffix.md) | 識別項應該使用正確的後置字元
[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md) | 識別項名稱不應該使用不正確的後置字元
[CA1712](ca1712-do-not-prefix-enum-values-with-type-name.md) | 不要使用類型名稱作為列舉值的前置字元
[CA1714](ca1714-flags-enums-should-have-plural-names.md) | 旗標列舉應該使用複數名稱
[CA1715](ca1715-identifiers-should-have-correct-prefix.md) | 識別項名稱應該使用正確的前置字元
[CA1716](ca1716-identifiers-should-not-match-keywords.md) | 識別項名稱不應該和關鍵字相符
[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md) | 只有 FlagsAttribute 列舉應該使用複數名稱
[CA1720](ca1720-identifiers-should-not-contain-type-names.md) | 識別碼包含類型名稱
[CA1721](ca1721-property-names-should-not-match-get-methods.md) | 屬性名稱不應該和其中有 get 的方法名稱相符
[CA1724](ca1724-type-names-should-not-match-namespaces.md) | 類型名稱不應與命名空間相符
[CA1725](ca1725-parameter-names-should-match-base-declaration.md) | 參數名稱應該符合基底類型的宣告
[CA1801](ca1801-review-unused-parameters.md) | 必須檢閱未使用的參數
[CA1802](ca1802-use-literals-where-appropriate.md) | 適當時使用常值
[CA1806](ca1806-do-not-ignore-method-results.md) | 不要忽略方法的結果
[CA1810](ca1810-initialize-reference-type-static-fields-inline.md) | 必須將參考類型內部的靜態欄位初始化
[CA1812](ca1812-avoid-uninstantiated-internal-classes.md) | 避免使用未執行個體化的內部類別
[CA1813](ca1813-avoid-unsealed-attributes.md) | 避免使用非密封屬性
[CA1814](ca1814-prefer-jagged-arrays-over-multidimensional.md) | 建議使用不規則陣列取代多維陣列
[CA1815](ca1815-override-equals-and-operator-equals-on-value-types.md) | 必須覆寫實值類型上的 Equals 方法和等號比較運算子
[CA1816](ca1816-call-gc-suppressfinalize-correctly.md) | Dispose 方法應該呼叫 Gc.suppressfinalize
[CA1819](ca1819-properties-should-not-return-arrays.md) | 屬性不應該傳回陣列
[CA1820](ca1820-test-for-empty-strings-using-string-length.md) | 應該使用字串長度測試空白字串
[CA1821](ca1821-remove-empty-finalizers.md) | 移除空的完成項
[CA1822](ca1822-mark-members-as-static.md) | 將成員標記為 static
[CA1823](ca1823-avoid-unused-private-fields.md) | 避免包含未使用的私用欄位
[CA1824](ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md) | 組件必須標記 NeutralResourcesLanguageAttribute
CA1825 | 避免長度為零的陣列配置。
CA1826 | 請勿在可編制索引的集合上使用可列舉的方法。 改為直接使用集合
[CA2000](ca2000-dispose-objects-before-losing-scope.md) | 必須在超出範圍前處置物件
[CA2002](ca2002-do-not-lock-on-objects-with-weak-identity.md) | 不要鎖定具有弱式識別的物件
[CA2007](ca2007-do-not-directly-await-task.md) | 請考慮在等待的工作上呼叫 ConfigureAwait
CA2008 | 請勿在未傳遞 TaskScheduler 的情況下建立工作
CA2009 | 不要在 ImmutableCollection 值上呼叫 Tolmmutablecollection
CA2010 | 一律使用以 PreserveSigAttribute 標記的方法所傳回的值
[CA2100](ca2100-review-sql-queries-for-security-vulnerabilities.md) | 必須檢閱 SQL 查詢中是否有安全性弱點
[CA2101](ca2101-specify-marshaling-for-p-invoke-string-arguments.md) | 必須指定 P/Invoke 字串引數的封送處理
[CA2119](ca2119-seal-methods-that-satisfy-private-interfaces.md) | 密封方法以滿足私用介面的要求
[CA2153](ca2153-avoid-handling-corrupted-state-exceptions.md) | 不攔截損毀狀態例外狀況
[CA2200](ca2200-rethrow-to-preserve-stack-details.md) | 重新擲回以保留堆疊詳細資料。
[CA2201](ca2201-do-not-raise-reserved-exception-types.md) | 不要引發保留的例外狀況類型
[CA2207](ca2207-initialize-value-type-static-fields-inline.md) | 必須將實值類型的靜態欄位內嵌初始化
[CA2208](ca2208-instantiate-argument-exceptions-correctly.md) | 必須正確執行個體化引數例外狀況
[CA2211](ca2211-non-constant-fields-should-not-be-visible.md) | 非常數欄位不應該為可見的
[CA2213](ca2213-disposable-fields-should-be-disposed.md) | 可處置的欄位應該受到處置
[CA2214](ca2214-do-not-call-overridable-methods-in-constructors.md) | 不要呼叫建構函式中的可覆寫方法
[CA2216](ca2216-disposable-types-should-declare-finalizer.md) | 可處置的類型應該宣告完成項
[CA2217](ca2217-do-not-mark-enums-with-flagsattribute.md) | 不要以 FlagsAttribute 標記列舉
[CA2218](ca2218-override-gethashcode-on-overriding-equals.md) | 覆寫 Equals 時必須一併覆寫 GetHashCode
[CA2219](ca2219-do-not-raise-exceptions-in-exception-clauses.md) | 請勿在 finally 子句中引發例外狀況
[CA2224](ca2224-override-equals-on-overloading-operator-equals.md) | 多載運算子 equals 的覆寫 Equals
[CA2225](ca2225-operator-overloads-have-named-alternates.md) | 運算子多載必須有具名的替代方法
[CA2226](ca2226-operators-should-have-symmetrical-overloads.md) | 運算子應該有對稱的多載
[CA2227](ca2227-collection-properties-should-be-read-only.md) | 集合屬性應該為唯讀
[CA2229](ca2229-implement-serialization-constructors.md) | 必須實作序列化建構函式
[CA2231](ca2231-overload-operator-equals-on-overriding-valuetype-equals.md) | 覆寫運算子 equals 覆寫數值型別 Equals
[CA2234](ca2234-pass-system-uri-objects-instead-of-strings.md) | 傳遞系統 uri 物件, 而不是字串
[CA2235](ca2235-mark-all-non-serializable-fields.md) | 必須標記所有不可序列化的欄位
[CA2237](ca2237-mark-iserializable-types-with-serializableattribute.md) | 以可序列化標記 ISerializable 類型
[CA2241](ca2241-provide-correct-arguments-to-formatting-methods.md) | 必須提供格式化方法的正確引數
[CA2242](ca2242-test-for-nan-correctly.md) | 必須正確測試 NaN
[CA2243](ca2243-attribute-string-literals-should-parse-correctly.md) | 屬性字串常值必須正確剖析
CA2244 | 不要複製索引的元素初始化
[CA2300](ca2300-do-not-use-insecure-deserializer-binaryformatter.md) | 請勿使用不安全的還原序列化程式 BinaryFormatter
[CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md) | 未先設定 BinaryFormatter.Binder 之前，請勿呼叫 BinaryFormatter.Deserialize
[CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md) | 呼叫 BinaryFormatter.Deserialize 之前，請務必先設定 BinaryFormatter.Binder
[CA2305](ca2305-do-not-use-insecure-deserializer-losformatter.md) | 請勿使用不安全的還原序列化程式 LosFormatter
[CA2310](ca2310-do-not-use-insecure-deserializer-netdatacontractserializer.md) | 請勿使用不安全的還原序列化程式 NetDataContractSerializer
[CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md) | 未先設定 NetDataContractSerializer.Binder 之前，請勿還原序列化
[CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md) | 還原序列化之前，請務必先設定 NetDataContractSerializer.Binder
[CA2315](ca2315-do-not-use-insecure-deserializer-objectstateformatter.md) | 請勿使用不安全的還原序列化程式 ObjectStateFormatter
[CA2321](ca2321.md) | 請勿使用 SimpleTypeResolver 搭配 JavaScriptSerializer 來還原序列化
[CA2322](ca2322.md) | 還原序列化之前，請確定不會使用 SimpleTypeResolver 來將 JavaScriptSerializer 初始化
[CA3001](ca3001-review-code-for-sql-injection-vulnerabilities.md) | 檢閱程式碼是否有 SQL 插入式攻擊弱點
[CA3002](ca3002-review-code-for-xss-vulnerabilities.md) | 檢閱程式碼是否有 XSS 弱點
[CA3003](ca3003-review-code-for-file-path-injection-vulnerabilities.md) | 檢閱程式碼是否有檔案路徑插入式攻擊弱點
[CA3004](ca3004-review-code-for-information-disclosure-vulnerabilities.md) | 檢閱程式碼是否有資訊洩漏弱點
[CA3005](ca3005-review-code-for-ldap-injection-vulnerabilities.md) | 檢閱程式碼是否有 LDAP 插入式攻擊弱點
[CA3006](ca3006-review-code-for-process-command-injection-vulnerabilities.md) | 檢閱程式碼是否有處理序命令插入式攻擊弱點
[CA3007](ca3007-review-code-for-open-redirect-vulnerabilities.md) | 檢閱程式碼是否有開放式重新導向弱點
[CA3008](ca3008-review-code-for-xpath-injection-vulnerabilities.md) | 檢閱程式碼是否有 XPath 插入式攻擊弱點
[CA3009](ca3009-review-code-for-xml-injection-vulnerabilities.md) | 檢閱程式碼是否有 XML 插入式攻擊弱點
[CA3010](ca3010-review-code-for-xaml-injection-vulnerabilities.md) | 檢閱程式碼是否有 XAML 插入式攻擊弱點
[CA3011](ca3011-review-code-for-dll-injection-vulnerabilities.md) | 檢閱程式碼是否有 DLL 插入式攻擊弱點
[CA3012](ca3012-review-code-for-regex-injection-vulnerabilities.md) | 檢閱程式碼是否有 regex 插入式攻擊弱點
CA3061 | 不要依 URL 新增架構
[CA3075](ca3075-insecure-dtd-processing.md) | XML 中不安全的 DTD 處理
[CA3076](ca3076-insecure-xslt-script-execution.md) | 不安全的 XSLT 腳本處理。
[CA3077](ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader.md) | API 設計、Xml 及 XmlTextReader 中的不安全處理
[CA3147](ca3147-mark-verb-handlers-with-validateantiforgerytoken.md) | 使用 Validate Antiforgery Token 標記動詞處理常式
[CA5350](ca5350-do-not-use-weak-cryptographic-algorithms.md) | 請勿使用弱式密碼編譯演算法
[CA5351](ca5351-do-not-use-broken-cryptographic-algorithms.md) | 請勿使用中斷的密碼編譯演算法
CA5358 | 不要使用 Unsafe 加密模式
CA5359 | 不要停用憑證驗證
CA5360 | 不要在還原序列化中呼叫危險的方法
CA5361 | 請勿停用使用安全加密的 SChannel
CA5362 | 不要在可序列化類別中參考自我
CA5363 | 不要停用要求驗證
CA5364 | 請勿使用已淘汰的安全性通訊協定
CA5365 | 不要停用 HTTP 標頭檢查
CA5366 | 針對資料集讀取 Xml 使用 XmlReader
CA5367 | 不要序列化具有指標欄位的類型
CA5368 | 為 [衍生自] 頁面的 [類別] 設定 ViewStateUserKey
CA5369 | 使用 XmlReader 進行還原序列化
CA5370 | 使用 XmlReader 來驗證讀取器
CA5371 | 使用 XmlReader 讀取架構
CA5372 | 針對 XPathDocument 使用 XmlReader
CA5373 | 請勿使用過時的金鑰衍生函式
CA5374 | 不要使用 XslTransform
CA5375 | 不使用帳戶共用存取簽章
CA5376 | 使用 SharedAccessProtocol HttpsOnly
CA5377 | 使用容器層級存取原則
CA5378 | 請勿停用 ServicePointManagerSecurityProtocols
CA5379 | 請勿使用弱式金鑰衍生函數演算法
CA9999 | 分析器版本不符

## <a name="unported-rules"></a>Unported license 規則

尚未移植到[FxCop 分析器](install-fxcop-analyzers.md)的規則集, 是由尚未[進行移植](#rules-that-may-be-ported)的規則, 以及已被取代且[不會移植](#deprecated-rules)的規則所組成。

### <a name="rules-that-may-be-ported"></a>可能會進行移植的規則

下列 FxCop 靜態程式碼分析規則尚未實作為分析器, 但仍可能是。 這可能是因為封鎖技術的原因, 或只是規則較低的優先順序。 如需每個規則之移植狀態的詳細資訊, 請按一下 [**追蹤問題**] 資料行中的連結。

規則識別碼 | 追蹤問題
--- | ---
[CA1002](ca1002-do-not-expose-generic-lists.md) | [https://github.com/dotnet/roslyn-analyzers/issues/369](https://github.com/dotnet/roslyn-analyzers/issues/369)
[CA1004](ca1004-generic-methods-should-provide-type-parameter.md) | [https://github.com/dotnet/roslyn-analyzers/issues/370](https://github.com/dotnet/roslyn-analyzers/issues/370)
[CA1005](ca1005-avoid-excessive-parameters-on-generic-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/371](https://github.com/dotnet/roslyn-analyzers/issues/371)
[CA1006](ca1006-do-not-nest-generic-types-in-member-signatures.md) | [https://github.com/dotnet/roslyn-analyzers/issues/372](https://github.com/dotnet/roslyn-analyzers/issues/372)
[CA1007](ca1007-use-generics-where-appropriate.md) | [https://github.com/dotnet/roslyn-analyzers/issues/373](https://github.com/dotnet/roslyn-analyzers/issues/373)
[CA1011](ca1011-consider-passing-base-types-as-parameters.md) | [https://github.com/dotnet/roslyn-analyzers/issues/375](https://github.com/dotnet/roslyn-analyzers/issues/375)
[CA1021](ca1021-avoid-out-parameters.md) | [https://github.com/dotnet/roslyn-analyzers/issues/377](https://github.com/dotnet/roslyn-analyzers/issues/377)
[CA1023](ca1023-indexers-should-not-be-multidimensional.md) | [https://github.com/dotnet/roslyn-analyzers/issues/378](https://github.com/dotnet/roslyn-analyzers/issues/378)
[CA1045](ca1045-do-not-pass-types-by-reference.md) | [https://github.com/dotnet/roslyn-analyzers/issues/391](https://github.com/dotnet/roslyn-analyzers/issues/391)
[CA1046](ca1046-do-not-overload-operator-equals-on-reference-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/392](https://github.com/dotnet/roslyn-analyzers/issues/392)
[CA1047](ca1047-do-not-declare-protected-members-in-sealed-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/393](https://github.com/dotnet/roslyn-analyzers/issues/393)
[CA1048](ca1048-do-not-declare-virtual-members-in-sealed-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/394](https://github.com/dotnet/roslyn-analyzers/issues/394)
[CA1049](ca1049-types-that-own-native-resources-should-be-disposable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/395](https://github.com/dotnet/roslyn-analyzers/issues/395)
[CA1057](ca1057-string-uri-overloads-call-system-uri-overloads.md) | [https://github.com/dotnet/roslyn-analyzers/issues/401](https://github.com/dotnet/roslyn-analyzers/issues/401)
[CA1300](ca1300-specify-messageboxoptions.md) | [https://github.com/dotnet/roslyn-analyzers/issues/408](https://github.com/dotnet/roslyn-analyzers/issues/408)
[CA1301](ca1301-avoid-duplicate-accelerators.md) | [https://github.com/dotnet/roslyn-analyzers/issues/409](https://github.com/dotnet/roslyn-analyzers/issues/409)
[CA1306](ca1306-set-locale-for-data-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/414](https://github.com/dotnet/roslyn-analyzers/issues/414)
[CA1402](ca1402-avoid-overloads-in-com-visible-interfaces.md) | [https://github.com/dotnet/roslyn-analyzers/issues/418](https://github.com/dotnet/roslyn-analyzers/issues/418)
[CA1403](ca1403-auto-layout-types-should-not-be-com-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/419](https://github.com/dotnet/roslyn-analyzers/issues/419)
[CA1404](ca1404-call-getlasterror-immediately-after-p-invoke.md) | [https://github.com/dotnet/roslyn-analyzers/issues/420](https://github.com/dotnet/roslyn-analyzers/issues/420)
[CA1405](ca1405-com-visible-type-base-types-should-be-com-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/421](https://github.com/dotnet/roslyn-analyzers/issues/421)
[CA1407](ca1407-avoid-static-members-in-com-visible-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/423](https://github.com/dotnet/roslyn-analyzers/issues/423)
[CA1408](ca1408-do-not-use-autodual-classinterfacetype.md) | [https://github.com/dotnet/roslyn-analyzers/issues/424](https://github.com/dotnet/roslyn-analyzers/issues/424)
[CA1409](ca1409-com-visible-types-should-be-creatable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/425](https://github.com/dotnet/roslyn-analyzers/issues/425)
[CA1410](ca1410-com-registration-methods-should-be-matched.md) | [https://github.com/dotnet/roslyn-analyzers/issues/426](https://github.com/dotnet/roslyn-analyzers/issues/426)
[CA1411](ca1411-com-registration-methods-should-not-be-visible.md) | [https://github.com/dotnet/roslyn-analyzers/issues/427](https://github.com/dotnet/roslyn-analyzers/issues/427)
[CA1412](ca1412-mark-comsource-interfaces-as-idispatch.md) | [https://github.com/dotnet/roslyn-analyzers/issues/428](https://github.com/dotnet/roslyn-analyzers/issues/428)
[CA1413](ca1413-avoid-non-public-fields-in-com-visible-value-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/429](https://github.com/dotnet/roslyn-analyzers/issues/429)
[CA1414](ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md) | [https://github.com/dotnet/roslyn-analyzers/issues/430](https://github.com/dotnet/roslyn-analyzers/issues/430)
[CA1415](ca1415-declare-p-invokes-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/431](https://github.com/dotnet/roslyn-analyzers/issues/431)
[CA1500](ca1500-variable-names-should-not-match-field-names.md) | [https://github.com/dotnet/roslyn-analyzers/issues/432](https://github.com/dotnet/roslyn-analyzers/issues/432)
[CA1600](ca1600-do-not-use-idle-process-priority.md) | [https://github.com/dotnet/roslyn-analyzers/issues/438](https://github.com/dotnet/roslyn-analyzers/issues/438)
[CA1601](ca1601-do-not-use-timers-that-prevent-power-state-changes.md) | [https://github.com/dotnet/roslyn-analyzers/issues/439](https://github.com/dotnet/roslyn-analyzers/issues/439)
[CA1700](ca1700-do-not-name-enum-values-reserved.md) | [https://github.com/dotnet/roslyn-analyzers/issues/440](https://github.com/dotnet/roslyn-analyzers/issues/440)
[CA1704](ca1704-identifiers-should-be-spelled-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/443](https://github.com/dotnet/roslyn-analyzers/issues/443)
[CA1709](ca1709-identifiers-should-be-cased-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/445](https://github.com/dotnet/roslyn-analyzers/issues/445)
[CA1713](ca1713-events-should-not-have-before-or-after-prefix.md) | [https://github.com/dotnet/roslyn-analyzers/issues/449](https://github.com/dotnet/roslyn-analyzers/issues/449)
[CA1719](ca1719-parameter-names-should-not-match-member-names.md) | [https://github.com/dotnet/roslyn-analyzers/issues/453](https://github.com/dotnet/roslyn-analyzers/issues/453)
[CA1722](ca1722-identifiers-should-not-have-incorrect-prefix.md) | [https://github.com/dotnet/roslyn-analyzers/issues/455](https://github.com/dotnet/roslyn-analyzers/issues/455)
[CA1726](ca1726-use-preferred-terms.md) | [https://github.com/dotnet/roslyn-analyzers/issues/458](https://github.com/dotnet/roslyn-analyzers/issues/458)
[CA1804](ca1804-remove-unused-locals.md) | [https://github.com/dotnet/roslyn-analyzers/issues/461](https://github.com/dotnet/roslyn-analyzers/issues/461)
[CA1811](ca1811-avoid-uncalled-private-code.md) | [https://github.com/dotnet/roslyn-analyzers/issues/464](https://github.com/dotnet/roslyn-analyzers/issues/464)
[CA1900](ca1900-value-type-fields-should-be-portable.md) | [https://github.com/dotnet/roslyn-analyzers/issues/474](https://github.com/dotnet/roslyn-analyzers/issues/474)
[CA2001](ca2001-avoid-calling-problematic-methods.md) | [https://github.com/dotnet/roslyn-analyzers/issues/477](https://github.com/dotnet/roslyn-analyzers/issues/477)
[CA2004](ca2004-remove-calls-to-gc-keepalive.md) | [https://github.com/dotnet/roslyn-analyzers/issues/479](https://github.com/dotnet/roslyn-analyzers/issues/479)
[CA2006](ca2006-use-safehandle-to-encapsulate-native-resources.md) | [https://github.com/dotnet/roslyn-analyzers/issues/480](https://github.com/dotnet/roslyn-analyzers/issues/480)
[CA2109](ca2109-review-visible-event-handlers.md) | [https://github.com/dotnet/roslyn-analyzers/issues/488](https://github.com/dotnet/roslyn-analyzers/issues/488)
[CA2204](ca2204-literals-should-be-spelled-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/529](https://github.com/dotnet/roslyn-analyzers/issues/529)
[CA2205](ca2205-use-managed-equivalents-of-win32-api.md) | [https://github.com/dotnet/roslyn-analyzers/issues/530](https://github.com/dotnet/roslyn-analyzers/issues/530)
[CA2212](ca2212-do-not-mark-serviced-components-with-webmethod.md) | [https://github.com/dotnet/roslyn-analyzers/issues/534](https://github.com/dotnet/roslyn-analyzers/issues/534)
[CA2215](ca2215-dispose-methods-should-call-base-class-dispose.md) | [https://github.com/dotnet/roslyn-analyzers/issues/535](https://github.com/dotnet/roslyn-analyzers/issues/535)
[CA2232](ca2232-mark-windows-forms-entry-points-with-stathread.md) | [https://github.com/dotnet/roslyn-analyzers/issues/545](https://github.com/dotnet/roslyn-analyzers/issues/545)
[CA2236](ca2236-call-base-class-methods-on-iserializable-types.md) | [https://github.com/dotnet/roslyn-analyzers/issues/548](https://github.com/dotnet/roslyn-analyzers/issues/548)
[CA2238](ca2238-implement-serialization-methods-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/549](https://github.com/dotnet/roslyn-analyzers/issues/549)
[CA2239](ca2239-provide-deserialization-methods-for-optional-fields.md) | [https://github.com/dotnet/roslyn-analyzers/issues/550](https://github.com/dotnet/roslyn-analyzers/issues/550)
[CA2240](ca2240-implement-iserializable-correctly.md) | [https://github.com/dotnet/roslyn-analyzers/issues/551](https://github.com/dotnet/roslyn-analyzers/issues/551)

### <a name="deprecated-rules"></a>已淘汰的規則

下列 FxCop 靜態程式碼分析規則已被取代, 且不會實作為分析器。 如需進一步資訊, 您可以在 [ [roslyn-分析器 GitHub 問題] 頁面](https://github.com/dotnet/roslyn-analyzers/issues?utf8=%E2%9C%93&q=is:issue+label:FxCop-Port)上依據規則識別碼 (例如, **CA1009**) 進行搜尋。

- [CA1009](ca1009-declare-event-handlers-correctly.md)
- [CA1020](ca1020-avoid-namespaces-with-few-types.md)
- [CA1025](ca1025-replace-repetitive-arguments-with-params-array.md)
- [CA1026](ca1026-default-parameters-should-not-be-used.md)
- [CA1035](ca1035-icollection-implementations-have-strongly-typed-members.md)
- [CA1038](ca1038-enumerators-should-be-strongly-typed.md)
- [CA1039](ca1039-lists-are-strongly-typed.md)
- [CA1059](ca1059-members-should-not-expose-certain-concrete-types.md)
- [CA1302](ca1302-do-not-hardcode-locale-specific-strings.md)
- [CA1400](ca1400-p-invoke-entry-points-should-exist.md)
- [CA1406](ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)
- [CA1504](ca1504-review-misleading-field-names.md)
- [CA1701](ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1702](ca1702-compound-words-should-be-cased-correctly.md)
- [CA1703](ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1800](ca1800-do-not-cast-unnecessarily.md)
- [CA1809](ca1809-avoid-excessive-locals.md)
- [CA1901](ca1901-p-invoke-declarations-should-be-portable.md)
- [CA1903](ca1903-use-only-api-from-targeted-framework.md)
- [CA2003](ca2003-do-not-treat-fibers-as-threads.md)
- [CA2102](ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)
- [CA2103](ca2103-review-imperative-security.md)
- [CA2104](ca2104-do-not-declare-read-only-mutable-reference-types.md)
- [CA2105](ca2105-array-fields-should-not-be-read-only.md)
- [CA2106](ca2106-secure-asserts.md)
- [CA2107](ca2107-review-deny-and-permit-only-usage.md)
- [CA2108](ca2108-review-declarative-security-on-value-types.md)
- [CA2111](ca2111-pointers-should-not-be-visible.md)
- [CA2112](ca2112-secured-types-should-not-expose-fields.md)
- [CA2114](ca2114-method-security-should-be-a-superset-of-type.md)
- [CA2115](ca2115-call-gc-keepalive-when-using-native-resources.md)
- [CA2116](ca2116-aptca-methods-should-only-call-aptca-methods.md)
- [CA2117](ca2117-aptca-types-should-only-extend-aptca-base-types.md)
- [CA2118](ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)
- [CA2120](ca2120-secure-serialization-constructors.md)
- [CA2121](ca2121-static-constructors-should-be-private.md)
- [CA2122](ca2122-do-not-indirectly-expose-methods-with-link-demands.md)
- [CA2123](ca2123-override-link-demands-should-be-identical-to-base.md)
- [CA2124](ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)
- [CA2126](ca2126-type-link-demands-require-inheritance-demands.md)
- [CA2130](ca2130-security-critical-constants-should-be-transparent.md)
- [CA2131](ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)
- [CA2132](ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)
- [CA2133](ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)
- [CA2134](ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)
- [CA2135](ca2135-level-2-assemblies-should-not-contain-linkdemands.md)
- [CA2136](ca2136-members-should-not-have-conflicting-transparency-annotations.md)
- [CA2137](ca2137-transparent-methods-must-contain-only-verifiable-il.md)
- [CA2138](ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)
- [CA2139](ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)
- [CA2140](ca2140-transparent-code-must-not-reference-security-critical-items.md)
- [CA2141](ca2141-transparent-methods-must-not-satisfy-linkdemands.md)
- [CA2142](ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)
- [CA2143](ca2143-transparent-methods-should-not-use-security-demands.md)
- [CA2144](ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)
- [CA2145](ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)
- [CA2146](ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)
- [CA2147](ca2147-transparent-methods-may-not-use-security-asserts.md)
- [CA2149](ca2149-transparent-methods-must-not-call-into-native-code.md)
- [CA2151](ca2151-fields-with-critical-types-should-be-security-critical.md)
- [CA2202](ca2202-do-not-dispose-objects-multiple-times.md)
- [CA2210](ca2210-assemblies-should-have-valid-strong-names.md)
- [CA2220](ca2220-finalizers-should-call-base-class-finalizer.md)
- [CA2221](ca2221-finalizers-should-be-protected.md)
- [CA2222](ca2222-do-not-decrease-inherited-member-visibility.md)([理由](https://github.com/dotnet/roslyn-analyzers/issues/1378))
- [CA2223](ca2223-members-should-differ-by-more-than-return-type.md)
- [CA2228](ca2228-do-not-ship-unreleased-resource-formats.md)
- [CA2230](ca2230-use-params-for-variable-arguments.md)
- [CA2233](ca2233-operations-should-not-overflow.md)
- [CA5122](ca5122-p-invoke-declarations-should-not-be-safe-critical.md)

## <a name="see-also"></a>另請參閱

- [CodeAnalysis. FxCopAnalyzers 規則](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)