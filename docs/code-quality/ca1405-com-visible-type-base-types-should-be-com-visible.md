---
title: "CA1405: COM 可見類型的基底類型應該是 COM 可見 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 86e12b30f27478ec8426dc152dbbfd784edad412
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405：COM 可見類型的基底類型應該是 COM 可見
|||  
|-|-|  
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|  
|CheckId|CA1405|  
|分類|Microsoft.Interoperability|  
|中斷變更|DependsOnFix|  
  
## <a name="cause"></a>原因  
 元件物件模型 (COM) 可見的型別衍生自不是 COM 可見的類型。  
  
## <a name="rule-description"></a>規則描述  
 當 COM 可見型別會在新的版本中加入成員時，它必須遵守嚴格的指導方針，以避免破壞繫結至目前版本的 COM 用戶端。 COM 不可見的型別會假設它沒有加入新成員時，請依照這些 COM 版本控制規則。 不過，如果 COM 可見型別衍生自 COM 可見型別，會公開類別介面<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName>或<xref:System.Runtime.InteropServices.ClassInterfaceType>（預設值），基底型別的所有公用成員 （除非有特別標示為 COM 可見，這會是備援）公開至 com。 如果基底型別會在後續版本中加入新成員，可能會中斷繫結至衍生類型的類別介面的 COM 用戶端。 COM 可見類型應該只從 COM 可見的類型，以降低中斷 COM 用戶端的衍生。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，讓 COM 可見的基底類型或衍生型別 COM 變成不可見。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 下列範例顯示違反規則的類型。  
  
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>   
 [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)