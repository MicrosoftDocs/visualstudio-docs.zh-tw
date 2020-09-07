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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd2f5919b0f48290ecc14cf71295e2af0bac4748
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509714"
---
# <a name="usage-warnings"></a>用法警告

使用警告支援適當使用 .NET。

## <a name="in-this-section"></a>本節內容

|規則|描述|
|----------|-----------------|
|[CA1801:必須檢閱未使用的參數](../code-quality/ca1801.md)|方法簽章包括不用於方法主體中的參數；|
|[CA1816:正確呼叫 GC.SuppressFinalize](../code-quality/ca1816.md)|屬於 Dispose 實作的方法不會呼叫 GC.SuppressFinalize，或不屬於 Dispose 實作的方法會呼叫 GC.SuppressFinalize，或呼叫 GC.SuppressFinalize 並傳遞非 this (在 Visual Basic 中為 Me) 的方法。|
|[CA2200:必須重新擲回以保存堆疊詳細資料](../code-quality/ca2200.md)|例外狀況遭到重新擲回，而且已在 throw 陳述式中明確指定此例外狀況。 如果例外狀況是透過在陳述式中指定例外狀況而重新擲回，則會遺失在擲回例外狀況之原始方法和目前方法之間呼叫的方法清單。|
|[CA2201:不要引發保留的例外狀況類型](../code-quality/ca2201.md)|這會讓原始錯誤難以偵測和偵測。|
|[CA2202:不要多次處置物件的 Dispose 方法](../code-quality/ca2202.md)|方法實作包含程式碼路徑，可在相同物件上造成多個 System.IDisposable.Dispose 呼叫或 Dispose 對等用法 (例如，部分類型上的 Close() 方法)。|
|[CA2207:必須將實值類型的靜態欄位內嵌初始化](../code-quality/ca2207.md)|實值類型會宣告明確的靜態建構函式。 若要修正此規則的違規情形，請在宣告所有靜態資料時將靜態資料初始化，並移除靜態建構函式。|
|[CA2208:必須正確執行個體化引數例外狀況](../code-quality/ca2208.md)|對例外狀況類型為 (或衍生自) ArgumentException 的預設 (無參數) 建構函式進行呼叫，或將錯誤的字串引數傳遞至例外狀況類型為 (或衍生自) ArgumentException 的參數化建構函式。|
|[CA2211:非常數欄位不應該為可見的](../code-quality/ca2211.md)|非常數或唯讀的靜態欄位不是安全線程。 對這類欄位的存取權必須謹慎控制，且需要先進的程式設計技巧來同步處理對類別物件的存取。|
|[CA2213:可處置的欄位應該受到處置](../code-quality/ca2213.md)|實作 System.IDisposable 的類型宣告了也實作 IDisposable 之類型的欄位。 宣告類型的 Dispose 方法不會呼叫欄位的 Dispose 方法。|
|[CA2214:不要呼叫建構函式中的可覆寫方法](../code-quality/ca2214.md)|當函式呼叫虛擬方法時，叫用方法之實例的函式可能尚未執行。|
|[CA2215:Dispose 方法應該呼叫基底類別處置](../code-quality/ca2215.md)|如果類型會繼承自可處置的類型，則必須從本身的 Dispose 方法呼叫基底類型的 Dispose 方法。|
|[CA2216:可處置的類型應該宣告完成項](../code-quality/ca2216.md)|型別會執行 IDisposable，而且有一些欄位建議使用非受控資源，並不會依照物件的說明來執行完成項。|
|[CA2217:不要以 FlagsAttribute 標記列舉](../code-quality/ca2217.md)|外部可見的列舉會以 FlagsAttribute 標示，而且有一或多個值不是兩個或列舉上其他已定義值的組合。|
|[CA2219:不要在 exception 子句中引發例外狀況](../code-quality/ca2219.md)|在 finally 或 fault 子句中引發例外狀況時，新的例外狀況會隱藏作用中的例外狀況。 在 filter 子句中引發例外狀況時，執行階段會以無訊息模式攔截例外狀況。 這會讓原始錯誤難以偵測和偵測。|
|[CA2225:運算子多載必須有具名的替代方法](../code-quality/ca2225.md)|偵測到運算子多載，且找不到預期的具名替代方法。 已命名的替代成員提供與運算子相同功能的存取權，並提供給以不支援多載運算子的語言撰寫程式的開發人員使用。|
|[CA2226:運算子應該有對稱的多載](../code-quality/ca2226.md)|型別會執行相等或不等比較運算子，且不會執行相反的運算子。|
|[CA2227:集合屬性應該為唯讀](../code-quality/ca2227.md)|可寫入的集合屬性允許使用者以不同的集合來取代該集合。 唯讀屬性會從取代過程中停止集合，但是仍然允許設定個別成員。|
|[CA2229:必須實作序列化建構函式](../code-quality/ca2229.md)|若要修正此規則的違規情形，請實作序列化建構函式。 針對密封類別，讓建構函式成為 private，否則為 protected。|
|[CA2231:在覆寫 ValueType.Equals 上多載等號運算子](../code-quality/ca2231.md)|實值型別 `Object.Equals` 會覆寫，但不會執行等號比較運算子。|
|[CA2232:Windows Forms 進入點必須標記 STAThread](../code-quality/ca2232.md)|STAThreadAttribute 表示應用程式的 COM 執行緒模型為單一執行緒 Apartment。 在使用 Windows Form 的任何應用程式之進入點上必須有此屬性。如果省略的話，Windows 元件就無法正常運作。|
|[CA2233:運算不應該發生溢位](../code-quality/ca2233.md)|不應先驗證運算元來執行算數運算，以確定作業的結果不在相關資料類型的可能值範圍之外。|
|[CA2234:必須傳遞 System.Uri 物件而非字串](../code-quality/ca2234.md)|呼叫字串參數名稱包含 "uri"、"URI"、"urn"、"URN"、"url" 或 "URL"，  而且此方法的宣告類型會包含具有 System.Uri 參數的對應方法多載。|
|[CA2235:必須標記所有不可序列化的欄位](../code-quality/ca2235.md)|可序列化之類型中所宣告之類型的執行個體 (Instance) 欄位是不可序列化的。|
|[CA2236:必須呼叫 ISerializable 類型上的基底類別方法](../code-quality/ca2236.md)|若要修正此規則的違規情形，請從對應的衍生類型方法或建構函式，呼叫基底類型 GetObjectData 方法或序列化建構函式。|
|[CA2237:ISerializable 類型必須標記 SerializableAttribute](../code-quality/ca2237.md)|若要以可序列化的 common language runtime 辨識，型別必須以 SerializableAttribute 屬性標記，即使型別使用自訂序列化常式透過 ISerializable 介面的實。|
|[CA2238:必須正確實作序列化方法](../code-quality/ca2238.md)|處理序列化事件的方法沒有正確的簽章、傳回型別或可視性。|
|[CA2239:必須為選擇性欄位提供還原序列化方法](../code-quality/ca2239.md)|型別具有以 System.runtime.serialization.optionalfieldattribute 屬性標記的欄位，而類型則不提供還原序列化事件的處理方法。|
|[CA2240:必須正確實作 ISerializable](../code-quality/ca2240.md)|若要修正此規則的違規情形，請讓 GetObjectData 方法變成可見和可覆寫，並確定所有實例欄位都包含在序列化程式中，或以 NonSerializedAttribute 屬性明確標記。|
|[CA2241:必須提供格式化方法的正確引數](../code-quality/ca2241.md)|傳遞給 System.string 的格式引數不包含對應至每個物件引數的格式專案，反之亦然。|
|[CA2242:必須正確測試 NaN](../code-quality/ca2242.md)|此運算式針對 Single.Nan 或 Double.Nan 測試值。 使用 Single.IsNan(Single) 或 Double.IsNan(Double) 即可測試值。|
|[CA2243:屬性字串常值必須正確剖析](../code-quality/ca2243.md)|屬性的字串常值參數未正確剖析 URL、GUID 或版本。|
|[CA2244：請勿複製索引元素初始化](../code-quality/ca2244.md)|物件初始化運算式有一個以上的索引元素初始化運算式具有相同的常數索引。 但最後一個初始化運算式是多餘的。|
|[CA2245：請勿將屬性指派給屬性自身](../code-quality/ca2245.md)|屬性意外指派給本身。|
|[CA2246：請勿在相同的陳述式中指派符號及其成員](../code-quality/ca2246.md)|不建議在相同的語句中指派符號及其成員，也就是欄位或屬性。 如果成員存取的目的是要在指派之前使用符號的舊值，或是在此語句中指派新值，則不會很清楚。|
|[CA2247：傳遞到 TaskCompletionSource 建構函式的引數應為 TaskCreationOptions 列舉，而非 TaskContinuationOptions 列舉](../code-quality/ca2246.md)|>taskcompletionsource 具有可使用 TaskCreationOptions 來控制基礎工作的函式，以及採用儲存在工作中之物件狀態的函式。  不小心傳遞 System.threading.tasks.taskcontinuationoptions> 而非 TaskCreationOptions，會導致呼叫將選項視為狀態。|
|[CA2248：提供正確的 ' enum ' 引數給 ' Enum. HasFlag '](../code-quality/ca2248.md)|作為引數傳遞至方法呼叫的列舉類型 `HasFlag` ，與呼叫列舉型別不同。|
|[CA2249：請考慮使用 String.Contains 而非 String.IndexOf](../code-quality/ca2249.md)|呼叫 `string.IndexOf` 結果的位置來檢查是否有子字串存在，可由取代 `string.Contains` 。|
