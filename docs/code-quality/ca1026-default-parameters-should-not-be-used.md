---
title: "CA1026： 應該不使用預設參數 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 43f83bf88e017da06ee3653019aa91807229d55e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026：不應使用預設參數
|||  
|-|-|  
|TypeName|DefaultParametersShouldNotBeUsed|  
|CheckId|CA1026|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 外部可見類型包含外部可見的方法會使用預設參數。  
  
## <a name="rule-description"></a>規則描述  
 允許在 Common Language Specification (CLS); 您可以使用預設參數的方法不過，CLS 允許編譯器忽略已指派給這些參數的值。 程式碼撰寫的編譯器會忽略預設參數值必須明確地提供每個預設參數的引數。 若要維持您想要在程式語言之間的行為，使用預設參數的方法應該取代提供預設參數的方法多載。  
  
 編譯器時，會忽略預設參數的值管理擴充功能用於 c + + 存取 managed 程式碼。 Visual Basic 編譯器支援使用的預設參數的方法[選擇性](/dotnet/visual-basic/language-reference/modifiers/optional)關鍵字。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，取代使用預設參數提供預設參數的方法多載的方法。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 下列範例會示範使用預設參數的方法，並提供對等功能的多載的方法。  
  
 [!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA1025：必須以參數陣列取代重複的引數](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)  
  
## <a name="see-also"></a>請參閱  
 [語言獨立性以及與語言無關的元件](/dotnet/standard/language-independence-and-language-independent-components)