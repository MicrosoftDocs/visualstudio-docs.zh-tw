---
title: CA1401:-Invokes 不應該為可見 |Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ee4afd777f46087a7497dbdf4734e4ced52f47d4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58939897"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401:P/Invokes 不應該為可見的
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|分類|Microsoft.Interoperability|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的方法，公用型別中具有<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>屬性 (也實作`Declare`中的關鍵字[!INCLUDE[vbprvb](../includes/vbprvb-md.md)])。

## <a name="rule-description"></a>規則描述
 方法標記著<xref:System.Runtime.InteropServices.DllImportAttribute>屬性 (或使用所定義的方法`Declare`中的關鍵字[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) 使用平台叫用服務來存取 unmanaged 程式碼。 但不得公開 (Expose) 此類方法。 私用或內部，請保留這些方法，您要確定您的程式庫不能用來允許呼叫端存取未受管理的 Api，它們無法呼叫破壞安全性項目。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，變更方法的存取層級。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會宣告方法違反此規則。

 [!code-csharp[FxCop.Interoperability.DllImports#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/cs/FxCop.Interoperability.DllImports.cs#1)]
 [!code-vb[FxCop.Interoperability.DllImports#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/vb/FxCop.Interoperability.DllImports.vb#1)]
