---
title: 程式碼品質規則概觀
ms.date: 09/01/2020
ms.topic: reference
f1_keywords:
- CA1000
- CA1001
- CA1002
- CA1003
- CA1005
- CA1008
- CA1010
- CA1012
- CS1014
- CA1016
- CA1017
- CA1018
- CA1019
- CA1021
- CA1024
- CA1027
- CA1028
- CA1029
- CA1030
- CA1031
- CA1032
- CA1033
- CA1034
- CA1036
- CA1040
- CA1041
- CA1043
- CA1044
- CA1045
- CA1046
- CA1047
- CA1050
- CA1051
- CA1052
- CA1053
- CA1054
- CA1055
- CA1056
- CA1058
- CA1060
- CA1061
- CA1062
- CA1063
- CA1064
- CA1065
- CA1066
- CA1067
- CA1068
- CA1069
- CA1070
- CA1200
- CA1303
- CA1304
- CA1305
- CA1307
- CA1308
- CA1309
- CA1310
- CA1401
- CA1417
- CA1501
- CA1502
- CA1505
- CA1506
- CA1507
- CA1508
- CA1509
- CA1700
- CA1707
- CA1708
- CA1710
- CA1711
- CA1712
- CA1713
- CA1714
- CA1715
- CA1716
- CA1717
- CA1720
- CA1721
- CA1724
- CA1725
- CA1801
- CA1802
- CA1805
- CA1806
- CA1810
- CA1812
- CA1813
- CA1814
- CA1815
- CA1816
- CA1819
- CA1820
- CA1821
- CA1822
- CA1823
- CA1824
- CA1825
- CA1826
- CA1827
- CA1828
- CA1829
- CA1830
- CA1831
- CA1832
- CA1833
- CA1834
- CA1835
- CA1836
- CA1837
- CA1838
- CA2000
- CA2002
- CA2007
- CA2008
- CA2009
- CA2011
- CA2012
- CA2013
- CA2014
- CA2015
- CA2016
- CA2100
- CA2101
- CA2109
- CA2119
- CA2153
- CA2200
- CA2201
- CA2207
- CA2208
- CA2211
- CA2213
- CA2214
- CA2215
- CA2216
- CA2217
- CA2219
- CA2225
- CA2226
- CA2227
- CA2229
- CA2231
- CA2234
- CA2235
- CA2237
- CA2241
- CA2242
- CA2243
- CA2245
- CA2246
- CA2247
- CA2248
- CA2249
- CA2300
- CA2301
- CA2302
- CA2305
- CA2310
- CA2311
- CA2312
- CA2315
- CA2321
- CA2322
- CA2326
- CA2327
- CA2328
- CA2329
- CA2330
- CA2350
- CA2351
- CA2352
- CA2353
- CA2354
- CA2355
- CA2356
- CA2361
- CA2362
- CA3001
- CA3002
- CA3003
- CA3004
- CA3005
- CA3006
- CA3007
- CA3008
- CA3009
- CA3010
- CA3011
- CA3012
- CA3061
- CA3075
- CA3076
- CA3077
- CA5347
- CA5350
- CA5351
- CA5359
- CA5360
- CA5361
- CA5362
- CA5363
- CA5364
- CA5365
- CA5366
- CA5367
- CA5368
- CA5369
- CA5370
- CA5371
- CA5372
- CA5373
- CA5374
- CA5375
- CA5376
- CA5377
- CA5378
- CA5379
- CA5380
- CA5381
- CA5382
- CA5383
- CA5384
- CA5385
- CA5386
- CA5387
- CA5388
- CA5389
- CA5390
- CA5391
- CA5392
- CA5393
- CA5394
- CA5395
- CA5397
- CA5398
- CA5399
- CA5400
- CA5401
- CA5402
- CA5403
- IL3000
- IL3001
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a298ab142ae6a44c1fb24b2cb1b752f6beb4a68e
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037233"
---
# <a name="code-quality-analysis-rules-by-rule-id"></a>依規則識別碼的程式碼品質分析規則

下表依規則識別碼列出程式碼品質分析規則。

