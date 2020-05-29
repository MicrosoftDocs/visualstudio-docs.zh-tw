---
title: 依據 CheckId 列出 Managed 程式碼的程式碼分析警告
ms.date: 04/18/2019
ms.topic: reference
f1_keywords:
- CA1000
- CA1001
- CA1002
- CA1003
- CA1004
- CA1005
- CA1006
- CA1007
- CA1008
- CA1009
- CA1010
- CA1011
- CA1012
- CS1013
- CS1014
- CA1016
- CA1017
- CA1018
- CA1019
- CA1020
- CA1021
- CA1022
- CA1023
- CA1024
- CS1025
- CA1026
- CA1027
- CA1028
- CA1029
- CA1030
- CA1031
- CA1032
- CA1033
- CA1034
- CA1035
- CA1036
- CA1037
- CA1038
- CA1039
- CA1040
- CA1041
- CA1042
- CA1043
- CA1044
- CA1045
- CA1046
- CA1047
- CA1048
- CA1049
- CA1050
- CA1051
- CA1052
- CA1053
- CA1054
- CA1055
- CA1056
- CA1057
- CA1058
- CA1059
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
- CA1300
- CA1301
- CA1302
- CA1303
- CA1304
- CA1305
- CA1306
- CA1307
- CA1308
- CA1309
- CA1400
- CA1401
- CA1402
- CA1403
- CA1404
- CA1405
- CA1406
- CA1407
- CA1408
- CA1409
- CA1410
- CA1411
- CA1412
- CA1413
- CA1414
- CA1415
- CA1500
- CA1501
- CA1502
- CA1503
- CA1504
- CA1505
- CA1506
- CA1507
- CA1508
- CA1509
- CA1600
- CA1601
- CA1700
- CA1701
- CA1702
- CA1703
- CA1704
- CA1707
- CA1708
- CA1709
- CA1710
- CA1711
- CA1712
- CA1713
- CA1714
- CA1715
- VA1716
- CA1717
- CA1719
- CA1720
- CA1721
- CA1722
- CA1723
- CA1724
- CA1725
- CA1726
- CA1727
- CA1728
- CA1729
- CA1730
- CA1800
- CA1801
- CA1802
- CA1803
- CA1804
- CA1806
- CA1809
- CA1810
- CA1811
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
- CA1900
- CA1901
- CA1903
- CA2000
- CA2001
- CA2002
- CA2003
- CA2004
- CA2006
- CA2007
- CA2009
- CA2011
- CA2015
- CA2100
- CA2101
- CA2102
- CA2103
- CA2104
- CA2105
- CA2106
- CA2107
- CA2108
- CA2109
- CA2110
- CA2111
- CA2112
- CA2114
- CA2115
- CA2116
- CA2117
- CA2118
- CA2119
- CA2120
- CA2121
- CA2122
- CA2123
- CA2124
- CA2126
- CA2127
- CA2128
- CA2129
- CA2130
- CA2131
- CA2132
- CA2133
- CA2134
- CA2135
- CA2136
- CA2137
- CA2138
- CA2139
- CA2140
- CA2141
- CA2142
- CA2143
- CA2144
- CA2145
- CA2146
- CA2147
- CA2148
- CA2149
- CA2150
- CA2151
- CA2200
- CA2201
- CA2202
- CA2204
- CA2205
- CA2207
- CA2208
- CA2210
- CA2211
- CA2212
- CA2213
- CA2214
- CA2215
- CA2216
- CA2217
- CA2218
- CA2219
- CA2220
- CA2221
- CA2222
- CA2223
- CA2224
- CA2225
- CA2226
- CA2228
- CA2229
- CA2227
- CA2230
- CA2231
- CA2232
- CA2233
- CA2234
- CA2235
- CA2236
- CA2237
- CA2238
- CA2239
- CA2240
- CA2241
- CA2242
- CA2243
- CA2245
- CA2246
- CA5122
- CA5374
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6ea04276b7b2fe3dfb5814fbd31602134641b8ef
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84180034"
---
# <a name="code-analysis-warnings-for-managed-code-by-checkid"></a>CheckId 受控碼的程式碼分析警告

下表依照警告的 CheckId 識別項列出 Managed 程式碼的程式碼分析警告。

