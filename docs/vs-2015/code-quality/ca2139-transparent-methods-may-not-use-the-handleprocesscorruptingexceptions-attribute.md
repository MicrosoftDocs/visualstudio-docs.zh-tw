---
title: CA2139:透明方法不能使用 HandleProcessCorruptingExceptions 屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a05813d01a05c02455d43e74029251e96e4e4580
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154275"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139:透明方法不能使用 HandleProcessCorruptingExceptions 屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|
|CheckId|CA2139|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 透明方法會標示<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>屬性。

## <a name="rule-description"></a>規則描述
 此規則會引發任何透明並且嘗試處理處理序損毀例外狀況所使用的方法<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>屬性。 處理序損毀例外狀況是這類的例外狀況的 CLR 4.0 版例外狀況分類<xref:System.AccessViolationException>。 HandleProcessCorruptedStateExceptionsAttribute 屬性只能供安全性關鍵方法使用，若套用至透明方法則會被忽略。 若要處理程序損毀例外狀況，這個方法必須成為安全性關鍵或安全性安全關鍵。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請移除<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>屬性，或將標記的方法<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 在此範例中，透明方法會標示<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>屬性，將會失敗的規則。 此方法應該也會以標記<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>屬性。

 [!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2139.transparentmethodsmustnothandleprocesscorruptingexceptions/cs/ca2139 - transparentmethodsmustnothandleprocesscorruptingexceptions.cs#1)]
