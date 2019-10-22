---
title: CA2105：陣列欄位不應為唯讀 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7599359899ca4860913b5bc0dd601fd06d9b8b54
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666018"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105：陣列欄位不應為唯讀
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Category|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 持有陣列的公用或受保護欄位會宣告為唯讀。

## <a name="rule-description"></a>規則描述
 當您將 `readonly` （在 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 中 `ReadOnly`）修飾詞套用至包含陣列的欄位時，無法將欄位變更為參考不同的陣列。 但是，儲存在唯讀欄位的陣列元素則可以變更。 根據可公開存取之唯讀陣列的元素，做出決策或執行作業的程式碼，可能會包含易受攻擊的安全性弱點。

 請注意，具有公用欄位也會違反設計規則[CA1051：不要宣告可見的實例欄位](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則所識別的安全性弱點，請勿依賴可公開存取之唯讀陣列的內容。 強烈建議您使用下列其中一個程式：

- 將陣列取代為無法變更的強型別集合。 如需詳細資訊，請參閱<xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>。

- 將公用欄位取代為傳回私用陣列複本的方法。 因為您的程式碼不依賴複製，所以如果修改元素，就不會有任何危險。

  如果您選擇第二種方法，請勿將欄位取代為屬性;傳回陣列的屬性會對效能造成不良影響。 如需詳細資訊，請參閱[CA1819：屬性不應傳回陣列](../code-quality/ca1819-properties-should-not-return-arrays.md)。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 強烈建議您不要排除此規則的警告。 幾乎不會發生任何情況，因為唯讀欄位的內容並不重要。 如果您的案例是這種情況，請移除 `readonly` 修飾詞，而不要排除訊息。

## <a name="example"></a>範例
 這個範例會示範違反此規則的危險。 第一個部分顯示類型為 `MyClassWithReadOnlyArrayField` 的範例程式庫，其中包含兩個不安全的欄位（`grades` 和 `privateGrades`）。 欄位 `grades` 是公用的，因此容易受到任何呼叫者的影響。 欄位 `privateGrades` 是私用的，但仍受到弱點的影響，因為 `GetPrivateGrades` 方法會將它傳回給呼叫者。 @No__t_1 方法會以安全的方式公開 [`securePrivateGrades`] 欄位。 它會宣告為私用，以遵循良好的設計實務。 第二個部分所顯示的程式碼會變更儲存在 `grades` 和 `privateGrades` 成員中的值。

 範例類別庫會出現在下列範例中。

 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ArrayFieldsNotReadOnly/cs/FxCop.Security.ArrayFieldsNotReadOnly.cs#1)]

## <a name="example"></a>範例
 下列程式碼會使用範例類別庫來說明唯讀陣列的安全性問題。

 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestArrayFieldsRead/cs/FxCop.Security.TestArrayFieldsRead.cs#1)]

 此範例的輸出為：

 **在進行篡改之前：90、90、90私用成績：90、90、90安全等級、90、90、90** 
**在篡改之後：成績：90、555、90私用成績：90、555、90安全等級、90、90、90**
## <a name="see-also"></a>請參閱
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
