---
title: 適用於 Managed 程式碼的 Managed 建議規則規則集
ms.date: 11/04/2016
description: 瞭解 Visual Studio 中受管理的建議規則規則集。 查看著重于安全性、穩定性和其他重大問題的規則描述。
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 1d1160f8-4e51-4e70-99cd-82ad10ee7b32
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e691e6dc48b33ff00f6824436b80e5f49721db98
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867902"
---
# <a name="managed-recommended-rules-rule-set-for-managed-code"></a>適用於 Managed 程式碼的 Managed 建議規則規則集

使用 Microsoft 受管理的建議規則規則集，將焦點放在 Managed 程式碼中最嚴重的問題，包括潛在的安全性漏洞、應用程式損毀，以及其他重要的邏輯和設計錯誤。 此規則集會包含「 [受管理的最小規則](managed-minimum-rules-rule-set-for-managed-code.md) 」規則集中的所有規則。

在您為專案建立的任何自訂規則集中包含此規則集。

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
