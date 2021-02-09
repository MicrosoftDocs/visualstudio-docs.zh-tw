---
title: FxCop 規則埠狀態
ms.date: 05/21/2019
description: 瞭解 Visual Studio 中已移植到 .NET 分析器的靜態程式碼分析規則。 查看移植更新上的移植規則和資源。
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- .NET analyzers, ported rules
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: de23f3529cfcd321b0a7c3f9844ac69d96fed9c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860317"
---
# <a name="fxcop-rule-port-status"></a>Fxcop 規則埠狀態

如果您先前在 Visual Studio 中使用了靜態程式碼分析，您可能會想知道哪些規則在目前的執行中是以 [.net 分析器](install-net-analyzers.md)的形式提供。 此頁面會列出已移植的規則。 請參閱 [Unported 規則](fxcop-unported-rules.md) ，以瞭解尚未移植的規則，以及是否有規劃將它們移植。

## <a name="ported-rules"></a>移植的規則

Roslyn-分析器存放庫中自動產生的 [檔頁面](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Microsoft.CodeAnalysis.NetAnalyzers.md) ，具有已移植至 roslyn 分析器的最新規則清單。 該頁面也有其他資訊，例如規則是否預設為啟用，以及是否有相關聯的 *程式碼修正*。  ([程式碼修正](../ide/quick-actions.md) 是在 Visual Studio 的燈泡圖示功能表中，可用的單鍵修正。 ) 

從這個頁面的日期開始，已移植到 [.net 分析器](install-net-analyzers.md) 的 FxCop 規則清單包括：

