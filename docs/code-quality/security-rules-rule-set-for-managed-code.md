---
title: 適用於 Managed 程式碼的安全性規則規則集
ms.date: 11/04/2016
description: 瞭解 Visual Studio 舊版程式碼分析的安全性規則規則集。 請參閱著重于潛在安全性問題的規則描述。
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 2568137d5724613b0f5ddf801df6302c85e430f1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859680"
---
# <a name="security-rules-rule-set-for-managed-code"></a>適用於 Managed 程式碼的安全性規則規則集

使用 Microsoft 安全性規則規則集進行舊版程式碼分析，以最大化回報的潛在安全性問題數目。

|規則|Description|
|----------|-----------------|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|必須檢閱 SQL 查詢中是否有安全性弱點|
|[CA2102](../code-quality/ca2102.md)|必須使用一般處理常式攔截非 CLSCompliant 例外狀況|
|[CA2103](../code-quality/ca2103.md)|必須檢閱命令式安全性|
|[CA2104](../code-quality/ca2104.md)|不要宣告唯讀的可變動參考類型|
|[CA2105](../code-quality/ca2105.md)|陣列欄位不應該為唯讀|
|[CA2106 必須](../code-quality/ca2106.md)|必須保護判斷提示|
|[CA2107](../code-quality/ca2107.md)|必須檢閱 Deny 和 Permit Only 的使用方式|
|[CA2108](../code-quality/ca2108.md)|必須檢閱實值類型上的宣告式安全性|
|[CA2109](/dotnet/fundamentals/code-analysis/quality-rules/ca2109)|必須檢閱可見的事件處理常式|
|[CA2111](../code-quality/ca2111.md)|指標不應該為可見的|
|[CA2112](../code-quality/ca2112.md)|受保護類型不應該公開欄位|
|[CA2114](../code-quality/ca2114.md)|方法安全性應該是類型的超集|
|[CA2115](../code-quality/ca2115.md)|使用原生資源時必須呼叫 GC.KeepAlive|
|[CA2116](../code-quality/ca2116.md)|APTCA 方法應該只呼叫 APTCA 方法|
|[CA2117](../code-quality/ca2117.md)|APTCA 類型應該只擴充 APTCA 基底類型|
|[CA2118](../code-quality/ca2118.md)|檢閱 SuppressUnmanagedCodeSecurityAttribute 使用方法|
|[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119)|密封方法以滿足私用介面的要求|
|[CA2120](../code-quality/ca2120.md)|必須保護序列化建構函式|
|[CA2121](../code-quality/ca2121.md)|靜態建構函式應該為私用的|
|[CA2122](../code-quality/ca2122.md)|不要間接公開具有連結要求的方法|
|[CA2123](../code-quality/ca2123.md)|覆寫連結要求應該與基底相同|
|[CA2124](../code-quality/ca2124.md)|必須將有弱點的 finally 子句包裝在外層 try 中|
|[CA2126](../code-quality/ca2126.md)|必須同時具有類型連結要求和繼承要求|
|[CA2130](../code-quality/ca2130.md)|安全性關鍵常數應該是透明的|
|[CA2131](../code-quality/ca2131.md)|安全性關鍵類型可能未參與類型等價|
|[CA2132](../code-quality/ca2132.md)|預設建構函式至少必須和基底類型的預設建構函式一樣關鍵|
|[CA2133](../code-quality/ca2133.md)|委派必須繫結至具有一致透明度的方法|
|[CA2134](../code-quality/ca2134.md)|覆寫基底方法時，方法必須保持一致的透明度|
|[CA2135](../code-quality/ca2135.md)|層級 2 組件不應該包含 LinkDemand|
|[CA2136](../code-quality/ca2136.md)|成員不應該具有衝突的透明度註釋|
|[CA2137](../code-quality/ca2137.md)|透明方法必須只包含可驗證的 IL|
|[CA2138](../code-quality/ca2138.md)|透明方法不可以使用 SuppressUnmanagedCodeSecurity 屬性呼叫方法|
|[CA2139](../code-quality/ca2139.md)|透明方法不能使用 HandleProcessCorruptingExceptions 屬性|
|[CA2140](../code-quality/ca2140.md)|透明程式碼不可以參考安全性關鍵項目|
|[CA2141](../code-quality/ca2141.md)|透明方法不能滿足 Linkdemand|
|[CA2142](../code-quality/ca2142.md)|透明程式碼不可以使用 LinkDemand 加以保護|
|[CA2143](../code-quality/ca2143.md)|透明方法不可以使用安全性要求|
|[CA2144](../code-quality/ca2144.md)|透明程式碼不可以從位元組陣列載入組件|
|[CA2145](../code-quality/ca2145.md)|透明方法不可以使用 SuppressUnmanagedCodeSecurityAttribute 來裝飾|
|[CA2146](../code-quality/ca2146.md)|類型至少必須和基底類型與介面一樣關鍵|
|[CA2147](../code-quality/ca2147.md)|CA2147：透明方法不可以使用安全性判斷提示|
|[CA2149](../code-quality/ca2149.md)|透明方法不可以呼叫機器碼|
|[CA2210](../code-quality/ca2210.md)|組件應該具備有效的強式名稱|
|[CA2300](/dotnet/fundamentals/code-analysis/quality-rules/ca2300)|請勿使用不安全的還原序列化程式 BinaryFormatter|
|[CA2301](/dotnet/fundamentals/code-analysis/quality-rules/ca2301)|未先設定 BinaryFormatter.Binder 之前，請勿呼叫 BinaryFormatter.Deserialize|
|[CA2302](/dotnet/fundamentals/code-analysis/quality-rules/ca2302)|呼叫 BinaryFormatter.Deserialize 之前，請務必先設定 BinaryFormatter.Binder|
|[CA2305](/dotnet/fundamentals/code-analysis/quality-rules/ca2305)|請勿使用不安全的還原序列化程式 LosFormatter|
|[CA2310](/dotnet/fundamentals/code-analysis/quality-rules/ca2310)|請勿使用不安全的還原序列化程式 NetDataContractSerializer|
|[CA2311](/dotnet/fundamentals/code-analysis/quality-rules/ca2311)|未先設定 NetDataContractSerializer.Binder 之前，請勿還原序列化|
|[CA2312](/dotnet/fundamentals/code-analysis/quality-rules/ca2312)|還原序列化之前，請務必先設定 NetDataContractSerializer.Binder|
|[CA2315](/dotnet/fundamentals/code-analysis/quality-rules/ca2315)|請勿使用不安全的還原序列化程式 ObjectStateFormatter|
|[CA2321](/dotnet/fundamentals/code-analysis/quality-rules/ca2321)|請勿使用 SimpleTypeResolver 搭配 JavaScriptSerializer 來還原序列化|
|[CA2322](/dotnet/fundamentals/code-analysis/quality-rules/ca2322)|還原序列化之前，請確定不會使用 SimpleTypeResolver 來將 JavaScriptSerializer 初始化|
|[CA3001](/dotnet/fundamentals/code-analysis/quality-rules/ca3001)|檢閱程式碼是否有 SQL 插入式攻擊弱點|
|[CA3002](/dotnet/fundamentals/code-analysis/quality-rules/ca3002)|檢閱程式碼是否有 XSS 弱點|
|[CA3003](/dotnet/fundamentals/code-analysis/quality-rules/ca3003)|檢閱程式碼是否有檔案路徑插入式攻擊弱點|
|[CA3004](/dotnet/fundamentals/code-analysis/quality-rules/ca3004)|檢閱程式碼是否有資訊洩漏弱點|
|[CA3005](/dotnet/fundamentals/code-analysis/quality-rules/ca3005)|檢閱程式碼是否有 LDAP 插入式攻擊弱點|
|[CA3006](/dotnet/fundamentals/code-analysis/quality-rules/ca3006)|檢閱程式碼是否有處理序命令插入式攻擊弱點|
|[CA3007](/dotnet/fundamentals/code-analysis/quality-rules/ca3007)|檢閱程式碼是否有開放式重新導向弱點|
|[CA3008](/dotnet/fundamentals/code-analysis/quality-rules/ca3008)|檢閱程式碼是否有 XPath 插入式攻擊弱點|
|[CA3009](/dotnet/fundamentals/code-analysis/quality-rules/ca3009)|檢閱程式碼是否有 XML 插入式攻擊弱點|
|[CA3010](/dotnet/fundamentals/code-analysis/quality-rules/ca3010)|檢閱程式碼是否有 XAML 插入式攻擊弱點|
|[CA3011](/dotnet/fundamentals/code-analysis/quality-rules/ca3011)|檢閱程式碼是否有 DLL 插入式攻擊弱點|
|[CA3012](/dotnet/fundamentals/code-analysis/quality-rules/ca3012)|檢閱程式碼是否有 regex 插入式攻擊弱點|
|[CA5358](/dotnet/fundamentals/code-analysis/quality-rules/ca5358)|不要使用不安全的 Cipher 模式|
|[CA5403](/dotnet/fundamentals/code-analysis/quality-rules/ca5403)|不要硬式編碼憑證|