---
title: CA2124:自動換行易受攻擊的 finally 子句在外層 try |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1eb503e9f5a9251cb9a348d29c7cd9636389a080
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943502"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124:必須將有弱點的 finally 子句包裝在外層 try 中
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 在 1.0 和 1.1 版[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]，包含公用或受保護的方法`try` / `catch` / `finally`區塊。 `finally`區塊似乎會重設安全性狀態，並不會使用括住`finally`區塊。

## <a name="rule-description"></a>規則描述
 此規則會找出`try` / `finally`中以版本 1.0 和 1.1 版為目標的程式碼區塊[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]可能容易受到惡意的例外狀況篩選條件出現在呼叫堆疊。 如果敏感的作業，例如模擬就會發生在 try 區塊中，而且會擲回例外狀況，可以執行篩選條件之前`finally`區塊。 模擬範例中，這表示篩選條件會執行以模擬的使用者。 篩選條件是目前實作，只要在 Visual Basic 中。

> [!WARNING]
>  **附註**2.0 和更新版本的版本[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]，執行階段自動保護`try` / `catch` /  `finally`阻止惡意的例外狀況篩選條件，如果重設，就會發生直接在方法內，其中包含例外狀況區塊。

## <a name="how-to-fix-violations"></a>如何修正違規
 將未包裝`try` / `finally`外部 try 區塊中。 請參閱接下來的第二個範例。 這會強制`finally`篩選程式碼之前執行。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="pseudo-code-example"></a>虛擬程式碼範例

### <a name="description"></a>描述
 下列虛擬程式碼會說明這個規則偵測到的模式。

### <a name="code"></a>程式碼

```
try {
   // Do some work.
   Impersonator imp = new Impersonator("John Doe");
   imp.AddToCreditCardBalance(100);
}
finally {
   // Reset security state.
   imp.Revert();
}
```

## <a name="example"></a>範例
 下列虛擬程式碼顯示的模式，您可用來保護您的程式碼，並符合此規則。

```
try {
     try {
        // Do some work.
     }
     finally {
        // Reset security state.
     }
}
catch()
{
    throw;
}
```
