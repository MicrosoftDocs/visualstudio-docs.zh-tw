---
title: CA2002： 請勿鎖定具有弱式識別的物件 |Microsoft Docs
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
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
ms.assetid: 16100b39-c6fc-452b-8fca-8b459a26c286
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 09e9fd213ca000afb163f37ddb659c0ea5cf3c53
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588505"
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002：請勿鎖定具有弱式識別的物件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[CA2002： 請勿鎖定具有弱式識別的物件](https://docs.microsoft.com/visualstudio/code-quality/ca2002-do-not-lock-on-objects-with-weak-identity)。

|||
|-|-|
|TypeName|DoNotLockOnObjectsWithWeakIdentity|
|CheckId|CA2002|
|分類|Microsoft.Reliability|
|中斷變更|非重大|

## <a name="cause"></a>原因
 執行緒嘗試鎖定具有弱式識別的物件。

## <a name="rule-description"></a>規則描述
 可以跨應用程式定義域範圍直接存取的物件，即所謂具有弱式識別的物件。 嘗試取得具有弱式識別之物件鎖定的執行緒，可以被不同應用程式定義域中具有相同物件鎖定的第二個執行緒所封鎖。 下列類型具有弱式識別，而規則所加上旗標：

-   <xref:System.MarshalByRefObject>

-   <xref:System.ExecutionEngineException>

-   <xref:System.OutOfMemoryException>

-   <xref:System.StackOverflowException>

-   <xref:System.String>

-   <xref:System.Reflection.MemberInfo>

-   <xref:System.Reflection.ParameterInfo>

-   <xref:System.Threading.Thread>

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，使用從型別不在 [描述] 部分中的清單中的物件。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="related-rules"></a>相關的規則
 [CA2213：可處置的欄位應該受到處置](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

## <a name="example"></a>範例
 下列範例會示範一些違反規則的物件鎖定。

 [!code-csharp[FxCop.Reliability.LockWeakObjects#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Reliability.LockWeakObjects/cs/FxCop.Reliability.LockWeakObjects.cs#1)]
 [!code-vb[FxCop.Reliability.LockWeakObjects#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Reliability.LockWeakObjects/vb/FxCop.Reliability.LockWeakObjects.vb#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.Threading.Monitor> <xref:System.AppDomain>
 [lock 陳述式](http://msdn.microsoft.com/library/656da1a4-707e-4ef6-9c6e-6d13b646af42) [SyncLock 陳述式](http://msdn.microsoft.com/library/14501703-298f-4d43-b139-c4b6366af176)



