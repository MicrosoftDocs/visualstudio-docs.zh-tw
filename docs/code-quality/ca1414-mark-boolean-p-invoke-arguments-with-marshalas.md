---
title: CA1414:以 MarshalAs 標記布林 P-Invoke 引數
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1a06197278c61a25c4baad15888f818ed1e1f673
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55955878"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414:以 MarshalAs 標記布林 P/Invoke 引數

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|分類|Microsoft.Interoperability|
|中斷變更|中斷|

## <a name="cause"></a>原因
 平台叫用方法宣告包含<xref:System.Boolean?displayProperty=fullName>參數或傳回值，但<xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName>屬性不會套用至參數或傳回值。

## <a name="rule-description"></a>規則描述
 平台叫用方法存取 unmanaged 程式碼，並使用定義`Declare`中的關鍵字[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]或<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>。 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 指定用來轉換資料類型，managed 和 unmanaged 程式碼之間封送處理行為。 許多簡單的資料類型，例如<xref:System.Byte?displayProperty=fullName>和<xref:System.Int32?displayProperty=fullName>、 unmanaged 程式碼中有單一的表示法，並不需要指定其封送處理行為; common language runtime 會自動提供正確的行為。

 <xref:System.Boolean>資料類型在 unmanaged 程式碼中有多種表示。 當<xref:System.Runtime.InteropServices.MarshalAsAttribute>未指定，預設值封送處理行為<xref:System.Boolean>資料類型是<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>。 這是 32 位元整數，也就是不適合所有情況。 Unmanaged 方法需要布林值表示應該決定，並對應到適當<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>。 UnmanagedType.Bool 是 Win32 BOOL 類型，這一律是 4 個位元組。 應該使用 c + + 的 UnmanagedType.U1`bool`或其他 1 個位元組類型。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，套用<xref:System.Runtime.InteropServices.MarshalAsAttribute>至<xref:System.Boolean>參數或傳回值。 將屬性的值設定為適當<xref:System.Runtime.InteropServices.UnmanagedType>。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 即使封送處理行為的預設值是適當，程式碼時的行為已明確指定時，更輕鬆地可保留。

## <a name="example"></a>範例

下列範例所示的平台叫用會標有適當的方法<xref:System.Runtime.InteropServices.MarshalAsAttribute>屬性。

 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>相關的規則
 [CA1901:P/Invoke 宣告應該為可移植的](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101： 必須指定的 P/Invoke 字串引數封送處理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)