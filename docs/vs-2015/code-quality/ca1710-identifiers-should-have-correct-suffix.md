---
title: CA1710：識別碼應具有正確的尾碼 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ee7ce7c4e9edad9d941b4a70b2a199a37130e43
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543984"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710:識別項應該使用正確的後置字元
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|類別|Microsoft. 命名|
|中斷變更|中斷|

## <a name="cause"></a>原因
 識別碼沒有正確的後置詞。

## <a name="rule-description"></a>規則描述
 依照慣例，擴充特定基底類型或執行特定介面的類型名稱，或衍生自這些類型的類型，會有與基底類型或介面相關聯的尾碼。

 命名慣例提供以通用語言執行時間為目標之程式庫的常見外觀。 這可減少新軟體程式庫所需的學習曲線，並提高客戶對於開發 managed 程式碼專業知識的人員所開發的信心。

 下表列出具有相關聯尾碼的基底類型和介面。

|基底類型/介面|後置詞|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|屬性|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|例外狀況|
|<xref:System.Collections.ICollection?displayProperty=fullName>|集合|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|字典|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|集合|
|<xref:System.Collections.Queue?displayProperty=fullName>|集合或佇列|
|<xref:System.Collections.Stack?displayProperty=fullName>|集合或堆疊|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|集合|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|字典|
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|
|<xref:System.Data.DataTable?displayProperty=fullName>|Collection 或 DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|STREAM|
|<xref:System.Security.IPermission?displayProperty=fullName>|權限|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|條件|
|事件處理常式委派。|EventHandler|

 實作為類型的 <xref:System.Collections.ICollection> 資料結構（例如字典、堆疊或佇列）的型別，是允許的名稱，這些型別可提供有關類型的預定使用方式的有意義資訊。

 實 <xref:System.Collections.ICollection> 作為特定專案集合的型別，其名稱會以 ' collection ' 這個字為結尾。 例如，物件的集合 <xref:System.Collections.Queue> 名稱會是 ' QueueCollection '。 ' Collection ' 後置詞表示可以使用 `foreach` （ `For Each` in）語句來列舉集合的成員 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 。

 執行的 <xref:System.Collections.IDictionary> 型別具有以「字典」單字結尾的名稱，即使類型也會執行 <xref:System.Collections.IEnumerable> 或 <xref:System.Collections.ICollection> 。 「集合」和「字典」尾碼的命名慣例可讓使用者區分下列兩種列舉模式。

 具有 ' Collection ' 尾碼的類型會遵循此列舉模式。

```
foreach(SomeType x in SomeCollection) { }
```

 具有「字典」尾碼的類型會遵循此列舉模式。

```
foreach(SomeType x in SomeDictionary.Values) { }
```

 <xref:System.Data.DataSet>物件是由物件的集合 <xref:System.Data.DataTable> 所組成，其中包含 <xref:System.Data.DataColumn?displayProperty=fullName> 和物件的集合 <xref:System.Data.DataRow?displayProperty=fullName> ，還有其他專案。 這些集合會 <xref:System.Collections.ICollection> 透過基類來執行 <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> 。

## <a name="how-to-fix-violations"></a>如何修正違規
 重新命名類型，使其後綴正確的字詞。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果類型是可以擴充的一般化資料結構，或是會保存任意一組不同的專案，則隱藏警告以使用 ' Collection ' 尾碼是安全的。 在此情況下，提供有關資料結構之執行、效能或其他特性的有意義資訊的名稱可能有意義（例如，BinaryTree）。 如果類型代表特定類型的集合（例如，StringCollection），請勿隱藏此規則的警告，因為後置詞表示可以使用語句來列舉該類型 `foreach` 。

 若為其他尾碼，請勿隱藏此規則的警告。 尾碼可讓您從類型名稱中看出預期的使用方式。

## <a name="related-rules"></a>相關規則
 [CA1711:識別項名稱不應該使用不正確的後置字元](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>另請參閱
 [屬性](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)[筆尖：事件和委派](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
