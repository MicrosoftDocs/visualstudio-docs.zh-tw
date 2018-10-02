---
title: ： Ca1710 識別項應該正確的後置詞 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7e9288e5d487adbc454ca6874a5cf6784c0ee960
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588286"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710：識別項應該使用正確的後置字元
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA1710： 識別項應該使用正確的後置詞](https://docs.microsoft.com/visualstudio/code-quality/ca1710-identifiers-should-have-correct-suffix)。

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|分類|Microsoft.Naming|
|中斷變更|中斷|

## <a name="cause"></a>原因
 識別項並沒有正確的後置詞。

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
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|
|<xref:System.Data.DataTable?displayProperty=fullName>|集合或 DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|資料流|
|<xref:System.Security.IPermission?displayProperty=fullName>|權限|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|條件|
|事件處理常式委派。|事件處理常式|

 型別都會實作<xref:System.Collections.ICollection>而產生的類型的資料結構，例如字典、 堆疊或佇列，可提供之型別的預定的使用方式的有意義資訊的名稱。

 型別都會實作<xref:System.Collections.ICollection>和一組特定的項目有 'Collection' 這個字結尾的名稱。 比方說，許多<xref:System.Collections.Queue>物件會具有 'QueueCollection' 的名稱。 'Collection' 後置詞表示集合的成員，可以透過列舉`foreach`(`For Each`在[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) 陳述式。

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

## <a name="related-rules"></a>相關的規則
 [CA1711：識別項名稱不應該使用不正確的後置字元](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>另請參閱
 [屬性](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [NIB： 事件與委派](http://msdn.microsoft.com/en-us/d98fd58b-fa4f-4598-8378-addf4355a115)



