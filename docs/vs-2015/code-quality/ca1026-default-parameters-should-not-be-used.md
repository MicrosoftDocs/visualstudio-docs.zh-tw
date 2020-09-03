---
title: CA1026：不應使用預設參數 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a63d6e788dd1722d0c593469b225a4f1aeb4738d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548435"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026:不應該使用預設參數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|類別|Microsoft. 設計|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見的類型包含外部可見的方法，該方法會使用預設參數。

## <a name="rule-description"></a>規則描述
 Common Language Specification (CLS) 下允許使用預設參數的方法;不過，CLS 允許編譯器忽略指派給這些參數的值。 針對忽略預設參數值的編譯器所撰寫的程式碼，必須明確地提供每個預設參數的引數。 若要維護跨程式設計語言的行為，使用預設參數的方法應該以提供預設參數的方法多載來取代。

 編譯器會在存取 managed 程式碼時，忽略 c + + Managed 延伸模組的預設參數值。 Visual Basic 編譯器支援具有使用 [選擇性](https://msdn.microsoft.com/library/4571ce88-a539-4115-b230-54eb277c6aa7) 關鍵字之預設參數的方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將使用預設參數的方法，取代為提供預設參數的方法多載。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示使用預設參數的方法，以及提供對等功能的多載方法。

 [!code-vb[FxCop.Design.DefaultParameters#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DefaultParameters/vb/FxCop.Design.DefaultParameters.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1025:以參數陣列取代重複的引數](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>另請參閱
 [語言獨立性以及與語言無關的元件](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
