---
title: "CA1064： 例外狀況必須是公用 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cd39b4655f4a1bc98e408655e86fa1068820c9f9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064：例外狀況必須是公用
|||  
|-|-|  
|TypeName|ExceptionsShouldBePublic|  
|CheckId|CA1064|  
|分類|Microsoft.Design|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 非公用例外狀況直接衍生自<xref:System.Exception>， <xref:System.SystemException>，或<xref:System.ApplicationException>。  
  
## <a name="rule-description"></a>規則描述  
 只有在它自己的內部範圍內顯示內部例外狀況。 當例外狀況超出內部範圍後，只能使用基本例外狀況來攔截例外狀況。 如果內部例外狀況繼承自<xref:System.Exception>， <xref:System.SystemException>，或<xref:System.ApplicationException>，外部的程式碼就沒有足夠的資訊可以知道該如何處理例外狀況。  
  
 但是，如果程式碼可於稍後當做基底的內部例外狀況的公用例外狀況，它是合理假設在進一步的程式碼時將能夠做到智慧型與基底例外狀況。 公用例外狀況必須由 T:System.Exception、 T:System.SystemException 或 T:System.ApplicationException 所提供的詳細資訊。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 將例外狀況設為公用，或衍生不是公用例外狀況的內部例外狀況<xref:System.Exception>， <xref:System.SystemException>，或<xref:System.ApplicationException>。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 如果您確定在所有情況下，會在它自己的內部範圍內攔截到的私用例外狀況，則隱藏此規則的訊息。  
  
## <a name="example"></a>範例  
 因為例外狀況類別直接衍生自例外狀況，而且是內部的第一個範例方法 FirstCustomException 引發此規則。 此規則不會引發 SecondCustomException 類別上，因為雖然直接從例外狀況也衍生類別，類別宣告為公用。 第三個類別也不會引發此規則因為它不是直接從<xref:System.Exception?displayProperty=fullName>， <xref:System.SystemException?displayProperty=fullName>，或<xref:System.ApplicationException?displayProperty=fullName>。  
  
 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]