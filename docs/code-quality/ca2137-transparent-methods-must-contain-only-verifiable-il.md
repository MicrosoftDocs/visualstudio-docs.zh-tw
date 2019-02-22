---
title: CA2137:透明方法必須只包含可驗證的 IL
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f74b539d9382bf8b5f5fe319ff319cdf6f372340
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55946011"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137:透明方法必須只包含可驗證的 IL

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

 若要確定您的程式碼包含只可驗證的 MSIL，執行[Peverify.exe （PEVerify 工具）](/dotnet/framework/tools/peverify-exe-peverify-tool)上您的組件。 執行與 PEVerify **/ 透明**選項將輸出限制為只有無法驗證透明方法會導致錯誤。 如果 / 未使用透明的選項，PEVerify 也會確認是否允許包含無法驗證的程式碼的關鍵方法。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將標記的方法<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>屬性，或移除未經驗證的程式碼。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 此範例中的方法使用未經驗證的程式碼，並應該標示<xref:System.Security.SecurityCriticalAttribute>或<xref:System.Security.SecuritySafeCriticalAttribute>屬性。

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../code-quality/codesnippet/CSharp/ca2137-transparent-methods-must-contain-only-verifiable-il_1.cs)]