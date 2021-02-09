---
title: 適用於 Managed 程式碼的擴充設計方針規則規則集
ms.date: 11/04/2016
description: 瞭解 Visual Studio 中的擴充設計指導方針規則規則集，其著重于可用性和可維護性。 請參閱規則描述。
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: a338caf2-b75d-4f23-a0f9-3024fa0bceac
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 3555014113f84a5e21f21d1ab7d9a658e2c9aa6c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860330"
---
# <a name="extended-design-guidelines-rules-rule-set-for-managed-code"></a>適用於 Managed 程式碼的擴充設計方針規則規則集

Microsoft 擴充設計指導方針規則規則集會擴充基本的設計指導方針規則，以最大化所報告的可用性和可維護性問題。 對命名指導方針有額外的強調。 如果您的專案包含程式庫程式碼，或如果您想要強制撰寫容易維護的程式碼，請考慮包含此規則集。

擴充的設計指導方針規則包含 [基本設計指導方針規則](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md) 規則集中的所有規則，其中包含 [受管理的建議規則](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) 規則集中的規則。

下表說明 Microsoft 擴充設計指導方針規則規則集中的所有規則。

|規則|Description|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|具有可處置欄位的類型應該為可處置|
|[CA1009](../code-quality/ca1009.md)|事件處理常式必須正確宣告|
|[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016)|組件必須標記 AssemblyVersionAttribute|
|[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033)|介面方法應該要可以由子類型呼叫|
|[CA1049](../code-quality/ca1049.md)|具有原生資源的類型應該要可呼叫 Dispose 方法明確釋放資源|
|[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060)|必須將 P/Invokes 移到 NativeMethods 類別|
|[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061)|不要隱藏基底類別方法|
|[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063)|必須正確實作 IDisposable|
|[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065)|不要在非預期的位置中引發例外狀況|
|[CA1301](../code-quality/ca1301.md)|避免使用重複的快速鍵|
|[CA1400](../code-quality/ca1400.md)|P/Invoke 進入點應該要存在|
|[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401)|P/Invokes 不應該為可見的|
|[CA1403](../code-quality/ca1403.md)|自動配置類型不應該是 COM 可見|
|[CA1404](../code-quality/ca1404.md)|必須在 P/Invoke 之後立即呼叫 GetLastError|
|[CA1405](../code-quality/ca1405.md)|COM 可見類型的基底類型應該是 COM 可見|
|[CA1410](../code-quality/ca1410.md)|應該和 COM 註冊方法對應|
|[CA1415](../code-quality/ca1415.md)|P/Invokes 必須正確宣告|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|必須移除空的完成項|
|[CA1900](../code-quality/ca1900.md)|實值類型欄位應該為可移植的|
|[CA1901](../code-quality/ca1901.md)|P/Invoke 宣告應該為可移植的|
|[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002)|不要鎖定具有弱式識別的物件|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|必須檢閱 SQL 查詢中是否有安全性弱點|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|必須指定 P/Invoke 字串引數的封送處理|
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
|[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200)|必須重新擲回以保存堆疊詳細資料|
|[CA2202](../code-quality/ca2202.md)|不要多次處置物件的 Dispose 方法|
|[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207)|必須將實值類型的靜態欄位內嵌初始化|
|[CA2212](../code-quality/ca2212.md)|不要以 WebMethod 標記 Serviced 元件|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|可處置的欄位應該受到處置|
|[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214)|不要呼叫建構函式中的可覆寫方法|
|[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216)|可處置的類型應該宣告完成項|
|[CA2220](../code-quality/ca2220.md)|完成項應該呼叫基底類別完成項|
|[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229)|必須實作序列化建構函式|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|在覆寫 ValueType.Equals 上多載等號運算子|
|[CA2232](../code-quality/ca2232.md)|Windows Forms 進入點必須標記 STAThread|
|[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235)|必須標記所有不可序列化的欄位|
|[CA2236 必須](../code-quality/ca2236.md)|必須呼叫 ISerializable 類型上的基底類別方法|
|[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237)|ISerializable 類型必須標記 SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|必須正確實作序列化方法|
|[CA2240 必須](../code-quality/ca2240.md)|必須正確實作 ISerializable|
|[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241)|必須提供格式化方法的正確引數|
|[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242)|必須正確測試 NaN|
|[CA1000](/dotnet/fundamentals/code-analysis/quality-rules/ca1000)|不要在泛型類型上宣告靜態成員|
|[CA1002](/dotnet/fundamentals/code-analysis/quality-rules/ca1002)|不要公開泛型清單|
|[CA1003](/dotnet/fundamentals/code-analysis/quality-rules/ca1003)|使用一般事件處理常式執行個體|
|[CA1004](../code-quality/ca1004.md)|泛型方法應該提供類型參數|
|[CA1005](/dotnet/fundamentals/code-analysis/quality-rules/ca1005)|避免在泛型類型上包含過多參數|
|[CA1006](../code-quality/ca1006.md)|不要在成員簽章中將泛型類型巢狀化|
|[CA1007](../code-quality/ca1007.md)|建議在適當時使用泛型|
|[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008)|列舉值中應該要有值為零的成員|
|[CA1010](/dotnet/fundamentals/code-analysis/quality-rules/ca1010)|集合應該實作泛型介面|
|[CA1011](../code-quality/ca1011.md)|建議將基底類型當作參數傳遞|
|[CA1012](/dotnet/fundamentals/code-analysis/quality-rules/ca1012)|抽象類型不應該有建構函式|
|[CA1013](../code-quality/ca1013.md)|多載加號和減號運算子時必須一併多載等號比較運算子|
|[CA1014](/dotnet/fundamentals/code-analysis/quality-rules/ca1014)|組件必須標記 CLSCompliantAttribute|
|[CA1017](/dotnet/fundamentals/code-analysis/quality-rules/ca1017)|組件必須標記 ComVisibleAttribute|
|[CA1018](/dotnet/fundamentals/code-analysis/quality-rules/ca1018)|必須以 AttributeUsageAttribute 標記屬性|
|[CA1019](/dotnet/fundamentals/code-analysis/quality-rules/ca1019)|定義屬性引數的存取子|
|[CA1023](../code-quality/ca1023.md)|不應該使用多維索引子|
|[CA1024](/dotnet/fundamentals/code-analysis/quality-rules/ca1024)|建議在適當時使用屬性|
|[CA1025 必須](../code-quality/ca1025.md)|以參數陣列取代重複的引數|
|[CA1026](../code-quality/ca1026.md)|不應該使用預設參數|
|[CA1027](/dotnet/fundamentals/code-analysis/quality-rules/ca1027)|必須以 FlagsAttribute 標記列舉|
|[CA1028](/dotnet/fundamentals/code-analysis/quality-rules/ca1028)|列舉儲存區應該是 Int32|
|[CA1030](/dotnet/fundamentals/code-analysis/quality-rules/ca1030)|建議在適當時使用事件|
|[CA1031](/dotnet/fundamentals/code-analysis/quality-rules/ca1031)|不要攔截一般例外狀況類型|
|[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)|必須實作標準例外狀況建構函式|
|[CA1034](/dotnet/fundamentals/code-analysis/quality-rules/ca1034)|巢狀類型不應該為可見的|
|[CA1035](../code-quality/ca1035.md)|ICollection 的實作有強類型成員|
|[CA1036](/dotnet/fundamentals/code-analysis/quality-rules/ca1036)|必須在 Comparable 類型中覆寫方法|
|[CA1038](../code-quality/ca1038.md)|列舉程式應該是強類型|
|[CA1039](../code-quality/ca1039.md)|清單為強類型|
|[CA1041](/dotnet/fundamentals/code-analysis/quality-rules/ca1041)|必須提供 ObsoleteAttribute 訊息|
|[CA1043](/dotnet/fundamentals/code-analysis/quality-rules/ca1043)|必須針對索引子使用整數或字串引數|
|[CA1044](/dotnet/fundamentals/code-analysis/quality-rules/ca1044)|屬性不應該為唯寫的|
|[CA1046](/dotnet/fundamentals/code-analysis/quality-rules/ca1046)|不要多載參考類型上的等號比較運算子|
|[CA1047](/dotnet/fundamentals/code-analysis/quality-rules/ca1047)|不要在密封類型中宣告 protected 成員|
|[CA1048](../code-quality/ca1048.md)|不要在密封類型中宣告 virtual 成員|
|[CA1050](/dotnet/fundamentals/code-analysis/quality-rules/ca1050)|類型必須在命名空間中宣告|
|[CA1051](/dotnet/fundamentals/code-analysis/quality-rules/ca1051)|不要宣告可見的執行個體欄位|
|[CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052)|靜態預留位置類型應該為密封的|
|[CA1053](/dotnet/fundamentals/code-analysis/quality-rules/ca1053)|靜態預留位置類型不應該包含建構函式|
|[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054)|URI 參數不應該為字串|
|[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055)|URI 傳回值不應該為字串|
|[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056)|URI 屬性不應該為字串|
|[CA1057](../code-quality/ca1057.md)|字串 URI 多載呼叫 System.Uri 多載|
|[CA1058](/dotnet/fundamentals/code-analysis/quality-rules/ca1058)|類型不應該擴充特定基底類型|
|[CA1059](../code-quality/ca1059.md)|成員不應該公開特定的具象類型|
|[CA1064](/dotnet/fundamentals/code-analysis/quality-rules/ca1064)|例外狀況必須是公用|
|[CA1500](../code-quality/ca1500.md)|變數名稱不應該與欄位名稱相符|
|[CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)|避免造成過度複雜的方法|
|[CA1708](/dotnet/fundamentals/code-analysis/quality-rules/ca1708)|識別項名稱不應該只靠大小寫區別|
|[CA1716](/dotnet/fundamentals/code-analysis/quality-rules/ca1716)|識別項名稱不應該和關鍵字相符|
|[CA1801](/dotnet/fundamentals/code-analysis/quality-rules/ca1801)|必須檢閱未使用的參數|
|[CA1804 必須](../code-quality/ca1804.md)|必須移除未使用的區域變數|
|[CA1809](../code-quality/ca1809.md)|避免在方法中包含過多區域變數|
|[CA1810](/dotnet/fundamentals/code-analysis/quality-rules/ca1810)|必須將參考類型內部的靜態欄位初始化|
|[CA1811](../code-quality/ca1811.md)|避免使用未呼叫的私用程式碼|
|[CA1812](/dotnet/fundamentals/code-analysis/quality-rules/ca1812)|避免使用未執行個體化的內部類別|
|[CA1813](/dotnet/fundamentals/code-analysis/quality-rules/ca1813)|避免使用非密封屬性|
|[CA1814](/dotnet/fundamentals/code-analysis/quality-rules/ca1814)|建議使用不規則陣列取代多維陣列|
|[CA1815](/dotnet/fundamentals/code-analysis/quality-rules/ca1815)|必須覆寫實值類型上的 Equals 方法和等號比較運算子|
|[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819)|屬性不應該傳回陣列|
|[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820)|應該使用字串長度測試空白字串|
|[CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822)|將成員標記為 static|
|[CA1823](/dotnet/fundamentals/code-analysis/quality-rules/ca1823)|避免包含未使用的私用欄位|
|[CA2201](/dotnet/fundamentals/code-analysis/quality-rules/ca2201)|不要引發保留的例外狀況類型|
|[CA2205 必須](../code-quality/ca2205.md)|必須使用 Win32 API 的受控對應項|
|[CA2208](/dotnet/fundamentals/code-analysis/quality-rules/ca2208)|必須正確執行個體化引數例外狀況|
|[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211)|非常數欄位不應該為可見的|
|[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217)|不要以 FlagsAttribute 標記列舉|
|[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219)|不要在 exception 子句中引發例外狀況|
|[CA2221](../code-quality/ca2221.md)|Finalizer 方法應該為 protected|
|[CA2222](../code-quality/ca2222.md)|不要降低繼承成員的可視性|
|[CA2223](../code-quality/ca2223.md)|成員不應該只有在傳回類型上不同|
|[CA2224](../code-quality/ca2224.md)|多載等號比較運算子時必須一併覆寫 Equals|
|[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225)|運算子多載必須有具名的替代方法|
|[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226)|運算子應該有對稱的多載|
|[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227)|集合屬性應該為唯讀|
|[CA2230](../code-quality/ca2230.md)|必須使用 params 作為變數引數|
|[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234)|必須傳遞 System.Uri 物件而非字串|
|[CA2239 必須](../code-quality/ca2239.md)|必須為選擇性欄位提供還原序列化方法|
|[CA1020](../code-quality/ca1020.md)|避免在命名空間中包含過少的類型|
|[CA1021](/dotnet/fundamentals/code-analysis/quality-rules/ca1021)|避免使用 out 參數|
|[CA1040](/dotnet/fundamentals/code-analysis/quality-rules/ca1040)|避免使用空的介面|
|[CA1045](/dotnet/fundamentals/code-analysis/quality-rules/ca1045)|不要以傳址方式傳遞類型|
|[CA1062](/dotnet/fundamentals/code-analysis/quality-rules/ca1062)|必須驗證公用方法的引數|
|[CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501)|避免在物件間過度繼承|
|[CA1504 必須](../code-quality/ca1504.md)|必須檢閱可能造成誤導的欄位名稱|
|[CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505)|應避免撰寫無法維護的程式碼|
|[CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506)|應避免使用結合過度的類別|
|[CA1700](/dotnet/fundamentals/code-analysis/quality-rules/ca1700)|不要在列舉值名稱中包含 'Reserved'|
|[CA1701](../code-quality/ca1701.md)|資源字串複合字應該使用正確的大小寫|
|[CA1702](../code-quality/ca1702.md)|複合字應該使用正確的大小寫|
|[CA1703](../code-quality/ca1703.md)|資源字串應該使用正確的拼字|
|[CA1704](../code-quality/ca1704.md)|識別項應該使用正確的拼字|
|[CA1707](/dotnet/fundamentals/code-analysis/quality-rules/ca1707)|識別項名稱不應該包含底線|
|[CA1709](../code-quality/ca1709.md)|識別項名稱應該使用正確的大小寫|
|[CA1710](/dotnet/fundamentals/code-analysis/quality-rules/ca1710)|識別項應該使用正確的後置字元|
|[CA1711](/dotnet/fundamentals/code-analysis/quality-rules/ca1711)|識別項名稱不應該使用不正確的後置字元|
|[CA1712](/dotnet/fundamentals/code-analysis/quality-rules/ca1712)|不要使用類型名稱作為列舉值的前置字元|
|[CA1713](/dotnet/fundamentals/code-analysis/quality-rules/ca1713)|事件不應該有 before 或 after 前置字元|
|[CA1714](/dotnet/fundamentals/code-analysis/quality-rules/ca1714)|旗標列舉應該使用複數名稱|
|[CA1715](/dotnet/fundamentals/code-analysis/quality-rules/ca1715)|識別項名稱應該使用正確的前置字元|
|[CA1717](/dotnet/fundamentals/code-analysis/quality-rules/ca1717)|只有 FlagsAttribute 列舉應該使用複數名稱|
|[CA1719](../code-quality/ca1719.md)|參數名稱不應該和成員名稱相符|
|[CA1720](/dotnet/fundamentals/code-analysis/quality-rules/ca1720)|識別項名稱不應該包含類型名稱|
|[CA1721](/dotnet/fundamentals/code-analysis/quality-rules/ca1721)|屬性名稱不應該和其中有 get 的方法名稱相符|
|[CA1722](../code-quality/ca1722.md)|識別項名稱不應該使用不正確的前置字元|
|[CA1724](/dotnet/fundamentals/code-analysis/quality-rules/ca1724)|類型名稱不應該和命名空間相符|
|[CA1725](/dotnet/fundamentals/code-analysis/quality-rules/ca1725)|參數名稱應該符合基底類型的宣告|
|[CA1726 建議](../code-quality/ca1726.md)|建議使用慣用詞彙|
|[CA2204](../code-quality/ca2204.md)|常值必須使用正確的拼字|
