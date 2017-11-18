---
title: "Ca1019： 必須定義存取子屬性引數 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9f04a49c8c68fcc597ecd98471b46932d467b365
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019：必須定義屬性引數的存取子
|||  
|-|-|  
|TypeName|DefineAccessorsForAttributeArguments|  
|CheckId|CA1019|  
|分類|Microsoft.Design|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 在其建構函式，屬性會定義並沒有對應的屬性的引數。  
  
## <a name="rule-description"></a>規則描述  
 屬性可以定義必須在將屬性套用至目標時指定的強制引數。 這些引數也稱為位置引數，因為它們會當做位置參數提供給屬性建構函式。 對於每個強制引數而言，屬性 (Attribute) 還須提供對應的唯讀屬性 (Property)，才可以在執行時期擷取引數值。 此規則會檢查每個建構函式參數，您已定義之對應的屬性。  
  
 屬性也可以定義選擇性引數，也稱為具名引數。 這些引數會依照名稱提供給屬性 (Attribute) 建構函式，且必須有對應的讀取/寫入屬性 (Property)。  
  
 必要和選擇性引數，對應的屬性和建構函式參數應該使用相同的名稱，但大小寫不同。 屬性，請使用 Pascal 大小寫，與參數使用 camel 命名法的大小寫。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，加入唯讀屬性，針對每個建構函式參數沒有任何一個。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 如果您不想要擷取必要的引數的值，則隱藏此規則的警告。  
  
## <a name="custom-attributes-example"></a>自訂屬性範例  
  
### <a name="description"></a>描述  
 下列範例定義必要的 （位置） 參數的兩個屬性。 首次實作的屬性定義不正確。 第二個實作是正確的。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]  
  
## <a name="positional-and-named-arguments"></a>位置和具名引數  
  
### <a name="description"></a>描述  
 位置和具名引數，請清除您的程式庫的引數是必要的屬性和哪些引數是選擇性的取用者。  
  
 下列範例顯示其屬性具有位置和具名引數的實作。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]  
  
### <a name="comments"></a>註解  
 下列範例顯示如何將自訂屬性套用至兩個屬性。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA1813：避免使用非密封屬性](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## <a name="see-also"></a>另請參閱  
 [屬性](/dotnet/standard/design-guidelines/attributes)