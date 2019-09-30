---
title: CA1812:避免使用未執行個體化的內部類別
ms.date: 05/16/2019
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f924e9530a7ee43ec2222366141c3af6be2efc29
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233603"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812:避免使用未執行個體化的內部類別

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|分類|Microsoft.Performance|
|重大變更|不中斷|

## <a name="cause"></a>原因

內部（元件層級）型別永遠不會具現化。

## <a name="rule-description"></a>規則描述

此規則會嘗試找出對類型的其中一個函式的呼叫，並在找不到任何呼叫時報告違規。

此規則不會檢查下列類型：

- 值類型

- 抽象類別型

- 列舉

- 委派

- 編譯器發出的陣列類型

- 無法具現化且只定義[`static`](/dotnet/csharp/language-reference/keywords/static) （[ `Shared`在 Visual Basic 中](/dotnet/visual-basic/language-reference/modifiers/shared)）方法的類型。

如果您將<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName>套用至要分析的元件，此規則就不會標示標記為[`internal`](/dotnet/csharp/language-reference/keywords/internal) （[ `Friend`在 Visual Basic 中](/dotnet/visual-basic/language-reference/modifiers/friend)）的類型，因為 friend 元件可能會使用欄位。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請移除類型或加入使用它的程式碼。 如果類型只`static`包含方法，請將下列其中一項加入至類型，以防止編譯器發出預設公用實例的函式：

- 以`static` .NET Framework 2.0 C#或更新版本為目標之類型的修飾詞。

- 以 .NET Framework 版本1.0 和1.1 為目標之類型的私用函數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

您可以放心地隱藏此規則的警告。 我們建議您在下列情況下隱藏此警告：

- 類別是透過晚期繫結的反映方法（例如） <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>所建立。

- 類別是由執行時間或 ASP.NET 自動建立的。 自動建立類別的一些範例是執行<xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName>或<xref:System.Web.IHttpHandler?displayProperty=fullName>的。

- 類別會當做具有[ `new`條件約束](/dotnet/csharp/language-reference/keywords/new-constraint)的型別參數傳遞。 下列範例會依規則 CA1812 標記：

    ```csharp
    internal class MyClass
    {
        public DoSomething()
        {
        }
    }
    public class MyGeneric<T> where T : new()
    {
        public T Create()
        {
            return new T();
        }
    }

    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
    mc.Create();
    ```

## <a name="related-rules"></a>相關規則

- [CA1811避免使用未呼叫的私用程式碼](../code-quality/ca1811-avoid-uncalled-private-code.md)
- [CA1801 必須審查未使用的參數](../code-quality/ca1801-review-unused-parameters.md)
- [CA1804 必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)