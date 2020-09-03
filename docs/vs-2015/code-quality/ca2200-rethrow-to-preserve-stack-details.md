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
ms.openlocfilehash: 6d63ef6ff3647742e931fd05f59c66b40059ad00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546363"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200:必須重新擲回以保存堆疊詳細資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|類別|Microsoft. 使用量|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 系統會重新擲回例外狀況，並在語句中明確指定例外狀況 `throw` 。

## <a name="rule-description"></a>規則描述
 一旦擲回例外狀況，它所攜帶的部分資訊就是堆疊追蹤。 堆疊追蹤是方法呼叫階層的清單，其開頭為擲回例外狀況的方法，並以捕捉例外狀況的方法結束。 如果在語句中指定例外狀況而重新擲回例外狀況 `throw` ，則會在目前的方法重新開機堆疊追蹤，並在擲回例外狀況的原始方法與目前的方法遺失之間進行方法呼叫的清單。 若要保留原始堆疊追蹤資訊的例外狀況，請使用 `throw` 語句而不指定例外狀況。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請重新擲回例外狀況，而不明確指定例外狀況。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會顯示違反規則的方法， `CatchAndRethrowExplicitly` 以及 `CatchAndRethrowImplicitly` 滿足規則的方法。

 [!code-csharp[FxCop.Usage.Rethrow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/cs/FxCop.Usage.Rethrow.cs#1)]
 [!code-vb[FxCop.Usage.Rethrow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow/vb/FxCop.Usage.Rethrow.vb#1)]
