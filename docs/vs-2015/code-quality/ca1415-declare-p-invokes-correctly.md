---
title: CA1415：宣告 P-正確地叫用 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b9931d29c818d95785146558637c32237e2c5276
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547845"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415：P/Invokes 必須正確宣告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|類別|Microsoft. 互通性|
|中斷變更|不中斷-如果宣告參數的 P/Invoke 無法在元件外部看到，則為。 中斷-如果宣告參數的 P/Invoke 可以在元件外部看到，則為。|

## <a name="cause"></a>原因
 平台叫用方法宣告不正確。

## <a name="rule-description"></a>規則描述
 平台叫用方法會存取未受管理的程式碼，並使用 `Declare` 或中的關鍵字來定義 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 。 目前，此規則會尋找以具有重迭結構參數指標的 Win32 函式為目標的平台叫用方法宣告，而且對應的 managed 參數不是結構的指標 <xref:System.Threading.NativeOverlapped?displayProperty=fullName> 。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請正確宣告平台叫用方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則並滿足規則的平台叫用方法。

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes/cs/FxCop.Interoperability.DeclarePInvokes.cs#1)]

## <a name="see-also"></a>另請參閱
 [與 Unmanaged 程式碼互通](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
