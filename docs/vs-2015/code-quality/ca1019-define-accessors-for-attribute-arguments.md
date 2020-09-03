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
ms.openlocfilehash: ec9be9dae502ec48570a85576f483518ed0d75d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534949"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019:定義屬性引數的存取子
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|CheckId|CA1019|
|類別|Microsoft. 設計|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 在其函式中，屬性會定義沒有對應屬性的引數。

## <a name="rule-description"></a>規則描述
 屬性可以定義必須在將屬性套用至目標時指定的強制引數。 這些引數也稱為位置引數，因為它們會當做位置參數提供給屬性建構函式。 對於每個強制引數而言，屬性 (Attribute) 還須提供對應的唯讀屬性 (Property)，才可以在執行時期擷取引數值。 這項規則會檢查每個函式參數是否已定義對應的屬性。

 屬性也可以定義選擇性引數，也稱為具名引數。 這些引數會依照名稱提供給屬性 (Attribute) 建構函式，且必須有對應的讀取/寫入屬性 (Property)。

 針對必要和選擇性引數，對應的屬性和函式參數應使用相同的名稱，但大小寫不同。 屬性使用 Pascal 大小寫，而參數則使用 camel 大小寫。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請為每個沒有一個的函式參數新增唯讀屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您不想要讓強制引數的值可以被抓取，請隱藏此規則的警告。

## <a name="custom-attributes-example"></a>自訂屬性範例

### <a name="description"></a>描述
 下列範例顯示兩個屬性，可定義強制的 (位置) 參數。 未正確定義屬性的第一次執行。 第二個執行是正確的。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/cs/FxCop.Design.AttributeAccessors.cs#1)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/vb/FxCop.Design.AttributeAccessors.vb#1)]

## <a name="positional-and-named-arguments"></a>位置和具名引數

### <a name="description"></a>描述
 位置和具名引數對您的程式庫的取用者而言，必須是屬性所需的引數，以及哪些引數是選擇性的。

 下列範例顯示具有位置和具名引數的屬性實作為。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamed/cs/FxCop.Design.AttributeAccessorsNamed.cs#1)]

### <a name="comments"></a>註解
 下列範例顯示如何將自訂屬性套用至兩個屬性。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamedApplied/cs/FxCop.Design.AttributeAccessorsNamedApplied.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA1813:避免使用非密封屬性](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>另請參閱
 [屬性](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