| CheckId | 警告 | 描述 |
|---------| - | - |
| CA1000 | [CA1000：不要在泛型類型上宣告靜態成員](../code-quality/ca1000.md) | 呼叫泛型類型的靜態成員時，必須為類型指定類型引數。 呼叫不支援介面的泛型執行個體 (Instance) 成員時，必須為成員指定類型引數。 在上述兩種情況下，指定型別引數的語法不同且容易混淆。 |
| CA1001 | [CA1001：具有可處置欄位的類型應該為可處置](../code-quality/ca1001.md) | 類別會宣告及實作類型為 System.IDisposable 的執行個體欄位，且該類別不會實作 IDisposable。 宣告 IDisposable 欄位的類別會間接擁有 Unmanaged 資源，且應實作 IDisposable 介面。 |
| CA1002 | [CA1002：不要公開泛型清單](../code-quality/ca1002.md) | \<(T>) # A1) 的< (，是針對效能而非繼承所設計的泛型集合。 因此，List 不包含任何虛擬成員。 應該改為公開專為繼承所設計的泛型集合。 |
| CA1003 | [CA1003：使用一般事件處理常式執行個體](../code-quality/ca1003.md) |類型包含會傳回 void 的委派，其簽章包含兩個參數 (第一個參數是物件，第二個參數則是可指派給 EventArgs 的類型)，而包含組件則會以 Microsoft .NET Framework 2.0 為目標。 |
| CA1005 | [CA1005：避免在泛型類型上包含過多參數](../code-quality/ca1005.md) | 泛型類型所包含的類型參數越多，就越難了解並記住每個類型參數所代表的含意。 通常會使用一個類型參數（如清單 \<T> ），以及在具有兩個型別參數的特定情況下（如同在字典中一樣） \<TKey, TValue> 。 不過，如果存在兩個以上的類型參數，則對大多數使用者而言都會變得難以理解。 |
| CA1008 | [CA1008:列舉值中應該要有值為零的成員](../code-quality/ca1008.md) | 如同其他實值類型一般，未初始化的列舉其預設值為零。 非旗標屬性的列舉應該要使用零值來定義成員，讓預設值成為列舉的有效值。 如果已套用 FlagsAttribute 屬性的列舉定義零值成員，則其名稱應該是 "None"，以表示列舉中未設定任何值。 |
| CA1010 | [CA1010:集合應該實作泛型介面](../code-quality/ca1010.md) | 若要放寬集合的可用性，請實作其中一個泛型集合介面。 接著，使用該集合填入泛型集合類型。 |
| CA1012 | [CA1012:抽象類型不應該有建構函式](../code-quality/ca1012.md) | 只有衍生類型 (Derived Type) 可以呼叫抽象類型上的建構函式。 因為公用建構函式會建立類型的執行個體，而且您無法建立抽象類型的執行個體，因此具有公用建構函式的抽象類型設計不正確。 |
| CA1014 | [CA1014:組件必須標記 CLSCompliantAttribute](../code-quality/ca1014.md) | Common Language Specification (CLS) 會定義命名限制、資料類型及組件必須遵守的規則 (如果組件會使用於跨程式設計語言時)。 良好的設計會要求所有組件使用 <xref:System.CLSCompliantAttribute> 明確表示 CLS 符合性。 如果這個屬性未出現於組件中，則表示組件不符合標準。 |
| CA1016 | [CA1016:組件必須標記 AssemblyVersionAttribute](../code-quality/ca1016.md) | .NET 會使用版本號碼來唯一識別元件，並系結至強式名稱元件中的類型。 版本號碼會與版本和發行者 (Publisher) 原則一起使用。 應用程式預設只會與建置它們的組件版本一起執行。 |
| CA1017 | [CA1017:組件必須標記 ComVisibleAttribute](../code-quality/ca1017.md) |ComVisibleAttribute 會判斷 COM 用戶端如何存取 Managed 程式碼。 良好的設計會要求組件明確表示 COM 的可視性。 COM 的可視性可以針對整個組件進行設定，然後針對個別類型及類型成員進行覆寫。 如果這個屬性不存在，則 COM 用戶端可以看到組件的內容。 |
| CA1018 | [CA1018:必須以 AttributeUsageAttribute 標記屬性](../code-quality/ca1018.md) | 當您定義自訂屬性時，請使用 AttributeUsageAttribute 標記它，以指出可以在原始程式碼的哪個位置套用自訂屬性。 屬性的意義和預期的用法將決定它在程式碼中的有效位置。 |
| CA1019 | [CA1019:定義屬性引數的存取子](../code-quality/ca1019.md) | 屬性可以定義必須在將屬性套用至目標時指定的強制引數。 這些引數也稱為位置引數，因為它們會當做位置參數提供給屬性建構函式。 對於每個強制引數而言，屬性 (Attribute) 還須提供對應的唯讀屬性 (Property)，才可以在執行時期擷取引數值。 屬性也可以定義選擇性引數，也稱為具名引數。 這些引數會依照名稱提供給屬性 (Attribute) 建構函式，且必須有對應的讀取/寫入屬性 (Property)。 |
| CA1021 | [CA1021:避免使用 out 參數](../code-quality/ca1021.md) | 以傳址方式傳遞類型時 (使用 out 或 ref)，您需要擁有使用指標的經驗、了解實值類型和參考類型之間的差異，並處理具有多個傳回值的方法。 此外，out 和 ref 參數之間的差異一般人不甚了解。 |
| CA1024 | [CA1024:建議在適當時使用屬性](../code-quality/ca1024.md) | 公用或保護的方法具有以 "Get" 開頭的名稱，該名稱不採用任何參數並且會傳回不是陣列的值。 此方法可能是成為屬性的不錯候選者。 |
| CA1027 |[CA1027:必須以 FlagsAttribute 標記列舉](../code-quality/ca1027.md) | 列舉類型是一種實值類型 (Value Type)，用以定義一組相關的具名常數。 當列舉的具名常數可以有意義地加以結合時，會將 FlagsAttribute 套用至此列舉。 |
| CA1028 | [CA1028:列舉儲存區應該是 Int32](../code-quality/ca1028.md) | 列舉類型是一種實值類型 (Value Type)，用以定義一組相關的具名常數。 根據預設，System.Int32 資料類型會用於儲存常數值。 雖然您可以變更這個基礎類型，但是大多數情節中仍不需要或不建議進行變更。 |
| CA1030 | [CA1030:建議在適當時使用事件](../code-quality/ca1030.md) |此規則會偵測具有事件常用名稱的方法。 如果方法因回應清楚定義的狀態變更而被呼叫，應該由事件處理常式叫用該方法。 呼叫方法的物件應該要引發事件，而不是直接呼叫方法。 |
| CA1031 | [CA1031:不要攔截一般例外狀況類型](../code-quality/ca1031.md) | 不應該攔截一般例外狀況。 請攔截較明確的例外狀況，或重新擲回一般例外狀況當做 catch 區塊中的最後一個陳述式。 |
| CA1032 |[CA1032:必須實作標準例外狀況建構函式](../code-quality/ca1032.md) | 無法提供整組的建構函式會導致難以正確地處理例外狀況。 |
| CA1033 | [CA1033:介面方法應該要可以由子類型呼叫](../code-quality/ca1033.md) | 非密封外部可見的類型會提供公用介面的明確方法實作，但未提供同名的替代外部可見方法。 |
| CA1034 | [CA1034:巢狀類型不應該為可見的](../code-quality/ca1034.md) | 巢狀類型是在其他類型範圍內宣告的類型。 巢狀類型可用來封裝包含類型 (Containing Type) 私用的 (Private) 實作細節。 因為有這樣的用途，所以巢狀類型不應為外部可見的。 |
| CA1036 | [CA1036:必須在 Comparable 類型中覆寫方法](../code-quality/ca1036.md) |公用或受保護的類型實作 System.IComparable 介面。 它不會覆寫 Object.Equals，也不會多載等號、不等、小於或大於的語言特定比較運算子。 |
| CA1040 |[CA1040:避免使用空的介面](../code-quality/ca1040.md) | 介面是用來定義一組可提供行為或程式使用合約的成員。 不論類型出現在繼承階層架構 (Inheritance Hierarchy) 中的何處，任何類型都可以採用介面所描述的功能。 類型會實作介面，方法是提供介面成員的實作。 空白介面不會定義任何成員，因此也不會定義能夠實作的合約。 |
| CA1041 | [CA1041:必須提供 ObsoleteAttribute 訊息](../code-quality/ca1041.md) | 類型或成員是使用並未指定其 ObsoleteAttribute.Message 屬性 (Property) 的 System.ObsoleteAttribute 屬性 (Attribute) 來標記。 編譯使用 ObsoleteAttribute 來標記的類型或成員之後，會顯示屬性 (Attribute) 的 Message 屬性 (Property)， 以便提供使用者有關過時類型或成員的資訊。 |
| CA1043 | [CA1043:必須針對索引子使用整數或字串引數](../code-quality/ca1043.md) | 索引子 (也就是索引的屬性) 應該使用整數類型或字串類型的索引。 這些類型通常會用於資料結構的索引，可以提升程式庫的可用性。 Object 類型的使用應限制於無法在設計階段指定特定整數類型或字串類型的情況。 |
| CA1044 | [CA1044:屬性不應該為唯寫的](../code-quality/ca1044.md) | 雖然它是可接受並經常需要具有唯讀屬性，設計方針會禁止使用唯寫屬性的屬性。 這是因為讓使用者，設定一個值，然後防止使用者檢視值並不會提供任何安全性。 同時，如果沒有讀取權限，則無法檢視共用物件的狀態，進而限制這些物件的使用性。 |
| CA1045 |[CA1045:不要以傳址方式傳遞類型](../code-quality/ca1045.md) | 以傳址方式傳遞類型時 (使用 out 或 ref)，您需要擁有使用指標的經驗、了解實值類型和參考類型之間的差異，並處理具有多個傳回值的方法。 設計一般物件的程式庫架構設計人員不應預期使用者使用 `out` 或 `ref` 參數。 |
| CA1046 | [CA1046:不要多載參考類型上的等號比較運算子](../code-quality/ca1046.md) | 對參考類型而言，等號比較運算子的預設實作 (Implementation) 永遠都是正確的。 根據預設，只有當兩項參考都指向相同物件時才會相等。 |
| CA1047 |[CA1047:不要在密封類型中宣告 protected 成員](../code-quality/ca1047.md) | 類型會宣告 protected 成員，如此繼承的類型即可存取或覆寫成員。 根據定義，密封類型無法被繼承，這表示無法呼叫密封類型上的受保護方法。 |
| CA1050 | [CA1050:類型必須在命名空間中宣告](../code-quality/ca1050.md) | 類型會在命名空間之內宣告以防止名稱衝突，而且可當做組織物件階層架構中相關類型的一種方法。 |
| CA1051 | [CA1051:不要宣告可見的執行個體欄位](../code-quality/ca1051.md) | 欄位的主要用法應該是當做實作詳細資料。 欄位應該是私用或內部的，而且應使用屬性公開。 |
| CA1052 | [CA1052:靜態預留位置類型應該為密封的](../code-quality/ca1052.md) | 公用或受保護的類型只包含靜態成員，因此不會利用 sealed (C# 參考) (NotInheritable) 修飾詞宣告它們。 預定不會繼承的類型應該使用 sealed 修飾詞來標記，以禁止使用它做為基底類型。 |
| CA1053 |[CA1053:靜態預留位置類型不應該包含建構函式](../code-quality/ca1053.md) | 公用或巢狀公用類型只宣告靜態成員，而且具有公用或保護的預設建構函式。 建構函式不是必要的，因為呼叫靜態成員不需類型的執行個體。 為了安全，字串多載應該使用字串引數來呼叫統一資源識別項 (URI) 多載。 |
| CA1054 | [CA1054:URI 參數不應該為字串](../code-quality/ca1054.md) | 如果方法使用 URI 字串表示，應該提供採用 URI 類別的對應多載，這樣就可以透過安全的方式提供這些服務。 |
| CA1055 | [CA1055:URI 傳回值不應該為字串](../code-quality/ca1055.md) | 這項規則假設方法會傳回 URI。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 System.Uri 類別以安全的方式提供這些服務。 |
| CA1056 | [CA1056:URI 屬性不應該為字串](../code-quality/ca1056.md) | 此規則假設屬性代表統一資源識別元 (URI)。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 System.Uri 類別以安全的方式提供這些服務。 |
| CA1058 | [CA1058:類型不應該擴充特定基底類型](../code-quality/ca1058.md) | 外部可見的類型會延伸某些基底類型 (Base Type)。 請使用其他作法。 |
| CA1060 | [CA1060：將 P/Invoke 移至 NativeMethods 類別](../code-quality/ca1060.md) | 平台引動方法 (例如使用 System.Runtime.InteropServices.DllImportAttribute 屬性標記的方法，或在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中使用 Declare 關鍵字定義的方法) 都會存取 Unmanaged 程式碼。 這些方法應該是 NativeMethods、SafeNativeMethods 或 UnsafeNativeMethods 類別。 |
| CA1061 |[CA1061:不要隱藏基底類別方法](../code-quality/ca1061.md) | 只有在衍生方法的參數簽章因類型衍生時比基底方法參數簽章中的類型還要弱時，基底類型中的方法才會被衍生類型中的相同具名方法所隱藏。 |
| CA1062 | [CA1062:必須驗證公用方法的引數](../code-quality/ca1062.md) | 所有傳遞至外部可見方法的參考引數都應經過 null 檢查。 |
| CA1063 | [CA1063:必須正確實作 IDisposable](../code-quality/ca1063.md) | 所有的 IDisposable 類型都需正確地實作 Dispose 模式。 |
| CA1064 | [CA1064:例外狀況必須是公用](../code-quality/ca1064.md) | 內部例外狀況只會在自己的內部範圍內顯示。 當例外狀況超出內部範圍後，只能使用基本例外狀況來攔截例外狀況。 如果內部例外狀況繼承自 <xref:System.Exception> 、 <xref:System.SystemException> 或 <xref:System.ApplicationException> ，則外部程式碼將不會有足夠的資訊來知道該如何處理例外狀況。 |
| CA1065 | [CA1065:不要在非預期的位置中引發例外狀況](../code-quality/ca1065.md) | 不可擲回例外狀況 (Exception) 的方法卻擲回例外狀況。 |
| CA1066 | [CA1066：覆寫 Equals 時實作 IEquatable](../code-quality/ca1066.md) | 實值型別 <xref:System.Object.Equals%2A> 會覆寫方法，但不會執行 <xref:System.IEquatable%601> 。 |
| CA1067 | [CA1067：實作 IEquatable 時覆寫 Equals](../code-quality/ca1067.md) | 型別 <xref:System.IEquatable%601> 會執行，但不會覆寫 <xref:System.Object.Equals%2A> 方法。 |
| CA1068 | [CA1068：CancellationToken 參數必須位於最後](../code-quality/ca1068.md) | 方法的 CancellationToken 參數不是最後一個參數。 |
| CA1069 | [CA1069：列舉不能有重複的值](../code-quality/ca1069.md) | 列舉具有多個明確指派相同常數值的成員。 |
| CA1070 | [CA1070：請勿將事件欄位宣告為 virtual](../code-quality/ca1070.md) | [類似欄位的事件](/dotnet/csharp/language-reference/language-specification/classes#field-like-events)已宣告為 virtual。 |
| CA1200 | [CA1200：請避免使用具有前置詞的 cref 標記](../code-quality/ca1200.md) | XML 檔標記中的 [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) 屬性工作表示「程式碼參考」。 它會指定標記的內部文字是程式碼項目，例如類型、方法或屬性。 避免使用具有前置詞的 `cref` 標記，因為它會防止編譯器驗證參考。 它也可防止 Visual Studio 整合式開發環境 (IDE) 在重構期間尋找和更新這些符號參考。 |
| CA1303 | [CA1303:不要將常值當作已當地語系化的參數傳遞](../code-quality/ca1303.md) | 外部可見的方法會將字串常值做為參數傳遞至 .NET 的函式或方法，且該字串應可當地語系化。 |
| CA1304 | [CA1304:必須指定 CultureInfo](../code-quality/ca1304.md) | 方法或建構函式會呼叫具有接受 System.Globalization.CultureInfo 參數之多載的成員，且方法或建構函式未呼叫採用 CultureInfo 參數的多載。 未提供 CultureInfo 或 System.IFormatProvider 物件時，多載成員所提供的預設值可能不會有您希望在所有地區設定中都有的效果。 |
| CA1305 | [CA1305:必須指定 IFormatProvider](../code-quality/ca1305.md) | 方法或建構函式所呼叫的一個或多個成員具有可接受 System.IFormatProvider 參數的多載，但該方法或建構函式並未呼叫可接受 IFormatProvider 參數的多載。 未提供 System.Globalization.CultureInfo 或 IFormatProvider 物件時，多載成員所提供的預設值可能不會有您希望在所有地區設定中都有的效果。 |
| CA1307 | [CA1307:指定 StringComparison 以提升明確性](../code-quality/ca1307.md) | 字串比較作業會使用未設定 StringComparison 參數的方法多載。 |
| CA1308 |[CA1308:必須將字串標準化為大寫字母](../code-quality/ca1308.md) | 字串應該標準化為大寫字母。 當一小組的字元轉換成小寫字母時，它們無法構成來回行程。 |
| CA1309 | [CA1309:使用循序的 StringComparison](../code-quality/ca1309.md) | 非語言的字串比較作業未將 StringComparison 參數設定為 Ordinal 或 OrdinalIgnoreCase。 藉由明確地將參數設定為 StringComparison.Ordinal 或 StringComparison.OrdinalIgnoreCase，您的程式碼通常可以提升速度、更為正確，也更加可靠。 |
| CA1310 | [CA1310：指定 StringComparison 以提升正確性](../code-quality/ca1310.md) | 字串比較作業會使用未設定 StringComparison 參數的方法多載，並預設使用特定文化特性的字串比較。 |
| CA1401 | [CA1401： P/Invoke 不應該為可見的](../code-quality/ca1401.md) | 公用類型中公用或保護的方法具有 System.Runtime.InteropServices.DllImportAttribute 屬性 (也會由 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中的 Declare 關鍵字實作)。 但不得公開 (Expose) 此類方法。 |
| CA1417 | [CA1417：不使用 `OutAttribute` P/invoke 的字串參數](../code-quality/ca1417.md) | 以傳值方式傳遞的字串參數， `OutAttribute` 會在字串為暫存字串時，使執行時間不穩定。 |
| CA1501 | [CA1501:避免在物件間過度繼承](../code-quality/ca1501.md) | 類型在其繼承階層架構 (Inheritance Hierarchy) 中超過四個層級的深度。 太深的巢狀類型階層架構可能會難以依循、了解和維護。 |
| CA1502 | [CA1502:避免造成過度複雜的方法](../code-quality/ca1502.md) | 這個規則會測量整個方法中線性獨立路徑的數目，此數目是由條件分支的數目與複雜度決定。 |
| CA1505 | [CA1505:應避免撰寫無法維護的程式碼](../code-quality/ca1505.md) | 類型或方法的維護性指標值很低。 維護性指標很低代表類型或方法很可能會難以維護，而應該列為需要重新設計的候選目標。 |
| CA1506 | [CA1506:應避免使用結合過度的類別](../code-quality/ca1506.md) | 這個規則會測量類別的耦合，方法是計算類型或方法包含的唯一類型參考數目。 |
| CA1507 | [CA1507:使用 nameof 取代字串](../code-quality/ca1507.md) | 字串常值會用來做為可使用運算式的引數 `nameof` 。 |
| CA1508 | [CA1508:避免使用無作用條件式程式碼](../code-quality/ca1508.md) | 方法的條件式程式碼一律會 `true` `false` 在執行時間評估為或。 這會導致條件的分支中有不正確程式碼 `false` 。 |
| CA1509 | [CA1509：程式碼度量設定檔中的項目無效](../code-quality/ca1509.md) | 程式碼度量規則（例如 [CA1501](ca1501.md)、 [CA1502](ca1502.md)、 [CA1505](ca1505.md) 和 [CA1506](ca1506.md)）提供了名為的設定檔， `CodeMetricsConfig.txt` 其專案無效。 |
| CA1700 | [CA1700:不要在列舉值名稱中包含 'Reserved'](../code-quality/ca1700.md) | 這項規則假設名稱中包含 "reserved" 的列舉成員目前並未使用，但是在未來版本會是重新命名或移除的替代符號 (Placeholder)。 重新命名或移除成員是中斷變更。 |
| CA1707 | [CA1707:識別項名稱不應該包含底線](../code-quality/ca1707.md) | 根據慣例，識別項名稱不包含底線 (_) 字元。 此規則會檢查命名空間、類型、成員和參數。 |
| CA1708 | [CA1708:識別項名稱不應該只靠大小寫區別](../code-quality/ca1708.md) | 因為以通用語言執行平台為目標的語言不需要區分大小寫，因此，命名空間、類型、成員和參數的識別項不能只有大小寫的不同。 |
| CA1710 | [CA1710:識別項應該使用正確的後置字元](../code-quality/ca1710.md) |依照慣例，擴充某些基底類型或實作某些介面的類型名稱，或從這些類型衍生的類型，都具有與基底類型或介面關聯的後置字元。 |
| CA1711 | [CA1711:識別項名稱不應該使用不正確的後置字元](../code-quality/ca1711.md) | 依照慣例，只有擴充特定基底類型或實作特定介面的類型名稱，或是從這些類型衍生的類型名稱，應以特定保留的後置字元結尾。 其他類型名稱不得使用這些保留的後置字元。 |
| CA1712 | [CA1712:不要使用類型名稱作為列舉值的前置字元](../code-quality/ca1712.md) | 因為開發工具應該提供類型資訊，所以列舉成員的名稱不能以類型名稱做為開頭。 |
| CA1713 | [CA1713:事件不應該有 before 或 after 前置字元](../code-quality/ca1713.md) | 事件的名稱會以 "Before" 或 "After" 為開頭。 若要命名在特定序列 (Sequence) 中引發的相關事件，請使用現在式或過去式表示動作序列相對的位置。 |
| CA1714 | [CA1714:旗標列舉應該使用複數名稱](../code-quality/ca1714.md) | 公用的列舉具有 System.FlagsAttribute 屬性，而且其名稱不能以 "s" 做結尾。 使用 FlagsAttribute 來標記的類型具有複數的名稱，因為這個屬性表示可以指定一個以上的值。 |
| CA1715 | [CA1715:識別項名稱應該使用正確的前置字元](../code-quality/ca1715.md) | 外部可見介面的名稱沒有以大寫 "I" 開頭。 外部可見類型或方法上泛型型別參數的名稱沒有以大寫 "T" 開頭。 |
| CA1716 | [CA1716:識別項名稱不應該和關鍵字相符](../code-quality/ca1716.md) | 命名空間 (Namespace) 名稱或類型名稱符合程式語言中的保留關鍵字。 命名空間和類型的識別項不應該符合語言所定義的關鍵字，而這些語言的目標為 Common Language Runtime。 |
| CA1717 | [CA1717:只有 FlagsAttribute 列舉應該使用複數名稱](../code-quality/ca1717.md) | 依照命名規範的要求，列舉的複數名稱代表可以同時指定多個列舉值。 |
| CA1720 |[CA1720:識別項名稱不應該包含類型名稱](../code-quality/ca1720.md) | 外部可見成員中的參數名稱包含資料類型名稱，或外部可見成員的名稱包含語言特定的資料類型名稱。 |
| CA1721 | [CA1721:屬性名稱不應該和其中有 get 的方法名稱相符](../code-quality/ca1721.md) |公用或保護之成員的名稱是以 "Get" 開頭，否則需符合公用或保護之屬性的名稱。 "Get" 方法和屬性的名稱應該清楚區別其功能。 |
| CA1724 | [CA1724:類型名稱不應該和命名空間相符](../code-quality/ca1724.md) | 類型名稱不應與 .NET 命名空間的名稱相符。 違反此規則會降低程式庫的可用性。 |
| CA1725 | [CA1725:參數名稱應該符合基底類型的宣告](../code-quality/ca1725.md) | 在覆寫階層架構中一致的參數命名方式，會增加方法覆寫的可用性。 與基底宣告中的名稱不同之衍生方法中的參數名稱，可能會造成方法為基底方法的覆寫或為方法的新多載而混淆。 |
| CA1801 | [CA1801:必須檢閱未使用的參數](../code-quality/ca1801.md) | 方法簽章包括不用於方法主體中的參數； |
| CA1802 |[CA1802:建議在適當時使用常值](../code-quality/ca1802.md) |欄位宣告為 static 和 read-only (在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中為 Shared 和 ReadOnly)，並使用編譯時期能計算的值進行初始化。 因為指派給目標欄位的值會在編譯時期可計算，所以請將宣告變更為) 欄位中 const (Const， [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 以便在編譯時間而非執行時間計算該值。 |
| CA1805 | [CA1805：請勿進行非必要的初始化](../code-quality/ca1805.md) | .NET 執行時間會在執行此函式之前，先將參考型別的所有欄位初始化為其預設值。 在大多數情況下，將欄位明確初始化為其預設值是多餘的，這會增加維護成本，而且可能會降低效能 (例如，元件大小) 增加。 |
| CA1806 | [CA1806:不要忽略方法的結果](../code-quality/ca1806.md) | 已建立但從未使用新物件、已呼叫會建立並傳回新字串的方法，而新字串從未使用過，或者 COM 或 P/Invoke 方法傳回從未使用的 HRESULT 或錯誤碼。 |
| CA1810 | [CA1810:必須將參考類型內部的靜態欄位初始化](../code-quality/ca1810.md) | 當類型宣告明確的靜態建構函式時，Just-In-Time (JIT) 編譯器會將檢查加入至類型的每個靜態方法和執行個體建構函式，確保之前已呼叫該靜態建構函式。 靜態建構函式檢查會降低效能。 |
| CA1812 | [CA1812:避免使用未執行個體化的內部類別](../code-quality/ca1812.md) | 組件層級類型的執行個體不是由組件中的程式碼所建立。 |
| CA1813 | [CA1813:避免使用非密封屬性](../code-quality/ca1813.md) | .NET 提供了用來取得自訂屬性的方法。 根據預設，這些方法會搜尋屬性繼承階層架構。 密封屬性會減少對整個繼承階層架構的搜尋，並且可以改進效能。 |
| CA1814 | [CA1814:建議使用不規則陣列取代多維陣列](../code-quality/ca1814.md) | 不規則陣列是一種陣列，其元素也是陣列。 組成元素的陣列大小可以不相同，對於某些資料集而言較不會浪費空間。 |
| CA1815 | [CA1815:必須覆寫實值類型上的 Equals 方法和等號比較運算子](../code-quality/ca1815.md) | 對於實值類型而言，Equals 的繼承實作會使用 Reflection 程式庫，並比較所有欄位的內容。 但是 Reflection 相當耗費運算資源，而且可能不需要比較每個欄位是否相等。 如果希望使用者比較或排序執行個體，或是使用執行個體做為雜湊資料表索引鍵，則您的實值類型應實作 Equals。 |
| CA1816 | [CA1816:正確呼叫 GC.SuppressFinalize](../code-quality/ca1816.md) | 屬於 Dispose 實作的方法不會呼叫 GC.SuppressFinalize，或不屬於 Dispose 實作的方法會呼叫 GC.SuppressFinalize，或呼叫 GC.SuppressFinalize 並傳遞非 this (在 Visual Basic 中為 Me) 的方法。 |
| CA1819 | [CA1819:屬性不應該傳回陣列](../code-quality/ca1819.md) | 即使屬性是唯讀，所傳回的陣列不會是寫入保護。 若要保持陣列為防止遭他人修改，屬性必須傳回陣列複本。 一般而言，使用者不了解呼叫這類屬性所造成的不良效能影響。 |
| CA1820 | [CA1820:應該使用字串長度測試空白字串](../code-quality/ca1820.md) | 使用 String.Length 屬性或 String.IsNullOrEmpty 方法比較字串，明顯地會比使用 Equals 還快。 |
| CA1821 | [CA1821:必須移除空的完成項](../code-quality/ca1821.md) | 請盡可能避免使用完成項，因為追蹤物件存留期 (Lifetime) 時將會產生額外的效能負荷。 空白完成項只會增加額外負荷，而沒有任何好處。 |
| CA1822 |[CA1822:將成員標記為 static](../code-quality/ca1822.md) | 不會存取執行個體資料或不會呼叫執行個體方法的成員，可以標記為 static (在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中為 Shared)。 將方法標記為 static 之後，編譯器將對這些成員發出非虛擬呼叫位置。 這麼做可以讓重視效能的程式碼獲得可觀的效能。 |
| CA1823 | [CA1823:避免包含未使用的私用欄位](../code-quality/ca1823.md) | 偵測到似乎不能在組件內存取的私用欄位。 |
| CA1824 |[CA1824:組件必須標記 NeutralResourcesLanguageAttribute](../code-quality/ca1824.md) | NeutralResourcesLanguage 屬性會通知資源管理員，該語言是用來顯示元件之中性文化特性的資源。 這可改善載入第一個資源的查詢效能，而且可以減少您的工作集。 |
| CA1825 |[CA1825：請避免長度為零的陣列配置](../code-quality/ca1825.md) | 初始化零長度的陣列會導致不必要的記憶體配置。 請改為呼叫，以使用靜態配置的空陣列實例 <xref:System.Array.Empty%2A?displayProperty=nameWithType> 。 記憶體配置會在此方法的所有調用之間共用。 |
| CA1826 |[CA1826：請使用屬性，不要使用 Linq Enumerable 方法](../code-quality/ca1826.md) | <xref:System.Linq.Enumerable> LINQ 方法用於支援相等、更有效率之屬性的類型。 |
| CA1827 |[CA1827：不要在可使用 Any 時使用 Count/LongCount](../code-quality/ca1827.md) | <xref:System.Linq.Enumerable.Count%2A> 或 <xref:System.Linq.Enumerable.LongCount%2A> 方法的使用方式 <xref:System.Linq.Enumerable.Any%2A> 較有效率。 |
| CA1828 |[CA1828：不要在可使用 AnyAsync 時使用 CountAsync/LongCountAsync](../code-quality/ca1828.md) | <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.CountAsync%2A> 或 <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.LongCountAsync%2A> 方法的使用方式 <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.AnyAsync%2A> 較有效率。 |
| CA1829 |[CA1829：請使用 Length/Count 屬性，不要使用 Enumerable.Count 方法](../code-quality/ca1829.md) | <xref:System.Linq.Enumerable.Count%2A> LINQ 方法用於支援相等、更有效率 `Length` 或屬性的類型 `Count` 。 |
| CA1830 |[CA1830：建議在 StringBuilder 上使用強型別 Append 及 Insert 方法多載](../code-quality/ca1830.md) | <xref:System.Text.StringBuilder.Append%2A> 並 <xref:System.Text.StringBuilder.Insert%2A> 提供多個類型的多載 <xref:System.String> 。  可能的話，最好使用 ToString 的強型別多載 ( # A1 和以字串為基礎的多載。 |
| CA1831 |[CA1831：在適用情況下，請使用 AsSpan 做為字串，不要使用範圍型的索引子](../code-quality/ca1831.md) | 在字串上使用範圍索引子，並將值隱含指派給 ReadOnlySpan &lt; char &gt; 類型時，將會 <xref:System.String.Substring%2A?#System_String_Substring_System_Int32_System_Int32_> 使用方法，而不是 <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> ，這會產生字串的要求部分複本。 |
| CA1832 |[CA1832：請使用 AsSpan 或 AsMemory 來取得陣列的 ReadOnlySpan 或 ReadOnlyMemory 部分，不要使用範圍型的索引子](../code-quality/ca1832.md) | 在陣列上使用範圍索引子，並將值隱含地指派給 <xref:System.ReadOnlySpan%601> 或 <xref:System.ReadOnlyMemory%601> 類型時，將會 <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> 使用方法，而不是 <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> ，這會產生陣列所要求部分的複本。 |
| CA1833 |[CA1833：請使用 AsSpan 或 AsMemory 取得陣列的 Span 或 Memory 部分，不要使用範圍型的索引子](../code-quality/ca1833.md) | 在陣列上使用範圍索引子，並將值隱含地指派給 <xref:System.Span%601> 或 <xref:System.Memory%601> 類型時，將會 <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> 使用方法，而不是 <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> ，這會產生陣列所要求部分的複本。 |
| CA1834 |[CA1834：針對單一字元字串使用 StringBuilder.Append(char)](../code-quality/ca1834.md) | <xref:System.Text.StringBuilder> 具有 `Append` 接受 `char` 作為其引數的多載。 基於效能考慮，偏好呼叫多載 `char` 。 |
| CA1835 |[CA1835：偏好 ' System.io.stream.readasync ' 和 ' System.io.stream.writeasync ' 以 Memory' 為基礎的多載](../code-quality/ca1835.md) | ' Stream ' 有一個 ' System.io.stream.readasync ' 多載，它會接受 ' Memory &lt; byte &gt; ' 做為第一個引數，並使用 ' system.io.stream.writeasync ' 多載（接受 ' ReadOnlyMemory &lt; Byte &gt; ' 做為第一個引數）。 偏好呼叫以記憶體為基礎的多載，這些多載較有效率。 |
| CA1836 |[CA1836：優先 `IsEmpty` `Count` 使用](../code-quality/ca1836.md) | 偏好 `IsEmpty` 比、或更有效率的屬性， `Count` `Length` <xref:System.Linq.Enumerable.Count%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> <xref:System.Linq.Enumerable.LongCount%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 以判斷物件是否包含任何專案。 |
| CA1837 | [CA1837：使用 `Environment.ProcessId` 而非 `Process.GetCurrentProcess().Id`](../code-quality/ca1837.md) | `Environment.ProcessId` 比更簡單且更快速 `Process.GetCurrentProcess().Id` 。 |
| CA1838 | [CA1838：避免 `StringBuilder` P/invoke 的參數](../code-quality/ca1838.md) | ' StringBuilder ' 的封送處理一律會建立原生緩衝區複本，導致一個封送處理作業有多個配置。 |
| CA2000 | [CA2000:必須在超出範圍前處置物件](../code-quality/ca2000.md) | 因為可能會發生例外事件以防止執行物件的完成項，所以應在物件的所有參考都超出範圍之前，明確處置物件。 |
| CA2002 |[CA2002:不要鎖定具有弱式識別的物件](../code-quality/ca2002.md) |可以跨應用程式定義域範圍直接存取的物件，即所謂具有弱式識別的物件。 嘗試取得具有弱式識別之物件鎖定的執行緒，可以被不同應用程式定義域中具有相同物件鎖定的第二個執行緒所封鎖。 |
| CA2007 | [CA2007:不直接等候工作](ca2007.md) | 非同步方法會[awaits](/dotnet/csharp/language-reference/keywords/await)直接等候 <xref:System.Threading.Tasks.Task> 。 當非同步方法直接等候時 <xref:System.Threading.Tasks.Task> ，會在建立工作的相同執行緒中發生接續。 這種行為在效能方面可能相當昂貴，而且可能會在 UI 執行緒上產生鎖死。 請考慮呼叫 <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> 以發出接續的意圖。 |
| CA2008 | [CA2008：建立工作時請務必傳遞 TaskScheduler](ca2008.md) | 工作建立或接續運算使用未指定參數的方法多載 <xref:System.Threading.Tasks.TaskScheduler> 。 |
| CA2009 | [CA2009：請勿對 ImmutableCollection 值呼叫 TolmmutableCollection](ca2009.md) | `ToImmutable` 方法在命名空間的不可變集合上不必要地呼叫 <xref:System.Collections.Immutable> 。 |
| CA2011 | [CA2011：請勿在屬性 setter 中指派屬性](ca2011.md) | 屬性在其本身的 [set 存取](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor)子中不小心指派了值。 |
| CA2012 | [CA2012：必須正確使用 ValueTasks](ca2012.md) | 從成員調用傳回的 ValueTasks 是要直接等待。  嘗試多次使用 ValueTask 或在已知完成之前直接存取一個結果可能會導致例外狀況或損毀。  忽略這類 ValueTask 可能表示功能錯誤，而且可能會降低效能。 |
| CA2013 | [CA2013：請勿使用具有值類型的 ReferenceEquals](ca2013.md) | 使用比較值時 <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> ，如果 objA 和 objB 是實值型別，則會在傳遞至方法之前先將它們裝箱 <xref:System.Object.ReferenceEquals%2A> 。 這表示即使 objA 和 objB 都代表實值型別的實例，方法仍會傳回 <xref:System.Object.ReferenceEquals%2A> false。 |
| CA2014 | [CA2014：不要在迴圈中使用 stackalloc。](ca2014.md) | Stackalloc 配置的堆疊空間只會在目前方法的調用結束時釋出。  在迴圈中使用它，可能會導致未系結的堆疊成長和最終的堆疊溢位狀況。 |
| CA2015 | [CA2015：請勿定義衍生自 MemoryManager T 之類型的完成項 &lt;&gt;](ca2015.md) | 將完成項加入至衍生自的型別 <xref:System.Buffers.MemoryManager%601> 時，可能會允許在記憶體仍在使用時釋放記憶體 <xref:System.Span%601> 。 |
| CA2016 | [CA2016：將 CancellationToken 參數傳遞給使用該參數的方法](ca2016.md) | 將 `CancellationToken` 參數轉寄至採用其中一個的方法，以確保作業取消通知會正確傳播，或明確地傳入 `CancellationToken.None` 以表示刻意不傳播權杖。 |
| CA2100 | [CA2100:必須檢閱 SQL 查詢中是否有安全性弱點](../code-quality/ca2100.md) | 方法會使用透過字串引數所建置的字串，將 System.Data.IDbCommand.CommandText 屬性設定為方法。 這項規則假設字串引數包含使用者輸入。 從使用者輸入所建置的 SQL 命令字串很容易遭到 SQL 插入 (SQL Injection) 攻擊。 |
| CA2101 |[CA2101 必須：指定 P/Invoke 字串引數的封送處理](../code-quality/ca2101.md) | 平台叫用成員允許部分信任的呼叫端、具有字串參數，並且未明確封送處理字串。 這樣會造成安全性弱點。 |
| CA2109 | [CA2109:必須檢閱可見的事件處理常式](../code-quality/ca2109.md) | 偵測到公用或保護的事件處理方法。 除非有絕對的必要性，否則不應該公開事件處理方法。 |
| CA2119 | [CA2119:密封方法以滿足私用介面的要求](../code-quality/ca2119.md) | 可繼承的公用類型會提供內部 (在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中為 Friend) 介面的可覆寫方法實作。 若要修正此規則的違規情形，請避免在組件外覆寫方法。 |
| CA2153 |[CA2153：避免處理損毀狀態例外狀況](../code-quality/ca2153.md) | 損毀狀態例外狀況 (Cse) 指出您的進程中有記憶體損毀。 如果攻擊者將攻擊放入損毀的記憶體區域，則攔截這些處理序而非讓它們損毀，會導致安全性弱點。 |
| CA2200 | [CA2200:必須重新擲回以保存堆疊詳細資料](../code-quality/ca2200.md) | 例外狀況遭到重新擲回，而且已在 throw 陳述式中明確指定此例外狀況。 如果例外狀況是透過在陳述式中指定例外狀況而重新擲回，則會遺失在擲回例外狀況之原始方法和目前方法之間呼叫的方法清單。 |
| CA2201 | [CA2201:不要引發保留的例外狀況類型](../code-quality/ca2201.md) | 這將使原始錯誤變得難以偵測及偵錯。 |
| CA2207 | [CA2207:必須將實值類型的靜態欄位內嵌初始化](../code-quality/ca2207.md) | 實值類型會宣告明確的靜態建構函式。 若要修正此規則的違規情形，請在宣告所有靜態資料時將靜態資料初始化，並移除靜態建構函式。 |
| CA2208 |[CA2208:必須正確執行個體化引數例外狀況](../code-quality/ca2208.md) | 對例外狀況類型為 (或衍生自) ArgumentException 的預設 (無參數) 建構函式進行呼叫，或將錯誤的字串引數傳遞至例外狀況類型為 (或衍生自) ArgumentException 的參數化建構函式。 |
| CA2211 |[CA2211:非常數欄位不應該為可見的](../code-quality/ca2211.md) | 既非常數，亦非唯讀的靜態欄位不是安全執行緒。 必須小心控制對這類欄位的存取，而且需要進階的程式設計技巧來同步處理對類別物件的存取。 |
| CA2213 | [CA2213:可處置的欄位應該受到處置](../code-quality/ca2213.md) | 實作 System.IDisposable 的類型宣告了也實作 IDisposable 之類型的欄位。 宣告類型的 Dispose 方法不會呼叫欄位的 Dispose 方法。 |
| CA2214 | [CA2214:不要呼叫建構函式中的可覆寫方法](../code-quality/ca2214.md) | 當建構函式呼叫虛擬方法時，叫用此方法之執行個體的建構函式可能尚未執行。 |
| CA2215 | [CA2215:Dispose 方法應該呼叫基底類別處置](../code-quality/ca2215.md) | 如果類型會繼承自可處置的類型，則必須從本身的 Dispose 方法呼叫基底類型的 Dispose 方法。 |
| CA2216 |[CA2216:可處置的類型應該宣告完成項](../code-quality/ca2216.md) | 實作 System.IDisposable 且具有建議 Unmanaged 資源用法之欄位的類型，未實作如 Object.Finalize 所述的完成項。 |
| CA2217 | [CA2217:不要以 FlagsAttribute 標記列舉](../code-quality/ca2217.md) |從外部可見的列舉會使用 FlagsAttribute 來標記，並且有一個或多個不是二的次方，或組合列舉上其他定義值之次方的值。 |
| CA2219 | [CA2219:不要在 exception 子句中引發例外狀況](../code-quality/ca2219.md) | 在 finally 或 fault 子句中引發例外狀況時，新的例外狀況會隱藏作用中的例外狀況。 在 filter 子句中引發例外狀況時，執行階段會以無訊息模式攔截例外狀況。 這將使原始錯誤變得難以偵測及偵錯。 |
| CA2225 | [CA2225:運算子多載必須有具名的替代方法](../code-quality/ca2225.md) |偵測到運算子多載，且找不到預期的具名替代方法。 具名的替代成員會提供與運算子相同的功能存取，並且可供以不支援多載運算子 (Overloaded Operator) 的語言設計程式的開發人員使用。 |
| CA2226 | [CA2226:運算子應該有對稱的多載](../code-quality/ca2226.md) | 類型實作等號比較運算子或不等比較運算子，但未實作相反的運算子。 |
| CA2227 |[CA2227:集合屬性應該為唯讀](../code-quality/ca2227.md) |可寫入的集合屬性允許使用者以不同的集合來取代該集合。 唯讀屬性會從取代過程中停止集合，但是仍然允許設定個別成員。 |
| CA2229 | [CA2229:必須實作序列化建構函式](../code-quality/ca2229.md) | 若要修正此規則的違規情形，請實作序列化建構函式。 針對密封類別，讓建構函式成為 private，否則為 protected。 |
| CA2231 | [CA2231:在覆寫 ValueType.Equals 上多載等號運算子](../code-quality/ca2231.md) | 實值類型會覆寫 Object.Equals，但不會實作等號比較運算子。 |
| CA2234 | [CA2234:必須傳遞 System.Uri 物件而非字串](../code-quality/ca2234.md) | 呼叫字串參數名稱包含 "uri"、"URI"、"urn"、"URN"、"url" 或 "URL"， 而且此方法的宣告類型會包含具有 System.Uri 參數的對應方法多載。 |
| CA2235 | [CA2235:必須標記所有不可序列化的欄位](../code-quality/ca2235.md) | 可序列化之類型中所宣告之類型的執行個體 (Instance) 欄位是不可序列化的。 |
| CA2237 | [CA2237:ISerializable 類型必須標記 SerializableAttribute](../code-quality/ca2237.md) | 若要讓通用語言執行平台辨認為可序列化，即使類型透過 ISerializable 介面的實作使用自訂序列化常式，類型仍必須使用 SerializableAttribute 屬性來標記。 |
| CA2241 | [CA2241:必須提供格式化方法的正確引數](../code-quality/ca2241.md) | 傳遞至 System.String.Format 的格式引數不包含對應至每個物件引數的格式項目，反之亦然。 |
| CA2242 |[CA2242:必須正確測試 NaN](../code-quality/ca2242.md) | 此運算式針對 Single.Nan 或 Double.Nan 測試值。 使用 Single.IsNan(Single) 或 Double.IsNan(Double) 即可測試值。 |
| CA2243 |[CA2243:屬性字串常值必須正確剖析](../code-quality/ca2243.md) | 屬性的字串常值參數未針對 URL、GUID 或版本進行正確剖析。 |
| CA2244 | [CA2244：請勿複製索引元素初始化](../code-quality/ca2244.md) | 物件初始化運算式有一個以上的索引元素初始化運算式具有相同的常數索引。 但最後一個初始化運算式是多餘的。 |
| CA2245 | [CA2245：請勿將屬性指派給屬性自身](../code-quality/ca2245.md) | 屬性意外指派給本身。 |
| CA2246 | [CA2246：請勿在相同的陳述式中指派符號及其成員](../code-quality/ca2246.md) | 不建議在相同的語句中指派符號及其成員，也就是欄位或屬性。 如果成員存取的目的是要在指派之前使用符號的舊值，或是在此語句中指派新值，則不會很清楚。 |
| CA2247 | [CA2247：傳遞至 >taskcompletionsource 函式的引數應該是 TaskCreationOptions 列舉，而不是 System.threading.tasks.taskcontinuationoptions> 列舉。](../code-quality/ca2247.md) | >taskcompletionsource 具有可使用 TaskCreationOptions 來控制基礎工作的函式，以及採用儲存在工作中之物件狀態的函式。  不小心傳遞 System.threading.tasks.taskcontinuationoptions> 而非 TaskCreationOptions，會導致呼叫將選項視為狀態。 |
| CA2248 | [CA2248：請提供正確的列舉引數給 Enum.HasFlag](../code-quality/ca2248.md) | 作為引數傳遞至方法呼叫的列舉類型 `HasFlag` ，與呼叫列舉型別不同。 |
| CA2249 | [CA2249：請考慮使用 String.Contains 而非 String.IndexOf](../code-quality/ca2249.md) | `string.IndexOf`使用結果來檢查子字串是否存在/不存在之位置的呼叫，可以取代為 `string.Contains` 。 |
| CA2300 | [CA2300：請勿使用不安全的還原序列化程式 BinaryFormatter](../code-quality/ca2300.md) | 在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。 |
| CA2301 | [CA2301：未先設定 BinaryFormatter.Binder 之前，請勿呼叫 BinaryFormatter.Deserialize](../code-quality/ca2301.md) | 在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。 |
| CA2302 | [CA2302：呼叫 BinaryFormatter.Deserialize 之前，請務必先設定 BinaryFormatter.Binder](../code-quality/ca2302.md) | 在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。 |
| CA2305 | [CA2305：請勿使用不安全的還原序列化程式 LosFormatter](../code-quality/ca2305.md) | 在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。 |
| CA2310 | [CA2310：請勿使用不安全的還原序列化程式 NetDataContractSerializer](../code-quality/ca2310.md) | 在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。 |
| CA2311 | [CA2311：未先設定 NetDataContractSerializer.Binder 之前，請勿還原序列化](../code-quality/ca2311.md) | 在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。 |
| CA2312 | [CA2312：還原序列化之前，請務必先設定 NetDataContractSerializer.Binder](../code-quality/ca2312.md) | 在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。 |
| CA2315 | [CA2315：請勿使用不安全的還原序列化程式 ObjectStateFormatter](../code-quality/ca2315.md) | 在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。 |
| CA2321 | [CA2321：請勿使用 SimpleTypeResolver 搭配 JavaScriptSerializer 來還原序列化](../code-quality/ca2321.md) | 在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。 |
| CA2322 | [CA2322：還原序列化之前，請確定不會使用 SimpleTypeResolver 來將 JavaScriptSerializer 初始化](../code-quality/ca2322.md) | 在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。 |
| CA2326 | [CA2326:請勿使用「無」以外的 TypeNameHandling 值](../code-quality/ca2326.md) | 在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。 |
| CA2327 | [CA2327:請勿使用不安全的 JsonSerializerSettings](../code-quality/ca2327.md) | 在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。 |
| CA2328 | [CA2328:確定 JsonSerializerSettings 安全](../code-quality/ca2328.md) | 在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。 |
| CA2329 | [CA2329:請勿使用不安全的組態來還原序列化 JsonSerializer](../code-quality/ca2329.md) | 在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。 |
| CA2330 | [CA2330:在還原序列化時，請確認 JsonSerializer 有安全的組態](../code-quality/ca2330.md) | 在還原序列化不受信任的資料時，不安全的還原序列化程式很容易。 攻擊者可以修改序列化的資料，以包含未預期的類型，以插入具有惡意副作用的物件。 |
| CA2350 | [CA2350：請確認 DataTable.ReadXml() 的輸入是受信任的](ca2350.md) | <xref:System.Data.DataTable>使用不受信任的輸入還原序列化時，攻擊者可以製作惡意輸入來執行阻斷服務攻擊。 可能有未知的遠端程式碼執行弱點。 |
| CA2351 | [CA2351：請確認 DataSet.ReadXml() 的輸入是受信任的](ca2351.md) | <xref:System.Data.DataSet>使用不受信任的輸入還原序列化時，攻擊者可以製作惡意輸入來執行阻斷服務攻擊。 可能有未知的遠端程式碼執行弱點。 |
| CA2352 | [CA2352：可序列化類型中的不安全 DataSet 或 DataTable 可能容易受到遠端程式碼執行攻擊](ca2352.md) | 標記為的類別或結構 <xref:System.SerializableAttribute> 包含 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 欄位或屬性，而且沒有 <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> 。 |
| CA2353 | [CA2353：可序列化類型中的不安全 DataSet 或 DataTable](ca2353.md) | 以 XML 序列化屬性（attribute）或資料合約屬性（attribute）標記的類別或結構包含 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 欄位或屬性（property）。 |
| CA2354 | [CA2354：還原序列化物件圖中的不安全 DataSet 或 DataTable 可能容易受到遠端程式碼執行攻擊](ca2354.md) | 使用序列化還原序列化 <xref:System.Runtime.Serialization.IFormatter?displayProperty=nameWithType> ，而轉換類型的物件圖形可以包含 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable> 。 |
| CA2355 | [CA2355：還原序列化物件圖中的不安全 DataSet 或 DataTable](ca2355.md) | 在轉換或指定類型的物件圖形可以包含或時還原 <xref:System.Data.DataSet> 序列化 <xref:System.Data.DataTable> 。 |
| CA2356 | [CA2356： web 還原序列化物件圖形中不安全的資料集或 DataTable](ca2356.md) | 具有或的方法 <xref:System.Web.Services.WebMethodAttribute?displayProperty=nameWithType> <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> 具有可參考或的參數 <xref:System.Data.DataSet> <xref:System.Data.DataTable> 。 |
| CA2361 | [CA2361：確認不會搭配不受信任的資料使用包含 DataSet.ReadXml() 的自動產生類別](ca2361.md) | <xref:System.Data.DataSet>使用不受信任的輸入還原序列化時，攻擊者可以製作惡意輸入來執行阻斷服務攻擊。 可能有未知的遠端程式碼執行弱點。 |
| CA2362 | [CA2362：自動產生之可序列化型別中不安全的 DataSet 或 DataTable，容易受到遠端程式碼執行攻擊](ca2362.md) | 當還原序列化未受信任的輸入，而且還原序列化 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 的物件圖形包含 <xref:System.Data.DataSet> 或時 <xref:System.Data.DataTable> ，攻擊者可以製作惡意的內容來執行遠端程式碼執行攻擊。 |
| CA3001 | [CA3001：檢閱程式碼是否有 SQL 插入式攻擊弱點](../code-quality/ca3001.md) | 使用不受信任的輸入和 SQL 命令時，請注意 SQL 插入式攻擊。 SQL 插入式攻擊可能會執行惡意的 SQL 命令，而危及應用程式的安全性和完整性。 |
| CA3002 | [CA3002：檢閱程式碼是否有 XSS 弱點](../code-quality/ca3002.md) | 從 web 要求處理不受信任的輸入時，請注意跨網站腳本 (XSS) 攻擊。 XSS 攻擊會將不受信任的輸入插入原始 HTML 輸出，讓攻擊者可以執行惡意腳本或惡意地修改您網頁中的內容。 |
| CA3003 | [CA3003：檢閱程式碼是否有檔案路徑插入式攻擊弱點](../code-quality/ca3003.md) | 使用來自 web 要求的未受信任輸入時，請留意在指定檔案路徑時使用使用者控制的輸入。 |
| CA3004 | [CA3004：檢閱程式碼是否有資訊洩漏弱點](../code-quality/ca3004.md) | 洩漏例外狀況資訊可讓攻擊者深入瞭解您的應用程式內部，這可協助攻擊者找出其他弱點來進行攻擊。 |
| CA3006 | [CA3006：檢閱程式碼是否有處理序命令插入式攻擊弱點](../code-quality/ca3006.md) | 使用不受信任的輸入時，請注意命令插入式攻擊。 命令插入式攻擊可在基礎作業系統上執行惡意命令，而危及伺服器的安全性和完整性。 |
| CA3007 | [CA3007：檢閱程式碼是否有開放式重新導向弱點](../code-quality/ca3007.md) | 使用不受信任的輸入時，請留意開放式重新導向弱點。 攻擊者可以利用開放式重新導向弱點，使用您的網站提供合法 URL 的外觀，但將不受信任的訪客重新導向至網路釣魚或其他惡意網頁。 |
| CA3008 | [CA3008：檢閱程式碼是否有 XPath 插入式攻擊弱點](../code-quality/ca3008.md) | 使用不受信任的輸入時，請注意 XPath 插入式攻擊。 使用不受信任的輸入來建立 XPath 查詢，可能會讓攻擊者惡意地操作查詢以傳回非預期的結果，而且可能會洩漏所查詢 XML 的內容。 |
| CA3009 | [CA3009：檢閱程式碼是否有 XML 插入式攻擊弱點](../code-quality/ca3009.md) | 使用不受信任的輸入時，請注意 XML 插入式攻擊。 |
| CA3010 | [CA3010：檢閱程式碼是否有 XAML 插入式攻擊弱點](../code-quality/ca3010.md) | 使用不受信任的輸入時，請注意 XAML 插入式攻擊。 XAML 是直接表示物件執行個體化和執行的標記語言。 這表示在 XAML 中建立的元素可以與系統資源互動 (例如，網路存取和檔案系統 IO) 。 |
| CA3011 | [CA3011：檢閱程式碼是否有 DLL 插入式攻擊弱點](../code-quality/ca3011.md) | 使用不受信任的輸入時，請注意載入未受信任的程式碼。 如果您的 web 應用程式載入未受信任的程式碼，攻擊者可能會將惡意 Dll 插入您的進程，並執行惡意程式碼。 |
| CA3012 | [CA3012：檢閱程式碼是否有 regex 插入式攻擊弱點](../code-quality/ca3012.md) | 使用不受信任的輸入時，請注意 RegEx 插入式攻擊。 攻擊者可以使用 RegEx 插入來惡意地修改正則運算式、讓 RegEx 符合非預期的結果，或讓 RegEx 耗用過多的 CPU，造成阻絕服務攻擊。 |
| CA3061 | [CA3061：請勿透過 URL 新增結構描述](../code-quality/ca3061.md) | 請勿使用 Add 方法的 unsafe 多載，因為它可能會造成危險的外部參考。 |
| CA3075 | [CA3075:不安全的 DTD 處理](../code-quality/ca3075.md) | 如果您使用不安全的 DTDProcessing 執行個體或參考外部實體來源，剖析器可能會接受未受信任的輸入，而將機密資訊洩漏給攻擊者。 |
| CA3076 | [CA3076:不安全的 XSLT 指令碼執行](../code-quality/ca3076.md) | 如果您在 .NET 應用程式, 中執行 (XSLT) 的可延伸樣式表語言轉換，處理器可能會解析可能洩漏機密資訊給攻擊者的不受信任 URI 參考，進而導致阻絕服務和跨網站攻擊。 |
| CA3077 | [CA3077:API 設計、XML 文件和 XML 文字讀取器中的不安全處理](../code-quality/ca3077.md) | 針對衍生自 XMLDocument 和 XMLTextReader 的 API 進行設計時，請留意 DtdProcessing。 若在參考或解析外部實體來源時使用不安全的 DTDProcessing 執行個體，或在 XML 中設定不安全的值，都可能會導致資訊洩漏。 |
| CA3147 | [CA3147:使用 ValidateAntiForgeryToken 標示動詞處理常式](../code-quality/ca3147.md) | 設計 ASP.NET MVC 控制器時，請留意跨網站偽造要求的攻擊。 跨網站偽造要求攻擊可以將來自已驗證使用者的惡意要求傳送到您的 ASP.NET MVC 控制器。 |
| CA5350 | [CA5350：請勿使用弱式密碼編譯演算法](../code-quality/ca5350.md) | 現今，弱式加密演算法和雜湊函式用於多種原因，但它們不應該用來保證所保護資料的機密性或完整性。 此規則會在它在程式碼中發現 TripleDES、SHA1 或 RIPEMD160 演算法時觸發。|
| CA5351 | [CA5351 不要使用中斷的密碼編譯演算法](../code-quality/ca5351.md) | 中斷的密碼編譯演算法較不安全，強烈建議您不要使用它們。 此規則會在它在程式碼中發現 MD5 雜湊演算法或 DES 或 RC2 加密演算法時觸發。 |
| CA5358 | [CA5358:不要使用不安全的 Cipher 模式](../code-quality/ca5358.md) | 不要使用不安全的 Cipher 模式 |
| CA5359 | [CA5359 不停用憑證驗證](../code-quality/ca5359.md) | 憑證可協助驗證服務器的身分識別。 用戶端應該驗證伺服器憑證，以確保會將要求傳送給預定的伺服器。 如果 ServerCertificateValidationCallback 一律 `true` 會傳回，任何憑證都會通過驗證。 |
| CA5360 | [CA5360 不會在還原序列化中呼叫危險的方法](../code-quality/ca5360.md) | 不安全的還原序列化是在未受信任的資料用來濫用應用程式邏輯、對拒絕服務 (DoS) 攻擊，或甚至在還原序列化時執行任意程式碼時，就會發生的弱點。 當應用程式將受信任的資料還原序列化時，惡意使用者通常可能會濫用這些還原序列化功能。 具體而言，在還原序列化的過程中叫用危險的方法。 成功的不安全還原序列化攻擊可能會讓攻擊者執行攻擊，例如 DoS 攻擊、驗證略過，以及遠端程式碼執行。 |
| CA5361 | [CA5361：不要停用安全加密的安全通道使用](../code-quality/ca5361.md) | 設定 `Switch.System.Net.DontEnableSchUseStrongCrypto` 以 `true` 削弱輸出傳輸層安全性中使用的密碼編譯 (TLS) 連接。 較弱的密碼編譯可能會危及應用程式與伺服器之間通訊的機密性，讓攻擊者更容易竊聽敏感性資料。 |
| CA5362 | [在還原序列化的物件圖形中 CA5362 可能的參考迴圈](../code-quality/ca5362.md) | 如果還原序列化不受信任的資料，則任何處理已還原序列化之物件圖形的程式碼都必須處理參考迴圈，而不會進入無限迴圈。 這包括屬於還原序列化回呼一部分的程式碼，以及完成還原序列化之後處理物件圖形的程式碼。 否則，攻擊者可能會使用包含參考週期的惡意資料來執行阻斷服務攻擊。 |
| CA5363 | [CA5363：請勿停用要求驗證](../code-quality/ca5363.md) | 要求驗證是 ASP.NET 中的一項功能，可檢查 HTTP 要求，並判斷它們是否包含可能會導致插入式攻擊的潛在危險內容，包括跨網站腳本。 |
| CA5364 | [CA5364:請勿使用已取代的安全性通訊協定](../code-quality/ca5364.md) | 傳輸層安全性 (TLS) 保護電腦之間的通訊安全，最常見的方式是使用超文字傳輸通訊協定安全 (HTTPS) 。 舊版的 TLS 通訊協定版本比 TLS 1.2 和 TLS 1.3 更不安全，而且可能會有新的弱點。 避免較舊的通訊協定版本，以將風險降至最低。 |
| CA5365 | [CA5365 不要停用 HTTP 標頭檢查](../code-quality/ca5365.md) | HTTP 標頭檢查可針對在回應標頭中找到的換行字元和分行符號（\r 和 \n）進行編碼。 這種編碼方式有助於避免利用應用程式回應標頭所含之不受信任資料的插入式攻擊。 |
| CA5366 | [CA5366 針對資料集讀取 XML 使用 XmlReader](../code-quality/ca5366.md) | 使用 <xref:System.Data.DataSet> 來讀取具有不受信任資料的 XML 可能會載入危險的外部參考，而這些參考應透過使用 <xref:System.Xml.XmlReader> 安全解析程式或停用 DTD 處理來限制。 |
| CA5367 | [CA5367 不會序列化具有指標欄位的類型](../code-quality/ca5367.md) | 此規則會檢查是否有具有指標欄位或屬性的可序列化類別。 無法序列化的成員可以是指標，例如以標記的靜態成員或欄位 <xref:System.NonSerializedAttribute> 。 |
| CA5368 | [衍生自頁面之類別的 CA5368 集 ViewStateUserKey](../code-quality/ca5368.md) | 設定此 <xref:System.Web.UI.Page.ViewStateUserKey> 屬性可讓您將識別碼指派給個別使用者的 view state 變數，讓攻擊者無法使用變數來產生攻擊，藉此協助您防止應用程式的攻擊。 否則，將會有跨網站要求偽造的弱點。 |
| CA5369 | [CA5369：請使用 XmlReader 進行還原序列化](../code-quality/ca5369.md) | 處理不受信任的 DTD 和 XML 架構可能會啟用載入危險的外部參考，應使用具有安全解析程式的 XmlReader，或停用 DTD 和 XML 內嵌架構處理來限制。 |
| CA5370 | [CA5370：請使用 XmlReader 驗證讀取器](../code-quality/ca5370.md) | 處理不受信任的 DTD 和 XML 架構可能會啟用載入危險的外部參考。 您可以使用具有安全解析程式的 XmlReader，或是停用 DTD 和 XML 內嵌架構處理，來限制這個危險的載入。 |
| CA5371 | [CA5371：請使用 XmlReader 讀取結構描述](../code-quality/ca5371.md) | 處理不受信任的 DTD 和 XML 架構可能會啟用載入危險的外部參考。 使用具有安全解析程式的 XmlReader，或已停用 DTD 和 XML 內嵌架構處理的 XmlReader 會限制這一點。 |
| CA5372 | [CA5372：請為 XPathDocument 使用 XmlReader](../code-quality/ca5372.md) | 處理來自不受信任資料的 XML 可能會載入危險的外部參考，可以使用具有安全解析程式或停用 DTD 處理的 XmlReader 來限制。 |
| CA5373 | [CA5373：不使用已過時的金鑰衍生函式](../code-quality/ca5373.md) | 此規則會偵測弱式金鑰衍生方法和的調用 <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> `Rfc2898DeriveBytes.CryptDeriveKey` 。 <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> 使用弱式演算法 PBKDF1。 |
| CA5374 | [CA5374 不使用 XslTransform](../code-quality/ca5374.md) | 這 <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> 項規則會檢查程式碼中是否具現化。 <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> 現在已過時，不應該使用。 |
| CA5375 | [CA5375 不要使用帳戶共用存取簽章](../code-quality/ca5375.md) | 帳戶 SAS 可將存取權委派給服務 SAS 不允許的 blob 容器、資料表、佇列和檔案共用的讀取、寫入和刪除作業。 不過，它不支援容器層級的原則，而且對授與的許可權不會有更大的彈性和控制權。 惡意使用者取得之後，您的儲存體帳戶將會很容易遭到入侵。 |
| CA5376 | [CA5376 Use SharedAccessProtocol HttpsOnly](../code-quality/ca5376.md) | SAS 是無法在 HTTP 上以純文字傳輸的機密資料。 |
| CA5377 | [CA5377 使用容器層級存取原則](../code-quality/ca5377.md) | 您可以隨時修改或撤銷容器層級的存取原則。 它對授與的許可權提供更大的彈性和控制權。 |
| CA5378 | [CA5378:請勿停用 ServicePointManagerSecurityProtocols](../code-quality/ca5378.md) | 將設定 `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` 為 `true` 限制 Windows Communication Framework 的 (WCF) 傳輸層安全性 (tls) 使用 tls 1.0 的連接。 該版本的 TLS 將會被取代。 |
| CA5379 | [CA5379 不要使用弱式金鑰衍生函數演算法](../code-quality/ca5379.md) | <xref:System.Security.Cryptography.Rfc2898DeriveBytes>類別預設會使用此 <xref:System.Security.Cryptography.HashAlgorithmName.SHA1> 演算法。 您應該在具有 <xref:System.Security.Cryptography.HashAlgorithmName.SHA256> 或更高版本的函式的某些多載中，指定要使用的雜湊演算法。 請注意， <xref:System.Security.Cryptography.Rfc2898DeriveBytes.HashAlgorithm> 屬性只有一個 `get` 存取子，而且沒有 `overriden` 修飾詞。 |
| CA5380 | [CA5380：不新增憑證至根存放區](../code-quality/ca5380.md) | 此規則會偵測將憑證新增至「信任的根憑證授權單位」憑證存放區中的程式碼。 根據預設，「受信任的根憑證授權單位」憑證存放區會使用符合「Microsoft 根憑證計畫」需求的一組公用 Ca 進行設定。 |
| CA5381 | [CA5381：確保憑證不新增至根存放區](../code-quality/ca5381.md) | 此規則會偵測可能將憑證新增至「信任的根憑證授權單位」憑證存放區中的程式碼。 根據預設，「受信任的根憑證授權單位」憑證存放區會設定一組公開憑證授權單位單位， (CAs) 符合「Microsoft 根憑證計畫」的需求。 |
| CA5382 | [CA5382 在 ASP.NET Core 中使用安全 cookie](../code-quality/ca5382.md) | 透過 HTTPS 提供的應用程式必須使用安全 cookie，這會向瀏覽器指出 cookie 應該只使用安全通訊端層 (SSL) 來傳送。 |
| CA5383 | [CA5383 確保在 ASP.NET Core 中使用安全 cookie](../code-quality/ca5383.md) | 透過 HTTPS 提供的應用程式必須使用安全 cookie，這會向瀏覽器指出 cookie 應該只使用安全通訊端層 (SSL) 來傳送。 |
| CA5384 | [CA5384 不使用數位簽章演算法 (DSA) ](../code-quality/ca5384.md) | DSA 是弱式非對稱式加密演算法。 |
| CA5385 | [CA5385 Use Rivest – Shamir – Adleman (RSA) 演算法的金鑰大小是否足夠](../code-quality/ca5385.md) | 小於2048位的 RSA 金鑰更容易遭受暴力密碼破解攻擊。 |
| CA5386 | [CA5386:避免將 SecurityProtocolType 值寫入程式碼](../code-quality/ca5386.md) | 傳輸層安全性 (TLS) 保護電腦之間的通訊安全，最常見的方式是使用超文字傳輸通訊協定安全 (HTTPS) 。 通訊協定版本 TLS 1.0 和 TLS 1.1 已被取代，而 TLS 1.2 和 TLS 1.3 是最新的。 未來，TLS 1.2 和 TLS 1.3 可能已被取代。 為了確保您的應用程式保持安全，請避免硬式編碼通訊協定版本，並以至少 .NET Framework v 4.7.1 為目標。 |
| CA5387 | [CA5387 不使用沒有反覆運算計數的弱式金鑰衍生函式](../code-quality/ca5387.md) | 這項規則會檢查密碼編譯金鑰是否 <xref:System.Security.Cryptography.Rfc2898DeriveBytes> 以小於100000的反復專案計數產生。 較高的反復專案計數有助於減輕嘗試猜測產生的密碼編譯金鑰的字典攻擊。 |
| CA5388 | [使用弱式金鑰衍生函式時，CA5388 確定有足夠的反復專案計數](../code-quality/ca5388.md) | 這項規則會檢查是否有產生密碼編譯金鑰 <xref:System.Security.Cryptography.Rfc2898DeriveBytes> ，且反覆運算計數可能小於100000。 較高的反復專案計數有助於減輕嘗試猜測產生的密碼編譯金鑰的字典攻擊。 |
| CA5389 | [CA5389：不將封存項目路徑新增至目標檔案系統路徑](../code-quality/ca5389.md) | 檔案路徑可以是相對路徑，而且可能會導致檔案系統在預期的檔案系統目標路徑以外存取，進而導致惡意的設定變更，以及透過配置和等候技術執行遠端程式碼。 |
| CA5390 | [CA5390 不會硬式編碼加密金鑰](../code-quality/ca5390.md) | 若要讓對稱演算法成功，秘密金鑰必須只有傳送者和接收者才知道。 當金鑰硬式編碼時，很容易就能找到。 即使是已編譯的二進位檔，惡意使用者也很容易將其解壓縮。 一旦私密金鑰遭到入侵，就可以直接解密加密文字，而不會再受到保護。 |
| CA5391 | [CA5391 在 ASP.NET Core MVC 控制器中使用 antiforgery 權杖](../code-quality/ca5391.md) | 處理 `POST` 、 `PUT` 、 `PATCH` 或 `DELETE` 要求而不驗證 antiforgery token，可能很容易受到跨網站偽造要求攻擊。 跨網站偽造要求攻擊可以將來自已驗證使用者的惡意要求傳送到您的 ASP.NET Core MVC 控制器。 |
| CA5392 | [CA5392 使用 P/Invoke 的 DefaultDllImportSearchPaths 屬性](../code-quality/ca5392.md) | 根據預設，P/Invoke 函式使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 探查許多目錄，包括要載入之程式庫的目前工作目錄。 這可能是某些應用程式的安全性問題，因而導致 DLL 劫持。 |
| CA5393 | [CA5393 不使用不安全的 DllImportSearchPath 值](../code-quality/ca5393.md) | 預設 DLL 搜尋目錄和元件目錄中可能有惡意的 DLL。 或者，根據執行應用程式的位置而定，應用程式的目錄中可能會有惡意的 DLL。 |
| CA5394 | [CA5394 不使用不安全的隨機性](../code-quality/ca5394.md) | 使用密碼編譯弱式虛擬亂數產生器可能會讓攻擊者預測將產生的安全性敏感性值。 |
| CA5395 | [動作方法的 CA5395 遺漏 HttpVerb 屬性](../code-quality/ca5395.md) | 建立、編輯、刪除或以其他方式修改資料的所有動作方法，都必須使用 antiforgery 屬性來保護，以防止跨網站偽造要求攻擊。 執行 GET 作業應該是安全的作業，不會有副作用，也不會修改您的保存資料。 |
| CA5396 | [CA5396 將 HttpCookie 的 HttpOnly 設定為 true](../code-quality/ca5396.md) | 作為深度防禦措施，請確定安全性敏感的 HTTP cookie 已標示為 HttpOnly。 這表示網頁瀏覽器不允許腳本存取 cookie。 插入的惡意腳本是竊取 cookie 的常見方式。 |
| CA5397 | [CA5397：請勿使用已過時的 SslProtocols 通訊協定](../code-quality/ca5397.md) | 傳輸層安全性 (TLS) 保護電腦之間的通訊安全，最常見的方式是使用超文字傳輸通訊協定安全 (HTTPS) 。 舊版的 TLS 通訊協定版本比 TLS 1.2 和 TLS 1.3 更不安全，而且可能會有新的弱點。 避免較舊的通訊協定版本，以將風險降至最低。 |
| CA5398 | [CA5398：避免以硬式編碼方式寫入 SslProtocols 值](../code-quality/ca5398.md) | 傳輸層安全性 (TLS) 保護電腦之間的通訊安全，最常見的方式是使用超文字傳輸通訊協定安全 (HTTPS) 。 通訊協定版本 TLS 1.0 和 TLS 1.1 已被取代，而 TLS 1.2 和 TLS 1.3 是最新的。 未來，TLS 1.2 和 TLS 1.3 可能已被取代。 為了確保您的應用程式保持安全，請避免硬式編碼通訊協定版本。 |
| CA5399 | [CA5399 肯定會停用 HttpClient 憑證撤銷清單檢查](../code-quality/ca5399.md) | 撤銷的憑證不再受到信任。 攻擊者可以使用它來傳遞某些惡意資料，或竊取 HTTPS 通訊中的敏感性資料。 |
| CA5400 | [CA5400 確定未停用 HttpClient 憑證撤銷清單檢查](../code-quality/ca5400.md) | 撤銷的憑證不再受到信任。 攻擊者可以使用它來傳遞某些惡意資料，或竊取 HTTPS 通訊中的敏感性資料。 |
| CA5401 | [CA5401 不使用 CreateEncryptor 搭配非預設的 IV](../code-quality/ca5401.md) | 對稱式加密應該一律使用不可重複的初始化向量來防止字典攻擊。 |
| CA5402 | [CA5402 使用 CreateEncryptor 搭配預設的 IV](../code-quality/ca5402.md) | 對稱式加密應該一律使用不可重複的初始化向量來防止字典攻擊。 |
| CA5403 | [CA5403:不要硬式編碼憑證](../code-quality/ca5403.md) | `data`或函式的或 `rawData` 參數 <xref:System.Security.Cryptography.X509Certificates.X509Certificate> <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 是硬式編碼。 |
| IL3000 | [IL3000 避免在以單一檔案形式發行時存取元件檔案路徑](../code-quality/il3000.md) | 在發行為單一檔案時，避免使用存取元件檔案路徑 |
| IL3001 | [IL3001 避免在以單一檔案形式發行時存取元件檔案路徑](../code-quality/il3001.md) | 在發佈為單一檔案時，避免存取元件檔案路徑 |
