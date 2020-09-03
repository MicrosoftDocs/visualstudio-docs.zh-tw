---
title: CA2151：具有關鍵類型的欄位應為安全性關鍵 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 09db9d25-7d58-4725-a252-4a07baadf046
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 48c3f55b60add1691fe31c764f31673bbf1ab47b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546350"
---
# <a name="ca2151-fields-with-critical-types-should-be-security-critical"></a>CA2151:具有關鍵類型的欄位應為安全性關鍵
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName||
|CheckId|CA2151|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 已宣告安全性透明欄位或安全性關鍵欄位。 它的指定類型為安全性關鍵類型。 例如：

```csharp
[assembly: AllowPartiallyTrustedCallers]

   [SecurityCritical]
   class Type1 { } // Security Critical type

   class Type2 // Security transparent type
   {
      Type1 m_field; // CA2151, transparent field of critical type
   }
```

 在此範例中，`m_field` 是屬於安全性關鍵類型的安全性透明欄位。

## <a name="rule-description"></a>規則描述
 若要使用安全性關鍵類型，參考該類型的程式碼必須是安全性關鍵或安全性安全關鍵。 即使是間接參考也是如此。 例如，當您參考屬於關鍵類型的透明欄位時，您的程式碼必須是安全性關鍵或安全性安全。 因此，使用安全性透明或安全性安全關鍵欄位容易發生錯誤，因為透明程式碼仍然無法存取該欄位。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請標示具有 <xref:System.Security.SecurityCriticalAttribute> 屬性的欄位，或是將該欄位所參考的類型設為安全性透明或安全性關鍵類型。

```csharp
// Fix 1: Make the referencing field security critical
[assembly: AllowPartiallyTrustedCallers]

   [SecurityCritical]
   class Type1 { } // Security Critical type

   class Type2 // Security transparent type
   {
      [SecurityCritical]
      Type1 m_field; // Fixed: critical type, critical field
   }

// Fix 2: Make the referencing field security critical
[assembly: AllowPartiallyTrustedCallers]

   class Type1 { } // Type1 is now transparent

   class Type2 // Security transparent type
   {
      [SecurityCritical]
      Type1 m_field; // Fixed: critical type, critical field
   }
```

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2145.transparentmethodsshouldnotusesuppressunmanagedcodesecurity/cs/ca2145.cs#1)]

### <a name="comments"></a>註解
