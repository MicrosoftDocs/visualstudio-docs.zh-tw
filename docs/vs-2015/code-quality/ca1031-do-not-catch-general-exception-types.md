---
title: CA1031： 不要攔截一般例外狀況類型 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fee08bdc2b93687a5415fdbd137c48f816f4acbb
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588322"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031：不要攔截一般例外狀況類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA1031： 不要攔截一般例外狀況類型](https://docs.microsoft.com/visualstudio/code-quality/ca1031-do-not-catch-general-exception-types)。

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|分類|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因
 一般的例外狀況，例如<xref:System.Exception?displayProperty=fullName>或是<xref:System.SystemException?displayProperty=fullName>陷入`catch`陳述式或這類的一般 catch 子句`catch()`用。

## <a name="rule-description"></a>規則描述
 不應該攔截一般例外狀況。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，攔截更特定的例外狀況，或重新擲回一般例外狀況中的最後一個陳述式`catch`區塊。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 攔截一般例外狀況類型時，可以隱藏執行階段程式庫使用者的問題，而且可能會使偵錯更困難。

> [!NOTE]
>  開頭[!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)]，common language runtime (CLR) 不會再提供中的作業系統和 managed 程式碼，例如存取違規發生的損毀的狀態例外狀況[!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)]、 由 managed 程式碼。 如果您想要編譯中的應用程式[!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)]或更新版本及維護的損毀的狀態例外狀況處理，您可以套用<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>屬性處理損毀的狀態例外狀況的方法。

## <a name="example"></a>範例
 下列範例顯示違反此規則的類型，以及正確地實作的型別`catch`區塊。

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA2200：必須重新擲回以保存堆疊詳細資料](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)



