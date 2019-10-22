---
title: CA1406：避免 Visual Basic 6 個用戶端的 Int64 引數 |Microsoft Docs
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
ms.openlocfilehash: c20ea7bd7bba6f221395c7e2c21d6c1dcc241fb4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661302"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406：避免對 Visual Basic 6 用戶端使用 Int64 引數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Category|Microsoft. 互通性|
|中斷變更|中斷|

## <a name="cause"></a>原因
 特別標示為「元件物件模型（COM）可見」的類型會宣告接受 <xref:System.Int64?displayProperty=fullName> 引數的成員。

## <a name="rule-description"></a>規則描述
 Visual Basic 6 COM 用戶端無法存取64位整數。

 根據預設，COM 會看到下列內容：元件、公用類型、公用類型中的公用實例成員，以及公用實數值型別的所有成員。 不過，若要減少誤報，此規則需要明確陳述類型的 COM 可見度;包含的元件必須標記為 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 設定為 `false`，而且類型必須標記為 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 設定為 `true`。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，其值一律可以表示為32位整數，請將參數類型變更為 <xref:System.Int32?displayProperty=fullName>。 如果參數的值可能大於可以表示為32位整數，請將參數類型變更為 <xref:System.Decimal?displayProperty=fullName>。 請注意，<xref:System.Single?displayProperty=fullName> 和 <xref:System.Double?displayProperty=fullName> 會在 <xref:System.Int64> 資料類型的上限範圍內遺失精確度。 如果成員不是要對 COM 可見，請將它標記為 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 設定為 `false`。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您確定 Visual Basic 6 個 COM 用戶端不會存取類型，可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的類型。

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/cs/FxCop.Interoperability.LongArgument.cs#1)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/vb/FxCop.Interoperability.LongArgument.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1413：避免在 COM 可見實值型別中使用非公用欄位](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407：避免在 COM 可見類型中使用靜態成員](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017：組件必須標記 ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>請參閱
 [與非受控程式碼](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [LONG 資料型別](https://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516)交互操作
