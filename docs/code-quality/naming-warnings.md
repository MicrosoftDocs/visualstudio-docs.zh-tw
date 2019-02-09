---
title: 命名警告
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.namingrules
helpviewer_keywords:
- managed code analysis warnings, naming warnings
- naming warnings
- warnings, naming
ms.assetid: f97223ce-1d39-4134-81c9-fff2c75d979b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3fc446207d2f8c2800135154ca435b821a0afd1
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55952524"
---
# <a name="naming-warnings"></a>命名警告
命名警告支援遵循.NET Framework 設計方針的命名慣例。

## <a name="in-this-section"></a>本節內容

|規則|描述|
|----------|-----------------|
|[CA1700:未命名的列舉值 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|這項規則假設名稱中包含 "reserved" 的列舉成員目前並未使用，但是在未來版本會是重新命名或移除的替代符號 (Placeholder)。 重新命名或移除成員是中斷變更。|
|[CA1713:事件應該不會有 before 或 after 前置詞](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|事件的名稱會以 "Before" 或 "After" 為開頭。 若要命名在特定序列 (Sequence) 中引發的相關事件，請使用現在式或過去式表示動作序列相對的位置。|
|[CA1714:旗標列舉應該使用複數名稱](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|公用列舉具有 System.FlagsAttribute 屬性，其名稱結尾不是"s"。 以 flagsattribute 標記列舉標記的類型具有是複數，因為此屬性會指出，可以指定多個值的名稱。|
|[CA1704:識別項應該使用正確的拼字](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|外部可見識別項的名稱包含一個或多個 Microsoft 拼字檢查程式庫無法辨識的字。|
|[CA1708:識別項應該不僅為大小寫不同](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|因為以通用語言執行平台為目標的語言不需要區分大小寫，因此，命名空間、類型、成員和參數的識別項不能只有大小寫的不同。|
|[CA1715:識別項應該使用正確的前置詞](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|外部可見的介面名稱不開頭資本"I"。  在外部可見類型或方法上泛型型別參數的名稱不會啟動以大寫"T"。|
|[CA1720:識別項不應包含類型名稱](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|外部可見成員中的參數名稱包含資料類型名稱，或外部可見成員的名稱包含語言特定的資料類型名稱。|
|[CA1722:識別項不應該有不正確的前置詞](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|根據慣例，只有特定程式設計項目的名稱會以特定的前置字元做為開頭。|
|[CA1711:識別項不應該有不正確的後置詞](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|依照慣例，只有擴充特定基底類型或實作特定介面的類型名稱，或是從這些類型衍生的類型名稱，應以特定保留的後置字元結尾。 其他類型名稱不得使用這些保留的後置字元。|
|[CA1717:只有 FlagsAttribute 列舉應該使用複數名稱](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md)|依照命名規範的要求，列舉的複數名稱代表可以同時指定多個列舉值。|
|[CA1725:參數名稱應該符合基底宣告](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|在覆寫階層架構中一致的參數命名方式，會增加方法覆寫的可用性。 與基底宣告中的名稱不同之衍生方法中的參數名稱，可能會造成方法為基底方法的覆寫或為方法的新多載而混淆。|
|[CA1719:參數名稱不應該和成員名稱相符](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|參數名稱應該傳達參數的意義和成員名稱應該傳達成員的意義。 兩者相同屬罕見的設計。 如果將參數命名為與成員名稱相同的名稱，則不僅會不容易了解，也會讓程式庫難以使用。|
|[CA1701:資源字串複合字應該使用正確的大小寫](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)|資源字串中的每個單字會分割成權杖為基礎的大小寫。 連續兩個語彙基元的組合都由 Microsoft 拼字檢查程式庫進行檢查。 如果可以辨識，這個字便會產生規則違規。|
|[CA1703:資源字串應該使用正確的拼字](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|資源字串包含一個或多個 Microsoft 拼字檢查程式庫無法辨識的字。|
|[CA1724:類型名稱不應該和命名空間相符](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|型別名稱應該不相符.NET Framework 類別庫中所定義的命名空間的名稱。 此規則的違規情形可能會降低程式庫的可用性。|
|[CA1707:識別項不應該包含底線](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|根據慣例，識別項名稱不包含底線 (_) 字元。 此規則會檢查命名空間、類型、成員和參數。|
|[CA1721:屬性名稱不應該相符的 get 方法](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|公用或保護之成員的名稱是以 "Get" 開頭，否則需符合公用或保護之屬性的名稱。 "Get" 方法和屬性的名稱應該清楚區別其功能。|
|[CA1716:識別項不應該和關鍵字相符](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|命名空間 (Namespace) 名稱或類型名稱符合程式語言中的保留關鍵字。 命名空間和類型的識別項不應該符合語言所定義的關鍵字，而這些語言的目標為 Common Language Runtime。|
|[CA1726： 建議使用慣用的詞彙](../code-quality/ca1726-use-preferred-terms.md)|外部可見的識別項名稱包含有替代慣用詞彙存在的詞彙。 或者該名稱包含 "Flag" 或 "Flags" 一詞。|
|[CA1709:識別項應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|依照慣例，參數名稱使用駝峰式命名法的大小寫和命名空間、 類型和成員名稱使用 pascal 命名法大小寫。|
|[CA1702:複合字應該使用正確的大小寫](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|識別項的名稱包含多個單字，而其中至少有一個單字是大小寫不正確的複合字。|
|[CA1712:不要使用型別名稱的列舉值的前置字元](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|因為類型資訊會預期由開發工具所提供的型別名稱不有前置列舉成員的名稱。|
|[CA1710:識別項應該使用正確的後置詞](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)|依照慣例的類型，擴充特定基底類型或實作特定介面或從這些型別，衍生的型別名稱會具有與基底類型或介面相關聯的後置字元。|