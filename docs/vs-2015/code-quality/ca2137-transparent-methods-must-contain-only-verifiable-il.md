---
title: CA2137:透明方法必須包含可驗證的 IL |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2876a70eedb1191aaed91204505286f97e00a27b
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "58943048"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137:透明方法必須只包含可驗證的 IL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustBeVerifiable|
|CheckId|CA2137|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 方法包含無法驗證的程式碼，或以傳址方式傳回類型。

## <a name="rule-description"></a>規則描述
 當安全性透明程式碼嘗試執行無法驗證的 MSIL (Microsoft Intermediate Language) 時，就會引發此規則。 不過，此規則不包含完整的 IL 驗證器，並是使用啟發式來擷取多數的 MSIL 驗證違規情形。

 若要確定您的程式碼包含只可驗證的 MSIL，執行[Peverify.exe （PEVerify 工具）](http://msdn.microsoft.com/library/f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa)上您的組件。 執行與 PEVerify **/ 透明**選項將輸出限制為只有無法驗證透明方法會導致錯誤。 如果 / 未使用透明的選項，PEVerify 也會確認是否允許包含無法驗證的程式碼的關鍵方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將標記的方法<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>屬性，或移除未經驗證的程式碼。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 此範例中的方法使用未經驗證的程式碼，並應該標示<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>屬性。

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2137.transparentmethodsmustbeverifiable/cs/ca2137 - transparentmethodsmustbeverifiable.cs#1)]
