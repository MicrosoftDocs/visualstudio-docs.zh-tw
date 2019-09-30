---
title: CA2124:必須將有弱點的 finally 子句包裝在外層 try 中
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0008767f7d37e2c088dad58a328b025f81090ad8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232456"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124:必須將有弱點的 finally 子句包裝在外層 try 中

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|分類|Microsoft.Security|
|重大變更|不中斷|

## <a name="cause"></a>原因
在 .NET Framework 的版本1.0 和1.1 中，公用或受保護的方法包含`try` / / `catch` `finally`區塊。 區塊會出現以重設安全性狀態，而且不會包含`finally`在區塊中。 `finally`

## <a name="rule-description"></a>規則描述
此規則`try` / 會找出程式碼中以版本1.0和1.1為目標的區塊，此.NETFramework可能容易受到呼叫堆疊中出現的惡意例外狀況`finally`篩選器影響。 如果在 try 區塊中發生諸如模擬之類的敏感作業，且擲回例外狀況，則篩選準則可以在`finally`區塊之前執行。 針對模擬範例，這表示篩選準則會以模擬的使用者身分執行。 篩選目前只能在 Visual Basic 中能實作。

> [!NOTE]
> 在 .NET Framework 的版本2.0 和更新版本中，如果在方法中`try`直接進行重設，則執行時間會自動保護/  / `catch` `finally`區塊免于惡意的例外狀況篩選準則。包含例外狀況區塊。

## <a name="how-to-fix-violations"></a>如何修正違規
將未包裝`try` /的放在外部try區塊中`finally` 。 請參閱接下來的第二個範例。 這會強制`finally`在篩選程式代碼之前執行。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="pseudo-code-example"></a>虛擬程式碼範例

### <a name="description"></a>描述

下列虛擬程式碼會說明這個規則偵測到的模式。

```csharp
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

下列虛擬程式碼顯示您可以用來保護程式碼並滿足此規則的模式。

```csharp
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