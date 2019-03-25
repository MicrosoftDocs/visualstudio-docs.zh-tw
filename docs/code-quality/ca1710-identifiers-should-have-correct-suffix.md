---
title: CA1710:識別項應該使用正確的後置字元
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65ac417476752da832e5e9ebe693f6c83a5c1cfe
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57868071"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710:識別項應該使用正確的後置字元

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因

識別項並沒有正確的後置詞。

根據預設，此規則只會查看外部可見的識別項，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

依照慣例的類型，擴充特定基底類型或實作特定介面或從這些型別，衍生的型別名稱會具有與基底類型或介面相關聯的後置字元。

命名慣例提供了通用程式庫 common language runtime 為目標。 這可降低學習曲線，需要新的軟體程式庫，並增加程式庫，開發人員專業開發的 managed 程式碼中的其他人的客戶信心。

下表列出具有相關聯的後置詞的介面與基底型別。

|基底型別/介面|尾碼|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|屬性|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|例外|
|<xref:System.Collections.ICollection?displayProperty=fullName>|集合|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|字典|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|集合|
|<xref:System.Collections.Queue?displayProperty=fullName>|集合或佇列|
|<xref:System.Collections.Stack?displayProperty=fullName>|集合或堆疊|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|集合|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|字典|
|<xref:System.Data.DataSet?displayProperty=fullName>|資料集|
|<xref:System.Data.DataTable?displayProperty=fullName>|集合或 DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|資料流|
|<xref:System.Security.IPermission?displayProperty=fullName>|權限|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|條件|
|事件處理常式委派。|EventHandler|

型別都會實作<xref:System.Collections.ICollection>而產生的類型的資料結構，例如字典、 堆疊或佇列，可提供之型別的預定的使用方式的有意義資訊的名稱。

型別都會實作<xref:System.Collections.ICollection>和一組特定的項目有 'Collection' 這個字結尾的名稱。 比方說，許多<xref:System.Collections.Queue>物件會具有 'QueueCollection' 的名稱。 'Collection' 後置詞表示集合的成員，可以透過列舉`foreach`(`For Each`在[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 陳述式。

型別都會實作<xref:System.Collections.IDictionary>具有名稱結尾為 「 字典 」 這個字，即使該型別也實作<xref:System.Collections.IEnumerable>或<xref:System.Collections.ICollection>。 'Collection' 和 '字典' 後置詞命名慣例可讓使用者能夠區別下列兩個列舉模式。

具有 'collection' 的型別會遵循這個列舉型別模式。

```
foreach(SomeType x in SomeCollection) { }
```

以 「 字典 」 字尾的型別會遵循這個列舉型別模式。

```
foreach(SomeType x in SomeDictionary.Values) { }
```

A<xref:System.Data.DataSet>物件所組成的集合<xref:System.Data.DataTable>組成的集合的物件<xref:System.Data.DataColumn?displayProperty=fullName>和<xref:System.Data.DataRow?displayProperty=fullName>物件，其他項目。 這些集合會實作<xref:System.Collections.ICollection>透過基底<xref:System.Data.InternalDataCollectionBase?displayProperty=fullName>類別。

## <a name="how-to-fix-violations"></a>如何修正違規

因此，它會加上正確的詞彙，請重新命名類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它可安全地隱藏警告，如果類型是一種通用的資料結構，可能會擴充，或將保留任意一組的各種不同的項目，請使用 ' collection '。 在此情況下，提供有意義的資訊有關實作、 效能或資料結構中的其他特性的名稱可能意義 (比方說，BinaryTree)。 在其中的型別代表特定的型別 (例如 StringCollection) 集合的情況下，請勿隱藏此規則的警告，可以藉由使用列舉類型的後置詞表示因為`foreach`陳述式。

對於其他後置字元，請勿隱藏此規則的警告。 後置詞允許的用途是明顯的是從型別名稱。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```
dotnet_code_quality.ca1710.api_surface = private, internal
```

此類別 （命名） 中，您可以設定此選項，只是這項規則，所有規則，或所有的規則。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="related-rules"></a>相關的規則

[CA1711:識別項不應該有不正確的後置詞](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>另請參閱

- [屬性](/dotnet/standard/design-guidelines/attributes)
- [處理和引發事件](/dotnet/standard/events/index)