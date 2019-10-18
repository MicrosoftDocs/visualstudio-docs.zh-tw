---
title: 用法警告
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- warnings, usage
- managed code analysis warnings, usage warnings
- usage warnings
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f58701cbebb4b738b635fac0c2805f07b4a5266f
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349548"
---
# <a name="usage-warnings"></a>用法警告

使用警告支援適當的 .NET 使用方式。

## <a name="in-this-section"></a>本章節內容

|規則|描述|
|----------|-----------------|
|[CA1801：必須檢閱未使用的參數](../code-quality/ca1801.md)|方法簽章包括不用於方法主體中的參數；|
|[CA1806：不要忽略方法的結果](../code-quality/ca1806.md)|已建立但從未使用新物件、已呼叫會建立並傳回新字串的方法，而新字串從未使用過，或者 COM 或 P/Invoke 方法傳回從未使用的 HRESULT 或錯誤碼。|
|[CA1816：正確呼叫 GC.SuppressFinalize](../code-quality/ca1816.md)|執行 Dispose 的方法不會呼叫 GC。Gc.suppressfinalize或不是 Dispose 呼叫 GC 的方法。Gc.suppressfinalize或方法會呼叫 GC。Gc.suppressfinalize 並傳遞這個以外的東西（我在 Visual Basic）。|
|[CA2200：必須重新擲回以保存堆疊詳細資料](../code-quality/ca2200.md)|例外狀況遭到重新擲回，而且已在 throw 陳述式中明確指定此例外狀況。 如果例外狀況是透過在陳述式中指定例外狀況而重新擲回，則會遺失在擲回例外狀況之原始方法和目前方法之間呼叫的方法清單。|
|[CA2201：不要引發保留的例外狀況類型](../code-quality/ca2201.md)|這會讓原始錯誤難以偵測和 debug。|
|[CA2202：不要多次處置物件](../code-quality/ca2202.md)|方法實作包含程式碼路徑，可在相同物件上造成多個 System.IDisposable.Dispose 呼叫或 Dispose 對等用法 (例如，部分類型上的 Close() 方法)。|
|[CA2204：常值必須使用正確的拼字](../code-quality/ca2204.md)|方法主體中的常值 (Literal) 字串包含一個或多個 Microsoft 拼字檢查程式庫無法辨識的字。|
|[CA2205：必須使用 Win32 API 的 Managed 對應項](../code-quality/ca2205.md)|已定義平台叫用方法，並提供具有對等功能的 .NET 方法。|
|[CA2207：必須初始化實值型別的靜態欄位內嵌](../code-quality/ca2207.md)|實值類型會宣告明確的靜態建構函式。 若要修正此規則的違規情形，請在宣告所有靜態資料時將靜態資料初始化，並移除靜態建構函式。|
|[CA2208：必須正確具現化引數例外狀況](../code-quality/ca2208.md)|對例外狀況類型為 (或衍生自) ArgumentException 的預設 (無參數) 建構函式進行呼叫，或將錯誤的字串引數傳遞至例外狀況類型為 (或衍生自) ArgumentException 的參數化建構函式。|
|[CA2211：非常數欄位不應該為可見的](../code-quality/ca2211.md)|不是常數或唯讀的靜態欄位不是安全線程。 對這類欄位的存取權必須謹慎控制，而且需要先進的程式設計技巧來同步處理對類別物件的存取。|
|[CA2212：不要以 WebMethod 標記 Serviced 元件](../code-quality/ca2212.md)|類型中繼承自 System.enterpriseservices. ServicedComponent 的方法會以 WebMethodAttribute 的標記。 因為 WebMethodAttribute 和 ServicedComponent 方法具有衝突的內容和異動流程的行為及需求，所以方法的行為在某些情節中會是不正確的。|
|[CA2213：可處置的欄位應該受到處置](../code-quality/ca2213.md)|實作 System.IDisposable 的類型宣告了也實作 IDisposable 之類型的欄位。 宣告類型的 Dispose 方法不會呼叫欄位的 Dispose 方法。|
|[CA2214：不要呼叫建構函式中的可覆寫方法](../code-quality/ca2214.md)|當函式呼叫虛擬方法時，叫用方法之實例的函式可能尚未執行。|
|[CA2215：Dispose 方法應該呼叫基底類別處置](../code-quality/ca2215.md)|如果類型會繼承自可處置的類型，則必須從本身的 Dispose 方法呼叫基底類型的 Dispose 方法。|
|[CA2216：可處置的類型應該宣告完成項](../code-quality/ca2216.md)|一種 IDisposable 的型別，其中包含建議使用非受控資源的欄位，並不會依照物件的說明來執行完成項。|
|[CA2217：不要以 FlagsAttribute 標記列舉](../code-quality/ca2217.md)|外部可見列舉會以 FlagsAttribute 標記，而且有一或多個值不是兩個的乘冪，或在列舉上有其他已定義值的組合。|
|[CA2218：覆寫 Equals 時必須一併覆寫 GetHashCode](../code-quality/ca2218.md)|GetHashCode 會依據目前執行個體傳回值，適用於雜湊演算法和資料結構，如雜湊資料表。 兩個類型相同且相等的物件必須傳回相同的雜湊程式碼。|
|[CA2219：不要在 exception 子句中引發例外狀況](../code-quality/ca2219.md)|在 finally 或 fault 子句中引發例外狀況時，新的例外狀況會隱藏作用中的例外狀況。 在 filter 子句中引發例外狀況時，執行階段會以無訊息模式攔截例外狀況。 這會讓原始錯誤難以偵測和 debug。|
|[CA2220：完成項應該呼叫基底類別完成項](../code-quality/ca2220.md)|最終化必須透過繼承階層架構 (Inheritance Hierarchy) 進行傳播。 若要確保這一點，則類型必須在它們自己的 Finalize 方法中呼叫基底類別 Finalize 方法。|
|[CA2221：完成項應該受到保護](../code-quality/ca2221.md)|完成項必須使用系列存取修飾詞 (Modifier)。|
|[CA2222：不要降低繼承成員的可見度](../code-quality/ca2222.md)|請勿變更繼承成員的存取修飾詞。 將繼承成員變更為私用不會防止呼叫端存取方法的基底類別 (Base Class) 實作。|
|[CA2223：成員不應該只有在傳回類型上不同](../code-quality/ca2223.md)|雖然通用語言執行平台允許使用傳回類型區分其他部分都相同的成員，但這個功能不屬於 Common Language Specification，也不是 .NET 程式語言共通的功能。|
|[CA2224：多載等號比較運算子時必須一併覆寫 Equals](../code-quality/ca2224.md)|公用類型會執行等號比較運算子，但不會覆寫 Object.equals。|
|[CA2225：運算子多載必須有具名的替代方法](../code-quality/ca2225.md)|偵測到運算子多載，且找不到預期的具名替代方法。 已命名的替代成員可存取與運算子相同的功能，並為以不支援多載運算子的語言設計程式的開發人員提供。|
|[CA2226：運算子應該有對稱的多載](../code-quality/ca2226.md)|型別會執行相等或不等比較運算子，而且不會實作用的運算子。|
|[CA2227：集合屬性應該為唯讀](../code-quality/ca2227.md)|可寫入的集合屬性允許使用者以不同的集合來取代該集合。 唯讀屬性會從取代過程中停止集合，但是仍然允許設定個別成員。|
|[CA2228：不要使用尚未發行版本所支援的格式建置資源](../code-quality/ca2228.md)|支援的 .NET 版本可能無法使用以 .NET 發行前版本所建立的資源檔。|
|[CA2229：必須實作序列化建構函式](../code-quality/ca2229.md)|若要修正此規則的違規情形，請實作序列化建構函式。 針對密封類別，讓建構函式成為 private，否則為 protected。|
|[CA2230：必須使用 params 做為變數引數](../code-quality/ca2230.md)|公用或保護的類型包含使用 VarArgs 呼叫慣例之公用或保護的方法，而不是 params 關鍵字。|
|[CA2231：覆寫 ValueType.Equals 時必須一併多載等號比較運算子](../code-quality/ca2231.md)|實值型別會覆寫 `Object.Equals` 但不會執行等號比較運算子。|
|[CA2232：Windows Forms 進入點必須標記 STAThread](../code-quality/ca2232.md)|STAThreadAttribute 表示應用程式的 COM 執行緒模型為單一執行緒 Apartment。 在使用 Windows Form 的任何應用程式之進入點上必須有此屬性。如果省略的話，Windows 元件就無法正常運作。|
|[CA2233：運算不應該發生溢位](../code-quality/ca2233.md)|不需要先驗證運算元即可執行算數運算，以確定作業的結果不在相關資料類型的可能值範圍外。|
|[CA2234：必須傳遞 System.Uri 物件而非字串](../code-quality/ca2234.md)|呼叫字串參數名稱包含 "uri"、"URI"、"urn"、"URN"、"url" 或 "URL"，  而且此方法的宣告類型會包含具有 System.Uri 參數的對應方法多載。|
|[CA2235：必須標記所有不可序列化的欄位](../code-quality/ca2235.md)|可序列化之類型中所宣告之類型的執行個體 (Instance) 欄位是不可序列化的。|
|[CA2236：必須呼叫 ISerializable 類型上的基底類別方法](../code-quality/ca2236.md)|若要修正此規則的違規情形，請從對應的衍生類型方法或建構函式，呼叫基底類型 GetObjectData 方法或序列化建構函式。|
|[CA2237：ISerializable 類型必須標記 SerializableAttribute](../code-quality/ca2237.md)|若要由 common language runtime 辨識為可序列化，即使類型透過 ISerializable 介面的實作為使用自訂序列化常式，也必須以 SerializableAttribute 屬性標記類型。|
|[CA2238：必須正確實作序列化方法](../code-quality/ca2238.md)|處理序列化事件的方法沒有正確的簽章、傳回型別或可視性。|
|[CA2239：必須為選擇性欄位提供還原序列化方法](../code-quality/ca2239.md)|型別具有以 OptionalFieldAttribute 屬性標記的欄位，而且型別不提供還原序列化事件處理方法（attribute）。|
|[CA2240：必須正確實作 ISerializable](../code-quality/ca2240.md)|若要修正此規則的違規，請讓 GetObjectData 方法可見且可覆寫，並確定所有實例欄位都包含在序列化程式中，或明確地以 NonSerializedAttribute 屬性標記。|
|[CA2241：必須提供格式化方法的正確引數](../code-quality/ca2241.md)|傳遞至 System.string 的格式引數不包含對應至每個物件引數的格式專案，反之亦然。|
|[CA2242：必須正確測試 NaN](../code-quality/ca2242.md)|此運算式針對 Single.Nan 或 Double.Nan 測試值。 使用 Single.IsNan(Single) 或 Double.IsNan(Double) 即可測試值。|
|[CA2243：屬性字串常值必須正確剖析](../code-quality/ca2243.md)|屬性的字串常值參數無法正確剖析 URL、GUID 或版本。|
