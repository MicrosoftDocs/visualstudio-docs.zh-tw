---
title: CA1052:靜態預留位置類型應該為密封的
ms.date: 03/11/2019
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
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 46a8c9a4e22c7a54a4b2b68f95bb2b81f3a0888e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778589"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052:靜態預留位置類型應該為密封的

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因

非抽象類型只包含靜態成員，並不以宣告[密封](/dotnet/csharp/language-reference/keywords/sealed)([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) 修飾詞。

根據預設，此規則只會查看外部可見的類型，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

規則 CA1052 假設，只包含靜態成員的型別不是繼承，因為類型不提供任何功能，您可以覆寫衍生型別。 不是繼承的型別應該用來標記`sealed`或`NotInheritable`修飾詞，以禁止其使用的基底類型。 此規則不會引發抽象類別。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，將標示為的型別`sealed`或`NotInheritable`。 如果您的目標.NET Framework 2.0 或更新版本，較好的方法將標示為的型別`static`或`Shared`。 以這種方式，您不需要宣告以防止建立類別的私用建構函式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

只有型別設計為繼承，則隱藏此規則的警告。 缺少`sealed`或`NotInheritable`修飾詞表示型別是有用的基底類型。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```
dotnet_code_quality.ca1052.api_surface = private, internal
```

此類別 （設計） 中，您可以設定此選項，只是這項規則，所有規則，或所有的規則。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example-of-a-violation"></a>發生違規的範例

下列範例顯示違反規則的型別：

[!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
[!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
[!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>修正使用 static 修飾詞

下列範例示範如何修正此規則的違規情形，來標記具有類型`static`修飾詞C#:

[!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]

## <a name="related-rules"></a>相關的規則

- [CA1053:靜態預留位置類型不應該有建構函式](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)