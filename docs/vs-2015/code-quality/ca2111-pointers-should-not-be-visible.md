---
title: CA2111： 指標不應該為可見 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0d96a71a27a235887fe1744bbee09027c2c6d434
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888923"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111：指標不應該為可見的
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護<xref:System.IntPtr?displayProperty=fullName>或<xref:System.UIntPtr?displayProperty=fullName>欄位不是唯讀的。

## <a name="rule-description"></a>規則描述
 <xref:System.IntPtr> 和<xref:System.UIntPtr>是用來存取 unmanaged 的記憶體的指標類型。 如果指標不是私用、 內部或唯讀的惡意程式碼就可以變更指標，可能會允許存取記憶體中的任意位置，或造成應用程式或系統失敗的值。

 如果您想要包含指標欄位的型別安全存取，請參閱[CA2112： 受保護的類型不應該公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)。

## <a name="how-to-fix-violations"></a>如何修正違規
 保護，以便唯讀、 內部或私人的指標。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您不會依賴指標的值，則隱藏此規則的警告。

## <a name="example"></a>範例
 下列程式碼顯示違反及符合規則的指標。 請注意，非私用指標也違反規則[CA1051： 不要宣告可見的執行個體欄位](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)。

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PointersArePrivate/cs/FxCop.Security.PointersArePrivate.cs#1)]

## <a name="related-rules"></a>相關的規則
 [CA2112：受保護類型不應該公開欄位](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051：不要宣告可見的執行個體欄位](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>另請參閱
 <xref:System.IntPtr?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName>



