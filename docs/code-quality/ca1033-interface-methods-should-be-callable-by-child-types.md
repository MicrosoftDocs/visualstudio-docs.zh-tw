---
title: "CA1033： 介面方法應該要可以由子類型呼叫 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4694e1dbcbcf541b502edbe5f2520229ee33f4a6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033：介面方法應該要可以由子類型呼叫
|||  
|-|-|  
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|  
|CheckId|CA1033|  
|分類|Microsoft.Design|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 非密封外部可見的類型會提供公用介面的明確方法實作，但未提供同名的替代外部可見方法。  
  
## <a name="rule-description"></a>規則描述  
 請考慮明確實作的公用介面方法的基底類型。 衍生自基底類型的型別可以存取繼承的介面方法，只能透過目前的執行個體的參考 (`this` C# 中)，會轉換成介面。 如果重新衍生的類型 （明確） 實作繼承的介面方法，可以再存取基底實作。 透過目前的執行個體參考的呼叫將會叫用的衍生的實作。這會導致遞迴和最終的堆疊溢位。  
  
 此規則不會報告的明確實作違反<xref:System.IDisposable.Dispose%2A?displayProperty=fullName>外部可見時`Close()`或`System.IDisposable.Dispose(Boolean)`方法提供。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，實作新的方法來公開相同的功能，而且衍生的類型可以看到或 nonexplicit 實作變更。 如果一項重大變更是接受的替代方法是讓密封類型。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告，如果外部可見的方法具有相同的功能，但是明確實作的方法不同的名稱。  
  
## <a name="example"></a>範例  
 下列範例顯示型別， `ViolatingBase`，違反此規則，並為型別， `FixedBase`，它會顯示發生違規的修正。  
  
 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [介面](/dotnet/csharp/programming-guide/interfaces/index)