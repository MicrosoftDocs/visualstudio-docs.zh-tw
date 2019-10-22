---
title: CA2200：重新擲回以保留堆疊詳細資料 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d20407d7cc708ac785e4a792bf8e64768ea58540
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667382"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200：請重新擲回以保存堆疊詳細資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Category|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 系統會重新擲回例外狀況，並在 `throw` 語句中明確指定例外狀況。

## <a name="rule-description"></a>規則描述
 一旦擲回例外狀況，它所攜帶的部分資訊就是堆疊追蹤。 堆疊追蹤是方法呼叫階層的清單，其開頭為會擲回例外狀況的方法，並以攔截例外狀況的方法做為結尾。 如果在 `throw` 的語句中指定例外狀況來重新擲回例外狀況，則會在目前的方法上重新開機堆疊追蹤，而原始方法（擲回例外狀況）與目前方法之間的方法呼叫清單也會遺失。 若要保留原始堆疊追蹤資訊與例外狀況，請使用 `throw` 語句，而不指定例外狀況。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請重新擲回例外狀況，而不明確指定例外狀況。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示的方法 `CatchAndRethrowExplicitly`，其違反規則和方法，`CatchAndRethrowImplicitly`，這會滿足規則。

 [!code-csharp[FxCop.Usage.Rethrow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/cs/FxCop.Usage.Rethrow.cs#1)]
 [!code-vb[FxCop.Usage.Rethrow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/vb/FxCop.Usage.Rethrow.vb#1)]
