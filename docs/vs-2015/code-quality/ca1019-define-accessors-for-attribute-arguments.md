---
title: CA1019 必須：定義屬性引數的存取子 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4e77f3a4eec7495e6b4abe13bec93d341f961463
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662006"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019：必須定義屬性引數的存取子
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|CheckId|CA1019|
|Category|Microsoft. Design|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 在它的函式中，屬性會定義沒有對應屬性的引數。

## <a name="rule-description"></a>規則描述
 屬性可以定義必須在將屬性套用至目標時指定的強制引數。 這些引數也稱為位置引數，因為它們會當做位置參數提供給屬性建構函式。 對於每個強制引數而言，屬性 (Attribute) 還須提供對應的唯讀屬性 (Property)，才可以在執行時期擷取引數值。 此規則會檢查每個函式參數是否已定義對應的屬性。

 屬性也可以定義選擇性引數，也稱為具名引數。 這些引數會依照名稱提供給屬性 (Attribute) 建構函式，且必須有對應的讀取/寫入屬性 (Property)。

 對於必要和選擇性引數，對應的屬性和函式參數應使用相同的名稱，但大小寫不同。 屬性使用 Pascal 大小寫，而參數則使用 camel 大小寫。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請為每個不具有一個的函式參數新增唯讀屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您不想要讓強制引數的值可供使用，請隱藏此規則的警告。

## <a name="custom-attributes-example"></a>自訂屬性範例

### <a name="description"></a>描述
 下列範例顯示兩個定義強制（位置）參數的屬性。 屬性的第一個執行定義不正確。 第二個執行是正確的。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/cs/FxCop.Design.AttributeAccessors.cs#1)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/vb/FxCop.Design.AttributeAccessors.vb#1)]

## <a name="positional-and-named-arguments"></a>位置和具名引數

### <a name="description"></a>描述
 位置和命名的引數會對您的程式庫取用者進行清除，屬性的引數是必要的，而哪些引數是選擇性的。

 下列範例顯示具有位置和具名引數的屬性的執行。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamed/cs/FxCop.Design.AttributeAccessorsNamed.cs#1)]

### <a name="comments"></a>註解
 下列範例顯示如何將自訂屬性套用至兩個屬性。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamedApplied/cs/FxCop.Design.AttributeAccessorsNamedApplied.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA1813：避免使用非密封屬性](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>請參閱
 [屬性](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
