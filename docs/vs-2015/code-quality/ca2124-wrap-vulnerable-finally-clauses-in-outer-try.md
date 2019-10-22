---
title: CA2124：在外部 try 中包裝易受攻擊的 finally 子句 |Microsoft Docs
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
ms.openlocfilehash: 7a2a296f5dd3680209c14849b5bd863c01e6351d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660239"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124：必須將有弱點的 finally 子句包裝在外層 try 中
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Category|Microsoft.Security|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 在 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 的版本1.0 和1.1 中，公用或受保護的方法包含 `try` / `catch` / `finally` 區塊。 @No__t_0 區塊會出現以重設安全性狀態，而且不會包含在 `finally` 區塊中。

## <a name="rule-description"></a>規則描述
 此規則會找出程式碼中的 `try` / `finally` 區塊，其目標為 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 的版本1.0 和1.1，這可能會容易遭受呼叫堆疊中的惡意例外狀況篩選準則。 如果在 try 區塊中發生諸如模擬之類的敏感作業，且擲回例外狀況，則篩選準則可以在 `finally` 區塊之前執行。 針對模擬範例，這表示篩選準則會以模擬的使用者身分執行。 篩選目前只能在 Visual Basic 中能實作。

> [!WARNING]
> 在 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 的版本2.0 和更新版本中，如果直接在包含例外狀況區塊的方法中進行重設，則執行時間會自動保護 `try` / `catch` /  `finally` 封鎖惡意的例外狀況篩選準則。

## <a name="how-to-fix-violations"></a>如何修正違規
 將未包裝的 `try` / `finally` 放在外部 try 區塊中。 請參閱接下來的第二個範例。 這會強制 `finally` 在篩選器程式碼之前執行。

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
 下列虛擬程式碼顯示您可以用來保護程式碼並滿足此規則的模式。

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
