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
ms.openlocfilehash: 31bf7fe33aa59c3a713d2da81ddbd11ed6899723
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546285"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202:不要多次處置物件的 Dispose 方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|類別|Microsoft. 使用量|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 方法執行包含的程式碼路徑可能會導致多個呼叫 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 或 Dispose 對等專案，例如在相同物件上的某些類型上關閉 ( # A1 方法。

## <a name="rule-description"></a>規則描述
 正確執行的 <xref:System.IDisposable.Dispose%2A> 方法可以呼叫多次，而不會擲回例外狀況。 不過，這並不保證，為了避免產生， <xref:System.ObjectDisposedException?displayProperty=fullName> 您不應該 <xref:System.IDisposable.Dispose%2A> 在物件上呼叫一次以上。

## <a name="related-rules"></a>相關規則
 [CA2000:必須在超出範圍前處置物件](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請變更實施，如此一來，不論程式碼路徑為何， <xref:System.IDisposable.Dispose%2A> 都只會針對物件呼叫一次。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 即使 <xref:System.IDisposable.Dispose%2A> 已知物件可以安全地呼叫多次，仍可能會在未來變更。

## <a name="example"></a>範例
 `using` `Using` Visual Basic) 中 (的嵌套語句可能會導致 CA2202 警告的違規。 如果 nested 內部語句的 IDisposable 資源 `using` 包含外部語句的資源 `using` ，則 `Dispose` 嵌套資源的方法會釋放包含的資源。 當這種情況發生時， `Dispose` 外部語句的方法 `using` 會嘗試再次處置其資源。

 在下列範例中，在 <xref:System.IO.Stream> 外部 using 語句中建立的物件，會在包含物件之物件的 Dispose 方法中，于內部 using 語句的結尾釋放 <xref:System.IO.StreamWriter> `stream` 。 在外部語句結束時 `using` ， `stream` 物件會第二次釋放。 第二個版本違反 CA2202。

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
 若要解決這個問題，請使用 `try` / `finally` 區塊，而不是外部 `using` 語句。 在 `finally` 區塊中，確認 `stream` 資源不是 null。

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
 <xref:System.IDisposable?displayProperty=fullName>[Dispose 模式](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
