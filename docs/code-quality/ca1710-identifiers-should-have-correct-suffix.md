---
title: "： Ca1710 識別項應該正確的後置詞 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d1593800a2cde8ff0aa1bbecd169f5f3ebd601cb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710：識別項應該使用正確的後置字元
|||  
|-|-|  
|TypeName|IdentifiersShouldHaveCorrectSuffix|  
|CheckId|CA1710|  
|分類|Microsoft.Naming|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 識別項並沒有正確的後置詞。  
  
## <a name="rule-description"></a>規則描述  
 依照慣例，擴充特定基底類型或實作特定介面或衍生自這些類型，類型的名稱會具有與基底類型或介面相關聯的後置字元。  
  
 命名慣例提供共同的外觀文件庫目標通用語言執行平台。 這會減少需要新的軟體程式庫，而增加文件庫由具備專業知識在開發 managed 程式碼開發的客戶信心的學習曲線。  
  
 下表列出具有相關聯的後置字元的介面與基底型別。  
  
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
  
 型別都會實作<xref:System.Collections.ICollection>而產生的型別之資料結構，例如字典、 堆疊或佇列，可提供有意義的預定使用方式的相關資訊之型別的名稱。  
  
 型別都會實作<xref:System.Collections.ICollection>且特定的項目集合的名稱會以 'Collection' 這個字結尾。 例如，集合<xref:System.Collections.Queue>物件會具有名稱 'QueueCollection'。 'Collection' 後置詞表示集合的成員可以在使用列舉`foreach`(`For Each`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 陳述式。  
  
 型別都會實作<xref:System.Collections.IDictionary>名稱以 「 字典 」 這個字結尾，即使類型也會實作<xref:System.Collections.IEnumerable>或<xref:System.Collections.ICollection>。 'Collection' 和 '字典' 後置詞命名慣例可讓使用者可以區別下列兩個列舉模式。  
  
 類型 'Collection' 後置詞，請遵循此列舉模式。  
  
```  
foreach(SomeType x in SomeCollection) { }  
```  
  
 類型 '字典' 後置詞，請遵循此列舉模式。  
  
```  
foreach(SomeType x in SomeDictionary.Values) { }  
```  
  
 A<xref:System.Data.DataSet>物件組成的集合<xref:System.Data.DataTable>組成的集合的物件<xref:System.Data.DataColumn?displayProperty=fullName>和<xref:System.Data.DataRow?displayProperty=fullName>物件，和其他項目。 實作這些集合<xref:System.Collections.ICollection>透過基底<xref:System.Data.InternalDataCollectionBase?displayProperty=fullName>類別。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 重新命名類型，使它的後置字元以正確的詞彙。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可安全地隱藏該類型時，可能會擴充，或將保留任意各種項目的一組通用的資料結構，請使用 'Collection' 後置詞的警告。 在此情況下，提供有關實作、 效能或資料結構中的其他特性有意義資訊的名稱可能有意義 (例如，BinaryTree)。 在其中的型別代表特定的型別 (例如，StringCollection) 集合的情況下，請勿隱藏此規則的警告因為後置詞表示型別可以使用列舉`foreach`陳述式。  
  
 對於其他後置字元，請勿隱藏此規則的警告。 後置詞可讓要盡相符的型別名稱的預定使用方式。  
  
## <a name="related-rules"></a>相關的規則  
 [CA1711：識別項名稱不應該使用不正確的後置字元](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)  
  
## <a name="see-also"></a>請參閱  
 [屬性](/dotnet/standard/design-guidelines/attributes)   
 [處理和引發事件](/dotnet/standard/events/index)  