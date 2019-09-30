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
ms.openlocfilehash: 22e62a1e3209399be4b10a3ec28db4afdd6f0f20
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234679"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414:以 MarshalAs 標記布林 P/Invoke 引數

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|分類|Microsoft.Interoperability|
|重大變更|中斷|

## <a name="cause"></a>原因
平台叫用方法宣告包含<xref:System.Boolean?displayProperty=fullName>參數或傳回值， <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName>但屬性不會套用至參數或傳回值。

## <a name="rule-description"></a>規則描述
平台叫用方法會存取未受管理的程式碼，並`Declare`使用或[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>中的關鍵字來定義。 <xref:System.Runtime.InteropServices.MarshalAsAttribute>指定在 managed 和非受控碼之間轉換資料類型時所使用的封送處理行為。 許多簡單的資料類型（例如<xref:System.Byte?displayProperty=fullName>和<xref:System.Int32?displayProperty=fullName>）在非受控程式碼中都有單一標記法，而且不需要指定其封送處理行為; common language runtime 會自動提供正確的行為。

<xref:System.Boolean>資料類型在非受控碼中有多個標記法。 當未指定時， <xref:System.Boolean>資料類型的預設封送處理行為是<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>。 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 這是32位整數，在所有情況下都不適用。 應判斷非受控方法所需的布林值表示，並將其符合適當<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>的。 Unmanagedtype.lpwstr 是 Win32 BOOL 類型，一律為4個位元組。 Unmanagedtype.lpwstr 應該用於C++ `bool`或其他1位元組類型。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規，請<xref:System.Runtime.InteropServices.MarshalAsAttribute>將套用<xref:System.Boolean>至參數或傳回值。 將屬性的值設定為適當<xref:System.Runtime.InteropServices.UnmanagedType>的。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。 即使預設的封送處理行為是適當的，當明確指定行為時，程式碼更容易維護。

## <a name="example"></a>範例

下列範例顯示以適當<xref:System.Runtime.InteropServices.MarshalAsAttribute>的屬性標示的平台叫用方法。

[!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
[!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
[!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>相關規則
[CA1901P/Invoke 宣告應該是可移植的](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

[CA2101 必須指定 P/Invoke 字串引數的封送處理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)