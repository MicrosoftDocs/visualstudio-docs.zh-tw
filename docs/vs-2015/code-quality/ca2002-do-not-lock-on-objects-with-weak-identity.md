---
title: CA2002：不要鎖定具有弱式識別的物件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
ms.assetid: 16100b39-c6fc-452b-8fca-8b459a26c286
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 79f97de740ace9ccb59b13b3e4e30b34f38eb2f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534663"
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002:不要鎖定具有弱式識別的物件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotLockOnObjectsWithWeakIdentity|
|CheckId|CA2002|
|類別|Microsoft 可靠性|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 執行緒嘗試取得具有弱式識別之物件的鎖定。

## <a name="rule-description"></a>規則描述
 可以跨應用程式定義域範圍直接存取的物件，即所謂具有弱式識別的物件。 嘗試取得具有弱式識別之物件鎖定的執行緒，可以被不同應用程式定義域中具有相同物件鎖定的第二個執行緒所封鎖。 下列類型具有弱式身分識別，並以規則標示：

- <xref:System.MarshalByRefObject>

- <xref:System.ExecutionEngineException>

- <xref:System.OutOfMemoryException>

- <xref:System.StackOverflowException>

- <xref:System.String>

- <xref:System.Reflection.MemberInfo>

- <xref:System.Reflection.ParameterInfo>

- <xref:System.Threading.Thread>

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請使用 [描述] 區段中不在清單中之類型的物件。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="related-rules"></a>相關規則
 [CA2213:可處置的欄位應該受到處置](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

## <a name="example"></a>範例
 下列範例顯示違反規則的部分物件鎖定。

 [!code-csharp[FxCop.Reliability.LockWeakObjects#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Reliability.LockWeakObjects/cs/FxCop.Reliability.LockWeakObjects.cs#1)]
 [!code-vb[FxCop.Reliability.LockWeakObjects#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Reliability.LockWeakObjects/vb/FxCop.Reliability.LockWeakObjects.vb#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.Threading.Monitor> <xref:System.AppDomain>
 [Lock 語句](https://msdn.microsoft.com/library/656da1a4-707e-4ef6-9c6e-6d13b646af42) [SyncLock 語句](https://msdn.microsoft.com/library/14501703-298f-4d43-b139-c4b6366af176)
