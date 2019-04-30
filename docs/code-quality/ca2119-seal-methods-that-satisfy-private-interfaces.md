---
title: CA2119:密封方法以滿足私用介面的要求
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4c019e98e7f1311b6521dff563cb8e7bb0a2356e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62544009"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119:密封方法以滿足私用介面的要求

|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 可繼承的公用類型提供的可覆寫方法實作`internal`(`Friend` Visual Basic 中) 介面。

## <a name="rule-description"></a>規則描述
 介面方法具有公用存取範圍，不能變更所實作的型別。 內部介面會建立不是要定義的介面組件外部實作的合約。 公用類型會實作內部介面使用的方法`virtual`(`Overridable` Visual Basic 中) 修飾詞可讓由衍生的型別，會在組件外覆寫的方法。 如果在定義組件中的第二個型別呼叫方法，並預期僅供內部使用的合約，相反地，覆寫的方法，在外部組件中執行時，可能會受到危害的行為。 這會造成安全性漏洞。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，防止方法遭到覆寫外部組件使用下列其中一項：

- 請宣告的型別`sealed`(`NotInheritable` Visual Basic 中)。

- 變更要宣告型別的存取範圍`internal`(`Friend` Visual Basic 中)。

- 移除的宣告型別中的所有公用建構函式。

- 實作方法，而不需使用`virtual`修飾詞。

- 明確實作的方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏這個警告規則在仔細檢閱之後, 沒有安全性問題存在，可能是如果在組件外覆寫此方法可利用來攻擊。

## <a name="example-1"></a>範例 1
 下列範例示範一個型別， `BaseImplementation`，會違反此規則。

 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]

## <a name="example-2"></a>範例 2
 下列範例會利用上述範例的虛擬方法實作。

 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]

## <a name="see-also"></a>另請參閱

- [介面](/dotnet/csharp/programming-guide/interfaces/index)
- [介面](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)