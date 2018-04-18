---
title: 'CA2215: Dispose 方法應該呼叫基底類別處置 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8eb5c56ab3affe6322a858dfcd34c3b138f26d7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215：Dispose 方法應該呼叫基底類別處置
|||  
|-|-|  
|TypeName|DisposeMethodsShouldCallBaseClassDispose|  
|CheckId|CA2215|  
|分類|Microsoft.Usage|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 實作的型別<xref:System.IDisposable?displayProperty=fullName>繼承自類型，也會實作<xref:System.IDisposable>。 <xref:System.IDisposable.Dispose%2A>繼承類型的方法不會呼叫<xref:System.IDisposable.Dispose%2A>父類型的方法。  
  
## <a name="rule-description"></a>規則描述  
 如果型別繼承自可處置的類型，則必須呼叫<xref:System.IDisposable.Dispose%2A>方法本身內的基底型別<xref:System.IDisposable.Dispose%2A>方法。 呼叫基底型別方法處置可確保會釋放 基底型別所建立的任何資源。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，呼叫`base`。<xref:System.IDisposable.Dispose%2A> 在您<xref:System.IDisposable.Dispose%2A>方法。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 安全地隱藏此規則的警告，如果呼叫`base`。<xref:System.IDisposable.Dispose%2A> 這個規則會檢查比更深入的呼叫層級，就會發生。  
  
## <a name="example"></a>範例  
 下列範例顯示型別`TypeA`實作<xref:System.IDisposable>。  
  
 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]  
  
## <a name="example"></a>範例  
 下列範例顯示型別`TypeB`繼承自型別`TypeA`和正確呼叫其<xref:System.IDisposable.Dispose%2A>方法。  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Dispose 模式](/dotnet/standard/design-guidelines/dispose-pattern)