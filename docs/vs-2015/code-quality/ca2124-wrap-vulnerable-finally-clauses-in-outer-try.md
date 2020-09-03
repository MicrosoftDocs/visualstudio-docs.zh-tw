---
title: CA2124：將易受攻擊的 finally 子句包裝在 outer try 中 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4e191ca10456f133e1213961ca2d1ed9cb8e040b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544296"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124:必須將有弱點的 finally 子句包裝在外層 try 中
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|類別|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 在的1.0 和1.1 版中 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ，公用或受保護的方法包含 `try` / `catch` / `finally` 區塊。 `finally`區塊似乎會重設安全性狀態，而且不會包含在 `finally` 區塊中。

## <a name="rule-description"></a>規則描述
 此規則 `try` / `finally` 會在程式碼中找出以版本1.0 和1.1 為目標的區塊，而這些區塊 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 可能會容易受到存在於呼叫堆疊中的惡意例外狀況篩選。 如果在 try 區塊中發生模擬之類的敏感作業，而且擲回例外狀況，則篩選準則可以在區塊之前執行 `finally` 。 在模擬範例中，這表示篩選準則會以模擬的使用者執行。 篩選目前只在 Visual Basic 中而且實作。

> [!WARNING]
> 在的2.0 版和更新版本中 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ， `try` / `catch` /  `finally` 如果在包含例外狀況區塊的方法內直接進行重設，則執行時間會自動保護區塊免于惡意的例外狀況篩選準則。

## <a name="how-to-fix-violations"></a>如何修正違規
 將未包裝的置於 `try` / `finally` 外部 try 區塊。 請參閱後面的第二個範例。 這會強制在 `finally` 篩選程式代碼之前執行。

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
 下列虛擬程式碼會顯示您可以用來保護程式碼並符合此規則的模式。

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
