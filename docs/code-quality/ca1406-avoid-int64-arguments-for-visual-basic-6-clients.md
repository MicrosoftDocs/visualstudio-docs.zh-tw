---
title: CA1406:避免對 Visual Basic 6 用戶端使用 int64 引數
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 82a8b1ea389c37dc63a9fe7366208a2a3028efb8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234803"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406:避免對 Visual Basic 6 用戶端使用 int64 引數

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|分類|Microsoft.Interoperability|
|重大變更|中斷|

## <a name="cause"></a>原因
特別標示為「元件物件模型（COM）可見」的類型會宣告接受<xref:System.Int64?displayProperty=fullName>引數的成員。

## <a name="rule-description"></a>規則描述
Visual Basic 6 COM 用戶端無法存取 64 位元整數。

根據預設，COM 會看到下列內容：元件、公用類型、公用類型中的公用實例成員，以及公用實數值型別的所有成員。 不過，若要減少誤報，此規則需要明確陳述類型的 COM 可見度;包含的<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>元件必須以設定為`false`的標記，而且類型<xref:System.Runtime.InteropServices.ComVisibleAttribute>必須以設定為`true`的標記。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規，其值一律可以表示為32位整數，請將參數類型變更為<xref:System.Int32?displayProperty=fullName>。 如果參數的值可能大於可以表示為32位整數，請將參數類型變更為<xref:System.Decimal?displayProperty=fullName>。 請注意， <xref:System.Double?displayProperty=fullName> <xref:System.Int64>和會在資料類型的上限範圍中遺失精確度。 <xref:System.Single?displayProperty=fullName> 如果成員不是要對 COM 可見，請將<xref:System.Runtime.InteropServices.ComVisibleAttribute>設定為，並將它標示為。 `false`

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
如果您確定 Visual Basic 6 個 COM 用戶端不會存取類型，可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
下列範例顯示違反規則的類型。

[!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
[!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]

## <a name="related-rules"></a>相關規則
[CA1413避免在 COM 可見實數值型別中的非公用欄位](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

[CA1407避免 COM 可見類型中的靜態成員](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017以 ComVisibleAttribute 標記元件](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>另請參閱

- [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)
- [Long 資料類型](/dotnet/visual-basic/language-reference/data-types/long-data-type)