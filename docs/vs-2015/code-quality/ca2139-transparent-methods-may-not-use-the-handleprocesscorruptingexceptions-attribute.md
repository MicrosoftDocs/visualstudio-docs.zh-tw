---
title: CA2139：透明方法不能使用 HandleProcessCorruptingExceptions 屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 821598d7708fa8681f1dbc5fee65978d7498dbb5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602995"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139：透明方法不能使用 HandleProcessCorruptingExceptions 屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|
|CheckId|CA2139|
|Category|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 透明方法會標記為 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> 屬性。

## <a name="rule-description"></a>規則描述
 此規則會引發任何透明的方法，並嘗試使用 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> 屬性來處理進程損毀例外狀況。 進程損毀例外狀況是 CLR 版本4.0 例外狀況分類，如 <xref:System.AccessViolationException>。 HandleProcessCorruptedStateExceptionsAttribute 屬性只能供安全性關鍵方法使用，若套用至透明方法則會被忽略。 若要處理進程損毀例外狀況，此方法必須成為安全性關鍵或安全性安全關鍵。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請移除 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> 屬性，或使用 <xref:System.Security.SecurityCriticalAttribute> 或 <xref:System.Security.SecuritySafeCriticalAttribute> 屬性來標記方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 在此範例中，透明的方法會以 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> 屬性標示，而規則將會失敗。 此方法也應該以 <xref:System.Security.SecurityCriticalAttribute> 或 <xref:System.Security.SecuritySafeCriticalAttribute> 屬性來標記。

 [!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2139.transparentmethodsmustnothandleprocesscorruptingexceptions/cs/ca2139 - transparentmethodsmustnothandleprocesscorruptingexceptions.cs#1)]
