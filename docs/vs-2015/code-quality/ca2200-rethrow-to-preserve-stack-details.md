---
title: CA2200:重新擲回以保存堆疊詳細資料 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ed2dd2884268511ae05ac89c132f73fdf8b2771e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943679"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200:必須重新擲回以保存堆疊詳細資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 會重新擲回的例外狀況和例外狀況會明確指定在`throw`陳述式。

## <a name="rule-description"></a>規則描述
 一旦擲回例外狀況，它所攜帶的資訊的一部分為堆疊追蹤。 堆疊追蹤是一份方法呼叫階層開頭的方法，就會擲回例外狀況，並攔截到例外狀況的方法的結尾。 如果重新擲回例外狀況的例外狀況中指定`throw`陳述式的堆疊追蹤會在目前的方法來進行重新啟動，並擲回例外狀況的原始方法和目前方法之間呼叫的方法清單將會遺失。 若要保留與例外狀況的原始堆疊追蹤資訊，請使用`throw`但未指定例外狀況的陳述式。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，重新擲回例外狀況但未明確指定例外狀況。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例示範的方法中， `CatchAndRethrowExplicitly`，這會違反此規則和方法， `CatchAndRethrowImplicitly`，這會滿足規則。

 [!code-csharp[FxCop.Usage.Rethrow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/cs/FxCop.Usage.Rethrow.cs#1)]
 [!code-vb[FxCop.Usage.Rethrow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/vb/FxCop.Usage.Rethrow.vb#1)]
