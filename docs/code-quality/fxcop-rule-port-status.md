---
title: FxCop 規則埠狀態
ms.date: 05/21/2019
ms.topic: reference
helpviewer_keywords:
- fxcop rules
- fxcop analyzers, ported rules
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 28429b43295956d29bb9fc04f80ccf7ba1b1e720
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508362"
---
# <a name="fxcop-rule-port-status"></a>Fxcop 規則埠狀態

如果您先前在 Visual Studio 中使用了靜態程式碼分析，您可能會想知道哪些規則在目前的實作為 [FxCop 分析器](install-fxcop-analyzers.md)中可用。 此頁面會列出已移植的規則。 請參閱 [Unported 規則](fxcop-unported-rules.md) ，以瞭解尚未移植的規則，以及是否有規劃將它們移植。

## <a name="ported-rules"></a>移植的規則

Roslyn-分析器存放庫中自動產生的 [檔頁面](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md) ，具有已移植至 FxCop 分析器的最新規則清單。 該頁面也有其他資訊，例如規則是否預設為啟用，以及是否有相關聯的 *程式碼修正*。  ([程式碼修正](../ide/quick-actions.md) 是在 Visual Studio 的燈泡圖示功能表中，可用的單鍵修正。 ) 

從這個頁面的日期開始，已移植至 [fxcop 分析器](install-fxcop-analyzers.md) 的 fxcop 規則清單包括：

