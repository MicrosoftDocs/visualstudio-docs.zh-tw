---
title: CA2139:透明方法不能使用 HandleProcessCorruptingExceptions 屬性
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6808c5e9b5d35ab6ec8d4012f08e15cba9a159d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920560"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139:透明方法不能使用 HandleProcessCorruptingExceptions 屬性

|||
|-|-|
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|
|CheckId|CA2139|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
透明方法會以<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>屬性標記。

## <a name="rule-description"></a>規則描述
此規則會引發任何透明的方法, 並嘗試使用<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>屬性來處理進程損毀例外狀況。 進程損毀例外狀況是 CLR 版本4.0 例外狀況分類 (例如<xref:System.AccessViolationException>)。 HandleProcessCorruptedStateExceptionsAttribute 屬性只能供安全性關鍵方法使用，若套用至透明方法則會被忽略。 若要處理進程損毀例外狀況, 此方法必須成為安全性關鍵或安全性安全關鍵。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規, 請移除<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>屬性, 或<xref:System.Security.SecurityCriticalAttribute>使用或<xref:System.Security.SecuritySafeCriticalAttribute>屬性來標記方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
在此範例中, 透明的方法會以<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>屬性標記, 而且將會使規則失敗。 方法也應該標記<xref:System.Security.SecurityCriticalAttribute>為<xref:System.Security.SecuritySafeCriticalAttribute>或屬性。

[!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../code-quality/codesnippet/CSharp/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute_1.cs)]