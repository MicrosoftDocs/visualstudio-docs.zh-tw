---
title: CA1019:定義存取子屬性引數 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 01d4b421f196eec7401f12ca8eeb7a52b2396065
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704205"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019:定義屬性引數的存取子
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

### <a name="description"></a>描述
 下列範例定義必要的 （位置） 參數的兩個屬性。 首次實作的屬性定義不正確。 第二個的實作是正確的。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/cs/FxCop.Design.AttributeAccessors.cs#1)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/vb/FxCop.Design.AttributeAccessors.vb#1)]

## <a name="positional-and-named-arguments"></a>位置和具名引數

### <a name="description"></a>描述
 位置和具名引數，請清除您哪些引數是必要的屬性，而哪些引數是選擇性的程式庫的取用者。

 下列範例顯示有位置和具名引數的屬性的實作。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamed/cs/FxCop.Design.AttributeAccessorsNamed.cs#1)]

### <a name="comments"></a>註解
 下列範例示範如何將自訂屬性套用至兩個屬性。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamedApplied/cs/FxCop.Design.AttributeAccessorsNamedApplied.cs#1)]

## <a name="related-rules"></a>相關的規則
 [CA1813:避免使用非密封的屬性](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>另請參閱
 [屬性](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
