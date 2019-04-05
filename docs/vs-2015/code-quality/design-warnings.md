---
title: 設計警告 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.designrules
helpviewer_keywords:
- design warnings
- managed code analysis warnings, design warnings
- warnings, design
ms.assetid: 34e65a18-560c-423f-814f-519089e318cf
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 58c5866e9aa78884aac89bbfab5894394116e79f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944094"
---
# <a name="design-warnings"></a>設計警告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

設計警告支援遵循.NET Framework 設計方針。  
  
## <a name="in-this-section"></a>本節內容  
  
|規則|描述|  
|----------|-----------------|  
|[CA1000:不要在泛型類型上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|呼叫泛型類型的靜態成員時，必須為類型指定類型引數。 呼叫不支援介面的泛型執行個體 (Instance) 成員時，必須為成員指定型別引數。 在上述兩種情況下，指定型別引數的語法不同且容易混淆。|  
|[CA1001：具有可處置欄位的類型應該為可處置](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|類別會宣告及實作類型為 System.IDisposable 的執行個體欄位和類別未實作 IDisposable。 宣告 IDisposable 欄位的類別會間接擁有 Unmanaged 資源，且應實作 IDisposable 介面。|  
|[CA1002:不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)|System.Collections.Generic.List < (的\<(T >) >) 是專為效能而非繼承的泛型集合。 因此，List 不包含任何虛擬成員。 應該改為公開專為繼承所設計的泛型集合。|  
|[CA1003： 必須使用一般事件處理常式執行個體](../code-quality/ca1003-use-generic-event-handler-instances.md)|型別包含的委派，會傳回 void，其簽章包含兩個參數 （物件的第一個和第二個是指派給 EventArgs 的類型） 和包含的組件目標[!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]。|  
|[CA1004:泛型方法應該提供型別參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|推斷是指如何利用傳遞到泛型方法的引數類型，而不是利用型別引數的明確規格，來決定泛型方法的型別引數。 若要啟用推斷，泛型方法的參數簽章必須包含與方法之型別參數具有相同類型的參數。 在上述情形中，不必指定類型引數。 當您使用推斷所有類型參數時，呼叫泛型和非泛型執行個體方法的語法是相同的。這可簡化泛型方法的可用性。|  
|[CA1005:避免在泛型類型上的過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|泛型類型所包含的類型參數越多，就越難了解並記住每個類型參數所代表的含意。 具有一個型別參數，如所示清單通常顯然\<T >，並在某些情況下，具有兩個類型參數，如\<TKey，TValue >。 不過，如果存在兩個以上的類型參數，則對大多數使用者而言都會變得難以理解。|  
|[CA1006:無法建立巢狀成員簽章中的泛型型別](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|巢狀型別引數就是也是泛型類型的型別引數。 若要呼叫其簽章含有巢狀型別引數的成員，則使用者必須具現化 (Instantiate) 一個泛型類型，並將這個類型傳遞給第二個泛型類型的建構函式。 必要程序及語法十分複雜，且應予以避免。|  
|[CA1007:在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)|外部可見的方法包含 System.Object 類型的傳址參數。 使用泛型方法可讓所有類型 (遵守條件約束) 傳遞給方法，而不需要先將類型轉型為傳址參數類型。|  
|[CA1008:列舉應該使用零值](../code-quality/ca1008-enums-should-have-zero-value.md)|如同其他實值類型一般，未初始化的列舉其預設值為零。 賦予屬性的有效值列舉應該使用值為零，因此預設值是有效的值的列舉型別定義的成員。 如果已套用 FlagsAttribute 屬性的列舉定義零值成員，則其名稱應該是 "None"，以表示列舉中未設定任何值。|  
|[CA1009:必須正確宣告事件處理常式](../code-quality/ca1009-declare-event-handlers-correctly.md)|事件處理常式方法會採用兩個參數。 第一個的類型為 System.Object 且名稱為 "sender"。 這是引發事件的物件。 第二個參數的類型為 System.EventArgs 且名稱為 "e"。 這是與事件相關聯的資料。 事件處理常式方法不應該傳回值；在 C# 程式設計語言中，這是由 void 傳回型別所表示。|  
|[CA1010:集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)|若要放寬集合的可用性，請實作其中一個泛型集合介面。 接著，使用該集合填入泛型集合類型。|  
|[CA1011:請考慮將基底類型當做參數傳遞](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|當方法宣告將基底類型指定為參數，則從此基底類型衍生的任何類型都可以當做對應引數傳遞給方法。 如果不需要以衍生參數類型提供額外的功能，則使用基底類型可以更廣泛地運用此方法。|  
|[CA1012:抽象類型不應該有建構函式](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|只有衍生類型 (Derived Type) 可以呼叫抽象類型上的建構函式。 因為公用建構函式會建立類型的執行個體，而且您無法建立抽象類型的執行個體，因此具有公用建構函式的抽象類型設計不正確。|  
|[CA1013:多載運算子等於多載加號和減號](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|公用或保護的類型會實作加法或減法運算，但不會實作等號比較運算子。|  
|[CA1014:組件必須標記 clscompliantattribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|Common Language Specification (CLS) 會定義命名限制、資料類型及組件必須遵守的規則 (如果組件會使用於跨程式設計語言時)。 良好的設計會要求所有組件明確使用 CLSCompliantAttribute 表示 cls 符合性。 如果這個屬性未出現於組件中，則表示組件不符合標準。|  
|[CA1016:組件必須標記 assemblyversionattribute](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|.NET Framework 使用的版本號碼，來唯一識別組件，並繫結至強式名稱組件中的類型。 版本號碼會與版本和發行者 (Publisher) 原則一起使用。 應用程式預設只會與建置它們的組件版本一起執行。|  
|[CA1017:組件必須標記 comvisibleattribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|ComVisibleAttribute 會判斷 COM 用戶端如何存取 Managed 程式碼。 良好的設計會要求組件明確表示 COM 的可視性。 COM 的可視性可以針對整個組件進行設定，然後針對個別類型及類型成員進行覆寫。 如果這個屬性不存在，則 COM 用戶端可以看到組件的內容。|  
|[CA1018:以 AttributeUsageAttribute 標記屬性](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|當您定義自訂屬性時，請使用 AttributeUsageAttribute 標記它，以指出可以在原始程式碼的哪個位置套用自訂屬性。 屬性的意義和預期的用法將決定它在程式碼中的有效位置。|  
|[CA1019： 必須定義存取子屬性引數](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|屬性可以定義必須在將屬性套用至目標時指定的強制引數。 這些引數也稱為位置引數，因為它們會當做位置參數提供給屬性建構函式。 對於每個強制引數而言，屬性 (Attribute) 還須提供對應的唯讀屬性 (Property)，才可以在執行時期擷取引數值。 屬性也可以定義選擇性引數，也稱為具名引數。 這些引數會依照名稱提供給屬性 (Attribute) 建構函式，且必須有對應的讀取/寫入屬性 (Property)。|  
|[CA1020:避免一些類型，在命名空間](../code-quality/ca1020-avoid-namespaces-with-few-types.md)|請確定每個命名空間具有邏輯組織，而且您有理由可將類型置於沒有嚴密填入的命名空間。|  
|[CA1021:避免使用 out 參數](../code-quality/ca1021-avoid-out-parameters.md)|以傳址方式傳遞類型時 (使用 out 或 ref)，您需要擁有使用指標的經驗、了解實值類型和參考類型之間的差異，並處理具有多個傳回值的方法。 此外，out 和 ref 參數之間的差異一般人不甚了解。|  
|[CA1023:索引子不應該使用多維](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|索引子 (也就是索引屬性) 應使用單一索引。 多維索引子會大幅降低程式庫的可用性。|  
|[CA1024:在適當時使用屬性](../code-quality/ca1024-use-properties-where-appropriate.md)|公用或保護的方法具有以 "Get" 開頭的名稱，該名稱不採用任何參數並且會傳回不是陣列的值。 此方法可能是成為屬性的不錯候選者。|  
|[CA1025： 必須以參數陣列取代重複的引數](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|當引數的正確數目未知，而且變數引數都是相同的類型 (或可以相同的類型傳遞) 時，需使用參數陣列而不是重複的引數。|  
|[CA1026:不應該使用預設參數](../code-quality/ca1026-default-parameters-should-not-be-used.md)|允許使用預設參數的方法受制於 CLS。不過，CLS 允許編譯器 (Compiler) 忽略已指派給這些參數的值。 若要在程式語言之間維護您要的行為，則必須以提供預設參數的方法多載來取代使用預設參數的方法。|  
|[CA1027:以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|列舉類型是一種實值類型 (Value Type)，用以定義一組相關的具名常數。 當列舉的具名常數可以有意義地加以結合時，會將 FlagsAttribute 套用至此列舉。|  
|[CA1028:列舉儲存區應該是 Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)|列舉類型是一種實值類型 (Value Type)，用以定義一組相關的具名常數。 根據預設，System.Int32 資料類型會用於儲存常數值。 雖然您可以變更這個基礎類型，它不需要或建議大部分的情況下。|  
|[CA1030:在適當時使用事件](../code-quality/ca1030-use-events-where-appropriate.md)|此規則會偵測具有事件常用名稱的方法。 如果方法因回應清楚定義的狀態變更而被呼叫，應該由事件處理常式叫用該方法。 呼叫方法的物件應該要引發事件，而不是直接呼叫方法。|  
|[CA1031:不要攔截一般例外狀況類型](../code-quality/ca1031-do-not-catch-general-exception-types.md)|不應該攔截一般例外狀況。 攔截更特定的例外狀況，或在 catch 區塊中，做為最後一個陳述式的一般例外狀況重新擲回。|  
|[CA1032： 必須實作標準例外狀況建構函式](../code-quality/ca1032-implement-standard-exception-constructors.md)|無法提供整組的建構函式會導致難以正確地處理例外狀況。|  
|[CA1033:介面方法應該要可以由子類型呼叫](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|非密封外部可見的類型會提供公用介面的明確方法實作，但未提供同名的替代外部可見方法。|  
|[CA1034:巢狀的類型不應該為可見](../code-quality/ca1034-nested-types-should-not-be-visible.md)|巢狀類型是在其他類型範圍內宣告的類型。 巢狀類型可用來封裝包含類型 (Containing Type) 私用的 (Private) 實作細節。 因為有這樣的用途，所以巢狀類型不應為外部可見的。|  
|[CA1035:實作包含強類型成員](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|這項規則要求 ICollection 實作提供強類型成員，讓使用者在使用介面所提供的功能時，不需將引數轉換為 Object 類型。 這項規則假設實作 ICollection 的類型會這樣做，以管理效力比 Object 還強之類型的執行個體集合。|  
|[CA1036： 必須覆寫在 comparable 類型的方法](../code-quality/ca1036-override-methods-on-comparable-types.md)|公用或受保護的類型實作 System.IComparable 介面。 它不會覆寫 Object.Equals，也不會多載等號、不等、小於或大於的語言特定比較運算子。|  
|[CA1038:應該是強類型列舉值](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|此規則要求 IEnumerator 實作同時也提供 Current 屬性的強類型版本，如此當使用者使用介面提供的功能時，就不需要將傳回值轉型為強類型。|  
|[CA1039:清單為強類型](../code-quality/ca1039-lists-are-strongly-typed.md)|這項規則要求 IList 實作提供強類型成員，讓使用者在使用介面所提供的功能時，不需將引數轉換為 System.Object 類型。|  
|[CA1040:避免使用空的介面](../code-quality/ca1040-avoid-empty-interfaces.md)|介面是用來定義一組可提供行為或程式使用合約的成員。 不論類型出現在繼承階層架構 (Inheritance Hierarchy) 中的何處，任何類型都可以採用介面所描述的功能。 類型會實作介面，方法是提供介面成員的實作。 空白介面不會定義任何成員，因此也不會定義能夠實作的合約。|  
|[CA1041:提供 ObsoleteAttribute 訊息](../code-quality/ca1041-provide-obsoleteattribute-message.md)|類型或成員是使用並未指定其 ObsoleteAttribute.Message 屬性 (Property) 的 System.ObsoleteAttribute 屬性 (Attribute) 來標記。 型別或成員，使用 ObsoleteAttribute 來標記編譯時，會顯示訊息屬性的屬性，讓擁有過時類型或成員的使用者資訊。|  
|[CA1043： 必須使用索引子的整數類或字串引數](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|索引子 (也就是索引的屬性) 應該使用整數類型或字串類型的索引。 這些類型通常會用於資料結構的索引，可以提升程式庫的可用性。 Object 類型的使用應限制於無法在設計階段指定特定整數類型或字串類型的情況。|  
|[CA1044:屬性不應該為唯寫](../code-quality/ca1044-properties-should-not-be-write-only.md)|雖然它是可接受並經常需要具有唯讀屬性，設計方針會禁止使用唯寫屬性的屬性。 這是因為讓使用者，設定一個值，然後防止使用者檢視值並不會提供任何安全性。 同時，如果沒有讀取權限，則無法檢視共用物件的狀態，進而限制這些物件的使用性。|  
|[CA1045:不要參考所傳遞類型](../code-quality/ca1045-do-not-pass-types-by-reference.md)|以傳址方式傳遞類型時 (使用 out 或 ref)，您需要擁有使用指標的經驗、了解實值類型和參考類型之間的差異，並處理具有多個傳回值的方法。 目標為一般使用者的程式庫架構設計人員不應預期使用者會熟練地運用 out 或 ref 參數。|  
|[CA1046:不要多載參考類型上的等號比較運算子](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|對參考類型而言，等號比較運算子的預設實作 (Implementation) 永遠都是正確的。 根據預設，只有當兩項參考都指向相同物件時才會相等。|  
|[CA1047:不要宣告在密封類型中的受保護的成員](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|類型會宣告 protected 成員，如此繼承的類型即可存取或覆寫成員。 根據定義，密封類型無法被繼承，這表示無法呼叫密封類型上的受保護方法。|  
|[CA1048:不要宣告在密封類型中的虛擬成員](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|類型會將方法宣告為 virtual，讓繼承類型可以覆寫 virtual 方法的實作。 根據預設，密封類型無法被繼承。 這會讓密封類型上的虛擬方法失去意義。|  
|[CA1049:擁有原生資源的類型應該是可處置的](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|配置 Unmanaged 資源的類型應實作 IDisposable，讓呼叫端視需要釋放這些資源，並且縮短持有資源之物件的存留期。|  
|[CA1050:宣告命名空間中的類型](../code-quality/ca1050-declare-types-in-namespaces.md)|類型會在命名空間之內宣告以防止名稱衝突，而且可當做組織物件階層架構中相關類型的一種方法。|  
|[CA1051:不要宣告可見的執行個體欄位](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|欄位的主要用法應該是當做實作詳細資料。 欄位應該是私用或內部的，而且應使用屬性公開。|  
|[CA1052:靜態預留位置類型應該為密封](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|公用或受保護的類型無法宣告使用 sealed (C#) 或 NotInheritable (Visual Basic) 修飾詞，且只包含靜態成員。 預定不會繼承的類型應該使用 sealed 修飾詞來標記，以禁止使用它做為基底類型。|  
|[CA1053:靜態預留位置類型不應該有建構函式](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|公用或巢狀公用類型只宣告靜態成員，而且具有公用或保護的預設建構函式。 建構函式不是必要的，因為呼叫靜態成員不需類型的執行個體。 為了安全，字串多載應該使用字串引數來呼叫統一資源識別項 (URI) 多載。|  
|[CA1054:URI 參數不應該為字串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|如果方法使用 URI 字串表示，應該提供採用 URI 類別的對應多載，這樣就可以透過安全的方式提供這些服務。|  
|[CA1055:URI 會傳回值不應該為字串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|這項規則假設方法會傳回 URI。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 System.Uri 類別以安全的方式提供這些服務。|  
|[CA1056:URI 屬性不應該為字串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|這項規則假設屬性表示的 URI。 URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。 System.Uri 類別以安全的方式提供這些服務。|  
|[CA1057:字串 URI 多載呼叫 System.Uri 多載](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|類型會宣告方法多載，這些方法多載的差別只在於以 System.Uri 參數取代字串參數。 接受字串參數的多載不會呼叫接受 URI 參數的多載。|  
|[CA1058:類型不應該擴充特定基底類型](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|外部可見的類型會延伸某些基底類型 (Base Type)。 請使用其他作法。|  
|[CA1059:成員不應該公開特定的具象類型](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|具象類型就是具有完整實作 (Implementation) 且因此能加以具現化 (Instantiated) 的類型。 若要讓成員能廣泛使用，請使用建議的介面來取代具象類型。|  
|[CA1060:將 P/Invokes 移到 NativeMethods 類別](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|平台叫用方法，例如標示<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>或使用中的 Declare 關鍵字定義的方法[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]，存取 unmanaged 程式碼。 這些方法應該是 NativeMethods、SafeNativeMethods 或 UnsafeNativeMethods 類別。|  
|[CA1061:不要隱藏基底類別方法](../code-quality/ca1061-do-not-hide-base-class-methods.md)|只有在衍生方法的參數簽章因類型衍生時比基底方法參數簽章中的類型還要弱時，基底類型中的方法才會被衍生類型中的相同具名方法所隱藏。|  
|[CA1062:驗證公用方法的引數](../code-quality/ca1062-validate-arguments-of-public-methods.md)|所有傳遞至外部可見方法的參考引數都應經過 null 檢查。|  
|[CA1063： 必須必須正確實作 IDisposable](../code-quality/ca1063-implement-idisposable-correctly.md)|所有的 IDisposable 類型都需正確地實作 Dispose 模式。|  
|[CA1064:例外狀況必須是公用](../code-quality/ca1064-exceptions-should-be-public.md)|內部例外狀況只會在自己的內部範圍內顯示。 當例外狀況超出內部範圍後，只能使用基本例外狀況來攔截例外狀況。 如果內部例外狀況繼承自<xref:System.Exception?displayProperty=fullName>， <xref:System.SystemException?displayProperty=fullName>，或<xref:System.ApplicationException?displayProperty=fullName>，外部程式碼不會知道該如何處理例外狀況的足夠資訊。|  
|[CA1065:不會引發非預期的位置中的例外狀況](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|不可擲回例外狀況 (Exception) 的方法卻擲回例外狀況。|  
|[CA2210:組件應該具備有效的強式名稱](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|強式名稱可避免用戶端在不知情的狀況下，載入已遭他人修改的組件。 除了極少數的案例以外，您都應該避免部署沒有強式名稱的組件。 如果您共用或散發未正確簽署的組件，表示這個組件或許已遭他人修改，通用語言執行平台可能不會載入組件，或是使用者可能必須停用電腦上的驗證作業。|
