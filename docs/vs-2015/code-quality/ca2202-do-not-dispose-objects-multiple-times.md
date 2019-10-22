---
title: CA2202：不要多次處置物件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e0be715d8aea84fac53ea2a796e71850b961730c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667394"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202：不要多次處置物件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Category|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 方法執行包含的程式碼路徑可能會導致多次呼叫 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 或對等的 Dispose，例如在相同物件上的某些類型上的 Close （）方法。

## <a name="rule-description"></a>規則描述
 正確執行的 <xref:System.IDisposable.Dispose%2A> 方法可以多次呼叫，而不會擲回例外狀況。 不過，這不是保證的，而且為了避免產生 <xref:System.ObjectDisposedException?displayProperty=fullName>，您不應該在物件上呼叫 <xref:System.IDisposable.Dispose%2A> 一次以上。

## <a name="related-rules"></a>相關規則
 [CA2000：必須在超出範圍前處置物件](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請變更此實作為，不論程式碼路徑為何，<xref:System.IDisposable.Dispose%2A> 只會針對物件呼叫一次。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 即使已知物件的 <xref:System.IDisposable.Dispose%2A> 可以安全地呼叫多次，未來的執行可能會改變。

## <a name="example"></a>範例
 Nested `using` 語句（Visual Basic 中的 `Using`）可能會造成 CA2202 警告的違規。 如果 nested 內部 `using` 語句的 IDisposable 資源包含外部 `using` 語句的資源，則嵌套資源的 `Dispose` 方法會釋放包含的資源。 發生這種情況時，外部 `using` 語句的 `Dispose` 方法會嘗試第二次處置其資源。

 在下列範例中，在外部 using 語句中建立的 <xref:System.IO.Stream> 物件，會在包含 `stream` 物件之 <xref:System.IO.StreamWriter> 物件的 Dispose 方法中，于內部 using 語句的結尾處釋放。 在外部 `using` 語句的結尾，`stream` 物件會第二次釋放。 第二個版本違反了 CA2202。

```
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}
```

## <a name="example"></a>範例
 若要解決此問題，請使用 `try` / `finally` 區塊，而不是外部 `using` 語句。 在 [`finally`] 區塊中，確認 `stream` 資源不是 null。

```
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
    if(stream != null)
        stream.Dispose();
}
```

## <a name="see-also"></a>請參閱
 <xref:System.IDisposable?displayProperty=fullName>[處置模式](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
