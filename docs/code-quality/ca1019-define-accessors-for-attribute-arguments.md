---
title: CA1019:定義屬性引數的存取子
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4e9491a608087565e84274d47c601b0629737d2f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779346"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019:定義屬性引數的存取子

|||
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|CheckId|CA1019|
|分類|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因
 在其建構函式，屬性會定義並沒有對應的屬性的引數。

## <a name="rule-description"></a>規則描述
 屬性可以定義必須在將屬性套用至目標時指定的強制引數。 這些引數也稱為位置引數，因為它們會當做位置參數提供給屬性建構函式。 對於每個強制引數而言，屬性 (Attribute) 還須提供對應的唯讀屬性 (Property)，才可以在執行時期擷取引數值。 此規則會檢查每個建構函式參數，您已定義對應的屬性。

 屬性也可以定義選擇性引數，也稱為具名引數。 這些引數會依照名稱提供給屬性 (Attribute) 建構函式，且必須有對應的讀取/寫入屬性 (Property)。

 必要和選擇性引數，對應的屬性和建構函式參數應該使用相同的名稱但大小寫不同。 屬性使用 pascal 命名法大小寫和參數使用駝峰式命名法大小寫。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，加入不具其中每個建構函式參數的唯讀屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您不想要擷取必要的引數的值，則隱藏此規則的警告。

## <a name="custom-attributes-example"></a>自訂屬性範例

下列範例定義必要的 （位置） 參數的兩個屬性。 首次實作的屬性定義不正確。 第二個的實作是正確的。

[!code-csharp[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
[!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]

## <a name="positional-and-named-arguments"></a>位置和具名引數

位置和具名引數讓清楚哪些引數是必要的屬性，而哪些引數是選擇性的程式庫的取用者。

下列範例示範具有位置和具名引數的屬性的實作：

[!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]

下列範例示範如何將自訂屬性套用至兩個屬性：

[!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]

## <a name="related-rules"></a>相關的規則
 [CA1813:避免使用非密封的屬性](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>另請參閱
 [屬性](/dotnet/standard/design-guidelines/attributes)