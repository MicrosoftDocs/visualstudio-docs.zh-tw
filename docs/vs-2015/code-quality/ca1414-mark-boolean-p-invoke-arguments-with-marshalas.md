---
title: CA1414：使用 MarshalAs 標記布林值 P-Invoke 引數 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 588e16a6b21b320ad7012bd20d79a62d027679e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652696"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414：以 MarshalAs 標記布林值 P/Invoke 引數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Category|Microsoft. 互通性|
|中斷變更|中斷|

## <a name="cause"></a>原因
 平台叫用方法宣告包含 <xref:System.Boolean?displayProperty=fullName> 參數或傳回值，但 <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> 屬性不會套用至參數或傳回值。

## <a name="rule-description"></a>規則描述
 平台叫用方法會存取未受管理的程式碼，並使用 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 或 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 中的 `Declare` 關鍵字來定義。 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 指定用來轉換 managed 和非受控碼之間之資料類型的封送處理行為。 許多簡單的資料類型（例如 <xref:System.Byte?displayProperty=fullName> 和 <xref:System.Int32?displayProperty=fullName>）在非受控碼中具有單一標記法，而且不需要指定其封送處理行為;common language runtime 會自動提供正確的行為。

 @No__t_0 資料類型在非受控碼中有多個標記法。 未指定 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 時，<xref:System.Boolean> 資料類型的預設封送處理行為會 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>。 這是32位整數，在所有情況下都不適用。 應判斷非受控方法所需的布林值表示，並將其符合適當的 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>。 Unmanagedtype.lpwstr 是 Win32 BOOL 類型，一律為4個位元組。 Unmanagedtype.lpwstr 應該用於C++ `bool` 或其他1位元組的類型。 如需詳細資訊，請參閱[布林值類型的預設封送處理](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請將 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 套用至 <xref:System.Boolean> 參數或傳回值。 將屬性的值設定為適當的 <xref:System.Runtime.InteropServices.UnmanagedType>。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 即使預設的封送處理行為是適當的，當明確指定行為時，程式碼更容易維護。

## <a name="example"></a>範例
 下列範例顯示兩個以適當的 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性標記的平台叫用方法。

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1901：P/Invoke 宣告應該為可移植](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101：指定 P/Invoke 字串引數的封送處理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>請參閱
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>[布林類型的預設封送處理](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)[與非受控程式碼互](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)操作
