---
title: CA1064：例外狀況應該是公用的 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fc78c4eaacc3ef0a480b913d20537aeebe5bfc01
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539265"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064:例外狀況必須是公用
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|ExceptionsShouldBePublic|
|CheckId|CA1064|
|類別|Microsoft. Design|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 非公用例外狀況直接衍生自 <xref:System.Exception> 、 <xref:System.SystemException> 或 <xref:System.ApplicationException> 。

## <a name="rule-description"></a>規則描述
 內部例外狀況只會顯示在它自己的內部範圍內。 當例外狀況超出內部範圍後，只能使用基本例外狀況來攔截例外狀況。 如果內部例外狀況是繼承自 <xref:System.Exception> 、 <xref:System.SystemException> 或 <xref:System.ApplicationException> ，外部程式碼將不會有足夠的資訊來知道該如何處理例外狀況。

 但是，如果程式碼有公開例外狀況，稍後用來當做內部例外狀況的基底，則合理地假設程式碼將能夠使用基底例外狀況進行智慧型作業。 公用例外狀況的資訊會比 T:System.Exception、T:System.SystemException 或 T:System.ApplicationException. 所提供的更多

## <a name="how-to-fix-violations"></a>如何修正違規
 將例外狀況設為公用，或從非、或的公用例外狀況衍生內部例外狀況 <xref:System.Exception> <xref:System.SystemException> <xref:System.ApplicationException> 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您確定在所有情況下，將會在其本身的內部範圍內攔截到私用例外狀況，請隱藏此規則中的訊息。

## <a name="example"></a>範例
 此規則會在第一個範例方法 FirstCustomException 上引發，因為例外狀況類別直接衍生自例外狀況，且為內部。 此規則不會在 SecondCustomException 類別上引發，因為雖然類別也直接衍生自例外狀況，但該類別已宣告為公用。 第三個類別也不會引發規則，因為它不是直接衍生自 <xref:System.Exception?displayProperty=fullName> 、 <xref:System.SystemException?displayProperty=fullName> 或 <xref:System.ApplicationException?displayProperty=fullName> 。

 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.design.exceptionsshouldbepublic.ca1064/cs/ca1064 - exceptionsshouldbepublic.cs#1)]
