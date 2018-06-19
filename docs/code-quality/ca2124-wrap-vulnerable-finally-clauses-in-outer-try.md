---
title: CA2124：必須將有弱點的 finally 子句包裝在外層 try 中
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c299652e779476f2936c193a8bdb646e7b655dd4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916138"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124：必須將有弱點的 finally 子句包裝在外層 try 中
|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|分類|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 1.0 和 1.1 版中[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]，公用或受保護的方法包含`try` / `catch` / `finally`區塊。 `finally`區塊似乎會重設安全性狀態，而且不會封入中`finally`區塊。

## <a name="rule-description"></a>規則描述
 此規則會找出`try` / `finally` 1.0 和 1.1 版為目標的程式碼中封鎖[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]可能容易受到惡意的例外狀況篩選條件出現在呼叫堆疊。 如果在 try 區塊中發生敏感的作業，例如模擬，會擲回例外狀況之前，可以執行篩選條件`finally`區塊。 模擬範例中，這表示篩選條件會執行與模擬的使用者。 篩選是目前可實作只能在 Visual Basic 中。

> [!WARNING]
>  **請注意**版本 2.0 和更新版本的[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]，執行階段自動保護`try` / `catch` /  `finally`封鎖惡意的例外狀況篩選條件，如果發生重設直接在方法中包含例外狀況區塊。

## <a name="how-to-fix-violations"></a>如何修正違規
 將包裝`try` / `finally`外部 try 區塊中。 接下來的第二個範例，請參閱。 這會強制`finally`篩選程式碼之前執行。

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
 下列虛擬程式碼會顯示可用來保護您的程式碼並符合此規則的模式。

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