規則識別碼 | 標題
--------|---------
[CA1000](ca1000.md) | 不要在泛型類型上宣告靜態成員
[CA1001 具有](ca1001.md) | 具有可處置欄位的類型應該為可處置
[CA1002](ca1002.md) | 不要公開泛型清單
[CA1003](ca1003.md) | 使用一般事件處理常式執行個體
[CA1005](ca1005.md) | 避免在泛型類型上包含過多參數
[CA1008](ca1008.md) | 列舉值中應該要有值為零的成員
[CA1010](ca1010.md) | 集合應該實作泛型介面
[CA1012](ca1012.md) | 抽象類型不應該有建構函式
[CA1014](ca1014.md) | 使用 CLSCompliant 標記元件
[CA1016](ca1016.md) | 標記元件版本的元件
[CA1017](ca1017.md) | 使用 ComVisible 標記元件
[CA1018](ca1018.md) | 必須以 AttributeUsageAttribute 標記屬性
[CA1019 必須](ca1019.md) | 定義屬性引數的存取子
[CA1021](ca1021.md) | 避免使用 out 參數
[CA1024](ca1024.md) | 建議在適當時使用屬性
[CA1027](ca1027.md) | 必須以 FlagsAttribute 標記列舉
[CA1028](ca1028.md) | 列舉儲存體應該是 Int32
[CA1030](ca1030.md) | 建議在適當時使用事件
[CA1031](ca1031.md) | 不要攔截一般例外狀況類型
[CA1032 必須](ca1032.md) | 必須實作標準例外狀況建構函式
[CA1033](ca1033.md) | 介面方法應該要可以由子類型呼叫
[CA1034](ca1034.md) | 巢狀類型不應該為可見的
[CA1036](ca1036.md) | 必須在 Comparable 類型中覆寫方法
[CA1040](ca1040.md) | 避免使用空的介面
[CA1041](ca1041.md) | 必須提供 ObsoleteAttribute 訊息
[CA1043 必須](ca1043.md) | 針對索引子使用整數或字串引數
[CA1044](ca1044.md) | 屬性不應該為唯寫的
[CA1045](ca1045.md) | 不要以傳址方式傳遞類型
[CA1046](ca1046.md) | 不要多載參考類型上的等號比較運算子
[CA1047](ca1047.md) | 不要在密封類型中宣告 protected 成員
[CA1050](ca1050.md) | 類型必須在命名空間中宣告
[CA1051](ca1051.md) | 不要宣告可見的執行個體欄位
[CA1052](ca1052.md) | 靜態預留位置類型應該是靜態或 NotInheritable
[CA1053](ca1053.md) | 靜態預留位置類型不應該有 (CA1053 為 FxCop 分析器 [CA1052](ca1052.md) 一部分的函式) 
[CA1054](ca1054.md) | Uri 參數不應為字串
[CA1055](ca1055.md) | Uri 傳回值不應該為字串
[CA1056](ca1056.md) | Uri 屬性不應為字串
[CA1058](ca1058.md) | 類型不應該擴充特定基底類型
[CA1060](ca1060.md) | 將 pinvokes 移至原生方法類別
[CA1061](ca1061.md) | 不要隱藏基底類別方法
[CA1062](ca1062.md) | 必須驗證公用方法的引數
[CA1063](ca1063.md) | 正確執行 IDisposable
[CA1064](ca1064.md) | 例外狀況必須是公用
[CA1065](ca1065.md) | 不要在非預期的位置中引發例外狀況
[CA1066](ca1066.md) | 類型 {0} 應該執行 IEquatable \<T> ，因為它會覆寫 Equals
[CA1067](ca1067.md) | 執行 IEquatable 時，覆寫物件 Equals (物件) \<T>
[CA1303](ca1303.md) | 不要將常值當作已當地語系化的參數傳遞
[CA1304](ca1304.md) | 必須指定 CultureInfo
[CA1305](ca1305.md) | 必須指定 IFormatProvider
[CA1307](ca1307.md) | 為清楚起見指定 StringComparison
[CA1308 必須](ca1308.md) | 必須將字串標準化為大寫字母
[CA1309](ca1309.md) | 使用序數位符串比較
[CA1401](ca1401.md) | P/Invokes 不應該為可見的
[CA1501](ca1501.md) | 避免在物件間過度繼承
[CA1502](ca1502.md) | 避免造成過度複雜的方法
[CA1505](ca1505.md) | 應避免撰寫無法維護的程式碼
[CA1506](ca1506.md) | 應避免使用結合過度的類別
[CA1700](ca1700.md) | 不要在列舉值名稱中包含 'Reserved'
[CA1707](ca1707.md) | 識別項名稱不應該包含底線
[CA1708](ca1708.md) | 識別項名稱不應該只靠大小寫區別
[CA1710](ca1710.md) | 識別項應該使用正確的後置字元
[CA1711](ca1711.md) | 識別項名稱不應該使用不正確的後置字元
[CA1712](ca1712.md) | 不要使用類型名稱作為列舉值的前置字元
[CA1713](ca1713.md) | 事件不應該有 before 或 after 前置字元
[CA1714](ca1714.md) | 旗標列舉應該使用複數名稱
[CA1715](ca1715.md) | 識別項名稱應該使用正確的前置字元
[CA1716](ca1716.md) | 識別項名稱不應該和關鍵字相符
[CA1717](ca1717.md) | 只有 FlagsAttribute 列舉應該使用複數名稱
[CA1720](ca1720.md) | 識別碼包含類型名稱
[CA1721](ca1721.md) | 屬性名稱不應該和其中有 get 的方法名稱相符
[CA1724](ca1724.md) | 類型名稱不應與命名空間相符
[CA1725](ca1725.md) | 參數名稱應該符合基底類型的宣告
[CA1801 必須](ca1801.md) | 必須檢閱未使用的參數
[CA1802 建議](ca1802.md) | 適當時使用常值
[CA1805](ca1805.md) | 請勿不必要地初始化
[CA1806](ca1806.md) | 不要忽略方法的結果
[CA1810 必須](ca1810.md) | 必須將參考類型內部的靜態欄位初始化
[CA1812](ca1812.md) | 避免使用未執行個體化的內部類別
[CA1813](ca1813.md) | 避免使用非密封屬性
[CA1814](ca1814.md) | 建議使用不規則陣列取代多維陣列
[>CA1815](ca1815.md) | 必須覆寫實值類型上的 Equals 方法和等號比較運算子
[CA1816](ca1816.md) | Dispose 方法應該呼叫 SuppressFinalize
[CA1819](ca1819.md) | 屬性不應該傳回陣列
[CA1820 應該](ca1820.md) | 應該使用字串長度測試空白字串
[CA1821 必須](ca1821.md) | 移除空白的完成項
[CA1822](ca1822.md) | 將成員標記為 static
[CA1823](ca1823.md) | 避免包含未使用的私用欄位
[CA1824](ca1824.md) | 組件必須標記 NeutralResourcesLanguageAttribute
[CA1825](ca1825.md) | 避免長度為零的陣列配置。
[CA2000](ca2000.md) | 必須在超出範圍前處置物件
[CA2002](ca2002.md) | 不要鎖定具有弱式識別的物件
[CA2100 必須](ca2100.md) | 必須檢閱 SQL 查詢中是否有安全性弱點
[CA2101 必須](ca2101.md) | 必須指定 P/Invoke 字串引數的封送處理
[CA2109 必須](ca2109.md) | 必須檢閱可見的事件處理常式
[CA2119](ca2119.md) | 密封方法以滿足私用介面的要求
[CA2153](ca2153.md) | 不要攔截損毀狀態例外狀況
[CA2200](ca2200.md) | 重新擲回以保留堆疊詳細資料。
[CA2201](ca2201.md) | 不要引發保留的例外狀況類型
[CA2207](ca2207.md) | 必須將實值類型的靜態欄位內嵌初始化
[CA2208](ca2208.md) | 必須正確執行個體化引數例外狀況
[CA2211](ca2211.md) | 非常數欄位不應該為可見的
[CA2213](ca2213.md) | 可處置的欄位應該受到處置
[CA2214](ca2214.md) | 不要呼叫建構函式中的可覆寫方法
[CA2215](ca2215.md) | Dispose 方法應該呼叫基底類別處置
[CA2216](ca2216.md) | 可處置的類型應該宣告完成項
[CA2217](ca2217.md) | 不要以 FlagsAttribute 標記列舉
[CA2219](ca2219.md) | 不要在 finally 子句中引發例外狀況
[CA2225](ca2225.md) | 運算子多載必須有具名的替代方法
[CA2226](ca2226.md) | 運算子應該有對稱的多載
[CA2227](ca2227.md) | 集合屬性應該為唯讀
[CA2229](ca2229.md) | 必須實作序列化建構函式
[CA2231](ca2231.md) | 覆寫實數值型別 Equals 上的多載運算子 equals
[CA2234 必須](ca2234.md) | 傳遞系統 uri 物件而非字串
[CA2235 必須](ca2235.md) | 必須標記所有不可序列化的欄位
[CA2237 必須](ca2237.md) | 以可序列化標記 ISerializable 類型
[CA2241](ca2241.md) | 必須提供格式化方法的正確引數
[CA2242](ca2242.md) | 必須正確測試 NaN
[CA2243](ca2243.md) | 屬性字串常值必須正確剖析
[CA2300](ca2300.md) | 請勿使用不安全的還原序列化程式 BinaryFormatter
[CA2301](ca2301.md) | 未先設定 BinaryFormatter.Binder 之前，請勿呼叫 BinaryFormatter.Deserialize
[CA2302](ca2302.md) | 呼叫 BinaryFormatter.Deserialize 之前，請務必先設定 BinaryFormatter.Binder
[CA2305](ca2305.md) | 請勿使用不安全的還原序列化程式 LosFormatter
[CA2310](ca2310.md) | 請勿使用不安全的還原序列化程式 NetDataContractSerializer
[CA2311](ca2311.md) | 未先設定 NetDataContractSerializer.Binder 之前，請勿還原序列化
[CA2312](ca2312.md) | 還原序列化之前，請務必先設定 NetDataContractSerializer.Binder
[CA2315](ca2315.md) | 請勿使用不安全的還原序列化程式 ObjectStateFormatter
[CA2321](ca2321.md) | 請勿使用 SimpleTypeResolver 搭配 JavaScriptSerializer 來還原序列化
[CA2322](ca2322.md) | 還原序列化之前，請確定不會使用 SimpleTypeResolver 來將 JavaScriptSerializer 初始化
[CA3001](ca3001.md) | 檢閱程式碼是否有 SQL 插入式攻擊弱點
[CA3002](ca3002.md) | 檢閱程式碼是否有 XSS 弱點
[CA3003](ca3003.md) | 檢閱程式碼是否有檔案路徑插入式攻擊弱點
[CA3004](ca3004.md) | 檢閱程式碼是否有資訊洩漏弱點
[CA3005](ca3005.md) | 檢閱程式碼是否有 LDAP 插入式攻擊弱點
[CA3006](ca3006.md) | 檢閱程式碼是否有處理序命令插入式攻擊弱點
[CA3007](ca3007.md) | 檢閱程式碼是否有開放式重新導向弱點
[CA3008](ca3008.md) | 檢閱程式碼是否有 XPath 插入式攻擊弱點
[CA3009](ca3009.md) | 檢閱程式碼是否有 XML 插入式攻擊弱點
[CA3010](ca3010.md) | 檢閱程式碼是否有 XAML 插入式攻擊弱點
[CA3011](ca3011.md) | 檢閱程式碼是否有 DLL 插入式攻擊弱點
[CA3012](ca3012.md) | 檢閱程式碼是否有 regex 插入式攻擊弱點
[CA3061](ca3061.md) | 不要依 URL 新增架構
[CA3075](ca3075.md) | XML 中不安全的 DTD 處理
[CA3076](ca3076.md) | 不安全的 XSLT 腳本處理。
[CA3077](ca3077.md) | API 設計、設計和 XmlTextReader 中的不安全處理
[CA3147](ca3147.md) | 使用 Validate Antiforgery Token 標記動詞處理常式
[CA5350](ca5350.md) | 請勿使用弱式密碼編譯演算法
[CA5351](ca5351.md) | 請勿使用中斷的密碼編譯演算法
[CA5358](ca5358.md) | 不要使用不安全的 Cipher 模式
CA5359 | 不要停用憑證驗證
CA5360 | 請勿在還原序列化中呼叫危險的方法
[CA5361](ca5361.md) | 請勿停用安全加密的 SChannel 使用
CA5362 | 請勿在 Serializable 類別中參考自我
[CA5363](ca5363.md) | 請勿停用要求驗證
[CA5364](ca5364.md) | 請勿使用已淘汰的安全性通訊協定
CA5365 | 請勿停用 HTTP 標頭檢查
CA5366 | 針對資料集讀取 Xml 使用 XmlReader
CA5367 | 不要以指標欄位序列化類型
CA5368 | 針對衍生自頁面的類別設定 ViewStateUserKey
[CA5369](ca5369.md) | 使用 XmlReader 進行還原序列化
[CA5370](ca5370.md) | 使用 XmlReader 驗證讀取器
[CA5371](ca5371.md) | 使用 XmlReader 讀取架構
[CA5372](ca5372.md) | 針對 XPathDocument 使用 XmlReader
[CA5373](ca5373.md) | 不使用已過時的金鑰衍生函式
CA5374 | 請勿使用 XslTransform
CA5375 | 請勿使用帳戶共用存取簽章
CA5376 | 使用 SharedAccessProtocol HttpsOnly
CA5377 | 使用容器層級存取原則
[CA5378](ca5378.md) | 請勿停用 ServicePointManagerSecurityProtocols
CA5379 | 不要使用弱式金鑰衍生函數演算法
CA9999 | 分析器版本不符

## <a name="see-also"></a>另請參閱

- [CodeAnalysis. 將 microsoft.codeanalysis.fxcopanalyzers 規則](https://github.com/dotnet/roslyn-analyzers/blob/master/src/Microsoft.CodeAnalysis.FxCopAnalyzers/Microsoft.CodeAnalysis.FxCopAnalyzers.md)
