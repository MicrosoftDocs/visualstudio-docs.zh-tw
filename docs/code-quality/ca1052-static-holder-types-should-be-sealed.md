---
title: CA1052:靜態預留位置類型應為靜態或 NotInheritable
ms.date: 07/25/2019
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
ms.openlocfilehash: 0a574f7f77277255acf2150c218c3f4db061e75c
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2019
ms.locfileid: "68604773"
---
# <a name="ca1052-static-holder-types-should-be-static-or-notinheritable"></a>CA1052:靜態預留位置類型應為靜態或 NotInheritable

|||
|-|-|
|TypeName|StaticHolderTypesAnalyzer|
|CheckId|CA1052|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因

非抽象類別型只包含靜態成員 (不是可能的預設函式), 而且不會使用[static](/dotnet/csharp/language-reference/keywords/static)或[Shared](/dotnet/visual-basic/language-reference/modifiers/shared)修飾詞來宣告。

根據預設, 此規則只會查看外部可見的類型, 但這是[可](#configurability)設定的。

## <a name="rule-description"></a>規則描述

規則 CA1052 假設僅包含靜態成員的類型不是為了繼承而設計, 因為該類型不會提供可在衍生類型中覆寫的任何功能。 不想要繼承的類型應該在中`static` C#以修飾詞標記, 以禁止其作為基底類型使用。 此外, 應該移除其預設的函式。 在 Visual Basic 中, 類別應該轉換成[模組](/dotnet/visual-basic/language-reference/statements/module-statement)。

對於具有基類的抽象類別或類別, 不會引發此規則。 不過, 此規則會針對支援空白介面的類別引發。

> [!NOTE]
> 在此規則的 FxCop 分析器執行中, 它也包含[規則 CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)的功能。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規, 請將類型標記`static`為, 並移除預設的C#函式 (), 或將它轉換成模組 (Visual Basic)。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

只有當類型設計為要繼承時, 才隱藏此規則的警告。 缺少`static`修飾詞, 會建議型別相當適合做為基底型別。

## <a name="configurability"></a>可設定性

如果您是從[FxCop 分析器](install-fxcop-analyzers.md)執行此規則 (而不是透過靜態程式碼分析), 您可以根據其存取範圍, 設定程式碼基底中的哪些部分, 以執行此規則。 例如, 若要指定規則只針對非公用 API 介面執行, 請將下列機碼值組新增至專案中的 EditorConfig 檔案:

```ini
dotnet_code_quality.ca1052.api_surface = private, internal
```

您可以只針對此規則、所有規則或此類別中的所有規則 (設計) 設定此選項。 如需詳細資訊, 請參閱[設定 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example-of-a-violation"></a>違規的範例

下列範例顯示違反規則的類型:

[!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
[!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
[!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]

## <a name="fix-with-the-static-modifier"></a>使用靜態修飾詞修正

下列範例顯示如何在中`static` C#以修飾詞標記類型, 以修正此規則的違規:

```csharp
public static class StaticMembers
{
    public static int SomeProperty { get; set; }
    public static void SomeMethod() { }
}
```