---
title: "CA1017： 標記以 ComVisibleAttribute 的組件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1cf713e2c177a24938c44c4577da88d8943e4fef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017：以 ComVisibleAttribute 標記組件
|||  
|-|-|  
|TypeName|MarkAssembliesWithComVisible|  
|CheckId|CA1017|  
|分類|Microsoft.Design|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 組件沒有<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>套用至它的屬性。  
  
## <a name="rule-description"></a>規則描述  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>屬性會判斷 COM 用戶端如何存取 managed 程式碼。 良好的設計會要求組件明確表示 COM 的可視性。 COM 的可視性可以針對整個組件並設定然後覆寫為個別的類型和類型成員。 如果屬性不存在，組件的內容會是可見對 COM 用戶端。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，加入組件中的屬性。 如果您不想要對 COM 用戶端可見的組件，將屬性套用並設定其值為`false`。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。 如果您想要顯示的組件，將屬性套用，並將其值設定為`true`。  
  
## <a name="example"></a>範例  
 下列範例示範具有的組件<xref:System.Runtime.InteropServices.ComVisibleAttribute>套用以防止它對 COM 用戶端可見的屬性。  
  
 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]  
  
## <a name="see-also"></a>請參閱  
 [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)   
 [限定互通的 .NET 類型](/dotnet/framework/interop/qualifying-net-types-for-interoperation)