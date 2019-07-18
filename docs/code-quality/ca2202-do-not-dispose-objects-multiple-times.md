---
title: CA2202:不要多次處置物件的 Dispose 方法
ms.date: 07/16/2019
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5fb70baa17bee484dc3c31d7c6ce9b302019403
ms.sourcegitcommit: 2bbcba305fd0f8800fd3d9aa16f7647ee27f3a4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2019
ms.locfileid: "68300606"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202:不要多次處置物件的 Dispose 方法

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因

方法執行包含的程式碼路徑, 可能會對相同<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>物件上的多個呼叫或 Dispose 對等, 例如某些類型的 Close () 方法。

## <a name="rule-description"></a>規則描述

正確執行<xref:System.IDisposable.Dispose%2A>的方法可以多次呼叫, 而不會擲回例外狀況。 不過, 這不是保證的<xref:System.ObjectDisposedException?displayProperty=fullName> , 若要避免產生, 您不應該在物件上呼叫<xref:System.IDisposable.Dispose%2A>超過一次。

## <a name="related-rules"></a>相關規則

- [CA2000 必須在失去範圍之前處置物件](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規, 請變更此程式碼<xref:System.IDisposable.Dispose%2A> , 使其僅針對物件呼叫一次。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。 <xref:System.IDisposable.Dispose%2A>即使已知物件可以安全地呼叫多次, 未來的執行可能會改變。

## <a name="example"></a>範例

嵌套`using`的語句`Using` (在 Visual Basic 中) 可能會導致 CA2202 警告的違規。 如果 nested 內部`using`語句的 IDisposable 資源包含外部`using`語句的資源, 則嵌套資源的`Dispose`方法會釋放包含的資源。 發生這種情況時, `Dispose`外部`using`語句的方法會嘗試第二次處置其資源。

在下列範例中, <xref:System.IO.Stream>在外部 using 語句中建立的物件, 會在包含`stream`物件<xref:System.IO.StreamWriter>之物件的 Dispose 方法中, 于內部 using 語句的結尾釋放。 在外部`using`語句的結尾`stream` , 會第二次釋放物件。 第二個版本違反了 CA2202。

```csharp
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}
```

## <a name="example"></a>範例

若要解決此問題, 請`try`使用/ `finally`區塊, 而不`using`是外部語句。 在區塊中, 請確定`stream`資源不是 null。 `finally`

```csharp
Stream stream = null;
try
{
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);
    using (StreamWriter writer = new StreamWriter(stream))
    {
        stream = null;
        // Use the writer object...
    }
}
finally
{
    stream?.Dispose();
}
```

> [!TIP]
> 上述語法是[null 條件運算子。](/dotnet/csharp/language-reference/operators/member-access-operators#null-conditional-operators--and-) `?.`

## <a name="see-also"></a>另請參閱

- <xref:System.IDisposable?displayProperty=fullName>
- [Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern)