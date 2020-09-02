---
title: CA1401： P-Invoke 不應該是可見的 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9f13669959a5874c74753d304371b8ab7db14d4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547286"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401：P/Invokes 不應該為可見的
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|類別|Microsoft. 互通性|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用類型中的公用或受保護的方法具有 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 屬性 (也會由 `Declare`) 中的關鍵字來執行 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 。

## <a name="rule-description"></a>規則描述
 以屬性（attribute）標記的方法 <xref:System.Runtime.InteropServices.DllImportAttribute> (或使用) 使用關鍵字定義的方法，會 `Declare` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 使用平台叫用服務來存取非受控碼。 但不得公開 (Expose) 此類方法。 藉由將這些方法保留為私用或內部，您可以讓呼叫端存取未受管理的 Api （否則無法呼叫），以確定您的程式庫無法用來缺口安全性。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請變更方法的存取層級。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會宣告違反此規則的方法。

 [!code-csharp[FxCop.Interoperability.DllImports#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/cs/FxCop.Interoperability.DllImports.cs#1)]
 [!code-vb[FxCop.Interoperability.DllImports#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/vb/FxCop.Interoperability.DllImports.vb#1)]
