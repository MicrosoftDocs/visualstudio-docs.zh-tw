---
title: CA1064:例外狀況必須是公用
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8196d4c48bfb93735b62c6f24cb08ec462e64c91
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788577"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064:例外狀況必須是公用

|||
|-|-|
|TypeName|ExceptionsShouldBePublic|
|CheckId|CA1064|
|分類|Microsoft.Design|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 非公用例外狀況直接衍生自<xref:System.Exception>， <xref:System.SystemException>，或<xref:System.ApplicationException>。

## <a name="rule-description"></a>規則描述
 內部例外狀況只會顯示在它自己的內部範圍的。 當例外狀況超出內部範圍後，只能使用基本例外狀況來攔截例外狀況。 如果內部例外狀況繼承自<xref:System.Exception>， <xref:System.SystemException>，或<xref:System.ApplicationException>，外部程式碼不會知道該如何處理例外狀況的足夠資訊。

 但是，如果程式碼具有公用的例外狀況，稍後會做為基底內部例外狀況，是合理假設程式碼進一步放大都能夠進行智慧型與基底例外狀況。 公用例外狀況會有詳細的資訊，藉由提供比<xref:System.Exception>， <xref:System.SystemException>，或<xref:System.ApplicationException>。

## <a name="how-to-fix-violations"></a>如何修正違規
 將例外狀況設為公用，或衍生不是公用例外狀況的內部例外狀況<xref:System.Exception>， <xref:System.SystemException>，或<xref:System.ApplicationException>。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您確定在所有情況下，將會在它自己內部的範圍內攔截到私用的例外狀況，則隱藏此規則的訊息。

## <a name="example"></a>範例
 因為例外狀況類別直接衍生自例外狀況，而且內部的第一個範例方法，FirstCustomException 會引發此規則。 此規則不會引發 SecondCustomException 類別上，因為雖然此類別也直接衍生自例外狀況，該類別已宣告為公用。 第三個類別也不會引發此規則因為它不是直接從衍生<xref:System.Exception?displayProperty=fullName>， <xref:System.SystemException?displayProperty=fullName>，或<xref:System.ApplicationException?displayProperty=fullName>。

 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]
