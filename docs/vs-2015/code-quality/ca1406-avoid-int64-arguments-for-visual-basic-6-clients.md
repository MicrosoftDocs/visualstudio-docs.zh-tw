---
title: CA1406：避免 Visual Basic 6 用戶端的 Int64 引數 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b6ab93c24cd97d498ae886c7a9184fd4a5f111f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534910"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406:避免對 Visual Basic 6 用戶端使用 int64 引數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|類別|Microsoft. 互通性|
|中斷變更|中斷|

## <a name="cause"></a>原因
 明確標示為元件物件模型可見的類型 (COM) 宣告採用 <xref:System.Int64?displayProperty=fullName> 引數的成員。

## <a name="rule-description"></a>規則描述
 Visual Basic 6 COM 用戶端無法存取 64 位元整數。

 根據預設，COM 可看到下列內容：元件、公用類型、公用類型中的公用實例成員，以及公用實數值型別的所有成員。 不過，若要減少誤報，此規則需要明確陳述型別的 COM 可見度;包含的元件必須標記 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 為， `false` 而且類型必須標記為，而且必須將 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 設為 `true` 。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的值，其值一律可以表示為32位整數的參數，請將參數類型變更為 <xref:System.Int32?displayProperty=fullName> 。 如果參數的值可能大於以32位整數來表示，請將參數類型變更為 <xref:System.Decimal?displayProperty=fullName> 。 請注意， <xref:System.Single?displayProperty=fullName> 和 <xref:System.Double?displayProperty=fullName> 會在資料類型的上方範圍遺失精確度 <xref:System.Int64> 。 如果成員不打算對 COM 顯示，請將它標示 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 為 `false` 。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您確定 Visual Basic 6 個 COM 用戶端將不會存取類型，則可以放心隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的類型。

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/cs/FxCop.Interoperability.LongArgument.cs#1)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/vb/FxCop.Interoperability.LongArgument.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1413:避免在 COM 可見實值類型中使用非公用欄位](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407:避免在 COM 可見類型中使用靜態成員](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017:組件必須標記 ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>另請參閱
 [與非受控碼](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [LONG 資料型別](https://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516)交互操作
