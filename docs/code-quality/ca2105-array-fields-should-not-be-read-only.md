---
title: "CA2105： 陣列欄位應該不唯讀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bfc20d1bb2ae34455c836219bb809221f2ca382e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105：陣列欄位不應為唯讀
|||  
|-|-|  
|TypeName|ArrayFieldsShouldNotBeReadOnly|  
|CheckId|CA2105|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 公用或受保護的欄位保存陣列宣告唯讀狀態。  
  
## <a name="rule-description"></a>規則描述  
 當您將套用`readonly`(`ReadOnly`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 修飾詞，以包含陣列中，欄位的欄位不能變更為參考不同的陣列。 但是，儲存在唯讀欄位的陣列元素則可以變更。 決定，或執行作業的可公開存取的唯讀陣列項目為基礎的程式碼可能包含利用的安全性弱點。  
  
 請注意，也需要公用欄位違反設計規則[CA1051： 不要宣告可見的執行個體欄位](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則所識別的安全性弱點，請勿依賴可公開存取的唯讀陣列的內容。 強烈建議使用下列程序的其中一個：  
  
-   無法變更的強類型集合取代陣列。 如需詳細資訊，請參閱<xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>。  
  
-   使用傳回的私用陣列複製品的方法取代公用欄位。 因為您的程式碼不會依賴複製品，不是可能如果已修改的項目。  
  
 如果您選擇第二種方法時，不要取代欄位與屬性。傳回陣列造成不良的屬性會影響效能。 如需詳細資訊，請參閱[CA1819： 屬性不應傳回陣列](../code-quality/ca1819-properties-should-not-return-arrays.md)。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 此規則的警告排除強烈。 幾乎在所有情況中，就會都發生唯讀欄位的內容中都很重要。 如果這是您的案例使用的情況下，移除`readonly`修飾詞，而不是排除訊息。  
  
## <a name="example"></a>範例  
 此範例示範違反此規則的資訊。 第一個部分顯示的範例程式庫，以類型、 `MyClassWithReadOnlyArrayField`，其中包含兩個欄位 (`grades`和`privateGrades`) 並未受到保護。 欄位`grades`是公用的且因此易於遭受任何呼叫端。 欄位`privateGrades`是私用，但是是仍然易受攻擊，因為它會傳回到呼叫端所`GetPrivateGrades`方法。 `securePrivateGrades`欄位會以安全的方式公開`GetSecurePrivateGrades`方法。 它宣告為私用遵循良好的設計作法。 第二部分顯示會變更值儲存在程式碼`grades`和`privateGrades`成員。  
  
 範例類別程式庫會出現在下列範例中。  
  
 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]  
  
## <a name="example"></a>範例  
 下列程式碼會使用範例類別庫說明唯讀陣列安全性問題。  
  
 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]  
  
 此範例的輸出為：  
  
 **之前遭到竄改： 成績： 90，90，90 的私用成績： 90，90，90 保護等級，90，90，90**  
**之後遭到竄改： 成績： 90、 555，90 的私用成績： 90、 555，90 保護等級，90，90，90**   
## <a name="see-also"></a>另請參閱  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>