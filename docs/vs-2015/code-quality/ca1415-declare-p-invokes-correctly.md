---
title: CA1415:-Invokes 必須正確宣告 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 57482b720b1a7801fc75e06a5eb5d05d3b1a1417
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691851"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415:P/Invokes 必須正確宣告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|分類|Microsoft.Interoperability|
|中斷變更|在組件外，看不到非-中斷-如果 P/Invoke 宣告的參數。 中斷-可以看到組件外部的 P/Invoke 宣告的參數。|

## <a name="cause"></a>原因
 平台叫用方法不正確地宣告。

## <a name="rule-description"></a>規則描述
 平台叫用方法存取 unmanaged 程式碼，並使用定義`Declare`中的關鍵字[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]或<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>。 目前，此規則會尋找平台叫用瞄準具有指向 OVERLAPPED 結構參數的 Win32 函式的方法宣告和對應的 managed 的參數不是指標<xref:System.Threading.NativeOverlapped?displayProperty=fullName>結構。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，正確地宣告平台叫用方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會顯示平台叫用方法違反此規則並滿足的規則。

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes/cs/FxCop.Interoperability.DeclarePInvokes.cs#1)]

## <a name="see-also"></a>另請參閱
 [與 Unmanaged 程式碼互通](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
