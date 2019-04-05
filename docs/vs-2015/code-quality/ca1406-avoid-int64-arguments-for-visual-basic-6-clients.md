---
title: CA1406:避免對 Visual Basic 6 用戶端的 Int64 引數 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a024f2a695729dcc5c06ff6c5d6ac9c189fee762
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58930538"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406:避免對 Visual Basic 6 用戶端使用 int64 引數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|分類|Microsoft.Interoperability|
|中斷變更|中斷|

## <a name="cause"></a>原因
 特別標示為可見的元件物件模型 (COM) 類型宣告的成員，會採用<xref:System.Int64?displayProperty=fullName>引數。

## <a name="rule-description"></a>規則描述
 Visual Basic 6 COM 用戶端無法存取 64 位元整數。

 根據預設，以下是為 COM 所見： 組件、 公用型別、 公用的型別中的公用執行個體成員和公用實值型別的所有成員。 不過，以減少誤判，此規則需要明確指示; 類型的 COM 的可視性包含組件必須標記為<xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>設定為`false`且型別必須標示有<xref:System.Runtime.InteropServices.ComVisibleAttribute>設定為`true`。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此參數，其值一律可以表示為 32 位元整數的規則的違規情形，將參數類型變更為<xref:System.Int32?displayProperty=fullName>。 如果參數的值大於可以表示為 32 位元整數時，請將參數類型變更為<xref:System.Decimal?displayProperty=fullName>。 請注意，同時<xref:System.Single?displayProperty=fullName>並<xref:System.Double?displayProperty=fullName>失去精確度的上限範圍<xref:System.Int64>資料型別。 如果成員不是要為 COM 所見，加以標示<xref:System.Runtime.InteropServices.ComVisibleAttribute>設定為`false`。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它會安全地隱藏此規則的警告，如果它是特定 Visual Basic 6 COM 用戶端將不會存取類型。

## <a name="example"></a>範例
 下列範例顯示違反規則的型別。

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/cs/FxCop.Interoperability.LongArgument.cs#1)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/vb/FxCop.Interoperability.LongArgument.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA1413:避免在 COM 可見實值類型中的非公用欄位](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407:避免在 COM 可見類型中的靜態成員](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017:組件必須標記 comvisibleattribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>另請參閱
 [以相互操作 Unmanaged 程式碼](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [Long 資料類型](http://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516)
