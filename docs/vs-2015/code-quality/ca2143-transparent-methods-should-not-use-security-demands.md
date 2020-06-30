---
title: CA2143：透明方法不應使用安全性需求 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ca8f049da83b99da7d36ebf74e756dd95f738d64
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546467"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143:透明方法不可以使用安全性要求
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|CheckId|CA2143|
|類別|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 透明類型或方法會以宣告方式標記 <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` 要求，或方法會呼叫 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> 方法。

## <a name="rule-description"></a>規則描述
 安全性透明程式碼不應負責驗證作業的安全性，因此不應要求權限。 安全性透明程式碼應使用完整的要求做出安全性決策，而且安全關鍵程式碼不應依賴透明程式碼提出完全要求。 執行安全性檢查的任何程式碼（例如安全性需求），都應該是安全關鍵。

## <a name="how-to-fix-violations"></a>如何修正違規
 一般而言，若要修正此規則的違規情形，請使用屬性來標記方法 <xref:System.Security.SecuritySafeCriticalAttribute> 。 您也可以移除需求。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列程式碼上的規則檔，因為透明方法會提出宣告式安全性需求。

 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2143.transparentmethodsshouldnotdemand/cs/ca2143 - transparentmethodsshouldnotdemand.cs#1)]

## <a name="see-also"></a>另請參閱
 [CA2142:透明程式碼不可以使用 LinkDemand 加以保護](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)
