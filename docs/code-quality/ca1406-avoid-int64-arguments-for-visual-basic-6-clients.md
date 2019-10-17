---
title: CA1406：避免對 Visual Basic 6 用戶端使用 Int64 引數
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
ms.openlocfilehash: 7ebf218b15dcb4048129e308822042efa5f6b0c9
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440508"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406：避免對 Visual Basic 6 用戶端使用 Int64 引數

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|分類|Microsoft. 互通性|
|重大變更|中斷|

## <a name="cause"></a>原因
特別標示為「元件物件模型（COM）可見」的類型會宣告接受 @no__t 0 引數的成員。

## <a name="rule-description"></a>規則描述
Visual Basic 6 COM 用戶端無法存取64位整數。

根據預設，COM 會看到下列內容：元件、公用類型、公用類型中的公用實例成員，以及公用實數值型別的所有成員。 不過，若要減少誤報，此規則需要明確陳述類型的 COM 可見度;包含的元件必須標記為 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 設定為 `false`，而且類型必須標記為 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 設定為 `true`。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規，其值一律可以表示為32位整數，請將參數類型變更為 <xref:System.Int32?displayProperty=fullName>。 如果參數的值可能大於可以表示為32位整數，請將參數類型變更為 <xref:System.Decimal?displayProperty=fullName>。 請注意，在 <xref:System.Int64> 資料類型的上方範圍中，<xref:System.Single?displayProperty=fullName> 和 @no__t 1 都會失去有效位數。 如果成員不是要對 COM 可見，請將它標記為 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 設定為 `false`。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
如果您確定 Visual Basic 6 個 COM 用戶端不會存取類型，可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
下列範例顯示違反規則的類型。

[!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
[!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]

## <a name="related-rules"></a>相關規則
[CA1413：避免在 COM 可見實值型別中使用非公用欄位](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

[CA1407：避免在 COM 可見類型中使用靜態成員](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017：組件必須標記 ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>請參閱

- [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)
- [Long 資料類型](/dotnet/visual-basic/language-reference/data-types/long-data-type)
