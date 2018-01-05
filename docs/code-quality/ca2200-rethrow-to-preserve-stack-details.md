---
title: "CA2200： 重新擲回以保存堆疊詳細資料 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 81dff0b9e876719fdfd26409772498390344cd2c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200：請重新擲回以保存堆疊詳細資料
|||  
|-|-|  
|TypeName|RethrowToPreserveStackDetails|  
|CheckId|CA2200|  
|分類|Microsoft.Usage|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 會重新擲回的例外狀況和例外狀況中明確指定`throw`陳述式。  
  
## <a name="rule-description"></a>規則描述  
 一旦擲回例外狀況後，部分資訊，它會是堆疊追蹤。 堆疊追蹤是一份方法呼叫階層開頭的方法，就會擲回例外狀況，並攔截例外狀況的方法的結尾。 如果重新擲回例外狀況指定中的例外狀況`throw`陳述式的堆疊追蹤在目前的方法重新啟動，並擲回例外狀況的原始方法和目前方法之間呼叫的方法清單將會遺失。 若要保留與例外狀況的原始堆疊追蹤資訊，請使用`throw`陳述式，但未指定例外狀況。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，重新擲回例外狀況未明確指定例外狀況。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 下列範例會示範一種方法， `CatchAndRethrowExplicitly`，這違反規則和方法， `CatchAndRethrowImplicitly`，符合此規則。  
  
 [!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
 [!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]