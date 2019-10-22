---
title: CA2137：透明方法必須只包含可驗證的 IL |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: be3732fbf1fc01deb18d2af6a183d47e618db337
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602979"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137：透明方法必須只包含可驗證的 IL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustBeVerifiable|
|CheckId|CA2137|
|Category|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 方法包含無法驗證的程式碼，或以傳址方式傳回類型。

## <a name="rule-description"></a>規則描述
 當安全性透明程式碼嘗試執行無法驗證的 MSIL (Microsoft Intermediate Language) 時，就會引發此規則。 不過，此規則不包含完整的 IL 驗證器，並是使用啟發式來擷取多數的 MSIL 驗證違規情形。

 若要確定您的程式碼只包含可驗證的 MSIL，請在您的元件上執行[Peverify （Peverify 工具）](https://msdn.microsoft.com/library/f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa) 。 使用 **/transparent**選項來執行 PEVerify，這會將輸出限制為只有無法驗證的透明方法會造成錯誤。 如果未使用/transparent 選項，PEVerify 也會驗證允許包含無法驗證之程式碼的重要方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請將方法標記為 <xref:System.Security.SecurityCriticalAttribute> 或 <xref:System.Security.SecuritySafeCriticalAttribute> 屬性，或移除無法驗證的程式碼。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 此範例中的方法使用無法驗證的程式碼，而且應該以 <xref:System.Security.SecurityCriticalAttribute> 或 <xref:System.Security.SecuritySafeCriticalAttribute> 屬性加以標記。

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2137.transparentmethodsmustbeverifiable/cs/ca2137 - transparentmethodsmustbeverifiable.cs#1)]
