---
title: CA1052：靜態預留位置類型應該為密封的
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2c5d22db6a973947faf228e2e3844d63a916e24e
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859493"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052：靜態預留位置類型應該為密封的

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的類型只包含靜態成員，並不以宣告[密封](/dotnet/csharp/language-reference/keywords/sealed)([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) 修飾詞。

## <a name="rule-description"></a>規則描述
 這項規則假設，只包含靜態成員的型別不是繼承，因為類型不提供任何功能，您可以覆寫衍生型別。 不是繼承的型別應該用來標記`sealed`修飾詞，以禁止其使用的基底類型。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將標記的類型為`sealed`。 如果您的目標.NET Framework 2.0 或更新版本，較好的方法來標記的類型為`static`。 如此一來，您可以避免必須宣告私用的建構函式，來防止建立類別。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 只有型別設計為繼承，則隱藏此規則的警告。 如果沒有`sealed`修飾詞表示型別是有用的基底類型。

## <a name="example-of-a-violation"></a>發生違規的範例

### <a name="description"></a>描述
 下列範例顯示違反規則的型別。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>修正使用 Static 修飾詞

### <a name="description"></a>描述
 下列範例示範如何修正此規則的違規情形，來標記具有類型`static`修飾詞。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]

## <a name="related-rules"></a>相關的規則
 [CA1053：靜態預留位置類型不應該包含建構函式](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
