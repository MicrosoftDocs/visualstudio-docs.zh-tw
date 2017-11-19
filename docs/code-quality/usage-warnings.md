---
title: "用法警告 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.usagerules
helpviewer_keywords:
- warnings, usage
- managed code analysis warnings, usage warnings
- usage warnings
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 57068ae8c3d6bb8f86b8a9b052f4d1e2f5fec2d4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="usage-warnings"></a>用法警告
用法警告支援.NET Framework 的正確用法。  
  
## <a name="in-this-section"></a>本章節內容  
  
|規則|說明|  
|----------|-----------------|  
|[CA1801：必須檢閱未使用的參數](../code-quality/ca1801-review-unused-parameters.md)|方法簽章包括不用於方法主體中的參數；|  
|[CA1806：不要忽略方法的結果](../code-quality/ca1806-do-not-ignore-method-results.md)|已建立但從未使用新物件、已呼叫會建立並傳回新字串的方法，而新字串從未使用過，或者 COM 或 P/Invoke 方法傳回從未使用的 HRESULT 或錯誤碼。|  
|[CA1816：正確呼叫 GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|是實作的 Dispose 方法不會呼叫 GC。SuppressFinalize;或不是實作的 Dispose 方法呼叫的 GC。SuppressFinalize;或方法呼叫 GC。SuppressFinalize，以及傳遞了非 this (Me 在 Visual Basic 中)。|  
|[CA2200：必須重新擲回以保存堆疊詳細資料](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|會重新擲回的例外狀況和 throw 陳述式中明確指定例外狀況。 如果在 throw 陳述式中指定的例外狀況重新擲回例外狀況，擲回例外狀況的原始方法和目前方法之間呼叫的方法清單將會遺失。|  
|[CA2201：不要引發保留的例外狀況類型](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|這使原始錯誤變得難以偵測及偵錯。|  
|[CA2202：不要多次處置物件](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|方法實作包含程式碼路徑，可在相同物件上造成多個 System.IDisposable.Dispose 呼叫或 Dispose 對等用法 (例如，部分類型上的 Close() 方法)。|  
|[CA2204：常值必須使用正確的拼字](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|方法主體中的常值 (Literal) 字串包含一個或多個 Microsoft 拼字檢查程式庫無法辨識的字。|  
|[CA2205：必須使用 Win32 API 的 Managed 對應項](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|平台叫用方法定義，且具有對等功能的方法有.NET Framework 類別庫中。|  
|[CA2207：必須初始化實值型別的靜態欄位內嵌](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|實值類型會宣告明確的靜態建構函式。 若要修正此規則的違規情形，請在宣告所有靜態資料時將靜態資料初始化，並移除靜態建構函式。|  
|[CA2208：必須正確具現化引數例外狀況](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|對例外狀況類型為 (或衍生自) ArgumentException 的預設 (無參數) 建構函式進行呼叫，或將錯誤的字串引數傳遞至例外狀況類型為 (或衍生自) ArgumentException 的參數化建構函式。|  
|[CA2211：非常數欄位不應該為可見的](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|既非常數，亦非唯讀的靜態欄位不是安全執行緒。 這類欄位存取必須要小心控制，而且需要進階的程式設計技巧來同步處理對類別物件的存取。|  
|[CA2212：不要以 WebMethod 標記 Serviced 元件](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|中的型別繼承自 System.EnterpriseServices.ServicedComponent 的方法是使用 system.web.services.webmethodattribute 來標記來標示。 因為 WebMethodAttribute 和 ServicedComponent 方法具有衝突的內容和異動流程的行為及需求，所以方法的行為在某些情節中會是不正確的。|  
|[CA2213：可處置的欄位應該受到處置](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|實作 System.IDisposable 的類型宣告了也實作 IDisposable 之類型的欄位。 宣告類型的 Dispose 方法不會呼叫欄位的 Dispose 方法。|  
|[CA2214：不要呼叫建構函式中的可覆寫方法](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|當建構函式呼叫虛擬方法時，很可能已不執行叫用方法的執行個體的建構函式。|  
|[CA2215：Dispose 方法應該呼叫基底類別處置](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|如果類型會繼承自可處置的類型，則必須從本身的 Dispose 方法呼叫基底類型的 Dispose 方法。|  
|[CA2216：可處置的類型應該宣告完成項](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|實作 System.IDisposable，且具有建議 unmanaged 資源，使用的欄位的類型未實作完成項，如 object.finalize 所述。|  
|[CA2217：不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|外部可見的列舉型別是以 flagsattribute 標記列舉，並且有一個或多個值不是兩個或組合列舉上其他定義值的次方。|  
|[CA2218：覆寫 Equals 時必須一併覆寫 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|GetHashCode 會依據目前執行個體傳回值，適用於雜湊演算法和資料結構，如雜湊資料表。 兩個類型相同且相等的物件必須傳回相同的雜湊程式碼。|  
|[CA2219：不要在 exception 子句中引發例外狀況](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|在 finally 或 fault 子句中引發例外狀況時，新的例外狀況會隱藏作用中的例外狀況。 在 filter 子句中引發例外狀況時，執行階段會以無訊息模式攔截例外狀況。 這使原始錯誤變得難以偵測及偵錯。|  
|[CA2220：完成項應該呼叫基底類別完成項](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|最終化必須透過繼承階層架構 (Inheritance Hierarchy) 進行傳播。 若要確保這一點，則類型必須在它們自己的 Finalize 方法中呼叫基底類別 Finalize 方法。|  
|[CA2221：完成項應該受到保護](../code-quality/ca2221-finalizers-should-be-protected.md)|完成項必須使用系列存取修飾詞 (Modifier)。|  
|[CA2222：不要降低繼承成員的可見度](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|您不得變更繼承成員的存取修飾詞 (Modifier)。 將繼承成員變更為私用不會防止呼叫端存取方法的基底類別 (Base Class) 實作。|  
|[CA2223：成員不應該只有在傳回類型上不同](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|雖然通用語言執行平台允許使用傳回型別區分其他部分都相同的成員，但這個功能不屬於 Common Language Specification，也不是 .NET 程式語言共通的功能。|  
|[CA2224：多載等號比較運算子時必須一併覆寫 Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|公用類型會實作等號比較運算子，但不是會覆寫 Object.Equals。|  
|[CA2225：運算子多載必須有具名的替代方法](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|偵測到運算子多載，且找不到預期的具名替代方法。 具名的替代成員存取運算子，與相同的功能，並提供的開發人員程式在語言不支援多載的運算子。|  
|[CA2226：運算子應該有對稱的多載](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|類型實作的相等或不等比較運算子，但未實作相反的運算子。|  
|[CA2227：集合屬性應該為唯讀](../code-quality/ca2227-collection-properties-should-be-read-only.md)|可寫入的集合屬性允許使用者以不同的集合來取代該集合。 唯讀屬性會從取代過程中停止集合，但是仍然允許設定個別成員。|  
|[CA2228：不要使用尚未發行版本所支援的格式建置資源](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md)|使用發行前版本的.NET framework 所建置的資源檔可能不支援的.NET framework 版本。|  
|[CA2229：必須實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)|若要修正此規則的違規情形，請實作序列化建構函式。 針對密封類別，讓建構函式成為 private，否則為 protected。|  
|[CA2230：必須使用 params 做為變數引數](../code-quality/ca2230-use-params-for-variable-arguments.md)|公用或保護的類型包含使用 VarArgs 呼叫慣例之公用或保護的方法，而不是 params 關鍵字。|  
|[CA2231：覆寫 ValueType.Equals 時必須一併多載等號比較運算子](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|實值類型會覆寫 Object.Equals，但不會實作等號比較運算子。|  
|[CA2232：Windows Forms 進入點必須標記 STAThread](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|STAThreadAttribute 表示應用程式的 COM 執行緒模型為單一執行緒 Apartment。 在使用 Windows Form 的任何應用程式之進入點上必須有此屬性。如果省略的話，Windows 元件就無法正常運作。|  
|[CA2233：運算不應該發生溢位](../code-quality/ca2233-operations-should-not-overflow.md)|應該先驗證運算元，請確定作業的結果不是相關的資料類型的可能值的範圍外執行算術運算。|  
|[CA2234：必須傳遞 System.Uri 物件而非字串](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|呼叫字串參數名稱包含 "uri"、"URI"、"urn"、"URN"、"url" 或 "URL"，  而且此方法的宣告類型會包含具有 System.Uri 參數的對應方法多載。|  
|[CA2235：必須標記所有不可序列化的欄位](../code-quality/ca2235-mark-all-non-serializable-fields.md)|可序列化之類型中所宣告之類型的執行個體 (Instance) 欄位是不可序列化的。|  
|[CA2236：必須呼叫 ISerializable 類型上的基底類別方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|若要修正此規則的違規情形，請從對應的衍生類型方法或建構函式，呼叫基底類型 GetObjectData 方法或序列化建構函式。|  
|[CA2237：ISerializable 類型必須標記 SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|可辨識的 common language runtime 為可序列化，類型必須標記 SerializableAttribute 屬性即使使用自訂序列化常式透過 ISerializable 介面的實作類型。|  
|[CA2238：必須正確實作序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)|處理序列化事件的方法沒有正確的簽章、傳回型別或可視性。|  
|[CA2239：必須為選擇性欄位提供還原序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|類型具有使用 System.Runtime.Serialization.OptionalFieldAttribute 屬性中，欄位和類型不提供還原序列化事件處理方法。|  
|[CA2240：必須正確實作 ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)|若要修正此規則的違規情形，將 GetObjectData 方法設為可見和可覆寫，並確定所有執行個體欄位都包含在序列化程序，或明確地標示為使用 NonSerializedAttribute 屬性。|  
|[CA2241：必須提供格式化方法的正確引數](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|傳遞至 System.String.Format 的格式引數不包含對應至每個物件引數，或反之亦然的格式項目。|  
|[CA2242：必須正確測試 NaN](../code-quality/ca2242-test-for-nan-correctly.md)|此運算式針對 Single.Nan 或 Double.Nan 測試值。 使用 Single.IsNan(Single) 或 Double.IsNan(Double) 即可測試值。|  
|[CA2243：屬性字串常值必須正確剖析](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|屬性的字串常值參數不正確剖析的 URL、 GUID 或版本中。|