| CheckId | 警告 | 描述 |
|---------| - | - |
| CA1000 | [CA1000：不要在泛型類型上宣告靜態成員](../code-quality/ca1000.md) | 呼叫泛型類型的靜態成員時，必須為類型指定類型引數。 呼叫不支援介面的泛型執行個體 (Instance) 成員時，必須為成員指定類型引數。 在上述兩種情況下，指定型別引數的語法不同且容易混淆。 |
| CA1001 | [CA1001：具有可處置欄位的類型應該為可處置](../code-quality/ca1001.md) | 類別會宣告及實作類型為 System.IDisposable 的執行個體欄位，且該類別不會實作 IDisposable。 宣告 IDisposable 欄位的類別會間接擁有 Unmanaged 資源，且應實作 IDisposable 介面。 |
| CA1002 | [CA1002：不要公開泛型清單](../code-quality/ca1002.md) | < （of \<(T> ） >）是針對效能（而非繼承）所設計的泛型集合。 因此，List 不包含任何虛擬成員。 應該改為公開專為繼承所設計的泛型集合。 |
| CA1003 | [CA1003：使用一般事件處理常式執行個體](../code-quality/ca1003.md) |類型包含會傳回 void 的委派，其簽章包含兩個參數 (第一個參數是物件，第二個參數則是可指派給 EventArgs 的類型)，而包含組件則會以 Microsoft .NET Framework 2.0 為目標。 |
| CA1004 | [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004.md) | 推斷是指如何利用傳遞到泛型方法的引數類型，而不是利用型別引數的明確規格，來決定泛型方法的型別引數。 若要啟用推斷，泛型方法的參數簽章必須包含與方法之型別參數具有相同類型的參數。 在上述情形中，不必指定類型引數。 使用所有型別參數的推斷時，呼叫泛型和非泛型執行個體方法之語法是相同的；這簡化泛型方法的可用性。 |
| CA1005 | [CA1005：避免在泛型類型上包含過多參數](../code-quality/ca1005.md) | 泛型類型所包含的類型參數越多，就越難了解並記住每個類型參數所代表的含意。 通常會有一個型別參數（如清單中 \<T> ），以及有兩個型別參數（如字典）的某些情況下很明顯 \<TKey, TValue> 。 不過，如果存在兩個以上的類型參數，則對大多數使用者而言都會變得難以理解。 |
| CA1006 | [CA1006：不要在成員簽章中將泛型類型巢狀化](../code-quality/ca1006.md) | 巢狀型別引數就是也是泛型類型的型別引數。 若要呼叫其簽章含有巢狀型別引數的成員，則使用者必須具現化 (Instantiate) 一個泛型類型，並將這個類型傳遞給第二個泛型類型的建構函式。 必要程序及語法十分複雜，且應予以避免。 |
| CA1007 |[CA1007:建議在適當時使用泛型](../code-quality/ca1007.md) | 外部可見的方法包含 System.Object 類型的傳址參數。 使用泛型方法可讓所有類型 (遵守條件約束) 傳遞給方法，而不需要先將類型轉型為傳址參數類型。 |
| CA1008 | [CA1008:列舉值中應該要有值為零的成員](../code-quality/ca1008.md) | 如同其他實值類型一般，未初始化的列舉其預設值為零。 非旗標屬性的列舉應該要使用零值來定義成員，讓預設值成為列舉的有效值。 如果已套用 FlagsAttribute 屬性的列舉定義零值成員，則其名稱應該是 "None"，以表示列舉中未設定任何值。 |
| CA1009 | [CA1009:事件處理常式必須正確宣告](../code-quality/ca1009.md) | 事件處理常式方法會採用兩個參數。 第一個的類型為 System.Object 且名稱為 "sender"。 這是引發事件的物件。 第二個參數的類型為 System.EventArgs 且名稱為 "e"。 這是與事件相關聯的資料。 事件處理常式方法不應該傳回值；在 C# 程式設計語言中，這是由 void 傳回型別所表示。 |
| CA1010 | [CA1010:集合應該實作泛型介面](../code-quality/ca1010.md) | 若要放寬集合的可用性，請實作其中一個泛型集合介面。 接著，使用該集合填入泛型集合類型。 |
| CA1011 |[CA1011:建議將基底類型當作參數傳遞](../code-quality/ca1011.md) | 當方法宣告將基底類型指定為參數，則從此基底類型衍生的任何類型都可以當做對應引數傳遞給方法。 如果不需要以衍生參數類型提供額外的功能，則使用基底類型可以更廣泛地運用此方法。 |
| CA1012 | [CA1012:抽象類型不應該有建構函式](../code-quality/ca1012.md) | 只有衍生類型 (Derived Type) 可以呼叫抽象類型上的建構函式。 因為公用建構函式會建立類型的執行個體，而且您無法建立抽象類型的執行個體，因此具有公用建構函式的抽象類型設計不正確。 |
| CA1013 | [CA1013:多載加號和減號運算子時必須一併多載等號比較運算子](../code-quality/ca1013.md) | 公用或保護的類型會實作加法或減法運算，但不會實作等號比較運算子。 |
| CA1014 | [CA1014:組件必須標記 CLSCompliantAttribute](../code-quality/ca1014.md) | Common Language Specification (CLS) 會定義命名限制、資料類型及組件必須遵守的規則 (如果組件會使用於跨程式設計語言時)。 良好的設計會要求所有組件使用 <xref:System.CLSCompliantAttribute> 明確表示 CLS 符合性。 如果這個屬性未出現於組件中，則表示組件不符合標準。 |
| CA1016 | [CA1016:組件必須標記 AssemblyVersionAttribute](../code-quality/ca1016.md) | .NET 會使用版本號碼來唯一識別元件，並系結至強式名稱元件中的類型。 版本號碼會與版本和發行者 (Publisher) 原則一起使用。 應用程式預設只會與建置它們的組件版本一起執行。 |
| CA1017 | [CA1017:組件必須標記 ComVisibleAttribute](../code-quality/ca1017.md) |ComVisibleAttribute 會判斷 COM 用戶端如何存取 Managed 程式碼。 良好的設計會要求組件明確表示 COM 的可視性。 COM 的可視性可以針對整個組件進行設定，然後針對個別類型及類型成員進行覆寫。 如果這個屬性不存在，則 COM 用戶端可以看到組件的內容。 |
| CA1018 | [CA1018:必須以 AttributeUsageAttribute 標記屬性](../code-quality/ca1018.md) | 當您定義自訂屬性時，請使用 AttributeUsageAttribute 標記它，以指出可以在原始程式碼的哪個位置套用自訂屬性。 屬性的意義和預期的用法將決定它在程式碼中的有效位置。 |
| CA1019 | [CA1019:定義屬性引數的存取子](../code-quality/ca1019.md) | 屬性可以定義必須在將屬性套用至目標時指定的強制引數。 這些引數也稱為位置引數，因為它們會當做位置參數提供給屬性建構函式。 對於每個強制引數而言，屬性 (Attribute) 還須提供對應的唯讀屬性 (Property)，才可以在執行時期擷取引數值。 屬性也可以定義選擇性引數，也稱為具名引數。 這些引數會依照名稱提供給屬性 (Attribute) 建構函式，且必須有對應的讀取/寫入屬性 (Property)。 |
| CA1020 | [CA1020:避免在命名空間中包含過少的類型](../code-quality/ca1020.md) | 請確定每個命名空間都有邏輯組織，而且存在合理的理由可以將類型置於沒有嚴密填入的命名空間中。 |
| CA1021 | [CA1021:避免使用 out 參數](../code-quality/ca1021.md) | 以傳址方式傳遞類型時 (使用 out 或 ref)，您需要擁有使用指標的經驗、了解實值類型和參考類型之間的差異，並處理具有多個傳回值的方法。 此外，out 和 ref 參數之間的差異一般人不甚了解。 |
| CA1023 | [CA1023:不應該使用多維索引子](../code-quality/ca1023.md) | 索引子 (也就是索引屬性) 應使用單一索引。 多維索引子會大幅降低程式庫的可用性。 |
| CA1024 | [CA1024:建議在適當時使用屬性](../code-quality/ca1024.md) | 公用或保護的方法具有以 "Get" 開頭的名稱，該名稱不採用任何參數並且會傳回不是陣列的值。 此方法可能是成為屬性的不錯候選者。 |
| CA1025 | [CA1025:以參數陣列取代重複的引數](../code-quality/ca1025.md) | 當引數的正確數目未知，而且變數引數都是相同的類型 (或可以相同的類型傳遞) 時，需使用參數陣列而不是重複的引數。 |
| CA1026 | [CA1026:不應該使用預設參數](../code-quality/ca1026.md) | 允許使用預設參數的方法受制於 CLS。不過，CLS 允許編譯器 (Compiler) 忽略已指派給這些參數的值。 若要在程式語言之間維護您要的行為，則必須以提供預設參數的方法多載來取代使用預設參數的方法。 |
| CA1027 |[CA1027:必須以 FlagsAttribute 標記列舉](../code-quality/ca1027.md) | 列舉類型是一種實值類型 (Value Type)，用以定義一組相關的具名常數。 當列舉的具名常數可以有意義地加以結合時，會將 FlagsAttribute 套用至此列舉。 |
| CA1028 | [CA1028:列舉儲存區應該是 Int32](../code-quality/ca1028.md) | 列舉類型是一種實值類型 (Value Type)，用以定義一組相關的具名常數。 根據預設，System.Int32 資料類型會用於儲存常數值。 雖然您可以變更這個基礎類型，但是大多數情節中仍不需要或不建議進行變更。 |
| CA1030 | [CA1030:建議在適當時使用事件](../code-quality/ca1030.md) |此規則會偵測具有事件常用名稱的方法。 如果方法因回應清楚定義的狀態變更而被呼叫，應該由事件處理常式叫用該方法。 呼叫方法的物件應該要引發事件，而不是直接呼叫方法。 |
| CA1031 | [CA1031:不要攔截一般例外狀況類型](../code-quality/ca1031.md) | 不應該攔截一般例外狀況。 請攔截較明確的例外狀況，或重新擲回一般例外狀況當做 catch 區塊中的最後一個陳述式。 |
| CA1032 |[CA1032:必須實作標準例外狀況建構函式](../code-quality/ca1032.md) | 無法提供整組的建構函式會導致難以正確地處理例外狀況。 |
| CA1033 | [CA1033:介面方法應該要可以由子類型呼叫](../code-quality/ca1033.md) | 非密封外部可見的類型會提供公用介面的明確方法實作，但未提供同名的替代外部可見方法。 |
| CA1034 | [CA1034:巢狀類型不應該為可見的](../code-quality/ca1034.md) | 巢狀類型是在其他類型範圍內宣告的類型。 巢狀類型可用來封裝包含類型 (Containing Type) 私用的 (Private) 實作細節。 因為有這樣的用途，所以巢狀類型不應為外部可見的。 |
| CA1035 | [CA1035:ICollection 的實作有強類型成員](../code-quality/ca1035.md) | 這項規則要求 ICollection 實作提供強類型成員，讓使用者在使用介面所提供的功能時，不需將引數轉換為 Object 類型。 這項規則假設實作 ICollection 的類型會這樣做，以管理效力比 Object 還強之類型的執行個體集合。 |
| CA1036 | [CA1036:必須在 Comparable 類型中覆寫方法](../code-quality/ca1036.md) |公用或受保護的類型實作 System.IComparable 介面。 它不會覆寫 Object.Equals，也不會多載等號、不等、小於或大於的語言特定比較運算子。 |
| CA1038 | [CA1038:列舉程式應該是強類型](../code-quality/ca1038.md) | 此規則要求 IEnumerator 實作同時也提供 Current 屬性的強類型版本，如此當使用者使用介面提供的功能時，就不需要將傳回值轉型為強類型。 |
| CA1039 | [CA1039:清單為強類型](../code-quality/ca1039.md) | 這項規則要求 IList 實作提供強類型成員，讓使用者在使用介面所提供的功能時，不需將引數轉換為 System.Object 類型。 |
| CA1040 |[CA1040:避免使用空的介面](../code-quality/ca1040.md) | 介面是用來定義一組可提供行為或程式使用合約的成員。 不論類型出現在繼承階層架構 (Inheritance Hierarchy) 中的何處，任何類型都可以採用介面所描述的功能。 類型會實作介面，方法是提供介面成員的實作。 空白介面不會定義任何成員，因此也不會定義能夠實作的合約。 |
| CA1041 | [CA1041:必須提供 ObsoleteAttribute 訊息](../code-quality/ca1041.md) | 類型或成員是使用並未指定其 ObsoleteAttribute.Message 屬性 (Property) 的 System.ObsoleteAttribute 屬性 (Attribute) 來標記。 編譯使用 ObsoleteAttribute 來標記的類型或成員之後，會顯示屬性 (Attribute) 的 Message 屬性 (Property)， 以便提供使用者有關過時類型或成員的資訊。 |
| CA1043 | [CA1043:必須針對索引子使用整數或字串引數](../code-quality/ca1043.md) | 索引子 (也就是索引的屬性) 應該使用整數類型或字串類型的索引。 這些類型通常會用於資料結構的索引，可以提升程式庫的可用性。 Object 類型的使用應限制於無法在設計階段指定特定整數類型或字串類型的情況。 |
| CA1044 | [CA1044:屬性不應該為唯寫的](../code-quality/ca1044.md) | 雖然它是可接受並經常需要具有唯讀屬性，設計方針會禁止使用唯寫屬性的屬性。 這是因為讓使用者，設定一個值，然後防止使用者檢視值並不會提供任何安全性。 同時，如果沒有讀取權限，則無法檢視共用物件的狀態，進而限制這些物件的使用性。 |
| CA1045 |[CA1045:不要以傳址方式傳遞類型](../code-quality/ca1045.md) | 以傳址方式傳遞類型時 (使用 out 或 ref)，您需要擁有使用指標的經驗、了解實值類型和參考類型之間的差異，並處理具有多個傳回值的方法。 設計一般物件的程式庫架構師不應預期使用者會使用 `out` 或參數來主控 `ref` 。 |
| CA1046 | [CA1046:不要多載參考類型上的等號比較運算子](../code-quality/ca1046.md) | 對參考類型而言，等號比較運算子的預設實作 (Implementation) 永遠都是正確的。 根據預設，只有當兩項參考都指向相同物件時才會相等。 |
| CA1047 |[CA1047:不要在密封類型中宣告 protected 成員](../code-quality/ca1047.md) | 類型會宣告 protected 成員，如此繼承的類型即可存取或覆寫成員。 根據定義，密封類型無法被繼承，這表示無法呼叫密封類型上的受保護方法。 |
| CA1048 | [CA1048:不要在密封類型中宣告 virtual 成員](../code-quality/ca1048.md) | 類型會將方法宣告為 virtual，讓繼承類型可以覆寫 virtual 方法的實作。 根據預設，密封類型無法被繼承。 這會讓密封類型上的虛擬方法失去意義。 |
| CA1049 | [CA1049:具有原生資源的類型應該要可呼叫 Dispose 方法明確釋放資源](../code-quality/ca1049.md) | 配置 Unmanaged 資源的類型應實作 IDisposable，讓呼叫端視需要釋放這些資源，並且縮短持有資源之物件的存留期。 |
| CA1050 | [CA1050:類型必須在命名空間中宣告](../code-quality/ca1050.md) | 類型會在命名空間之內宣告以防止名稱衝突，而且可當做組織物件階層架構中相關類型的一種方法。 |
| CA1051 | [CA1051:不要宣告可見的執行個體欄位](../code-quality/ca1051.md) | 欄位的主要用法應該是當做實作詳細資料。 欄位應該是私用或內部的，而且應使用屬性公開。 |
| CA1052 | [CA1052:靜態預留位置類型應該為密封的](../code-quality/ca1052.md) | 公用或受保護的類型只包含靜態成員，因此不會利用 sealed (C# 參考) (NotInheritable) 修飾詞宣告它們。 預定不會繼承的類型應該使用 sealed 修飾詞來標記，以禁止使用它做為基底類型。 |
| CA1053 |[CA1053:靜態預留位置類型不應該包含建構函式](../code-quality/ca1053.md) | 公用或巢狀公用類型只宣告靜態成員，而且具有公用或保護的預設建構函式。 建構函式不是必要的，因為呼叫靜態成員不需類型的執行個體。 為了安全，字串多載應該使用字串引數來呼叫統一資源識別項 (URI) 多載。 |
| CA1054 | [CA1054:URI 參數不應該為字串](../code-quality/ca1054.md) | 如果方法使用 URI 字串表示，應該提供採用 URI 類別的對應多載，這樣就可以透過安全的方式提供這些服務。 |
| CA1055 | [CA1055:URI 傳回值不應該為字串](../code-quality/ca1055.md) | 這項規則假設方法會傳回 URI。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 System.Uri 類別以安全的方式提供這些服務。 |
| CA1056 | [CA1056:URI 屬性不應該為字串](../code-quality/ca1056.md) | 此規則假設屬性代表統一資源識別元 (URI)。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 System.Uri 類別以安全的方式提供這些服務。 |
| CA1057 | [CA1057:字串 URI 多載呼叫 System.Uri 多載](../code-quality/ca1057.md) | 類型會宣告方法多載，這些方法多載的差別只在於以 System.Uri 參數取代字串參數。 接受字串參數的多載不會呼叫接受 URI 參數的多載。 |
| CA1058 | [CA1058:類型不應該擴充特定基底類型](../code-quality/ca1058.md) | 外部可見的類型會延伸某些基底類型 (Base Type)。 請使用其他作法。 |
| CA1059 |[CA1059:成員不應該公開特定的具象類型](../code-quality/ca1059.md) | 具象類型就是具有完整實作 (Implementation) 且因此能加以具現化 (Instantiated) 的類型。 若要讓成員能廣泛使用，請使用建議的介面來取代具象類型。 |
| CA1060 | [CA1060：將 P/Invoke 移至 NativeMethods 類別](../code-quality/ca1060.md) | 平台引動方法 (例如使用 System.Runtime.InteropServices.DllImportAttribute 屬性標記的方法，或在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中使用 Declare 關鍵字定義的方法) 都會存取 Unmanaged 程式碼。 這些方法應該是 NativeMethods、SafeNativeMethods 或 UnsafeNativeMethods 類別。 |
| CA1061 |[CA1061:不要隱藏基底類別方法](../code-quality/ca1061.md) | 只有在衍生方法的參數簽章因類型衍生時比基底方法參數簽章中的類型還要弱時，基底類型中的方法才會被衍生類型中的相同具名方法所隱藏。 |
| CA1062 | [CA1062:必須驗證公用方法的引數](../code-quality/ca1062.md) | 所有傳遞至外部可見方法的參考引數都應經過 null 檢查。 |
| CA1063 | [CA1063:必須正確實作 IDisposable](../code-quality/ca1063.md) | 所有的 IDisposable 類型都需正確地實作 Dispose 模式。 |
| CA1064 | [CA1064:例外狀況必須是公用](../code-quality/ca1064.md) | 內部例外狀況只會在自己的內部範圍內顯示。 當例外狀況超出內部範圍後，只能使用基本例外狀況來攔截例外狀況。 如果內部例外狀況是繼承自 <xref:System.Exception> 、 <xref:System.SystemException> 或 <xref:System.ApplicationException> ，外部程式碼將不會有足夠的資訊來知道該如何處理例外狀況。 |
| CA1065 | [CA1065:不要在非預期的位置中引發例外狀況](../code-quality/ca1065.md) | 不可擲回例外狀況 (Exception) 的方法卻擲回例外狀況。 |
| CA1066 | [CA1066：覆寫 Equals 時實作 IEquatable](../code-quality/ca1066.md) | 實值型別 <xref:System.Object.Equals%2A> 會覆寫方法，但不會執行 <xref:System.IEquatable%601> 。 |
| CA1067 | [CA1067：實作 IEquatable 時覆寫 Equals](../code-quality/ca1067.md) | 型別 <xref:System.IEquatable%601> 會執行，但不會覆寫 <xref:System.Object.Equals%2A> 方法。 |
| CA1068 | [CA1068：CancellationToken 參數必須位於最後](../code-quality/ca1068.md) | 方法的 CancellationToken 參數不是最後一個參數。 |
| CA1069 | [CA1069：列舉不能有重複的值](../code-quality/ca1069.md) | 列舉有多個成員明確指派相同的常數值。 |
| CA1070 | [CA1070：不要將事件欄位宣告為虛擬](../code-quality/ca1070.md) | [類似欄位的事件](/dotnet/csharp/language-reference/language-specification/classes#field-like-events)已宣告為虛擬。 |
| CA1200 | [CA1200：請避免使用具有前置詞的 cref 標記](../code-quality/ca1200.md) | XML 檔標記中的[cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute)屬性工作表示「程式碼參考」。 它會指定標記的內部文字是程式碼項目，例如類型、方法或屬性。 請避免使用具有前置詞 `cref` 的標記，因為它會防止編譯器驗證參考。 它也會防止 Visual Studio 的整合式開發環境（IDE）在重構期間尋找和更新這些符號參考。 |
| CA1300 | [CA1300:必須指定 MessageBoxOptions](../code-quality/ca1300.md) | 若要對使用由右至左讀取順序的文化特性 (Culture) 正確顯示訊息方塊，MessageBoxOptions 列舉類型的 RightAlign 和 RtlReading 成員必須傳遞至 Show 方法。 |
| CA1301 | [CA1301:避免使用重複的快速鍵](../code-quality/ca1301.md) | 便捷鍵也稱為快速鍵，可讓鍵盤使用 ALT 鍵存取控制項。 當多個控制項有重複的存取金鑰時，存取金鑰的行為未妥善定義。 |
| CA1302 | [CA1302:不要以硬式編碼的方式加入適用於特定地區設定的字串](../code-quality/ca1302.md) | System.Environment.SpecialFolder 列舉 (Enumeration) 包含參考特殊系統資料夾的成員。 這些資料夾的位置在不同的作業系統上可有不同的值，使用者可以變更某些位置，而且位置會當地語系化。 Environment.GetFolderPath 方法會傳回與 Environment.SpecialFolder 列舉相關聯、已當地語系化且適用於目前執行中之電腦的位置。 |
| CA1303 | [CA1303:不要將常值當作已當地語系化的參數傳遞](../code-quality/ca1303.md) | 外部可見的方法會將字串常值當做參數傳遞至 .NET 的函式或方法，而且該字串應該是可當地語系化的。 |
| CA1304 | [CA1304:必須指定 CultureInfo](../code-quality/ca1304.md) | 方法或建構函式會呼叫具有接受 System.Globalization.CultureInfo 參數之多載的成員，且方法或建構函式未呼叫採用 CultureInfo 參數的多載。 未提供 CultureInfo 或 System.IFormatProvider 物件時，多載成員所提供的預設值可能不會有您希望在所有地區設定中都有的效果。 |
| CA1305 | [CA1305:必須指定 IFormatProvider](../code-quality/ca1305.md) | 方法或建構函式所呼叫的一個或多個成員具有可接受 System.IFormatProvider 參數的多載，但該方法或建構函式並未呼叫可接受 IFormatProvider 參數的多載。 未提供 System.Globalization.CultureInfo 或 IFormatProvider 物件時，多載成員所提供的預設值可能不會有您希望在所有地區設定中都有的效果。 |
| CA1306 | [CA1306:必須設定資料類型的地區設定](../code-quality/ca1306.md) | 地區設定會決定資料的文化特性特定展示項目，例如用於數值、貨幣符號和排序次序的格式。 當您建立 DataTable 或 DataSet 時，您應該明確設定地區設定。 |
| CA1307 | [CA1307:必須指定 StringComparison](../code-quality/ca1307.md) | 字串比較作業會使用未設定 StringComparison 參數的方法多載。 |
| CA1308 |[CA1308:必須將字串標準化為大寫字母](../code-quality/ca1308.md) | 字串應該標準化為大寫字母。 當一小組的字元轉換成小寫字母時，它們無法構成來回行程。 |
| CA1309 | [CA1309:使用循序的 StringComparison](../code-quality/ca1309.md) | 非語言的字串比較作業未將 StringComparison 參數設定為 Ordinal 或 OrdinalIgnoreCase。 藉由明確地將參數設定為 StringComparison.Ordinal 或 StringComparison.OrdinalIgnoreCase，您的程式碼通常可以提升速度、更為正確，也更加可靠。 |
| CA1400 | [CA1400： P/Invoke 進入點應該存在](../code-quality/ca1400.md) |公用或受保護的方法是使用 System.Runtime.InteropServices.DllImportAttribute 屬性來標記。 有可能是找不到 Unmanaged 程式庫，或是方法不符合程式庫中的函式。 |
| CA1401 | [CA1401： P/Invoke 不應為可見](../code-quality/ca1401.md) | 公用類型中公用或保護的方法具有 System.Runtime.InteropServices.DllImportAttribute 屬性 (也會由 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中的 Declare 關鍵字實作)。 但不得公開 (Expose) 此類方法。 |
| CA1402 |[CA1402:避免在 COM 可見介面中多載](../code-quality/ca1402.md) | 當多載方法會對 COM 用戶端公開 (Expose) 時，只有第一個方法多載會保留它的名稱。 後續的多載則會透過將名稱附加至底線字元 (_) 和對應於多載宣告之順序的整數，重新命名為唯一的名稱。 |
| CA1403 | [CA1403:自動配置類型不應該是 COM 可見](../code-quality/ca1403.md) | COM 可見的實值型別會使用設定為 Layoutkind.sequential 標示的 System.runtime.interopservices.outattribute. StructLayoutAttribute 屬性來標記。這些類型的配置可能會在 .NET 版本之間變更，這會中斷需要特定版面配置的 COM 用戶端。 |
| CA1404 | [CA1404 必須：在 P/Invoke 之後立即呼叫 GetLastError](../code-quality/ca1404.md) | 對 Marshal.getlastwin32error 方法或對等的 GetLastError 函式進行呼叫 [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] ，而且緊接在先前的呼叫中，不是作業系統叫用方法。 |
| CA1405 | [CA1405:COM 可見類型的基底類型應該是 COM 可見](../code-quality/ca1405.md) | COM 可見類型會衍生自不是 COM 可見的類型。 |
| CA1406 |[CA1406:避免對 Visual Basic 6 用戶端使用 int64 引數](../code-quality/ca1406.md) | Visual Basic 6 COM 用戶端無法存取 64 位元整數。 |
| CA1407 |[CA1407:避免在 COM 可見類型中使用靜態成員](../code-quality/ca1407.md) | COM 不支援靜態方法。 |
| CA1408 | [CA1408:不要使用 AutoDual ClassInterfaceType](../code-quality/ca1408.md) | 使用雙重介面 (Dual Interface) 的類型可讓用戶端繫結至特定的介面配置。 在未來版本中，若類型或任何基底類型 (Base Type) 的配置有所變更，將會中斷繫結至此介面的 COM 用戶端。 根據預設，如果未指定 ClassInterfaceAttribute 屬性，則會使用分派介面。 |
| CA1409 | [CA1409:Com 可見類型應該是可建立的](../code-quality/ca1409.md) |特別標示為 COM 可見的參考類型 (Reference Type) 包含公用參數化建構函式，但不包含公用預設 (無參數) 建構函式。 COM 用戶端無法建立沒有公用預設建構函式的類型。 |
| CA1410 | [CA1410:應該和 COM 註冊方法對應](../code-quality/ca1410.md) | 類型會宣告使用 System.Runtime.InteropServices.ComRegisterFunctionAttribute 屬性來標記的方法，但是不會宣告使用 System.Runtime.InteropServices.ComUnregisterFunctionAttribute 屬性來標記的方法，反之亦然。 |
| CA1411 | [CA1411:COM 註冊方法不應該為可見的](../code-quality/ca1411.md) | 使用 System.Runtime.InteropServices.ComRegisterFunctionAttribute 屬性或 System.Runtime.InteropServices.ComUnregisterFunctionAttribute 屬性來標記的方法為外部可見。 |
| CA1412 | [CA1412:ComSource 介面必須標記為 IDispatch](../code-quality/ca1412.md) | 類型是使用 System.Runtime.InteropServices.ComSourceInterfacesAttribute 屬性來標記，而且至少其中一個指定的介面不是使用設為 ComInterfaceType.InterfaceIsIDispatch 的 System.Runtime.InteropServices.InterfaceTypeAttribute 屬性來標記。 |
| CA1413 | [CA1413:避免在 COM 可見實值類型中使用非公用欄位](../code-quality/ca1413.md) | COM 可見實值類型的非公用執行個體欄位對 COM 用戶端而言是可見的。 請檢閱不應該公開之資訊的欄位內容，或是會造成未預期的設計或安全性結果的欄位內容。 |
| CA1414 | [CA1414：使用 MarshalAs 標記布林值 P/Invoke 引數](../code-quality/ca1414.md) | 布林資料類型在 Unmanaged 程式碼中有多種表示。 |
| CA1415 | [CA1415：正確宣告 P/Invoke](../code-quality/ca1415.md) | 此規則會尋找以 [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] 函式為目標 (具有指向 OVERLAPPED 結構參數的指標) 的作業系統叫用方法宣告，而且相對應的 Managed 參數不是指向 System.Threading.NativeOverlapped 結構的指標。 |
| CA1500 | [CA1500:變數名稱不應該與欄位名稱相符](../code-quality/ca1500.md) | 執行個體方法宣告參數或區域變數，而其名稱符合宣告類型的執行個體欄位，因此導致錯誤。 |
| CA1501 | [CA1501:避免在物件間過度繼承](../code-quality/ca1501.md) | 類型在其繼承階層架構 (Inheritance Hierarchy) 中超過四個層級的深度。 太深的巢狀類型階層架構可能會難以依循、了解和維護。 |
| CA1502 | [CA1502:避免造成過度複雜的方法](../code-quality/ca1502.md) | 這個規則會測量整個方法中線性獨立路徑的數目，此數目是由條件分支的數目與複雜度決定。 |
| CA1504 | [CA1504:必須檢閱可能造成誤導的欄位名稱](../code-quality/ca1504.md) | 執行個體欄位名稱的開頭為 "s_"，或是 static (在 Visual Basic 中為 Shared) 欄位名稱的開頭為 "m_"。 |
| CA1505 | [CA1505:應避免撰寫無法維護的程式碼](../code-quality/ca1505.md) | 類型或方法的維護性指標值很低。 維護性指標很低代表類型或方法很可能會難以維護，而應該列為需要重新設計的候選目標。 |
| CA1506 | [CA1506:應避免使用結合過度的類別](../code-quality/ca1506.md) | 這個規則會測量類別的耦合，方法是計算類型或方法包含的唯一類型參考數目。 |
| CA1507 | [CA1507:使用 nameof 取代字串](../code-quality/ca1507.md) | 字串常值是用來做為可使用運算式的引數 `nameof` 。 |
| CA1508 | [CA1508:避免使用無作用條件式程式碼](../code-quality/ca1508.md) | 方法具有條件式程式碼，一律會 `true` `false` 在執行時間評估為或。 這會導致條件分支中的無作用程式碼 `false` 。 |
| CA1509 | [CA1509：程式碼度量設定檔中的項目無效](../code-quality/ca1509.md) | 程式碼度量規則（如[CA1501](ca1501.md)、 [CA1502](ca1502.md)、 [CA1505](ca1505.md)和[CA1506](ca1506.md)）提供名為且 `CodeMetricsConfig.txt` 具有無效專案的設定檔。 |
| CA1600 | [CA1600:不要使用 Idle 處理序優先順序](../code-quality/ca1600.md) | 請勿將處理序優先權設定為 Idle。 具有 System.Diagnostics.ProcessPriorityClass.Idle 的處理序會在應該閒置的時候佔用 CPU，因而阻礙 CPU 待命。 |
| CA1601 | [CA1601:不要使用會妨礙電源狀態變更的計時器](../code-quality/ca1601.md) | 更高頻率的週期性活動會使 CPU 始終處於忙碌狀態，並且會干擾用於關閉顯示器和硬碟的省電閒置計時器。 |
| CA1700 | [CA1700:不要在列舉值名稱中包含 'Reserved'](../code-quality/ca1700.md) | 這項規則假設名稱中包含 "reserved" 的列舉成員目前並未使用，但是在未來版本會是重新命名或移除的替代符號 (Placeholder)。 重新命名或移除成員是中斷變更。 |
| CA1701 | [CA1701:資源字串複合字應該使用正確的大小寫](../code-quality/ca1701.md) | 資源字串中的每個字都可依大小寫分割成語彙基元 (Token)。 連續兩個語彙基元的組合都由 Microsoft 拼字檢查程式庫進行檢查。 如果可以辨識，這個字便會產生規則違規。 |
| CA1702 | [CA1702:複合字應該使用正確的大小寫](../code-quality/ca1702.md) | 識別項的名稱包含多個單字，而其中至少有一個單字是大小寫不正確的複合字。 |
| CA1703 | [CA1703:資源字串應該使用正確的拼字](../code-quality/ca1703.md) | 資源字串包含一個或多個 Microsoft 拼字檢查程式庫無法辨識的字。 |
| CA1704 | [CA1704:識別項應該使用正確的拼字](../code-quality/ca1704.md) | 外部可見識別項的名稱包含一個或多個 Microsoft 拼字檢查程式庫無法辨識的字。 |
| CA1707 | [CA1707:識別項名稱不應該包含底線](../code-quality/ca1707.md) | 根據慣例，識別項名稱不包含底線 (_) 字元。 此規則會檢查命名空間、類型、成員和參數。 |
| CA1708 | [CA1708:識別項名稱不應該只靠大小寫區別](../code-quality/ca1708.md) | 因為以通用語言執行平台為目標的語言不需要區分大小寫，因此，命名空間、類型、成員和參數的識別項不能只有大小寫的不同。 |
| CA1709 | [CA1709:識別項名稱應該使用正確的大小寫](../code-quality/ca1709.md) | 依照慣例，參數名稱是使用 Camel 命名法的大小寫慣例，而命名空間、類型和成員名稱則使用 Pascal 命名法的大小寫慣例。 |
| CA1710 | [CA1710:識別項應該使用正確的後置字元](../code-quality/ca1710.md) |依照慣例，擴充某些基底類型或實作某些介面的類型名稱，或從這些類型衍生的類型，都具有與基底類型或介面關聯的後置字元。 |
| CA1711 | [CA1711:識別項名稱不應該使用不正確的後置字元](../code-quality/ca1711.md) | 依照慣例，只有擴充特定基底類型或實作特定介面的類型名稱，或是從這些類型衍生的類型名稱，應以特定保留的後置字元結尾。 其他類型名稱不得使用這些保留的後置字元。 |
| CA1712 | [CA1712:不要使用類型名稱作為列舉值的前置字元](../code-quality/ca1712.md) | 因為開發工具應該提供類型資訊，所以列舉成員的名稱不能以類型名稱做為開頭。 |
| CA1713 | [CA1713:事件不應該有 before 或 after 前置字元](../code-quality/ca1713.md) | 事件的名稱會以 "Before" 或 "After" 為開頭。 若要命名在特定序列 (Sequence) 中引發的相關事件，請使用現在式或過去式表示動作序列相對的位置。 |
| CA1714 | [CA1714:旗標列舉應該使用複數名稱](../code-quality/ca1714.md) | 公用的列舉具有 System.FlagsAttribute 屬性，而且其名稱不能以 "s" 做結尾。 使用 FlagsAttribute 來標記的類型具有複數的名稱，因為這個屬性表示可以指定一個以上的值。 |
| CA1715 | [CA1715:識別項名稱應該使用正確的前置字元](../code-quality/ca1715.md) | 外部可見介面的名稱沒有以大寫 "I" 開頭。 外部可見類型或方法上泛型型別參數的名稱沒有以大寫 "T" 開頭。 |
| CA1716 | [CA1716:識別項名稱不應該和關鍵字相符](../code-quality/ca1716.md) | 命名空間 (Namespace) 名稱或類型名稱符合程式語言中的保留關鍵字。 命名空間和類型的識別項不應該符合語言所定義的關鍵字，而這些語言的目標為 Common Language Runtime。 |
| CA1717 | [CA1717:只有 FlagsAttribute 列舉應該使用複數名稱](../code-quality/ca1717.md) | 依照命名規範的要求，列舉的複數名稱代表可以同時指定多個列舉值。 |
| CA1719 | [CA1719:參數名稱不應該和成員名稱相符](../code-quality/ca1719.md) | 參數名稱應該要能傳達參數的意義，而成員名稱應該要能傳達成員的意義。 兩者相同屬罕見的設計。 如果將參數命名為與成員名稱相同的名稱，則不僅會不容易了解，也會讓程式庫難以使用。 |
| CA1720 |[CA1720:識別項名稱不應該包含類型名稱](../code-quality/ca1720.md) | 外部可見成員中的參數名稱包含資料類型名稱，或外部可見成員的名稱包含語言特定的資料類型名稱。 |
| CA1721 | [CA1721:屬性名稱不應該和其中有 get 的方法名稱相符](../code-quality/ca1721.md) |公用或保護之成員的名稱是以 "Get" 開頭，否則需符合公用或保護之屬性的名稱。 "Get" 方法和屬性的名稱應該清楚區別其功能。 |
| CA1722 | [CA1722:識別項名稱不應該使用不正確的前置字元](../code-quality/ca1722.md) | 根據慣例，只有特定程式設計項目的名稱會以特定的前置字元做為開頭。 |
| CA1724 | [CA1724:類型名稱不應該和命名空間相符](../code-quality/ca1724.md) | 類型名稱不應與 .NET 命名空間的名稱相符。 違反此規則會降低程式庫的可用性。 |
| CA1725 | [CA1725:參數名稱應該符合基底類型的宣告](../code-quality/ca1725.md) | 在覆寫階層架構中一致的參數命名方式，會增加方法覆寫的可用性。 與基底宣告中的名稱不同之衍生方法中的參數名稱，可能會造成方法為基底方法的覆寫或為方法的新多載而混淆。 |
| CA1726 | [CA1726:建議使用慣用詞彙](../code-quality/ca1726.md) | 外部可見的識別項名稱包含有替代慣用詞彙存在的詞彙。 或者該名稱包含 "Flag" 或 "Flags" 一詞。 |
| CA1800 | [CA1800:不要執行不必要的轉換](../code-quality/ca1800.md) | 重複轉型會降低效能，尤其是在精簡型態的反覆運算陳述式中執行轉型時。 |
| CA1801 | [CA1801:必須檢閱未使用的參數](../code-quality/ca1801.md) | 方法簽章包括不用於方法主體中的參數； |
| CA1802 |[CA1802:建議在適當時使用常值](../code-quality/ca1802.md) |欄位宣告為 static 和 read-only (在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中為 Shared 和 ReadOnly)，並使用編譯時期能計算的值進行初始化。 因為指派給目標欄位的值是在編譯時期可，所以請將宣告變更為 const （Const in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ）欄位，以便在編譯時期（而不是在執行時間）計算該值。 |
| CA1804 | [CA1804:必須移除未使用的區域變數](../code-quality/ca1804.md) | 未使用的區域變數和不必要的設定，會增加組件的大小並降低效能。 |
| CA1806 | [CA1806:不要忽略方法的結果](../code-quality/ca1806.md) | 已建立但從未使用新物件、已呼叫會建立並傳回新字串的方法，而新字串從未使用過，或者 COM 或 P/Invoke 方法傳回從未使用的 HRESULT 或錯誤碼。 |
| CA1809 |[CA1809:避免在方法中包含過多區域變數](../code-quality/ca1809.md) | 常見的效能最佳化作法是在處理器暫存器中儲存值，而非記憶體，這稱為「註冊 (Enregistering) 值」。 若要增加所有區域變數都能註冊的機率，請將區域變數的數目限制為 64。 |
| CA1810 | [CA1810:必須將參考類型內部的靜態欄位初始化](../code-quality/ca1810.md) | 當類型宣告明確的靜態建構函式時，Just-In-Time (JIT) 編譯器會將檢查加入至類型的每個靜態方法和執行個體建構函式，確保之前已呼叫該靜態建構函式。 靜態建構函式檢查會降低效能。 |
| CA1811 | [CA1811:避免使用未呼叫的私用程式碼](../code-quality/ca1811.md) | 私用或內部 (組件層級) 成員在組件中沒有呼叫端、不會由通用語言執行平台叫用，而且委派也未叫用該成員。 |
| CA1812 | [CA1812:避免使用未執行個體化的內部類別](../code-quality/ca1812.md) | 組件層級類型的執行個體不是由組件中的程式碼所建立。 |
| CA1813 | [CA1813:避免使用非密封屬性](../code-quality/ca1813.md) | .NET 提供用來抓取自訂屬性的方法。 根據預設，這些方法會搜尋屬性繼承階層架構。 密封屬性會減少對整個繼承階層架構的搜尋，並且可以改進效能。 |
| CA1814 | [CA1814:建議使用不規則陣列取代多維陣列](../code-quality/ca1814.md) | 不規則陣列是一種陣列，其元素也是陣列。 組成元素的陣列大小可以不相同，對於某些資料集而言較不會浪費空間。 |
| CA1815 | [CA1815:必須覆寫實值類型上的 Equals 方法和等號比較運算子](../code-quality/ca1815.md) | 對於實值類型而言，Equals 的繼承實作會使用 Reflection 程式庫，並比較所有欄位的內容。 但是 Reflection 相當耗費運算資源，而且可能不需要比較每個欄位是否相等。 如果希望使用者比較或排序執行個體，或是使用執行個體做為雜湊資料表索引鍵，則您的實值類型應實作 Equals。 |
| CA1816 | [CA1816:正確呼叫 GC.SuppressFinalize](../code-quality/ca1816.md) | 屬於 Dispose 實作的方法不會呼叫 GC.SuppressFinalize，或不屬於 Dispose 實作的方法會呼叫 GC.SuppressFinalize，或呼叫 GC.SuppressFinalize 並傳遞非 this (在 Visual Basic 中為 Me) 的方法。 |
| CA1819 | [CA1819:屬性不應該傳回陣列](../code-quality/ca1819.md) | 即使屬性是唯讀，所傳回的陣列不會是寫入保護。 若要保持陣列為防止遭他人修改，屬性必須傳回陣列複本。 一般而言，使用者不了解呼叫這類屬性所造成的不良效能影響。 |
| CA1820 | [CA1820:應該使用字串長度測試空白字串](../code-quality/ca1820.md) | 使用 String.Length 屬性或 String.IsNullOrEmpty 方法比較字串，明顯地會比使用 Equals 還快。 |
| CA1821 | [CA1821:必須移除空的完成項](../code-quality/ca1821.md) | 請盡可能避免使用完成項，因為追蹤物件存留期 (Lifetime) 時將會產生額外的效能負荷。 空白完成項只會增加額外負荷，而沒有任何好處。 |
| CA1822 |[CA1822:將成員標記為 static](../code-quality/ca1822.md) | 不會存取執行個體資料或不會呼叫執行個體方法的成員，可以標記為 static (在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中為 Shared)。 將方法標記為 static 之後，編譯器將對這些成員發出非虛擬呼叫位置。 這麼做可以讓重視效能的程式碼獲得可觀的效能。 |
| CA1823 | [CA1823:避免包含未使用的私用欄位](../code-quality/ca1823.md) | 偵測到似乎不能在組件內存取的私用欄位。 |
| CA1824 |[CA1824:組件必須標記 NeutralResourcesLanguageAttribute](../code-quality/ca1824.md) | NeutralResourcesLanguage 屬性會通知資源管理員，這是用來顯示元件中性文化特性之資源的語言。 這可改善載入第一個資源的查詢效能，而且可以減少您的工作集。 |
| CA1825 |[CA1825：請避免長度為零的陣列配置](../code-quality/ca1825.md) | 初始化長度為零的陣列會導致不必要的記憶體配置。 相反地，請藉由呼叫來使用靜態配置的空陣列實例 <xref:System.Array.Empty%2A?displayProperty=nameWithType> 。 記憶體配置會在此方法的所有調用之間共用。 |
| CA1826 |[CA1826：請使用屬性，不要使用 Linq Enumerable 方法](../code-quality/ca1826.md) | <xref:System.Linq.Enumerable>LINQ 方法是在支援對等、更有效率的屬性的型別上使用。 |
| CA1827 |[CA1827：不要在可使用 Any 時使用 Count/LongCount](../code-quality/ca1827.md) | <xref:System.Linq.Enumerable.Count%2A><xref:System.Linq.Enumerable.LongCount%2A>使用了或方法，其中 <xref:System.Linq.Enumerable.Any%2A> 方法會更有效率。 |
| CA1828 |[CA1828：不要在可使用 AnyAsync 時使用 CountAsync/LongCountAsync](../code-quality/ca1828.md) | <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.CountAsync%2A><xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.LongCountAsync%2A>使用了或方法，其中 <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.AnyAsync%2A> 方法會更有效率。 |
| CA1829 |[CA1829：請使用 Length/Count 屬性，不要使用 Enumerable.Count 方法](../code-quality/ca1829.md) | <xref:System.Linq.Enumerable.Count%2A>LINQ 方法是在支援對等、更有效率或屬性的型別上使用 `Length` `Count` 。 |
| CA1900 | [CA1900:實值類型欄位應該為可移植的](../code-quality/ca1900.md) | 這項規則會檢查在 64 位元作業系統上封送處理至 Unmanaged 程式碼時，使用明確配置所宣告的結構是否會正確地對齊。 |
| CA1901 | [CA1901： P/Invoke 宣告應該是可移植的](../code-quality/ca1901.md) | 這項規則會評估每個參數的大小和 P/Invoke 的傳回值，並且在 32 位元和 64 位元作業系統上封送處理至 Unmanaged 程式碼時驗證參數的大小是否正確。 |
| CA1903 | [CA1903:只使用來自目標架構的 API](../code-quality/ca1903.md) | 某一個成員或類型使用的是 Service Pack 中所導入的成員或類型，但是專案的目標 Framework 中卻沒有包含該成員或類型。 |
| CA2000 | [CA2000:必須在超出範圍前處置物件](../code-quality/ca2000.md) | 因為可能會發生例外事件以防止執行物件的完成項，所以應在物件的所有參考都超出範圍之前，明確處置物件。 |
| CA2001 | [CA2001:避免呼叫有問題的方法](../code-quality/ca2001.md) | 成員呼叫了可能有危險或問題的方法。 |
| CA2002 |[CA2002:不要鎖定具有弱式識別的物件](../code-quality/ca2002.md) |可以跨應用程式定義域範圍直接存取的物件，即所謂具有弱式識別的物件。 嘗試取得具有弱式識別之物件鎖定的執行緒，可以被不同應用程式定義域中具有相同物件鎖定的第二個執行緒所封鎖。 |
| CA2003 |[CA2003:不要將 Fiber 視為執行緒](../code-quality/ca2003.md) | Managed 執行緒已視為 [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] 執行緒。 |
| CA2004 | [CA2004:必須移除對 GC.KeepAlive 的呼叫](../code-quality/ca2004.md) | 如果轉換成 SafeHandle 用法，則會移除對 GC.KeepAlive (物件) 的所有呼叫。 在這種情況下，類別應該不需要呼叫 GC.KeepAlive。 這是假設它們沒有完成項，但會根據 SafeHandle 最終處理其 OS 控制代碼。 |
| CA2006 | [CA2006:必須使用 SafeHandle 封裝原生資源](../code-quality/ca2006.md) | 在 Managed 程式碼中使用 IntPtr，可能會有潛在的安全性和可靠性問題。 必須檢閱所有使用 IntPtr 的情況，判斷是否需要在該處使用 SafeHandle (或類似技術)。 |
| CA2007 | [CA2007:不直接等候工作](ca2007.md) | 非同步方法會[awaits](/dotnet/csharp/language-reference/keywords/await)直接等候 <xref:System.Threading.Tasks.Task> 。 當非同步方法直接等候時 <xref:System.Threading.Tasks.Task> ，接續會在建立工作的同一個執行緒中發生。 這種行為在效能方面可能會很昂貴，而且可能會導致 UI 執行緒上發生鎖死。 請考慮呼叫 <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> 以指示接續的意圖。 |
| CA2009 | [CA2009：請勿對 ImmutableCollection 值呼叫 TolmmutableCollection](ca2009.md) | `ToImmutable`不必要地在命名空間的不可變集合上呼叫方法 <xref:System.Collections.Immutable> 。 |
| CA2011 | [CA2011：不要在其 setter 中指派屬性](ca2011.md) | 屬性在其本身的[set 存取](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor)子中不小心指派了值。 |
| CA2015 | [CA2015：請勿針對衍生自 MemoryManager T 的類型定義完成項 &lt;&gt;](ca2015.md) | 將完成項加入至衍生自的類型 <xref:System.Buffers.MemoryManager%601> 時，可能會允許記憶體在仍由使用時釋放 <xref:System.Span%601> 。 |
| CA2100 | [CA2100:必須檢閱 SQL 查詢中是否有安全性弱點](../code-quality/ca2100.md) | 方法會使用透過字串引數所建置的字串，將 System.Data.IDbCommand.CommandText 屬性設定為方法。 這項規則假設字串引數包含使用者輸入。 從使用者輸入所建置的 SQL 命令字串很容易遭到 SQL 插入 (SQL Injection) 攻擊。 |
| CA2101 |[CA2101 必須：指定 P/Invoke 字串引數的封送處理](../code-quality/ca2101.md) | 平台叫用成員允許部分信任的呼叫端、具有字串參數，並且未明確封送處理字串。 這樣會造成安全性弱點。 |
| CA2102 | [CA2102:必須使用一般處理常式攔截非 CLSCompliant 例外狀況](../code-quality/ca2102.md) | 組件中不是使用 RuntimeCompatibilityAttribute 來標記或是以 RuntimeCompatibility(WrapNonExceptionThrows = false) 標記的成員包含處理 System.Exception 的 catch 區塊，同時不包含緊接其後的一般 catch 區塊。 |
| CA2103 | [CA2103:必須檢閱命令式安全性](../code-quality/ca2103.md) |方法會使用命令式安全性，而且可能會利用只要要求正在使用中就可能變更的狀態資訊或傳回值建構權限。 請盡可能使用宣告式安全性。 |
| CA2104 |[CA2104:不要宣告唯讀的可變動參考類型](../code-quality/ca2104.md) | 外部可見類型包含了可變動參考類型的外部可見唯讀欄位。 可變動類型是可以修改執行個體資料的類型。 |
| CA2105 | [CA2105:陣列欄位不應該為唯讀](../code-quality/ca2105.md) |當您將唯讀 (在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中為 ReadOnly) 修飾詞套用至包含陣列的欄位時，欄位就不能變更為參考不同的陣列。 但是，儲存在唯讀欄位的陣列元素則可以變更。 |
| CA2106 | [CA2106:必須保護判斷提示](../code-quality/ca2106.md) | 方法會判斷提示使用權限，而且不會在呼叫端上執行安全性檢查。 判斷提示安全性權限但未執行任何安全性檢查，會在您的程式碼中留下可能遭利用的安全性弱點。 |
| CA2107 | [CA2107:必須檢閱 Deny 和 Permit Only 的使用方式](../code-quality/ca2107.md) |只有具備 .NET 安全性的先進知識的使用者，才應該使用 PermitOnly 方法和 Codeaccesspermission.deny 安全性動作。 而使用這些安全性動作的程式碼應該接受安全性檢閱。 |
| CA2108 | [CA2108:必須檢閱實值類型上的宣告式安全性](../code-quality/ca2108.md) | 公用或受保護的實值類型受到資料存取或連結要求保護。 |
| CA2109 | [CA2109:必須檢閱可見的事件處理常式](../code-quality/ca2109.md) | 偵測到公用或保護的事件處理方法。 除非有絕對的必要性，否則不應該公開事件處理方法。 |
| CA2111 |[CA2111:指標不應該為可見的](../code-quality/ca2111.md) | 指標不為私用、內部或唯讀。 惡意的程式碼可變更指標值，進而可能會允許存取記憶體中的任意位置，或是造成應用程式或系統失敗。 |
| CA2112 | [CA2112:受保護類型不應該公開欄位](../code-quality/ca2112.md) | 公用或受保護的類型包含公用欄位，而且受到連結要求保護。 如果程式碼可存取受連結要求保護的類型執行個體，則程式碼不必滿足連結要求即可存取類型的欄位。 |
| CA2114 | [CA2114:方法安全性應該是類型的超集](../code-quality/ca2114.md) | 方法不應該同時具有相同動作的方法層級和類型層級宣告式安全性。 |
| CA2115 | [CA2115:使用原生資源時必須呼叫 GC.KeepAlive](../code-quality/ca2115.md) | 此規則所偵測的錯誤，可能是因為在 Unmanaged 程式碼仍在使用 Unmanaged 資源時，就完成 Unmanaged 資源所致。 |
| CA2116 | [CA2116:APTCA 方法應該只呼叫 APTCA 方法](../code-quality/ca2116.md) |當完全信任的組件中出現 APTCA (AllowPartiallyTrustedCallersAttribute) 屬性，並且組件在不允許部分信任呼叫端的另一個組件中執行程式碼時，可能會發生安全性弱點攻擊。 |
| CA2117 | [CA2117:APTCA 類型應該只擴充 APTCA 基底類型](../code-quality/ca2117.md) | 當完全受信任的組件中含有 APTCA，並且組件中的類型會繼承自不允許部分信任之呼叫端的類型時，就可能會產生安全性弱點。 |
| CA2118 | [CA2118:檢閱 SuppressUnmanagedCodeSecurityAttribute 使用方法](../code-quality/ca2118.md) |對於執行使用 COM Interop 或作業系統引動過程之 Unmanaged 程式碼的成員，SuppressUnmanagedCodeSecurityAttribute 會變更安全性系統的預設行為。 這個屬性主要是用於增加效能，不過，效能提升會伴隨顯著的安全性風險。 |
| CA2119 | [CA2119:密封方法以滿足私用介面的要求](../code-quality/ca2119.md) | 可繼承的公用類型會提供內部 (在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中為 Friend) 介面的可覆寫方法實作。 若要修正此規則的違規情形，請避免在組件外覆寫方法。 |
| CA2120 | [CA2120:必須保護序列化建構函式](../code-quality/ca2120.md) | 這個類型有接受 System.Runtime.Serialization.SerializationInfo 物件和 System.Runtime.Serialization.StreamingContext 物件 (序列化建構函式的簽章) 的建構函式。 這個建構函式未受到安全性檢查的保護，但類型中有一個或多個規則建構函式是受到保護的。 |
| CA2121 | [CA2121:靜態建構函式應該為私用的](../code-quality/ca2121.md) | 系統會在建立類型的第一個執行個體或參考任何靜態成員之前呼叫靜態建構函式。 如果靜態建構函式不是私用的，則可由系統以外的程式碼呼叫。 視建構函式中執行的作業而定，這會造成非預期的行為。 |
| CA2122 | [CA2122:不要間接公開具有連結要求的方法](../code-quality/ca2122.md) | 公用或受保護的成員具有連結要求，而且是由未執行任何安全性檢查的成員所呼叫。 連結要求只會檢查立即呼叫端的使用權限。 |
| CA2123 | [CA2123:覆寫連結要求應該與基底相同](../code-quality/ca2123.md) | 這項規則會使方法符合它的基底方法，即另一個類型中的介面或虛擬方法，然後比較每個方法上的連結要求。 如果違反這項規則，則惡意呼叫端只需呼叫不安全的方法，就可以略過連結要求。 |
| CA2124 | [CA2124:必須將有弱點的 finally 子句包裝在外層 try 中](../code-quality/ca2124.md) | 公用或受保護的方法包含 try/finally 區塊。 finally 區塊似乎會重設安全性狀態，而且不會封入 finally 區塊中。 |
| CA2126 | [CA2126:必須同時具有類型連結要求和繼承要求](../code-quality/ca2126.md) | 公用 unsealed 類型是使用連結要求提供保護，並且具有可以覆寫的方法。 此類型或方法都不是使用繼承要求提供保護。 |
| CA2130 | [CA2130:安全性關鍵常數應該是透明的](../code-quality/ca2130.md) | 因為編譯器內嵌常數的值，所以沒有針對常數值強制透明度，因此在執行階段不需要查詢。 常數欄位應該具備安全性透明，程式碼檢閱者才不會假設透明程式碼無法存取常數。 |
| CA2131 | [CA2131:安全性關鍵類型可能未參與類型等價](../code-quality/ca2131.md) | 類型會參與使用 SecurityCriticalAttribute 屬性標記的類型等價或類型本身，或是類型的成員或欄位。 當任何關鍵類型包含的關鍵方法或欄位有參與類型等價時，就會針對此類型引發此規則。 當 CLR 偵測到這種類型時，它不會在執行階段使用 TypeLoadException 載入此類型。 一般而言，當使用者手動實作類型等價 (而非依賴 tlbimp 而由編譯器執行類型等價) 時，會引發此規則。 |
| CA2132 | [CA2132:預設建構函式至少必須和基底類型的預設建構函式一樣關鍵](../code-quality/ca2132.md) |Silverlight 應用程式的程式碼不能使用內含 SecurityCriticalAttribute 的類型和成員。 重視安全性的類型以及成員，只能夠由 .NET Framework for Silverlight 類別庫中的受信任程式碼使用。 由於衍生類別中的公用或受保護建構所具有的透明度必須大於或等於其基底類別，因此應用程式中的類別不可衍生自標記為 SecurityCritical 的類別。 |
| CA2133 | [CA2133:委派必須繫結至具有一致透明度的方法](../code-quality/ca2133.md) | 當方法會將使用 SecurityCriticalAttribute 標記的委派繫結到透明方法，或繫結到使用 SecuritySafeCriticalAttribute 標記的方法時，就會針對此方法發出警告。 此警告也會針對將透明或安全關鍵性的委派繫結至關鍵方法的方法引發。 |
| CA2134 | [CA2134:覆寫基底方法時，方法必須保持一致的透明度](../code-quality/ca2134.md) |當使用 SecurityCriticalAttribute 標記的方法覆寫透明方法，或覆寫使用 SecuritySafeCriticalAttribute 標記的方法時，就會引發此規則。 當透明或使用 SecuritySafeCriticalAttribute 來標記的方法覆寫使用 SecurityCriticalAttribute 來標記的方法時，也會引發此規則。 覆寫虛擬方法或實作介面時會套用此規則。 |
| CA2135 | [CA2135:層級 2 組件不應該包含 LinkDemand](../code-quality/ca2135.md) | LinkDemand 在層級 2 安全性規則集中已被取代。 不使用 LinkDemand 在 JIT 編譯時期強制執行安全性，改為使用 SecurityCriticalAttribute 屬性來標記方法、類型和欄位。 |
| CA2127 | [CA2136:成員不應該具有衝突的透明度註釋](../code-quality/ca2136.md) | 關鍵程式碼不能出現在100% 透明的元件中。 此規則會針對類型、欄位和方法層級的任何 SecurityCritical 注釋，分析100% 透明的元件。 |
| CA2136 | [CA2136:成員不應該具有衝突的透明度註釋](../code-quality/ca2136.md) | 透明度屬性會從較大範圍的程式碼項目套用至較小範圍的項目。 範圍較大之程式碼項目的透明度屬性優先於第一個項目中所包含之程式碼項目的透明度屬性。 例如，使用 SecurityCriticalAttribute 屬性來標記的類別不得包含使用 SecuritySafeCriticalAttribute 屬性來標記的方法。 |
| CA2137 | [CA2137:透明方法必須只包含可驗證的 IL](../code-quality/ca2137.md) | 方法包含無法驗證的程式碼，或以傳址方式傳回類型。 當安全性透明程式碼嘗試執行無法驗證的 Microsoft Intermediate Language (MISL) 時，就會引發此規則。 不過，此規則不包含完整的 IL 驗證器，並是使用啟發式來擷取多數的 MSIL 驗證違規情形。 |
| CA2138 | [CA2138:透明方法不可以使用 SuppressUnmanagedCodeSecurity 屬性呼叫方法](../code-quality/ca2138.md) | 安全性透明方法會呼叫使用 SuppressUnmanagedCodeSecurityAttribute 屬性標記的方法。 |
| CA2139 | [CA2139:透明方法不能使用 HandleProcessCorruptingExceptions 屬性](../code-quality/ca2139.md) | 此規則是由任何透明並且嘗試使用 HandleProcessCorruptedStateExceptionsAttribute 屬性來處理處理序損毀例外狀況的方法所引發。 處理序損毀例外狀況是 AccessViolationException 這類例外狀況的 CLR 4.0 版例外狀況分類。 HandleProcessCorruptedStateExceptionsAttribute 屬性只能供安全性關鍵方法使用，若套用至透明方法則會被忽略。 |
| CA2129 | [CA2140:透明程式碼不可以參考安全性關鍵項目](../code-quality/ca2140.md) | 由 SecurityTransparentAttribute 標記的方法可呼叫標記為 SecurityCritical 的非公用成員。 此規則會分析混合透明/關鍵之組件中的所有方法和類型，而且如果從透明程式碼對非公用關鍵程式碼所做的任何呼叫未標記為 SecurityTreatAsSafe，也會將這些呼叫加上旗標。 |
| CA2140 | [CA2140:透明程式碼不可以參考安全性關鍵項目](../code-quality/ca2140.md) | 使用 SecurityCriticalAttribute 屬性來標記的程式碼項目就是安全性關鍵。 透明方法不能使用安全性關鍵項目。 如果透明類型嘗試使用安全性關鍵類型，就會引發 TypeAccessException、MethodAccessException 或 FieldAccessException。 |
| CA2141 |[CA2141：透明方法不可以滿足 LinkDemand](../code-quality/ca2141.md) | 安全性透明方法會呼叫未使用 APTCA 標記之組件中的方法，或是安全性透明方法會滿足類型或方法的 LinkDemand。 |
| CA2142 | [CA2142:透明程式碼不可以使用 LinkDemand 加以保護](../code-quality/ca2142.md) | 此規則會針對需要 LinkDemand 才能存取的透明方法引發。 安全性透明程式碼不應負責驗證作業的安全性，因此不應要求權限。 |
| CA2143 | [CA2143:透明方法不可以使用安全性要求](../code-quality/ca2143.md) | 安全性透明程式碼不應負責驗證作業的安全性，因此不應要求權限。 安全性透明程式碼應使用完整的要求做出安全性決策，而且安全關鍵程式碼不應依賴透明程式碼提出完全要求。 |
| CA2144 | [CA2144:透明程式碼不可以從位元組陣列載入組件](../code-quality/ca2144.md) | 透明程式碼的安全性檢閱不如關鍵性程式碼的安全性檢閱完整，因為透明程式碼無法執行安全性敏感動作。 透明程式碼中可能不會注意到從位元組陣列載入的組件，而該位元組陣列可能包含需要稽核之重大或更重要的安全關鍵性程式碼。 |
| CA2145 | [CA2145:透明方法不可以使用 SuppressUnmanagedCodeSecurityAttribute 來裝飾](../code-quality/ca2145.md) | 以 SuppressUnmanagedCodeSecurityAttribute 屬性裝飾的方法會在任何方法呼叫它時放置隱含的 LinkDemand。 這個 LinkDemand 會要求呼叫程式碼具備安全性關鍵。 使用 SecurityCriticalAttribute 屬性來標記使用 SuppressUnmanagedCodeSecurity 的方法會使方法呼叫端的這個需求更為明顯。 |
| CA2146 | [CA2146:類型至少必須和基底類型與介面一樣關鍵](../code-quality/ca2146.md) | 當衍生類型有安全性透明屬性，且該屬性的重要性不如基底類型或已實作之介面時，就會引發這個規則。 只有關鍵類型可以衍生自關鍵基底類型或實作關鍵介面，而且只有關鍵或安全關鍵類型可以衍生自安全關鍵基底類型或實作安全關鍵介面。 |
| CA2128 |[CA2147:CA2147：透明方法不可以使用安全性判斷提示](../code-quality/ca2147.md) | 此規則會分析元件中的所有方法和類型，其為100% 透明或混合透明/重大，並會旗標判斷提示的任何宣告式或命令式用法。 |
| CA2147 |[CA2147:CA2147：透明方法不可以使用安全性判斷提示](../code-quality/ca2147.md) | 標記為 SecurityTransparentAttribute 的程式碼並未具備足夠的使用權限可以進行判斷提示。 |
| CA2149 | [CA2149:透明方法不可以呼叫機器碼](../code-quality/ca2149.md) | 在任何直接呼叫進入機器碼的透明方法上 (例如，透過 P/Invoke)，都會引發此規則。 違反此規則會導致層級 2 透明度模型出現 MethodAccessException，而在層級 1 透明度模型會出現對 UnmanagedCode 的完整要求。 |
| CA2151 |[CA2151:具有關鍵類型的欄位應為安全性關鍵](../code-quality/ca2151.md) | 若要使用安全性關鍵類型，參考該類型的程式碼必須是安全性關鍵或安全性安全關鍵。 即使是間接參考也是如此。 因此，使用安全性透明或安全性安全關鍵欄位容易發生錯誤，因為透明程式碼仍然無法存取該欄位。 |
| CA2200 | [CA2200:必須重新擲回以保存堆疊詳細資料](../code-quality/ca2200.md) | 例外狀況遭到重新擲回，而且已在 throw 陳述式中明確指定此例外狀況。 如果例外狀況是透過在陳述式中指定例外狀況而重新擲回，則會遺失在擲回例外狀況之原始方法和目前方法之間呼叫的方法清單。 |
| CA2201 | [CA2201:不要引發保留的例外狀況類型](../code-quality/ca2201.md) | 這將使原始錯誤變得難以偵測及偵錯。 |
| CA2202 | [CA2202:不要多次處置物件的 Dispose 方法](../code-quality/ca2202.md) |方法實作包含程式碼路徑，可在相同物件上造成多個 System.IDisposable.Dispose 呼叫或 Dispose 對等用法 (例如，部分類型上的 Close() 方法)。 |
| CA2204 | [CA2204:常值必須使用正確的拼字](../code-quality/ca2204.md) | 方法主體中的常值 (Literal) 字串包含一個或多個 Microsoft 拼字檢查程式庫無法辨識的字。 |
| CA2205 | [CA2205:必須使用 Win32 API 的受控對應項](../code-quality/ca2205.md) | 已定義作業系統叫用方法，且具有對等功能的 .NET 方法可供使用。 |
| CA2207 | [CA2207:必須將實值類型的靜態欄位內嵌初始化](../code-quality/ca2207.md) | 實值類型會宣告明確的靜態建構函式。 若要修正此規則的違規情形，請在宣告所有靜態資料時將靜態資料初始化，並移除靜態建構函式。 |
| CA2208 |[CA2208:必須正確執行個體化引數例外狀況](../code-quality/ca2208.md) | 對例外狀況類型為 (或衍生自) ArgumentException 的預設 (無參數) 建構函式進行呼叫，或將錯誤的字串引數傳遞至例外狀況類型為 (或衍生自) ArgumentException 的參數化建構函式。 |
| CA2210 |[CA2210:組件應該具備有效的強式名稱](../code-quality/ca2210.md) | 強式名稱可避免用戶端在不知情的狀況下，載入已遭他人修改的組件。 除了極少數的案例以外，您都應該避免部署沒有強式名稱的組件。 如果您共用或散發未正確簽署的組件，表示這個組件或許已遭他人修改，通用語言執行平台可能不會載入組件，或是使用者可能必須停用電腦上的驗證作業。 |
| CA2211 |[CA2211:非常數欄位不應該為可見的](../code-quality/ca2211.md) | 既非常數，亦非唯讀的靜態欄位不是安全執行緒。 必須小心控制對這類欄位的存取，而且需要進階的程式設計技巧來同步處理對類別物件的存取。 |
| CA2212 | [CA2212:不要以 WebMethod 標記 Serviced 元件](../code-quality/ca2212.md) |類型中繼承自 System.EnterpriseServices.ServicedComponent 的方法是使用 System.Web.Services.WebMethodAttribute 來標記。 因為 WebMethodAttribute 和 ServicedComponent 方法具有衝突的內容和異動流程的行為及需求，所以方法的行為在某些情節中會是不正確的。 |
| CA2213 | [CA2213:可處置的欄位應該受到處置](../code-quality/ca2213.md) | 實作 System.IDisposable 的類型宣告了也實作 IDisposable 之類型的欄位。 宣告類型的 Dispose 方法不會呼叫欄位的 Dispose 方法。 |
| CA2214 | [CA2214:不要呼叫建構函式中的可覆寫方法](../code-quality/ca2214.md) | 當建構函式呼叫虛擬方法時，叫用此方法之執行個體的建構函式可能尚未執行。 |
| CA2215 | [CA2215:Dispose 方法應該呼叫基底類別處置](../code-quality/ca2215.md) | 如果類型會繼承自可處置的類型，則必須從本身的 Dispose 方法呼叫基底類型的 Dispose 方法。 |
| CA2216 |[CA2216:可處置的類型應該宣告完成項](../code-quality/ca2216.md) | 實作 System.IDisposable 且具有建議 Unmanaged 資源用法之欄位的類型，未實作如 Object.Finalize 所述的完成項。 |
| CA2217 | [CA2217:不要以 FlagsAttribute 標記列舉](../code-quality/ca2217.md) |從外部可見的列舉會使用 FlagsAttribute 來標記，並且有一個或多個不是二的次方，或組合列舉上其他定義值之次方的值。 |
| CA2218 |[CA2218:覆寫 Equals 時必須一併覆寫 GetHashCode](../code-quality/ca2218.md) | GetHashCode 會依據目前執行個體傳回值，適用於雜湊演算法和資料結構，如雜湊資料表。 兩個類型相同且相等的物件必須傳回相同的雜湊程式碼。 |
| CA2219 | [CA2219:不要在 exception 子句中引發例外狀況](../code-quality/ca2219.md) | 在 finally 或 fault 子句中引發例外狀況時，新的例外狀況會隱藏作用中的例外狀況。 在 filter 子句中引發例外狀況時，執行階段會以無訊息模式攔截例外狀況。 這將使原始錯誤變得難以偵測及偵錯。 |
| CA2220 | [CA2220:完成項應該呼叫基底類別完成項](../code-quality/ca2220.md) | 最終化必須透過繼承階層架構 (Inheritance Hierarchy) 進行傳播。 若要確保這一點，則類型必須在它們自己的 Finalize 方法中呼叫基底類別 Finalize 方法。 |
| CA2221 |[CA2221:Finalizer 方法應該為 protected](../code-quality/ca2221.md) | 完成項必須使用系列存取修飾詞 (Modifier)。 |
| CA2222 | [CA2222:不要降低繼承成員的可視性](../code-quality/ca2222.md) |您不得變更繼承成員的存取修飾詞 (Modifier)。 將繼承成員變更為私用不會防止呼叫端存取方法的基底類別 (Base Class) 實作。 |
| CA2223 | [CA2223:成員不應該只有在傳回類型上不同](../code-quality/ca2223.md) | 雖然通用語言執行平台允許使用傳回類型區分其他部分都相同的成員，但這個功能不屬於 Common Language Specification，也不是 .NET 程式語言共通的功能。 |
| CA2224 | [CA2224:多載等號比較運算子時必須一併覆寫 Equals](../code-quality/ca2224.md) | 公用類型會實作等號比較運算子，但不會覆寫 Object.Equals。 |
| CA2225 | [CA2225:運算子多載必須有具名的替代方法](../code-quality/ca2225.md) |偵測到運算子多載，且找不到預期的具名替代方法。 具名的替代成員會提供與運算子相同的功能存取，並且可供以不支援多載運算子 (Overloaded Operator) 的語言設計程式的開發人員使用。 |
| CA2226 | [CA2226:運算子應該有對稱的多載](../code-quality/ca2226.md) | 類型實作等號比較運算子或不等比較運算子，但未實作相反的運算子。 |
| CA2227 |[CA2227:集合屬性應該為唯讀](../code-quality/ca2227.md) |可寫入的集合屬性允許使用者以不同的集合來取代該集合。 唯讀屬性會從取代過程中停止集合，但是仍然允許設定個別成員。 |
| CA2228 | [CA2228:不要使用尚未發行版本所支援的格式建置資源](../code-quality/ca2228.md) | 支援的 .NET 版本可能無法使用以發行前版本 .NET 建立的資源檔。 |
| CA2229 | [CA2229:必須實作序列化建構函式](../code-quality/ca2229.md) | 若要修正此規則的違規情形，請實作序列化建構函式。 針對密封類別，讓建構函式成為 private，否則為 protected。 |
| CA2230 | [CA2230:必須使用 params 作為變數引數](../code-quality/ca2230.md) | 公用或保護的類型包含使用 VarArgs 呼叫慣例之公用或保護的方法，而不是 params 關鍵字。 |
| CA2231 | [CA2231:在覆寫 ValueType.Equals 上多載等號運算子](../code-quality/ca2231.md) | 實值類型會覆寫 Object.Equals，但不會實作等號比較運算子。 |
| CA2232 | [CA2232:Windows Forms 進入點必須標記 STAThread](../code-quality/ca2232.md) | STAThreadAttribute 表示應用程式的 COM 執行緒模型為單一執行緒 Apartment。 在使用 Windows Form 的任何應用程式之進入點上必須有此屬性。如果省略的話，Windows 元件就無法正常運作。 |
| CA2233 |[CA2233:運算不應該發生溢位](../code-quality/ca2233.md) | 您不應該在沒有先驗證運算元的情況下，執行算術運算。 這樣做可確保運算結果不會超過所包含之資料類型的可能值範圍。 |
| CA2234 | [CA2234:必須傳遞 System.Uri 物件而非字串](../code-quality/ca2234.md) | 呼叫字串參數名稱包含 "uri"、"URI"、"urn"、"URN"、"url" 或 "URL"， 而且此方法的宣告類型會包含具有 System.Uri 參數的對應方法多載。 |
| CA2235 | [CA2235:必須標記所有不可序列化的欄位](../code-quality/ca2235.md) | 可序列化之類型中所宣告之類型的執行個體 (Instance) 欄位是不可序列化的。 |
| CA2236 | [CA2236:必須呼叫 ISerializable 類型上的基底類別方法](../code-quality/ca2236.md) | 若要修正此規則的違規情形，請從對應的衍生類型方法或建構函式，呼叫基底類型 GetObjectData 方法或序列化建構函式。 |
| CA2237 | [CA2237:ISerializable 類型必須標記 SerializableAttribute](../code-quality/ca2237.md) | 若要讓通用語言執行平台辨認為可序列化，即使類型透過 ISerializable 介面的實作使用自訂序列化常式，類型仍必須使用 SerializableAttribute 屬性來標記。 |
| CA2238 |[CA2238:必須正確實作序列化方法](../code-quality/ca2238.md) | 處理序列化事件的方法沒有正確的簽章、傳回型別或可視性。 |
| CA2239 | [CA2239:必須為選擇性欄位提供還原序列化方法](../code-quality/ca2239.md) | 類型具有使用 System.Runtime.Serialization.OptionalFieldAttribute 屬性來標記的欄位，而且類型不提供還原序列化事件處理方法。 |
| CA2240 | [CA2240:必須正確實作 ISerializable](../code-quality/ca2240.md) | 若要修正此規則的違規情形，請將 GetObjectData 方法設為可見和可覆寫的，並確定所有執行個體欄位都加入序列化處理序中，或已使用 NonSerializedAttribute 屬性來明確標記。 |
| CA2241 | [CA2241:必須提供格式化方法的正確引數](../code-quality/ca2241.md) | 傳遞至 System.String.Format 的格式引數不包含對應至每個物件引數的格式項目，反之亦然。 |
| CA2242 |[CA2242:必須正確測試 NaN](../code-quality/ca2242.md) | 此運算式針對 Single.Nan 或 Double.Nan 測試值。 使用 Single.IsNan(Single) 或 Double.IsNan(Double) 即可測試值。 |
| CA2243 |[CA2243:屬性字串常值必須正確剖析](../code-quality/ca2243.md) | 屬性的字串常值參數未針對 URL、GUID 或版本進行正確剖析。 |
| CA2244 | [CA2244：不要複製索引的元素初始化](../code-quality/ca2244.md) | 物件初始化運算式有一個以上具有相同常數索引的索引項目目初始化運算式。 除了最後一個初始化運算式之外，所有的都是多餘的。 |
| CA2245 | [CA2245：不要將屬性指派給本身](../code-quality/ca2245.md) | 屬性不小心指派給本身。 |
| CA2246 | [CA2246：不要在相同的語句中指派符號和其成員](../code-quality/ca2246.md) | 不建議在相同的語句中指派符號和其成員（也就是欄位或屬性）。 如果成員存取預定要在指派之前使用符號的舊值，或在此語句中指派新的值，則不會很清楚。 |
| CA5122 | [CA5122 P-INVOKE P/Invoke 宣告不應該是安全關鍵](../code-quality/ca5122.md) | 在執行安全性敏感作業時，會將方法標記為 SecuritySafeCritical，但透明程式碼也能安全地使用。 透明程式碼不可直接透過 P/Invoke 呼叫機器碼。 因此，即使將 P/Invoke 標示為安全性安全關鍵，透明程式碼仍然不能呼叫它，而且會導致安全性分析錯誤。 |
| CA5359 | [CA5359 不要停用憑證驗證](../code-quality/ca5359.md) | 憑證可以協助驗證服務器的身分識別。 用戶端應該驗證伺服器憑證，以確保要求會傳送到預期的伺服器。 如果 Servicepointmanager.servercertificatevalidationcallback 一律 `true` 會傳回，任何憑證都會通過驗證。 |
| CA5362 | [CA5362 已還原序列化物件圖形中的潛在參考週期](../code-quality/ca5362.md) | 如果還原序列化不受信任的資料，則處理已還原序列化之物件圖形的任何程式碼都必須處理參考迴圈，而不會進入無限迴圈。 這同時包含屬於還原序列化回呼一部分的程式碼，以及在還原序列化完成後處理物件圖形的程式碼。 否則，攻擊者可能會使用包含參考週期的惡意資料來執行拒絕服務攻擊。 |
| CA5365 | [CA5365 不要停用 HTTP 標頭檢查](../code-quality/ca5365.md) | HTTP 標頭檢查可以編碼在回應標頭中找到的換行字元和分行符號（\r 和 \n）。 這種編碼方式有助於避免利用回應標頭所包含之不受信任資料之應用程式的插入式攻擊。 |
| CA5366 | [CA5366 Use 資料集讀取 XML 的 XmlReader](../code-quality/ca5366.md) | 使用 <xref:System.Data.DataSet> 來讀取具有不受信任資料的 XML 可能會載入危險的外部參考，這應該藉由使用 <xref:System.Xml.XmlReader> 安全解析程式或停用 DTD 處理來加以限制。 |
| CA5367 | [CA5367 不要將具有指標欄位的類型序列化](../code-quality/ca5367.md) | 此規則會檢查是否有具有指標欄位或屬性的可序列化類別。 無法序列化的成員可以是指標，例如靜態成員或以標記的欄位 <xref:System.NonSerializedAttribute> 。 |
| CA5368 | [衍生自頁面之類別的 CA5368 設定 ViewStateUserKey](../code-quality/ca5368.md) | 設定 <xref:System.Web.UI.Page.ViewStateUserKey> 屬性可協助您防止應用程式的攻擊，方法是允許您將識別碼指派給個別使用者的檢視狀態變數，讓攻擊者無法使用變數來產生攻擊。 否則，跨網站偽造要求會有弱點。 |
| CA5374 | [CA5374 不使用 XslTransform](../code-quality/ca5374.md) | 此規則會檢查 <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> 是否在程式碼中具現化。 <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType>現在已過時，不應使用。 |
| CA5379 | [CA5379 不使用弱式金鑰衍生函數演算法](../code-quality/ca5379.md) | <xref:System.Security.Cryptography.Rfc2898DeriveBytes>類別預設為使用 <xref:System.Security.Cryptography.HashAlgorithmName.SHA1> 演算法。 您應該指定雜湊演算法，以便在具有 <xref:System.Security.Cryptography.HashAlgorithmName.SHA256> 或更高版本的函式的某些多載中使用。 請注意， <xref:System.Security.Cryptography.Rfc2898DeriveBytes.HashAlgorithm> 屬性只有 `get` 存取子，而且沒有修飾詞 `overriden` 。 |
| CA5382 | [CA5382 在 ASP.NET Core 中使用安全 cookie](../code-quality/ca5382.md) | 透過 HTTPS 提供的應用程式必須使用安全 cookie，這會向瀏覽器指出 cookie 應僅使用安全通訊端層（SSL）來傳輸。 |
| CA5383 | [CA5383 確保在 ASP.NET Core 中使用安全 cookie](../code-quality/ca5383.md) | 透過 HTTPS 提供的應用程式必須使用安全 cookie，這會向瀏覽器指出 cookie 應僅使用安全通訊端層（SSL）來傳輸。 |
| CA5384 | [CA5384 不使用數位簽章演算法（DSA）](../code-quality/ca5384.md) | DSA 是弱式非對稱式加密演算法。 |
| CA5385 | [CA5385 Use Rivest – Shamir – Adleman （RSA）演算法具有足夠的金鑰大小](../code-quality/ca5385.md) | 小於2048位的 RSA 金鑰較容易遭受暴力密碼破解攻擊。 |
| CA5387 | [CA5387 不使用沒有足夠反覆運算計數的弱式金鑰衍生函數](../code-quality/ca5387.md) | 此規則會檢查是否以小於100000的反復專案計數來產生密碼編譯金鑰 <xref:System.Security.Cryptography.Rfc2898DeriveBytes> 。 較高的反復專案計數有助於減輕嘗試猜測產生的密碼編譯金鑰的字典攻擊。 |
| CA5388 | [CA5388 在使用弱式金鑰衍生函式時，確保有足夠的反復專案計數](../code-quality/ca5388.md) | 此規則會檢查是否使用產生的密碼編譯金鑰 <xref:System.Security.Cryptography.Rfc2898DeriveBytes> 具有小於100000的反復專案計數。 較高的反復專案計數有助於減輕嘗試猜測產生的密碼編譯金鑰的字典攻擊。 |
| CA5390 | [CA5390 不會硬式編碼加密金鑰](../code-quality/ca5390.md) | 若要讓對稱演算法成功，只有傳送者和接收者才必須知道秘密金鑰。 當金鑰是硬式編碼時，很容易就會發現。 即使使用已編譯的二進位檔，惡意使用者也很容易將它解壓縮。 一旦私密金鑰遭到入侵，就可以直接解密加密文字，而不會再受到保護。 |
| CA5394 | [CA5394 不使用不安全的隨機性](../code-quality/ca5394.md) | 使用密碼編譯弱式虛擬亂數產生器可能會讓攻擊者預測產生的安全性敏感值。 |
| CA5396 | [CA5396 將 HttpCookie 的 HttpOnly 設定為 true](../code-quality/ca5396.md) | 做為深層防禦措施，請確定安全性敏感的 HTTP cookie 已標示為 HttpOnly。 這表示 web 瀏覽器應該不允許腳本存取 cookie。 插入的惡意腳本是竊取 cookie 的常見方式。 |
| CA5399 | [CA5399 明確停用 HttpClient 憑證撤銷清單檢查](../code-quality/ca5399.md) | 已撤銷的憑證已不再受信任。 攻擊者可以使用它來傳遞某些惡意資料，或竊取 HTTPS 通訊中的敏感性資料。 |
| CA5400 | [CA5400 確保不會停用 HttpClient 憑證撤銷清單檢查](../code-quality/ca5400.md) | 已撤銷的憑證已不再受信任。 攻擊者可以使用它來傳遞某些惡意資料，或竊取 HTTPS 通訊中的敏感性資料。 |
| CA5401 | [CA5401 不使用非預設 IV 的 CreateEncryptor](../code-quality/ca5401.md) | 對稱式加密應一律使用不可重複的初始化向量來防止字典攻擊。 |
| CA5402 | [CA5402 使用 CreateEncryptor 搭配預設的 IV](../code-quality/ca5402.md) | 對稱式加密應一律使用不可重複的初始化向量來防止字典攻擊。 |
