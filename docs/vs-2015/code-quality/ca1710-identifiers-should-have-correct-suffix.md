---
title: CA1710：識別碼應該有正確的尾碼 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543984"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710:識別項應該使用正確的後置字元
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|類別|Microsoft。命名|
|中斷變更|中斷|

## <a name="cause"></a>原因
 識別碼的尾碼不正確。

## <a name="rule-description"></a>規則描述
 依照慣例，擴充特定基底類型或實作為某些介面的類型名稱，或是從這些類型衍生的類型，其後綴會與基底類型或介面相關聯。

 命名慣例可針對以 common language runtime 為目標的程式庫提供常見的外觀。 這可減少新軟體程式庫所需的學習曲線，並提高客戶的信賴度，以開發受管理程式碼的專業知識的人員來開發該程式庫。

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
|<xref:System.IO.Stream?displayProperty=fullName>|資料流|
|<xref:System.Security.IPermission?displayProperty=fullName>|權限|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|條件|
|事件處理常式委派。|EventHandler|

 實作為型別（ <xref:System.Collections.ICollection> 例如字典、堆疊或佇列）的型別，可以用來提供有關型別之預定使用方式的有意義資訊的名稱。

 實作為 <xref:System.Collections.ICollection> 特定專案集合的型別，其名稱結尾為 ' collection ' 這個字。 例如，物件集合的 <xref:System.Collections.Queue> 名稱為 ' QueueCollection '。 ' Collection ' 後置詞表示可以使用 `foreach` `For Each`) 語句中的 (來列舉集合的成員 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 。

 實作為的 <xref:System.Collections.IDictionary> 型別，其名稱會以 ' Dictionary ' 這個字結尾，即使型別也會執行 <xref:System.Collections.IEnumerable> 或 <xref:System.Collections.ICollection> 。 「集合」和「字典」尾碼命名慣例可讓使用者區分下列兩個列舉模式。

 具有 ' Collection ' 後置字元的類型會遵循此列舉模式。

```
foreach(SomeType x in SomeCollection) { }
```

 具有「字典」尾碼的型別會遵循此列舉模式。

```
foreach(SomeType x in SomeDictionary.Values) { }
```

 <xref:System.Data.DataSet>物件是由物件集合所組成 <xref:System.Data.DataTable> ，這些物件是由和物件的集合所組成 <xref:System.Data.DataColumn?displayProperty=fullName> <xref:System.Data.DataRow?displayProperty=fullName> 。 這些集合會 <xref:System.Collections.ICollection> 透過基類來執行 <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> 。

## <a name="how-to-fix-violations"></a>如何修正違規
 將類型重新命名，使其以正確的詞彙尾碼。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果類型是可能會擴充的一般化資料結構，或是將保留任意一組不同的專案，則可以安全地隱藏警告以使用 ' Collection ' 尾碼。 在此情況下，提供資料結構之執行、效能或其他特性相關有意義資訊的名稱可能會有意義 (例如 BinaryTree) 。 如果類型代表特定類型的集合 (例如，StringCollection) ，請勿隱藏此規則的警告，因為後置詞表示可以使用語句來列舉型別 `foreach` 。

 若為其他尾碼，請勿隱藏此規則的警告。 尾碼允許從型別名稱看出預期的使用方式。

## <a name="related-rules"></a>相關規則
 [CA1711:識別項名稱不應該使用不正確的後置字元](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>另請參閱
 [屬性](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)[筆尖：事件和委派](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
