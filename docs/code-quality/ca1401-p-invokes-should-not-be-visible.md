---
title: CA1401:P-Invokes 不應該為可見的
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d4a0a1c001407d947988497c422fdb8e88dd7c83
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234888"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401:P/Invokes 不應該為可見的

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|分類|Microsoft.Interoperability|
|重大變更|中斷|

## <a name="cause"></a>原因
公用類型中的公用或受保護方法具有<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>屬性（也是由中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]的`Declare`關鍵字來執行）。

## <a name="rule-description"></a>規則描述
以<xref:System.Runtime.InteropServices.DllImportAttribute>屬性（或在中`Declare` [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]使用關鍵字定義的方法）標記的方法會使用平台叫用服務來存取未受管理的程式碼。 但不得公開 (Expose) 此類方法。 藉由將這些方法保留為私用或內部，您可以藉由允許呼叫端存取非受控 Api （否則無法呼叫），確保您的程式庫無法用來入侵安全性。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形，請變更方法的存取層級。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。

## <a name="example"></a>範例
下列範例會宣告違反此規則的方法。

[!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
[!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]