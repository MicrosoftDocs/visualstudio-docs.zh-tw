---
title: CA2002：請勿鎖定具有弱式識別的物件
ms.date: 01/31/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0ddeb32032f7fbd6ff088980c342405261e5b473
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548461"
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002：請勿鎖定具有弱式識別的物件

|||
|-|-|
|TypeName|DoNotLockOnObjectsWithWeakIdentity|
|CheckId|CA2002|
|類別|Microsoft.Reliability|
|中斷變更|非重大|

## <a name="cause"></a>原因

執行緒嘗試鎖定具有弱式識別的物件。

## <a name="rule-description"></a>規則描述

可以跨應用程式定義域範圍直接存取的物件，即所謂具有弱式識別的物件。 嘗試取得具有弱式識別之物件鎖定的執行緒，可以被不同應用程式定義域中具有相同物件鎖定的第二個執行緒所封鎖。

下列類型具有弱式識別，而規則所加上旗標：

- <xref:System.String>

- 陣列的實值類型，包括[整數類資料類型](/dotnet/csharp/language-reference/keywords/integral-types-table)，[浮點型別](/dotnet/csharp/language-reference/keywords/floating-point-types-table)，和<xref:System.Boolean>。

- <xref:System.MarshalByRefObject>

- <xref:System.ExecutionEngineException>

- <xref:System.OutOfMemoryException>

- <xref:System.StackOverflowException>

- <xref:System.Reflection.MemberInfo>

- <xref:System.Reflection.ParameterInfo>

- <xref:System.Threading.Thread>

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，使用從型別不在 [描述] 部分中的清單中的物件。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

請勿隱藏此規則的警告。

## <a name="related-rules"></a>相關的規則

[CA2213：可處置的欄位應該受到處置](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

## <a name="example"></a>範例

下列範例會示範一些違反規則的物件鎖定。

[!code-vb[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/VisualBasic/ca2002-do-not-lock-on-objects-with-weak-identity_1.vb)]
[!code-csharp[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/CSharp/ca2002-do-not-lock-on-objects-with-weak-identity_1.cs)]

## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Monitor>
- <xref:System.AppDomain>
- [lock 陳述式 (C#)](/dotnet/csharp/language-reference/keywords/lock-statement)
- [SyncLock 陳述式 (Visual Basic)](/dotnet/visual-basic/language-reference/statements/synclock-statement)