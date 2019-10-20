---
title: 適用於 Managed 程式碼的擴充設計方針規則規則集
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: a338caf2-b75d-4f23-a0f9-3024fa0bceac
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f1063b65c0b82900edf2b13010b9aa55139970dd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649639"
---
# <a name="extended-design-guidelines-rules-rule-set-for-managed-code"></a>適用於 Managed 程式碼的擴充設計方針規則規則集

Microsoft 擴充設計指導方針規則規則集會擴充基本的設計指導方針規則，以最大化所報告的可用性和可維護性問題。 額外的強調會放在命名指導方針上。 如果您的專案包含程式庫程式碼，或者您想要強制最高的標準來撰寫容易維護的程式碼，您應該考慮包含這個規則集。

擴充的設計指導方針規則包含[基本設計方針規則](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)規則集中的所有規則，其中包括[受管理的建議規則](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)規則集內的規則。

下表描述 Microsoft 擴充設計指導方針規則規則集中的所有規則。

|規則|描述|
|----------|-----------------|
|[CA1001 具有](../code-quality/ca1001.md)|具有可處置欄位的類型應該為可處置|
|[CA1009](../code-quality/ca1009.md)|事件處理常式必須正確宣告|
|[CA1016](../code-quality/ca1016.md)|組件必須標記 AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033.md)|介面方法應該要可以由子類型呼叫|
|[CA1049](../code-quality/ca1049.md)|具有原生資源的類型應該要可呼叫 Dispose 方法明確釋放資源|
|[CA1060](../code-quality/ca1060.md)|必須將 P/Invokes 移到 NativeMethods 類別|
|[CA1061](../code-quality/ca1061.md)|不要隱藏基底類別方法|
|[CA1063 必須](../code-quality/ca1063.md)|必須正確實作 IDisposable|
|[CA1065](../code-quality/ca1065.md)|不要在非預期的位置中引發例外狀況|
|[CA1301](../code-quality/ca1301.md)|避免使用重複的快速鍵|
|[CA1400](../code-quality/ca1400.md)|P/Invoke 進入點應該要存在|
|[CA1401](../code-quality/ca1401.md)|P/Invokes 不應該為可見的|
|[CA1403](../code-quality/ca1403.md)|自動配置類型不應該是 COM 可見|
|[CA1404 必須](../code-quality/ca1404.md)|必須在 P/Invoke 之後立即呼叫 GetLastError|
|[CA1405](../code-quality/ca1405.md)|COM 可見類型的基底類型應該是 COM 可見|
|[CA1410](../code-quality/ca1410.md)|應該和 COM 註冊方法對應|
|[CA1415](../code-quality/ca1415.md)|P/Invokes 必須正確宣告|
|[CA1821 必須](../code-quality/ca1821.md)|必須移除空的完成項|
|[CA1900 實](../code-quality/ca1900.md)|實值類型欄位應該為可移植的|
|[CA1901](../code-quality/ca1901.md)|P/Invoke 宣告應該為可移植的|
|[CA2002](../code-quality/ca2002.md)|不要鎖定具有弱式識別的物件|
|[CA2100 必須](../code-quality/ca2100.md)|必須檢閱 SQL 查詢中是否有安全性弱點|
|[CA2101 必須](../code-quality/ca2101.md)|必須指定 P/Invoke 字串引數的封送處理|
|[CA2108](../code-quality/ca2108.md)|必須檢閱實值類型上的宣告式安全性|
|[CA2111](../code-quality/ca2111.md)|指標不應該為可見的|
|[CA2112](../code-quality/ca2112.md)|受保護類型不應該公開欄位|
|[CA2114](../code-quality/ca2114.md)|方法安全性應該是類型的超集|
|[CA2116](../code-quality/ca2116.md)|APTCA 方法應該只呼叫 APTCA 方法|
|[CA2117](../code-quality/ca2117.md)|APTCA 類型應該只擴充 APTCA 基底類型|
|[CA2122](../code-quality/ca2122.md)|不要間接公開具有連結要求的方法|
|[CA2123](../code-quality/ca2123.md)|覆寫連結要求應該與基底相同|
|[CA2124](../code-quality/ca2124.md)|必須將有弱點的 finally 子句包裝在外層 try 中|
|[CA2126](../code-quality/ca2126.md)|必須同時具有類型連結要求和繼承要求|
|[CA2131](../code-quality/ca2131.md)|安全性關鍵類型可能未參與類型等價|
|[CA2132](../code-quality/ca2132.md)|預設建構函式至少必須和基底類型的預設建構函式一樣關鍵|
|[CA2133](../code-quality/ca2133.md)|委派必須繫結至具有一致透明度的方法|
|[CA2134](../code-quality/ca2134.md)|覆寫基底方法時，方法必須保持一致的透明度|
|[CA2137](../code-quality/ca2137.md)|透明方法必須只包含可驗證的 IL|
|[CA2138](../code-quality/ca2138.md)|透明方法不可以使用 SuppressUnmanagedCodeSecurity 屬性呼叫方法|
|[CA2140](../code-quality/ca2140.md)|透明程式碼不可以參考安全性關鍵項目|
|[CA2141](../code-quality/ca2141.md)|透明方法不能滿足 Linkdemand|
|[CA2146](../code-quality/ca2146.md)|類型至少必須和基底類型與介面一樣關鍵|
|[CA2147](../code-quality/ca2147.md)|CA2147：透明方法不可以使用安全性判斷提示|
|[CA2149](../code-quality/ca2149.md)|透明方法不可以呼叫機器碼|
|[CA2200](../code-quality/ca2200.md)|必須重新擲回以保存堆疊詳細資料|
|[CA2202](../code-quality/ca2202.md)|不要多次處置物件的 Dispose 方法|
|[CA2207](../code-quality/ca2207.md)|必須將實值類型的靜態欄位內嵌初始化|
|[CA2212](../code-quality/ca2212.md)|不要以 WebMethod 標記 Serviced 元件|
|[CA2213](../code-quality/ca2213.md)|可處置的欄位應該受到處置|
|[CA2214](../code-quality/ca2214.md)|不要呼叫建構函式中的可覆寫方法|
|[CA2216](../code-quality/ca2216.md)|可處置的類型應該宣告完成項|
|[CA2220](../code-quality/ca2220.md)|完成項應該呼叫基底類別完成項|
|[CA2229](../code-quality/ca2229.md)|必須實作序列化建構函式|
|[CA2231](../code-quality/ca2231.md)|在覆寫 ValueType.Equals 上多載等號運算子|
|[CA2232](../code-quality/ca2232.md)|Windows Forms 進入點必須標記 STAThread|
|[CA2235 必須](../code-quality/ca2235.md)|必須標記所有不可序列化的欄位|
|[CA2236 必須](../code-quality/ca2236.md)|必須呼叫 ISerializable 類型上的基底類別方法|
|[CA2237 必須](../code-quality/ca2237.md)|ISerializable 類型必須標記 SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|必須正確實作序列化方法|
|[CA2240 必須](../code-quality/ca2240.md)|必須正確實作 ISerializable|
|[CA2241 必須](../code-quality/ca2241.md)|必須提供格式化方法的正確引數|
|[CA2242 必須](../code-quality/ca2242.md)|必須正確測試 NaN|
|[CA1000](../code-quality/ca1000.md)|不要在泛型類型上宣告靜態成員|
|[CA1002](../code-quality/ca1002.md)|不要公開泛型清單|
|[CA1003 必須](../code-quality/ca1003.md)|使用一般事件處理常式執行個體|
|[CA1004](../code-quality/ca1004.md)|泛型方法應該提供類型參數|
|[CA1005](../code-quality/ca1005.md)|避免在泛型類型上包含過多參數|
|[CA1006](../code-quality/ca1006.md)|不要在成員簽章中將泛型類型巢狀化|
|[CA1007 建議](../code-quality/ca1007.md)|建議在適當時使用泛型|
|[CA1008](../code-quality/ca1008.md)|列舉值中應該要有值為零的成員|
|[CA1010](../code-quality/ca1010.md)|集合應該實作泛型介面|
|[CA1011](../code-quality/ca1011.md)|建議將基底類型當作參數傳遞|
|[CA1012](../code-quality/ca1012.md)|抽象類型不應該有建構函式|
|[CA1013](../code-quality/ca1013.md)|多載加號和減號運算子時必須一併多載等號比較運算子|
|[CA1014](../code-quality/ca1014.md)|組件必須標記 CLSCompliantAttribute|
|[CA1017](../code-quality/ca1017.md)|組件必須標記 ComVisibleAttribute|
|[CA1018](../code-quality/ca1018.md)|必須以 AttributeUsageAttribute 標記屬性|
|[CA1019 必須](../code-quality/ca1019.md)|定義屬性引數的存取子|
|[CA1023](../code-quality/ca1023.md)|不應該使用多維索引子|
|[CA1024 建議](../code-quality/ca1024.md)|建議在適當時使用屬性|
|[CA1025 必須](../code-quality/ca1025.md)|以參數陣列取代重複的引數|
|[CA1026](../code-quality/ca1026.md)|不應該使用預設參數|
|[CA1027 必須](../code-quality/ca1027.md)|必須以 FlagsAttribute 標記列舉|
|[CA1028](../code-quality/ca1028.md)|列舉儲存區應該是 Int32|
|[CA1030 建議](../code-quality/ca1030.md)|建議在適當時使用事件|
|[CA1031](../code-quality/ca1031.md)|不要攔截一般例外狀況類型|
|[CA1032 必須](../code-quality/ca1032.md)|必須實作標準例外狀況建構函式|
|[CA1034](../code-quality/ca1034.md)|巢狀類型不應該為可見的|
|[CA1035](../code-quality/ca1035.md)|ICollection 的實作有強類型成員|
|[CA1036 必須](../code-quality/ca1036.md)|必須在 Comparable 類型中覆寫方法|
|[CA1038](../code-quality/ca1038.md)|列舉程式應該是強類型|
|[CA1039](../code-quality/ca1039.md)|清單為強類型|
|[CA1041](../code-quality/ca1041.md)|必須提供 ObsoleteAttribute 訊息|
|[CA1043 必須](../code-quality/ca1043.md)|必須針對索引子使用整數或字串引數|
|[CA1044](../code-quality/ca1044.md)|屬性不應該為唯寫的|
|[CA1046](../code-quality/ca1046.md)|不要多載參考類型上的等號比較運算子|
|[CA1047](../code-quality/ca1047.md)|不要在密封類型中宣告 protected 成員|
|[CA1048](../code-quality/ca1048.md)|不要在密封類型中宣告 virtual 成員|
|[CA1050](../code-quality/ca1050.md)|類型必須在命名空間中宣告|
|[CA1051](../code-quality/ca1051.md)|不要宣告可見的執行個體欄位|
|[CA1052](../code-quality/ca1052.md)|靜態預留位置類型應該為密封的|
|[CA1053](../code-quality/ca1053.md)|靜態預留位置類型不應該包含建構函式|
|[CA1054](../code-quality/ca1054.md)|URI 參數不應該為字串|
|[CA1055](../code-quality/ca1055.md)|URI 傳回值不應該為字串|
|[CA1056](../code-quality/ca1056.md)|URI 屬性不應該為字串|
|[CA1057](../code-quality/ca1057.md)|字串 URI 多載呼叫 System.Uri 多載|
|[CA1058](../code-quality/ca1058.md)|類型不應該擴充特定基底類型|
|[CA1059](../code-quality/ca1059.md)|成員不應該公開特定的具象類型|
|[CA1064](../code-quality/ca1064.md)|例外狀況必須是公用|
|[CA1500](../code-quality/ca1500.md)|變數名稱不應該與欄位名稱相符|
|[CA1502](../code-quality/ca1502.md)|避免造成過度複雜的方法|
|[CA1708](../code-quality/ca1708.md)|識別項名稱不應該只靠大小寫區別|
|[CA1716](../code-quality/ca1716.md)|識別項名稱不應該和關鍵字相符|
|[CA1801 必須](../code-quality/ca1801.md)|必須檢閱未使用的參數|
|[CA1804 必須](../code-quality/ca1804.md)|必須移除未使用的區域變數|
|[CA1809](../code-quality/ca1809.md)|避免在方法中包含過多區域變數|
|[CA1810 必須](../code-quality/ca1810.md)|必須將參考類型內部的靜態欄位初始化|
|[CA1811](../code-quality/ca1811.md)|避免使用未呼叫的私用程式碼|
|[CA1812](../code-quality/ca1812.md)|避免使用未執行個體化的內部類別|
|[CA1813](../code-quality/ca1813.md)|避免使用非密封屬性|
|[CA1814](../code-quality/ca1814.md)|建議使用不規則陣列取代多維陣列|
|[CA1815](../code-quality/ca1815.md)|必須覆寫實值類型上的 Equals 方法和等號比較運算子|
|[CA1819](../code-quality/ca1819.md)|屬性不應該傳回陣列|
|[CA1820 應該](../code-quality/ca1820.md)|應該使用字串長度測試空白字串|
|[CA1822](../code-quality/ca1822.md)|將成員標記為 static|
|[CA1823](../code-quality/ca1823.md)|避免包含未使用的私用欄位|
|[CA2201](../code-quality/ca2201.md)|不要引發保留的例外狀況類型|
|[CA2205 必須](../code-quality/ca2205.md)|必須使用 Win32 API 的受控對應項|
|[CA2208](../code-quality/ca2208.md)|必須正確執行個體化引數例外狀況|
|[CA2211](../code-quality/ca2211.md)|非常數欄位不應該為可見的|
|[CA2217](../code-quality/ca2217.md)|不要以 FlagsAttribute 標記列舉|
|[CA2219](../code-quality/ca2219.md)|不要在 exception 子句中引發例外狀況|
|[CA2221](../code-quality/ca2221.md)|Finalizer 方法應該為 protected|
|[CA2222](../code-quality/ca2222.md)|不要降低繼承成員的可視性|
|[CA2223](../code-quality/ca2223.md)|成員不應該只有在傳回類型上不同|
|[CA2224](../code-quality/ca2224.md)|多載等號比較運算子時必須一併覆寫 Equals|
|[CA2225](../code-quality/ca2225.md)|運算子多載必須有具名的替代方法|
|[CA2226](../code-quality/ca2226.md)|運算子應該有對稱的多載|
|[CA2227](../code-quality/ca2227.md)|集合屬性應該為唯讀|
|[CA2230 必須](../code-quality/ca2230.md)|必須使用 params 作為變數引數|
|[CA2234 必須](../code-quality/ca2234.md)|必須傳遞 System.Uri 物件而非字串|
|[CA2239 必須](../code-quality/ca2239.md)|必須為選擇性欄位提供還原序列化方法|
|[CA1020](../code-quality/ca1020.md)|避免在命名空間中包含過少的類型|
|[CA1021](../code-quality/ca1021.md)|避免使用 out 參數|
|[CA1040](../code-quality/ca1040.md)|避免使用空的介面|
|[CA1045](../code-quality/ca1045.md)|不要以傳址方式傳遞類型|
|[CA1062](../code-quality/ca1062.md)|必須驗證公用方法的引數|
|[CA1501](../code-quality/ca1501.md)|避免在物件間過度繼承|
|[CA1504 必須](../code-quality/ca1504.md)|必須檢閱可能造成誤導的欄位名稱|
|[CA1505](../code-quality/ca1505.md)|應避免撰寫無法維護的程式碼|
|[CA1506](../code-quality/ca1506.md)|應避免使用結合過度的類別|
|[CA1700](../code-quality/ca1700.md)|不要在列舉值名稱中包含 'Reserved'|
|[CA1701](../code-quality/ca1701.md)|資源字串複合字應該使用正確的大小寫|
|[CA1702](../code-quality/ca1702.md)|複合字應該使用正確的大小寫|
|[CA1703](../code-quality/ca1703.md)|資源字串應該使用正確的拼字|
|[CA1704](../code-quality/ca1704.md)|識別項應該使用正確的拼字|
|[CA1707](../code-quality/ca1707.md)|識別項名稱不應該包含底線|
|[CA1709](../code-quality/ca1709.md)|識別項名稱應該使用正確的大小寫|
|[CA1710](../code-quality/ca1710.md)|識別項應該使用正確的後置字元|
|[CA1711](../code-quality/ca1711.md)|識別項名稱不應該使用不正確的後置字元|
|[CA1712](../code-quality/ca1712.md)|不要使用類型名稱作為列舉值的前置字元|
|[CA1713](../code-quality/ca1713.md)|事件不應該有 before 或 after 前置字元|
|[CA1714](../code-quality/ca1714.md)|旗標列舉應該使用複數名稱|
|[CA1715](../code-quality/ca1715.md)|識別項名稱應該使用正確的前置字元|
|[CA1717](../code-quality/ca1717.md)|只有 FlagsAttribute 列舉應該使用複數名稱|
|[CA1719](../code-quality/ca1719.md)|參數名稱不應該和成員名稱相符|
|[CA1720](../code-quality/ca1720.md)|識別項名稱不應該包含類型名稱|
|[CA1721](../code-quality/ca1721.md)|屬性名稱不應該和其中有 get 的方法名稱相符|
|[CA1722](../code-quality/ca1722.md)|識別項名稱不應該使用不正確的前置字元|
|[CA1724](../code-quality/ca1724.md)|類型名稱不應該和命名空間相符|
|[CA1725](../code-quality/ca1725.md)|參數名稱應該符合基底類型的宣告|
|[CA1726 建議](../code-quality/ca1726.md)|建議使用慣用詞彙|
|[CA2204](../code-quality/ca2204.md)|常值必須使用正確的拼字|
