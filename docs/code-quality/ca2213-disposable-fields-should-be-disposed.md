---
title: "CA2213： 應該處置可處置的欄位 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 77cd32f97e3798362371fc21f8b38c14ce22c7fb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213：可處置的欄位應該受到處置
|||  
|-|-|  
|TypeName|DisposableFieldsShouldBeDisposed|  
|CheckId|CA2213|  
|分類|Microsoft.Usage|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 實作的型別<xref:System.IDisposable?displayProperty=fullName>宣告了也實作之類型的欄位<xref:System.IDisposable>。 <xref:System.IDisposable.Dispose%2A>欄位方法不由呼叫<xref:System.IDisposable.Dispose%2A>宣告型別的方法。  
  
## <a name="rule-description"></a>規則描述  
 型別會負責處理這些項目及其所有 unmanaged 資源;這是藉由實作<xref:System.IDisposable>。 此規則會檢查以查看是否可處置的類型`T`宣告欄位`F`也就是可處置的類型執行個體`FT`。 每個欄位`F`，此規則會嘗試找出呼叫`FT.Dispose`。 此規則會搜尋呼叫的方法`T.Dispose`，和一個較低的層級 (呼叫的方法呼叫的方法`FT.Dispose`)。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，呼叫<xref:System.IDisposable.Dispose%2A>實作之類型的欄位上<xref:System.IDisposable>如果您是負責配置及釋放 unmanaged 的資源保留的欄位。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 安全地隱藏此規則的警告，如果您就要負責無法釋放資源保留的欄位，或呼叫<xref:System.IDisposable.Dispose%2A>比這個規則會檢查更深入的呼叫層級，就會發生。  
  
## <a name="example"></a>範例  
 下列範例顯示型別`TypeA`實作<xref:System.IDisposable>(`FT` previosu 討論中)。  
  
 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]  
  
## <a name="example"></a>範例  
 下列範例顯示型別`TypeB`，藉由宣告欄位違反此規則`aFieldOfADisposableType`(`F`在先前的討論內容) 做為可處置的類型 (`TypeA`) 並不會呼叫<xref:System.IDisposable.Dispose%2A>欄位上。 `TypeB`對應至`T`中先前的討論。  
  
 [!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IDisposable?displayProperty=fullName>   
 [處置模式](/dotnet/standard/design-guidelines/dispose-pattern)