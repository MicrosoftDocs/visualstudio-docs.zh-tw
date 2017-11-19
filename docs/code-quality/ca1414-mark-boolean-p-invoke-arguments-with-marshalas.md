---
title: "CA1414： 標記布林值的 P 叫用引數，以 MarshalAs |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 25fd80168e78feda70b86f512598a850acae7010
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414：以 MarshalAs 標記布林值 P/Invoke 引數
|||  
|-|-|  
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|  
|CheckId|CA1414|  
|分類|Microsoft.Interoperability|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 平台叫用方法宣告中包含<xref:System.Boolean?displayProperty=fullName>參數或傳回值，但<xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName>屬性不會套用至參數或傳回值。  
  
## <a name="rule-description"></a>規則描述  
 平台叫用方法存取 unmanaged 程式碼，並使用定義`Declare`關鍵字[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]或<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>。 <xref:System.Runtime.InteropServices.MarshalAsAttribute>指定用於 managed 和 unmanaged 程式碼之間轉換資料類型的封送處理行為。 許多的簡單資料類型，例如<xref:System.Byte?displayProperty=fullName>和<xref:System.Int32?displayProperty=fullName>、 unmanaged 程式碼中有單一表示法，而且不需要其封送處理行為的規格，則 common language runtime 會自動提供正確的行為。  
  
 <xref:System.Boolean>資料類型在 unmanaged 程式碼中有多種表示。 當<xref:System.Runtime.InteropServices.MarshalAsAttribute>未指定，預設封送處理行為的<xref:System.Boolean>資料類型是<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>。 這是 32 位元整數，但不適合所有情況。 應該決定，對應到適當的布林值表示所需的 unmanaged 方法<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>。 UnmanagedType.Bool 是 Win32 BOOL 類型，它一律是 4 個位元組。 UnmanagedType.U1 適用於 c + +`bool`或其他 1 個位元組類型。 如需詳細資訊，請參閱[預設針對布林類型封送處理](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，套用<xref:System.Runtime.InteropServices.MarshalAsAttribute>至<xref:System.Boolean>參數或傳回值。 屬性的值設定為適當<xref:System.Runtime.InteropServices.UnmanagedType>。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。 即使封送處理行為的預設值是適當時，程式碼更容易維護時明確指定的行為。  
  
## <a name="example"></a>範例  
 下列範例示範兩個平台叫用方法標示為適當的<xref:System.Runtime.InteropServices.MarshalAsAttribute>屬性。  
  
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA1901: P/Invoke 宣告應該為可移植](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)  
  
 [Ca2101： 必須指定 P/Invoke 字串引數的封送處理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>   
 [預設封送處理針對布林類型](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)   
 [與 Unmanaged 程式碼互通](/dotnet/framework/interop/index)