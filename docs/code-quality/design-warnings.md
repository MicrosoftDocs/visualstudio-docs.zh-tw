---
title: 設計規則
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.designrules
helpviewer_keywords:
- design rules
- managed code analysis rules, design rules
- rules, design
ms.assetid: 34e65a18-560c-423f-814f-519089e318cf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d626231bcfe298a225cc916c356290a94042992
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808661"
---
# <a name="design-rules"></a>設計規則

設計規則支援遵循 .NET Framework 的 [設計指導方針](/dotnet/standard/design-guidelines/)。

## <a name="in-this-section"></a>本節內容

| 規則 | 描述 |
| - | - |
| [CA1000：不要在泛型類型上宣告靜態成員](../code-quality/ca1000.md) | 呼叫泛型類型的靜態成員時，必須為類型指定類型引數。 呼叫不支援介面的泛型執行個體 (Instance) 成員時，必須為成員指定類型引數。 在上述兩種情況下，指定型別引數的語法不同且容易混淆。 |
| [CA1001：具有可處置欄位的類型應該為可處置](../code-quality/ca1001.md) | 類別會宣告並實作為 IDisposable 類型的實例欄位，而且類別不會執行 IDisposable。 宣告 IDisposable 欄位的類別會間接擁有 Unmanaged 資源，且應實作 IDisposable 介面。 |
| [CA1002：不要公開泛型清單](../code-quality/ca1002.md) | \<(T>) # A1) 的< (，是針對效能而非繼承所設計的泛型集合。 因此，List 不包含任何虛擬成員。 應該改為公開專為繼承所設計的泛型集合。 |
| [CA1003：使用一般事件處理常式執行個體](../code-quality/ca1003.md) | 型別包含傳回 void 的委派，其簽章包含兩個參數 (第一個物件，第二個則是可指派給 EventArgs) 的型別，而包含元件的目標則是 .NET Framework 2.0。 |
| [CA1005：避免在泛型類型上包含過多參數](../code-quality/ca1005.md) | 泛型類型所包含的類型參數越多，就越難了解並記住每個類型參數所代表的含意。 它通常會使用一個型別參數（如清單 \<T> ），以及在具有兩個型別參數的特定情況下很明顯，如同在字典中一樣 \<TKey, TValue> 。 不過，如果存在兩個以上的類型參數，則對大多數使用者而言都會變得難以理解。 |
| [CA1008:列舉值中應該要有值為零的成員](../code-quality/ca1008.md) | 如同其他實值類型一般，未初始化的列舉其預設值為零。 有效值屬性化列舉應該使用值零來定義成員，如此一來，預設值就是列舉的有效值。 如果已套用 FlagsAttribute 屬性的列舉定義零值成員，則其名稱應該是 "None"，以表示列舉中未設定任何值。 |
| [CA1010:集合應該實作泛型介面](../code-quality/ca1010.md) | 若要放寬集合的可用性，請實作其中一個泛型集合介面。 接著，使用該集合填入泛型集合類型。 |
| [CA1012:抽象類型不應該有建構函式](../code-quality/ca1012.md) | 只有衍生類型 (Derived Type) 可以呼叫抽象類型上的建構函式。 因為公用建構函式會建立類型的執行個體，而且您無法建立抽象類型的執行個體，因此具有公用建構函式的抽象類型設計不正確。 |
| [CA1014:組件必須標記 CLSCompliantAttribute](../code-quality/ca1014.md) | Common Language Specification (CLS) 會定義命名限制、資料類型及組件必須遵守的規則 (如果組件會使用於跨程式設計語言時)。 良好的設計規定所有的元件都使用 >clscompliantattribute 明確指出符合 CLS 標準。 如果這個屬性未出現於組件中，則表示組件不符合標準。 |
| [CA1016:組件必須標記 AssemblyVersionAttribute](../code-quality/ca1016.md) | .NET 會使用版本號碼來唯一識別元件，並系結至強式名稱元件中的類型。 版本號碼會與版本和發行者 (Publisher) 原則一起使用。 應用程式預設只會與建置它們的組件版本一起執行。 |
| [CA1017:組件必須標記 ComVisibleAttribute](../code-quality/ca1017.md) | ComVisibleAttribute 會判斷 COM 用戶端如何存取 Managed 程式碼。 良好的設計會要求組件明確表示 COM 的可視性。 COM 的可視性可以針對整個組件進行設定，然後針對個別類型及類型成員進行覆寫。 如果這個屬性不存在，則 COM 用戶端可以看到組件的內容。 |
| [CA1018:必須以 AttributeUsageAttribute 標記屬性](../code-quality/ca1018.md) | 當您定義自訂屬性時，請使用 AttributeUsageAttribute 標記它，以指出可以在原始程式碼的哪個位置套用自訂屬性。 屬性的意義和預期的用法將決定它在程式碼中的有效位置。 |
| [CA1019:定義屬性引數的存取子](../code-quality/ca1019.md) | 屬性可以定義必須在將屬性套用至目標時指定的強制引數。 這些引數也稱為位置引數，因為它們會當做位置參數提供給屬性建構函式。 對於每個強制引數而言，屬性 (Attribute) 還須提供對應的唯讀屬性 (Property)，才可以在執行時期擷取引數值。 屬性也可以定義選擇性引數，也稱為具名引數。 這些引數會依照名稱提供給屬性 (Attribute) 建構函式，且必須有對應的讀取/寫入屬性 (Property)。 |
| [CA1021:避免使用 out 參數](../code-quality/ca1021.md) | 以傳址方式傳遞類型時 (使用 out 或 ref)，您需要擁有使用指標的經驗、了解實值類型和參考類型之間的差異，並處理具有多個傳回值的方法。 此外，out 和 ref 參數之間的差異一般人不甚了解。 |
| [CA1024:建議在適當時使用屬性](../code-quality/ca1024.md) | 公用或保護的方法具有以 "Get" 開頭的名稱，該名稱不採用任何參數並且會傳回不是陣列的值。 此方法可能是成為屬性的不錯候選者。 |
| [CA1027:必須以 FlagsAttribute 標記列舉](../code-quality/ca1027.md) | 列舉類型是一種實值類型 (Value Type)，用以定義一組相關的具名常數。 當列舉的具名常數可以有意義地加以結合時，會將 FlagsAttribute 套用至此列舉。 |
| [CA1028:列舉儲存區應該是 Int32](../code-quality/ca1028.md) | 列舉類型是一種實值類型 (Value Type)，用以定義一組相關的具名常數。 根據預設，System.Int32 資料類型會用於儲存常數值。 雖然您可以變更此基礎類型，但在大部分的情況下都不需要或建議您這樣做。 |
| [CA1030:建議在適當時使用事件](../code-quality/ca1030.md) | 此規則會偵測具有事件常用名稱的方法。 如果方法因回應清楚定義的狀態變更而被呼叫，應該由事件處理常式叫用該方法。 呼叫方法的物件應該要引發事件，而不是直接呼叫方法。 |
| [CA1031:不要攔截一般例外狀況類型](../code-quality/ca1031.md) | 不應該攔截一般例外狀況。 攔截更明確的例外狀況，或重新擲回一般例外狀況做為 catch 區塊中的最後一個語句。 |
| [CA1032:必須實作標準例外狀況建構函式](../code-quality/ca1032.md) | 無法提供整組的建構函式會導致難以正確地處理例外狀況。 |
| [CA1033:介面方法應該要可以由子類型呼叫](../code-quality/ca1033.md) | 非密封外部可見的類型會提供公用介面的明確方法實作，但未提供同名的替代外部可見方法。 |
| [CA1034:巢狀類型不應該為可見的](../code-quality/ca1034.md) | 巢狀類型是在其他類型範圍內宣告的類型。 巢狀類型可用來封裝包含類型 (Containing Type) 私用的 (Private) 實作細節。 因為有這樣的用途，所以巢狀類型不應為外部可見的。 |
| [CA1036:必須在 Comparable 類型中覆寫方法](../code-quality/ca1036.md) | 公用或受保護的類型實作 System.IComparable 介面。 它不會覆寫 Object.Equals，也不會多載等號、不等、小於或大於的語言特定比較運算子。 |
| [CA1040:避免使用空的介面](../code-quality/ca1040.md) | 介面是用來定義一組可提供行為或程式使用合約的成員。 不論類型出現在繼承階層架構 (Inheritance Hierarchy) 中的何處，任何類型都可以採用介面所描述的功能。 類型會實作介面，方法是提供介面成員的實作。 空白介面不會定義任何成員，因此也不會定義能夠實作的合約。 |
| [CA1041:必須提供 ObsoleteAttribute 訊息](../code-quality/ca1041.md) | 類型或成員是使用並未指定其 ObsoleteAttribute.Message 屬性 (Property) 的 System.ObsoleteAttribute 屬性 (Attribute) 來標記。 當編譯使用 ObsoleteAttribute 標示的類型或成員時，會顯示內容的訊息屬性，以提供有關過時類型或成員的使用者資訊。 |
| [CA1043:必須針對索引子使用整數或字串引數](../code-quality/ca1043.md) | 索引子 (也就是索引的屬性) 應該使用整數類型或字串類型的索引。 這些類型通常會用於資料結構的索引，可以提升程式庫的可用性。 Object 類型的使用應限制於無法在設計階段指定特定整數類型或字串類型的情況。 |
| [CA1044:屬性不應該為唯寫的](../code-quality/ca1044.md) | 雖然它是可接受並經常需要具有唯讀屬性，設計方針會禁止使用唯寫屬性的屬性。 這是因為讓使用者，設定一個值，然後防止使用者檢視值並不會提供任何安全性。 同時，如果沒有讀取權限，則無法檢視共用物件的狀態，進而限制這些物件的使用性。 |
| [CA1045:不要以傳址方式傳遞類型](../code-quality/ca1045.md) | 以傳址方式傳遞類型時 (使用 out 或 ref)，您需要擁有使用指標的經驗、了解實值類型和參考類型之間的差異，並處理具有多個傳回值的方法。 目標為一般使用者的程式庫架構設計人員不應預期使用者會熟練地運用 out 或 ref 參數。 |
| [CA1046:不要多載參考類型上的等號比較運算子](../code-quality/ca1046.md) | 對參考類型而言，等號比較運算子的預設實作 (Implementation) 永遠都是正確的。 根據預設，只有當兩項參考都指向相同物件時才會相等。 |
| [CA1047:不要在密封類型中宣告 protected 成員](../code-quality/ca1047.md) | 類型會宣告 protected 成員，如此繼承的類型即可存取或覆寫成員。 根據定義，密封類型無法被繼承，這表示無法呼叫密封類型上的受保護方法。 |
| [CA1050:類型必須在命名空間中宣告](../code-quality/ca1050.md) | 類型會在命名空間之內宣告以防止名稱衝突，而且可當做組織物件階層架構中相關類型的一種方法。 |
| [CA1051:不要宣告可見的執行個體欄位](../code-quality/ca1051.md) | 欄位的主要用法應該是當做實作詳細資料。 欄位應該是私用或內部的，而且應使用屬性公開。 |
| [CA1052:靜態預留位置類型應該為密封的](../code-quality/ca1052.md) | 公用或受保護的型別只包含靜態成員，而不是使用 sealed (c # ) 或 NotInheritable (Visual Basic) 修飾詞來宣告。 預定不會繼承的類型應該使用 sealed 修飾詞來標記，以禁止使用它做為基底類型。 |
| [CA1053:靜態預留位置類型不應該包含建構函式](../code-quality/ca1053.md) | 公用或巢狀公用類型只宣告靜態成員，而且具有公用或保護的預設建構函式。 建構函式不是必要的，因為呼叫靜態成員不需類型的執行個體。 為了安全，字串多載應該使用字串引數來呼叫統一資源識別項 (URI) 多載。 |
| [CA1054:URI 參數不應該為字串](../code-quality/ca1054.md) | 如果方法使用 URI 字串表示，應該提供採用 URI 類別的對應多載，這樣就可以透過安全的方式提供這些服務。 |
| [CA1055:URI 傳回值不應該為字串](../code-quality/ca1055.md) | 這項規則假設方法會傳回 URI。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 System.Uri 類別以安全的方式提供這些服務。 |
| [CA1056:URI 屬性不應該為字串](../code-quality/ca1056.md) | 此規則假設屬性代表 URI。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 System.Uri 類別以安全的方式提供這些服務。 |
| [CA1058:類型不應該擴充特定基底類型](../code-quality/ca1058.md) | 外部可見的類型會延伸某些基底類型 (Base Type)。 請使用其他作法。 |
| [CA1060：將 P/Invoke 移至 NativeMethods 類別](../code-quality/ca1060.md) | 平台叫用方法（例如， <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 使用 Declare 關鍵字定義的或方法所標記的方法）會 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 存取非受控碼。 這些方法應該是 NativeMethods、SafeNativeMethods 或 UnsafeNativeMethods 類別。 |
| [CA1061:不要隱藏基底類別方法](../code-quality/ca1061.md) | 只有在衍生方法的參數簽章因類型衍生時比基底方法參數簽章中的類型還要弱時，基底類型中的方法才會被衍生類型中的相同具名方法所隱藏。 |
| [CA1062:必須驗證公用方法的引數](../code-quality/ca1062.md) | 所有傳遞至外部可見方法的參考引數都應經過 null 檢查。 |
| [CA1063:必須正確實作 IDisposable](../code-quality/ca1063.md) | 所有的 IDisposable 類型都需正確地實作 Dispose 模式。 |
| [CA1064:例外狀況必須是公用](../code-quality/ca1064.md) | 內部例外狀況只會在自己的內部範圍內顯示。 當例外狀況超出內部範圍後，只能使用基本例外狀況來攔截例外狀況。 如果內部例外狀況繼承自 <xref:System.Exception?displayProperty=fullName> 、 <xref:System.SystemException?displayProperty=fullName> 或 <xref:System.ApplicationException?displayProperty=fullName> ，則外部程式碼將不會有足夠的資訊來知道該如何處理例外狀況。 |
| [CA1065:不要在非預期的位置中引發例外狀況](../code-quality/ca1065.md) | 不可擲回例外狀況 (Exception) 的方法卻擲回例外狀況。 |
| [CA1066：覆寫 Equals 時實作 IEquatable](../code-quality/ca1066.md) | 實值型別 <xref:System.Object.Equals%2A> 會覆寫方法，但不會執行 <xref:System.IEquatable%601> 。 |
| [CA1067：實作 IEquatable 時覆寫 Equals](../code-quality/ca1067.md) | 型別 <xref:System.IEquatable%601> 會執行，但不會覆寫 <xref:System.Object.Equals%2A> 方法。 |
| [CA1068：CancellationToken 參數必須位於最後](../code-quality/ca1068.md) | 方法的 CancellationToken 參數不是最後一個參數。 |
| [CA1069：列舉不能有重複的值](../code-quality/ca1069.md) | 列舉具有多個明確指派相同常數值的成員。 |
| [CA1070：請勿將事件欄位宣告為 virtual](../code-quality/ca1070.md) | [類似欄位的事件](/dotnet/csharp/language-reference/language-specification/classes#field-like-events)已宣告為 virtual。 |
