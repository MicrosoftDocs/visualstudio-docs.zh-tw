---
title: 適用於 Managed 程式碼的基本正確性規則規則集
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 631f0daf-1d42-4c90-a7dc-1a6a9de64c93
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 53d17f51a777c4b39cd5ff8e0a444d1aec56583c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607719"
---
# <a name="basic-correctness-rules-rule-set-for-managed-code"></a>適用於 Managed 程式碼的基本正確性規則規則集

基本正確性規則規則集會著重于邏輯錯誤，以及使用 framework Api 時的常見錯誤。 基本正確性規則包含「[受管理的建議規則](managed-recommended-rules-rule-set-for-managed-code.md)」規則集中的規則。

下表描述 Microsoft 基本正確性規則規則集中的所有規則。

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
|[CA1008](../code-quality/ca1008.md)|列舉值中應該要有值為零的成員|
|[CA1013](../code-quality/ca1013.md)|多載加號和減號運算子時必須一併多載等號比較運算子|
|[CA1303](../code-quality/ca1303.md)|不要將常值當作已當地語系化的參數傳遞|
|[CA1308 必須](../code-quality/ca1308.md)|必須將字串標準化為大寫字母|
|[CA1806](../code-quality/ca1806.md)|不要忽略方法的結果|
|[CA1816](../code-quality/ca1816.md)|正確呼叫 GC.SuppressFinalize|
|[CA1819](../code-quality/ca1819.md)|屬性不應該傳回陣列|
|[CA1820 應該](../code-quality/ca1820.md)|應該使用字串長度測試空白字串|
|[CA1903](../code-quality/ca1903.md)|只使用來自目標架構的 API|
|[CA2004 必須](../code-quality/ca2004.md)|必須移除對 GC.KeepAlive 的呼叫|
|[CA2006](../code-quality/ca2006.md)|必須使用 SafeHandle 封裝原生資源|
|[CA2102](../code-quality/ca2102.md)|必須使用一般處理常式攔截非 CLSCompliant 例外狀況|
|[CA2104](../code-quality/ca2104.md)|不要宣告唯讀的可變動參考類型|
|[CA2105](../code-quality/ca2105.md)|陣列欄位不應該為唯讀|
|[CA2106 必須](../code-quality/ca2106.md)|必須保護判斷提示|
|[CA2115](../code-quality/ca2115.md)|使用原生資源時必須呼叫 GC.KeepAlive|
|[CA2119](../code-quality/ca2119.md)|密封方法以滿足私用介面的要求|
|[CA2120 必須](../code-quality/ca2120.md)|必須保護序列化建構函式|
|[CA2121](../code-quality/ca2121.md)|靜態建構函式應該為私用的|
|[CA2130](../code-quality/ca2130.md)|安全性關鍵常數應該是透明的|
|[CA2205 必須](../code-quality/ca2205.md)|必須使用 Win32 API 的受控對應項|
|[CA2215](../code-quality/ca2215.md)|Dispose 方法應該呼叫基底類別處置|
|[CA2221](../code-quality/ca2221.md)|Finalizer 方法應該為 protected|
|[CA2222](../code-quality/ca2222.md)|不要降低繼承成員的可視性|
|[CA2223](../code-quality/ca2223.md)|成員不應該只有在傳回類型上不同|
|[CA2224](../code-quality/ca2224.md)|多載等號比較運算子時必須一併覆寫 Equals|
|[CA2226](../code-quality/ca2226.md)|運算子應該有對稱的多載|
|[CA2227](../code-quality/ca2227.md)|集合屬性應該為唯讀|
|[CA2239 必須](../code-quality/ca2239.md)|必須為選擇性欄位提供還原序列化方法|
