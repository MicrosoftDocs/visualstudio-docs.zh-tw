---
title: CA1052：靜態預留位置類型應該為密封的
ms.date: 11/09/2018
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
ms.openlocfilehash: 937a5eba672eef928dd4f8c0e5356e504d769153
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348658"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052：靜態預留位置類型應該為密封的

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因

公用或受保護，非抽象型別只包含靜態成員，並不以宣告[密封](/dotnet/csharp/language-reference/keywords/sealed)([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) 修飾詞。

## <a name="rule-description"></a>規則描述

規則 CA1052 假設，只包含靜態成員的型別不是繼承，因為類型不提供任何功能，您可以覆寫衍生型別。 不是繼承的型別應該用來標記`sealed`或`NotInheritable`修飾詞，以禁止其使用的基底類型。 此規則不會引發抽象類別。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，將標示為的型別`sealed`或`NotInheritable`。 如果您的目標.NET Framework 2.0 或更新版本，較好的方法將標示為的型別`static`或`Shared`。 以這種方式，您不需要宣告以防止建立類別的私用建構函式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

只有型別設計為繼承，則隱藏此規則的警告。 缺少`sealed`或`NotInheritable`修飾詞表示型別是有用的基底類型。

## <a name="example-of-a-violation"></a>發生違規的範例

下列範例顯示違反規則的型別。

[!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
[!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
[!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>修正使用 static 修飾詞

下列範例示範如何修正此規則的違規情形，來標記具有類型`static`修飾詞C#。

[!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]

## <a name="related-rules"></a>相關的規則

[CA1053：靜態預留位置類型不應該包含建構函式](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)