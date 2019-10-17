---
title: CA1414：以 MarshalAs 標記布林值 P/Invoke 引數
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
ms.openlocfilehash: 0f8140e78d1ee3340e9ee5441e183b55d4c5111c
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444180"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414：以 MarshalAs 標記布林值 P/Invoke 引數

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|分類|Microsoft. 互通性|
|重大變更|中斷|

## <a name="cause"></a>原因
平台叫用方法宣告包含 @no__t 0 參數或傳回值，但 <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> 屬性不會套用至參數或傳回值。

## <a name="rule-description"></a>規則描述
平台叫用方法會存取未受管理的程式碼，並使用 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 或 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 中的 `Declare` 關鍵字來定義。 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 指定用來轉換 managed 和非受控碼之間之資料類型的封送處理行為。 許多簡單的資料類型（例如 <xref:System.Byte?displayProperty=fullName> 和 <xref:System.Int32?displayProperty=fullName>）在非受控碼中具有單一標記法，而且不需要指定其封送處理行為;common language runtime 會自動提供正確的行為。

@No__t 0 資料類型在非受控碼中有多個標記法。 未指定 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 時，<xref:System.Boolean> 資料類型的預設封送處理行為會 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>。 這是32位整數，在所有情況下都不適用。 應判斷非受控方法所需的布林值表示，並將其符合適當的 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>。 Unmanagedtype.lpwstr 是 Win32 BOOL 類型，一律為4個位元組。 Unmanagedtype.lpwstr 應該用於C++ `bool` 或其他1位元組的類型。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規，請將 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 套用至 <xref:System.Boolean> 參數或傳回值。 將屬性的值設定為適當的 <xref:System.Runtime.InteropServices.UnmanagedType>。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。 即使預設的封送處理行為是適當的，當明確指定行為時，程式碼更容易維護。

## <a name="example"></a>範例

下列範例顯示以適當的 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性標記的平台叫用方法。

[!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
[!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
[!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>相關規則
[CA1901：P/Invoke 宣告應該為可移植](../code-quality/ca1901.md)

[CA2101：指定 P/Invoke 字串引數的封送處理](../code-quality/ca2101.md)

## <a name="see-also"></a>請參閱

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)
