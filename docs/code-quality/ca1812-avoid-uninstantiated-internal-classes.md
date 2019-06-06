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
ms.openlocfilehash: a0d55af3c5522c6bb9aa3ad8a023f070c187ca6f
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714262"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812:避免使用未執行個體化的內部類別

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|分類|Microsoft.Performance|
|中斷變更|非重大|

## <a name="cause"></a>原因

內部 （組件層級） 型別永遠不會具現化。

## <a name="rule-description"></a>規則描述

此規則會嘗試找出其中的型別建構函式的呼叫，並報告違規情形，如果不找到任何呼叫。

此規則就不會檢查下列類型：

- 值類型

- 抽象類型

- 列舉

- 委派

- 編譯器發出的陣列類型

- 類型，無法具現化，並只定義[ `static` ](/dotnet/csharp/language-reference/keywords/static) ([ `Shared`在 Visual Basic 中](/dotnet/visual-basic/language-reference/modifiers/shared)) 方法。

如果您套用<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName>正在分析之組件，此規則會不加上旗標標示為的型別[ `internal` ](/dotnet/csharp/language-reference/keywords/internal) ([ `Friend`在 Visual Basic 中](/dotnet/visual-basic/language-reference/modifiers/friend)) 欄位可能是因為使用 friend 組件。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，移除類型，或加入程式碼使用它。 如果型別只包含`static`方法，加入下列其中一種類型，以避免編譯器發出的預設公用執行個體建構函式：

- `static`修飾詞C#類型的目標[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]或更新版本。

- 私用建構函式以.NET Framework 1.0 和 1.1 版為目標的類型。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它可安全地隱藏此規則的警告。 我們建議您隱藏這個警告，在下列情況：

- 這類的類別建立透過晚期繫結反映方法<xref:System.Activator.CreateInstance%2A?displayProperty=fullName>。

- 類別會自動建立，藉由執行階段或 ASP.NET。 自動建立類別的一些範例包括實作<xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName>或<xref:System.Web.IHttpHandler?displayProperty=fullName>。

- 類別會當做有類型參數傳遞[`new`條件約束](/dotnet/csharp/language-reference/keywords/new-constraint)。 下列範例會標示規則 CA1812:

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

## <a name="related-rules"></a>相關的規則

- [CA1811:避免使用未呼叫的私用程式碼](../code-quality/ca1811-avoid-uncalled-private-code.md)
- [CA1801： 必須檢閱未使用的參數](../code-quality/ca1801-review-unused-parameters.md)
- [CA1804： 必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)