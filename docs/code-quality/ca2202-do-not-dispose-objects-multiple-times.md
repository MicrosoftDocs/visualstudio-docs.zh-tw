---
title: CA2202：不要多次處置物件
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c7eb35e556e8edd6e840f2fbd6701e182895706
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202：不要多次處置物件
|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 方法實作包含程式碼路徑，可能會導致多個呼叫<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>或 Dispose 對等用法，例如，在相同物件上的部分類型上的 close （） 方法。

## <a name="rule-description"></a>規則描述
 正確地實作 A<xref:System.IDisposable.Dispose%2A>方法可以被呼叫多次而不擲回例外狀況。 不過，這不保證，以避免產生<xref:System.ObjectDisposedException?displayProperty=fullName>不應該呼叫<xref:System.IDisposable.Dispose%2A>一次以上的物件上。

## <a name="related-rules"></a>相關的規則
 [CA2000：必須在超出範圍前處置物件](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請變更的程式碼路徑，因此，不論實作<xref:System.IDisposable.Dispose%2A>呼叫物件一次。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 即使<xref:System.IDisposable.Dispose%2A>實作的已知物件可安全地呼叫多次，可能會在未來變更。

## <a name="example"></a>範例
 巢狀`using`陳述式 (`Using`在 Visual Basic 中) 可能會導致 CA2202 警告。 如果巢狀內部的 IDisposable 資源`using`陳述式包含的外部資源`using`陳述式，`Dispose`巢狀資源的方法會釋放所含的資源。 當發生這種情況時，`Dispose`方法的外部`using`陳述式嘗試將第二次處置其資源。

 在下列範例中，<xref:System.IO.Stream>中為外部建立的物件使用陳述式內部的 Dispose 方法中使用陳述式的結尾釋放<xref:System.IO.StreamWriter>物件，其中包含`stream`物件。 結尾的外部`using`陳述式，`stream`第二次釋放物件。 第二個版本是 CA2202 的違規情形。

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
 若要解決此問題，請使用`try` / `finally`區塊，而不是外部`using`陳述式。 在`finally`封鎖，請確定`stream`資源不是 null。

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

## <a name="see-also"></a>另請參閱
 <xref:System.IDisposable?displayProperty=fullName> [處置模式](/dotnet/standard/design-guidelines/dispose-pattern)