規則識別碼 | 標題
--------|---------
[CA1000](/dotnet/fundamentals/code-analysis/quality-rules/ca1000) | 不要在泛型類型上宣告靜態成員
[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001) | 具有可處置欄位的類型應該為可處置
[CA1002](/dotnet/fundamentals/code-analysis/quality-rules/ca1002) | 不要公開泛型清單
[CA1003](/dotnet/fundamentals/code-analysis/quality-rules/ca1003) | 使用一般事件處理常式執行個體
[CA1005](/dotnet/fundamentals/code-analysis/quality-rules/ca1005) | 避免在泛型類型上包含過多參數
[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008) | 列舉值中應該要有值為零的成員
[CA1010](/dotnet/fundamentals/code-analysis/quality-rules/ca1010) | 集合應該實作泛型介面
[CA1012](/dotnet/fundamentals/code-analysis/quality-rules/ca1012) | 抽象類型不應該有建構函式
[CA1014](/dotnet/fundamentals/code-analysis/quality-rules/ca1014) | 使用 CLSCompliant 標記元件
[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016) | 標記元件版本的元件
[CA1017](/dotnet/fundamentals/code-analysis/quality-rules/ca1017) | 使用 ComVisible 標記元件
[CA1018](/dotnet/fundamentals/code-analysis/quality-rules/ca1018) | 必須以 AttributeUsageAttribute 標記屬性
[CA1019](/dotnet/fundamentals/code-analysis/quality-rules/ca1019) | 定義屬性引數的存取子
[CA1021](/dotnet/fundamentals/code-analysis/quality-rules/ca1021) | 避免使用 out 參數
[CA1024](/dotnet/fundamentals/code-analysis/quality-rules/ca1024) | 建議在適當時使用屬性
[CA1027](/dotnet/fundamentals/code-analysis/quality-rules/ca1027) | 必須以 FlagsAttribute 標記列舉
[CA1028](/dotnet/fundamentals/code-analysis/quality-rules/ca1028) | 列舉儲存體應該是 Int32
[CA1030](/dotnet/fundamentals/code-analysis/quality-rules/ca1030) | 建議在適當時使用事件
[CA1031](/dotnet/fundamentals/code-analysis/quality-rules/ca1031) | 不要攔截一般例外狀況類型
[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032) | 必須實作標準例外狀況建構函式
[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033) | 介面方法應該要可以由子類型呼叫
[CA1034](/dotnet/fundamentals/code-analysis/quality-rules/ca1034) | 巢狀類型不應該為可見的
[CA1036](/dotnet/fundamentals/code-analysis/quality-rules/ca1036) | 必須在 Comparable 類型中覆寫方法
[CA1040](/dotnet/fundamentals/code-analysis/quality-rules/ca1040) | 避免使用空的介面
[CA1041](/dotnet/fundamentals/code-analysis/quality-rules/ca1041) | 必須提供 ObsoleteAttribute 訊息
[CA1043](/dotnet/fundamentals/code-analysis/quality-rules/ca1043) | 針對索引子使用整數或字串引數
[CA1044](/dotnet/fundamentals/code-analysis/quality-rules/ca1044) | 屬性不應該為唯寫的
[CA1045](/dotnet/fundamentals/code-analysis/quality-rules/ca1045) | 不要以傳址方式傳遞類型
[CA1046](/dotnet/fundamentals/code-analysis/quality-rules/ca1046) | 不要多載參考類型上的等號比較運算子
[CA1047](/dotnet/fundamentals/code-analysis/quality-rules/ca1047) | 不要在密封類型中宣告 protected 成員
[CA1050](/dotnet/fundamentals/code-analysis/quality-rules/ca1050) | 類型必須在命名空間中宣告
[CA1051](/dotnet/fundamentals/code-analysis/quality-rules/ca1051) | 不要宣告可見的執行個體欄位
[CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052) | 靜態預留位置類型應該是靜態或 NotInheritable
[CA1053](/dotnet/fundamentals/code-analysis/quality-rules/ca1053) | 靜態預留位置類型不應該有 (CA1053 為 .NET 分析器 [CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052) 一部分的函式) 
[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054) | Uri 參數不應為字串
[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055) | Uri 傳回值不應該為字串
[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056) | Uri 屬性不應為字串
[CA1058](/dotnet/fundamentals/code-analysis/quality-rules/ca1058) | 類型不應該擴充特定基底類型
[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060) | 將 pinvokes 移至原生方法類別
[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061) | 不要隱藏基底類別方法
[CA1062](/dotnet/fundamentals/code-analysis/quality-rules/ca1062) | 必須驗證公用方法的引數
[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063) | 正確執行 IDisposable
[CA1064](/dotnet/fundamentals/code-analysis/quality-rules/ca1064) | 例外狀況必須是公用
[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065) | 不要在非預期的位置中引發例外狀況
[CA1066](/dotnet/fundamentals/code-analysis/quality-rules/ca1066) | 類型 {0} 應該執行 IEquatable \<T> ，因為它會覆寫 Equals
[CA1067](/dotnet/fundamentals/code-analysis/quality-rules/ca1067) | 執行 IEquatable 時，覆寫物件 Equals (物件) \<T>
[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303) | 不要將常值當作已當地語系化的參數傳遞
[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304) | 必須指定 CultureInfo
[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305) | 必須指定 IFormatProvider
[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307) | 為清楚起見指定 StringComparison
[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308) | 必須將字串標準化為大寫字母
[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309) | 使用序數位符串比較
[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401) | P/Invokes 不應該為可見的
[CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501) | 避免在物件間過度繼承
[CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502) | 避免造成過度複雜的方法
[CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505) | 應避免撰寫無法維護的程式碼
[CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506) | 應避免使用結合過度的類別
[CA1700](/dotnet/fundamentals/code-analysis/quality-rules/ca1700) | 不要在列舉值名稱中包含 'Reserved'
[CA1707](/dotnet/fundamentals/code-analysis/quality-rules/ca1707) | 識別項名稱不應該包含底線
[CA1708](/dotnet/fundamentals/code-analysis/quality-rules/ca1708) | 識別項名稱不應該只靠大小寫區別
[CA1710](/dotnet/fundamentals/code-analysis/quality-rules/ca1710) | 識別項應該使用正確的後置字元
[CA1711](/dotnet/fundamentals/code-analysis/quality-rules/ca1711) | 識別項名稱不應該使用不正確的後置字元
[CA1712](/dotnet/fundamentals/code-analysis/quality-rules/ca1712) | 不要使用類型名稱作為列舉值的前置字元
[CA1713](/dotnet/fundamentals/code-analysis/quality-rules/ca1713) | 事件不應該有 before 或 after 前置字元
[CA1714](/dotnet/fundamentals/code-analysis/quality-rules/ca1714) | 旗標列舉應該使用複數名稱
[CA1715](/dotnet/fundamentals/code-analysis/quality-rules/ca1715) | 識別項名稱應該使用正確的前置字元
[CA1716](/dotnet/fundamentals/code-analysis/quality-rules/ca1716) | 識別項名稱不應該和關鍵字相符
[CA1717](/dotnet/fundamentals/code-analysis/quality-rules/ca1717) | 只有 FlagsAttribute 列舉應該使用複數名稱
[CA1720](/dotnet/fundamentals/code-analysis/quality-rules/ca1720) | 識別碼包含類型名稱
[CA1721](/dotnet/fundamentals/code-analysis/quality-rules/ca1721) | 屬性名稱不應該和其中有 get 的方法名稱相符
[CA1724](/dotnet/fundamentals/code-analysis/quality-rules/ca1724) | 類型名稱不應與命名空間相符
[CA1725](/dotnet/fundamentals/code-analysis/quality-rules/ca1725) | 參數名稱應該符合基底類型的宣告
[CA1801](/dotnet/fundamentals/code-analysis/quality-rules/ca1801) | 必須檢閱未使用的參數
[CA1802](/dotnet/fundamentals/code-analysis/quality-rules/ca1802) | 適當時使用常值
[CA1805](/dotnet/fundamentals/code-analysis/quality-rules/ca1805) | 請勿不必要地初始化
[CA1806](/dotnet/fundamentals/code-analysis/quality-rules/ca1806) | 不要忽略方法的結果
[CA1810](/dotnet/fundamentals/code-analysis/quality-rules/ca1810) | 必須將參考類型內部的靜態欄位初始化
[CA1812](/dotnet/fundamentals/code-analysis/quality-rules/ca1812) | 避免使用未執行個體化的內部類別
[CA1813](/dotnet/fundamentals/code-analysis/quality-rules/ca1813) | 避免使用非密封屬性
[CA1814](/dotnet/fundamentals/code-analysis/quality-rules/ca1814) | 建議使用不規則陣列取代多維陣列
[CA1815](/dotnet/fundamentals/code-analysis/quality-rules/ca1815) | 必須覆寫實值類型上的 Equals 方法和等號比較運算子
[CA1816](/dotnet/fundamentals/code-analysis/quality-rules/ca1816) | Dispose 方法應該呼叫 SuppressFinalize
[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819) | 屬性不應該傳回陣列
[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820) | 應該使用字串長度測試空白字串
[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821) | 移除空白的完成項
[CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) | 將成員標記為 static
[CA1823](/dotnet/fundamentals/code-analysis/quality-rules/ca1823) | 避免包含未使用的私用欄位
[CA1824](/dotnet/fundamentals/code-analysis/quality-rules/ca1824) | 組件必須標記 NeutralResourcesLanguageAttribute
[CA1825](/dotnet/fundamentals/code-analysis/quality-rules/ca1825) | 避免長度為零的陣列配置。
[CA2000](/dotnet/fundamentals/code-analysis/quality-rules/ca2000) | 必須在超出範圍前處置物件
[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002) | 不要鎖定具有弱式識別的物件
[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100) | 必須檢閱 SQL 查詢中是否有安全性弱點
[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101) | 必須指定 P/Invoke 字串引數的封送處理
[CA2109](/dotnet/fundamentals/code-analysis/quality-rules/ca2109) | 必須檢閱可見的事件處理常式
[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119) | 密封方法以滿足私用介面的要求
[CA2153](/dotnet/fundamentals/code-analysis/quality-rules/ca2153) | 不要攔截損毀狀態例外狀況
[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200) | 重新擲回以保留堆疊詳細資料。
[CA2201](/dotnet/fundamentals/code-analysis/quality-rules/ca2201) | 不要引發保留的例外狀況類型
[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207) | 必須將實值類型的靜態欄位內嵌初始化
[CA2208](/dotnet/fundamentals/code-analysis/quality-rules/ca2208) | 必須正確執行個體化引數例外狀況
[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211) | 非常數欄位不應該為可見的
[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213) | 可處置的欄位應該受到處置
[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214) | 不要呼叫建構函式中的可覆寫方法
[CA2215](/dotnet/fundamentals/code-analysis/quality-rules/ca2215) | Dispose 方法應該呼叫基底類別處置
[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216) | 可處置的類型應該宣告完成項
[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217) | 不要以 FlagsAttribute 標記列舉
[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219) | 不要在 finally 子句中引發例外狀況
[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225) | 運算子多載必須有具名的替代方法
[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226) | 運算子應該有對稱的多載
[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227) | 集合屬性應該為唯讀
[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229) | 必須實作序列化建構函式
[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231) | 覆寫實數值型別 Equals 上的多載運算子 equals
[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234) | 傳遞系統 uri 物件而非字串
[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235) | 必須標記所有不可序列化的欄位
[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237) | 以可序列化標記 ISerializable 類型
[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241) | 必須提供格式化方法的正確引數
[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242) | 必須正確測試 NaN
[CA2243](/dotnet/fundamentals/code-analysis/quality-rules/ca2243) | 屬性字串常值必須正確剖析
[CA2300](/dotnet/fundamentals/code-analysis/quality-rules/ca2300) | 請勿使用不安全的還原序列化程式 BinaryFormatter
[CA2301](/dotnet/fundamentals/code-analysis/quality-rules/ca2301) | 未先設定 BinaryFormatter.Binder 之前，請勿呼叫 BinaryFormatter.Deserialize
[CA2302](/dotnet/fundamentals/code-analysis/quality-rules/ca2302) | 呼叫 BinaryFormatter.Deserialize 之前，請務必先設定 BinaryFormatter.Binder
[CA2305](/dotnet/fundamentals/code-analysis/quality-rules/ca2305) | 請勿使用不安全的還原序列化程式 LosFormatter
[CA2310](/dotnet/fundamentals/code-analysis/quality-rules/ca2310) | 請勿使用不安全的還原序列化程式 NetDataContractSerializer
[CA2311](/dotnet/fundamentals/code-analysis/quality-rules/ca2311) | 未先設定 NetDataContractSerializer.Binder 之前，請勿還原序列化
[CA2312](/dotnet/fundamentals/code-analysis/quality-rules/ca2312) | 還原序列化之前，請務必先設定 NetDataContractSerializer.Binder
[CA2315](/dotnet/fundamentals/code-analysis/quality-rules/ca2315) | 請勿使用不安全的還原序列化程式 ObjectStateFormatter
[CA2321](/dotnet/fundamentals/code-analysis/quality-rules/ca2321) | 請勿使用 SimpleTypeResolver 搭配 JavaScriptSerializer 來還原序列化
[CA2322](/dotnet/fundamentals/code-analysis/quality-rules/ca2322) | 還原序列化之前，請確定不會使用 SimpleTypeResolver 來將 JavaScriptSerializer 初始化
[CA3001](/dotnet/fundamentals/code-analysis/quality-rules/ca3001) | 檢閱程式碼是否有 SQL 插入式攻擊弱點
[CA3002](/dotnet/fundamentals/code-analysis/quality-rules/ca3002) | 檢閱程式碼是否有 XSS 弱點
[CA3003](/dotnet/fundamentals/code-analysis/quality-rules/ca3003) | 檢閱程式碼是否有檔案路徑插入式攻擊弱點
[CA3004](/dotnet/fundamentals/code-analysis/quality-rules/ca3004) | 檢閱程式碼是否有資訊洩漏弱點
[CA3005](/dotnet/fundamentals/code-analysis/quality-rules/ca3005) | 檢閱程式碼是否有 LDAP 插入式攻擊弱點
[CA3006](/dotnet/fundamentals/code-analysis/quality-rules/ca3006) | 檢閱程式碼是否有處理序命令插入式攻擊弱點
[CA3007](/dotnet/fundamentals/code-analysis/quality-rules/ca3007) | 檢閱程式碼是否有開放式重新導向弱點
[CA3008](/dotnet/fundamentals/code-analysis/quality-rules/ca3008) | 檢閱程式碼是否有 XPath 插入式攻擊弱點
[CA3009](/dotnet/fundamentals/code-analysis/quality-rules/ca3009) | 檢閱程式碼是否有 XML 插入式攻擊弱點
[CA3010](/dotnet/fundamentals/code-analysis/quality-rules/ca3010) | 檢閱程式碼是否有 XAML 插入式攻擊弱點
[CA3011](/dotnet/fundamentals/code-analysis/quality-rules/ca3011) | 檢閱程式碼是否有 DLL 插入式攻擊弱點
[CA3012](/dotnet/fundamentals/code-analysis/quality-rules/ca3012) | 檢閱程式碼是否有 regex 插入式攻擊弱點
[CA3061](/dotnet/fundamentals/code-analysis/quality-rules/ca3061) | 不要依 URL 新增架構
[CA3075](/dotnet/fundamentals/code-analysis/quality-rules/ca3075) | XML 中不安全的 DTD 處理
[CA3076](/dotnet/fundamentals/code-analysis/quality-rules/ca3076) | 不安全的 XSLT 腳本處理。
[CA3077](/dotnet/fundamentals/code-analysis/quality-rules/ca3077) | API 設計、設計和 XmlTextReader 中的不安全處理
[CA3147](/dotnet/fundamentals/code-analysis/quality-rules/ca3147) | 使用 Validate Antiforgery Token 標記動詞處理常式
[CA5350](/dotnet/fundamentals/code-analysis/quality-rules/ca5350) | 請勿使用弱式密碼編譯演算法
[CA5351](/dotnet/fundamentals/code-analysis/quality-rules/ca5351) | 請勿使用中斷的密碼編譯演算法
[CA5358](/dotnet/fundamentals/code-analysis/quality-rules/ca5358) | 不要使用不安全的 Cipher 模式
CA5359 | 不要停用憑證驗證
CA5360 | 請勿在還原序列化中呼叫危險的方法
[CA5361](/dotnet/fundamentals/code-analysis/quality-rules/ca5361) | 請勿停用安全加密的 SChannel 使用
CA5362 | 請勿在 Serializable 類別中參考自我
[CA5363](/dotnet/fundamentals/code-analysis/quality-rules/ca5363) | 請勿停用要求驗證
[CA5364](/dotnet/fundamentals/code-analysis/quality-rules/ca5364) | 請勿使用已淘汰的安全性通訊協定
CA5365 | 請勿停用 HTTP 標頭檢查
CA5366 | 針對資料集讀取 Xml 使用 XmlReader
CA5367 | 不要以指標欄位序列化類型
CA5368 | 針對衍生自頁面的類別設定 ViewStateUserKey
[CA5369](/dotnet/fundamentals/code-analysis/quality-rules/ca5369) | 使用 XmlReader 進行還原序列化
[CA5370](/dotnet/fundamentals/code-analysis/quality-rules/ca5370) | 使用 XmlReader 驗證讀取器
[CA5371](/dotnet/fundamentals/code-analysis/quality-rules/ca5371) | 使用 XmlReader 讀取架構
[CA5372](/dotnet/fundamentals/code-analysis/quality-rules/ca5372) | 針對 XPathDocument 使用 XmlReader
[CA5373](/dotnet/fundamentals/code-analysis/quality-rules/ca5373) | 不使用已過時的金鑰衍生函式
CA5374 | 請勿使用 XslTransform
CA5375 | 請勿使用帳戶共用存取簽章
CA5376 | 使用 SharedAccessProtocol HttpsOnly
CA5377 | 使用容器層級存取原則
[CA5378](/dotnet/fundamentals/code-analysis/quality-rules/ca5378) | 請勿停用 ServicePointManagerSecurityProtocols
CA5379 | 不要使用弱式金鑰衍生函數演算法
CA9999 | 分析器版本不符

## <a name="see-also"></a>另請參閱

- [.NET 分析器規則](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Microsoft.CodeAnalysis.NetAnalyzers.md)
