---
title: CA1414： 標記，則為 true 的 P-invoke 引數，以 MarshalAs |Microsoft Docs
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
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7f8378d2b3f498146fc960e57d1d3562827fe347
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49918398"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414：以 MarshalAs 標記布林值 P/Invoke 引數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|分類|Microsoft.Interoperability|
|中斷變更|中斷|

## <a name="cause"></a>原因
 平台叫用方法宣告包含<xref:System.Boolean?displayProperty=fullName>參數或傳回值，但<xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName>屬性不會套用至參數或傳回值。

## <a name="rule-description"></a>規則描述
 平台叫用方法存取 unmanaged 程式碼，並使用定義`Declare`中的關鍵字[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]或<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>。 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 指定用來轉換資料類型，managed 和 unmanaged 程式碼之間封送處理行為。 許多簡單的資料類型，例如<xref:System.Byte?displayProperty=fullName>和<xref:System.Int32?displayProperty=fullName>、 unmanaged 程式碼中有單一的表示法，並不需要指定其封送處理行為; common language runtime 會自動提供正確的行為。

 <xref:System.Boolean>資料類型在 unmanaged 程式碼中有多種表示。 當<xref:System.Runtime.InteropServices.MarshalAsAttribute>未指定，預設值封送處理行為<xref:System.Boolean>資料類型是<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>。 這是 32 位元整數，也就是不適合所有情況。 Unmanaged 方法需要布林值表示應該決定，並對應到適當<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>。 UnmanagedType.Bool 是 Win32 BOOL 類型，這一律是 4 個位元組。 應該使用 c + + 的 UnmanagedType.U1`bool`或其他 1 個位元組類型。 如需詳細資訊，請參閱 <<c0> [ 預設為布林值類型封送處理](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，套用<xref:System.Runtime.InteropServices.MarshalAsAttribute>至<xref:System.Boolean>參數或傳回值。 將屬性的值設定為適當<xref:System.Runtime.InteropServices.UnmanagedType>。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。 即使封送處理行為的預設值是適當，程式碼時的行為已明確指定時，更輕鬆地可保留。

## <a name="example"></a>範例
 下列範例顯示兩個平台叫用的標記具有適當的方法，<xref:System.Runtime.InteropServices.MarshalAsAttribute>屬性。

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA1901：P/Invoke 宣告應該為可移植](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101：指定 P/Invoke 字串引數的封送處理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>另請參閱
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> [預設值的布林值類型封送處理](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)[與相互操作 Unmanaged 程式碼](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



