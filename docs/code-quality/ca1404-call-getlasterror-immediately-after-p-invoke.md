---
title: "Ca1404： 必須在 P Invoke 之後立即呼叫 GetLastError |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c12d90fe9ae453f3b02c9e6c3f961e54084081aa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404：必須在 P/Invoke 之後立即呼叫 GetLastError
|||  
|-|-|  
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|  
|CheckId|CA1404|  
|分類|Microsoft.Interoperability|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 進行呼叫以<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName>方法或對等的 Win32`GetLastError`函式，而且來自前立即呼叫並不在平台叫用方法。  
  
## <a name="rule-description"></a>規則描述  
 平台叫用方法存取 unmanaged 程式碼，並使用定義`Declare`關鍵字[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]或<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>屬性。 一般而言，在發生錯誤時，unmanaged 函式呼叫 Win32`SetLastError`函式可設定為與下列失敗相關的錯誤代碼。 失敗函式的呼叫端會呼叫 Win32`GetLastError`函式來擷取錯誤程式碼，並判斷失敗的原因。 錯誤碼會維護每個執行緒為基礎，並且會覆寫的下一個呼叫`SetLastError`。 Managed 程式碼的呼叫失敗的平台叫用方法之後，可以藉由呼叫擷取錯誤碼<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>方法。 因為錯誤碼將會覆寫其他受管理的類別程式庫方法，從內部呼叫`GetLastError`或<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>方法應該平台叫用方法呼叫之後立即呼叫。  
  
 此規則會忽略下列呼叫 managed 的成員平台的呼叫之間發生時叫用方法，並以呼叫<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>。 這些成員不會變更錯誤程式碼，而且有助於決定是否成功的某些平台叫用方法呼叫。  
  
-   <xref:System.IntPtr.Zero?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，呼叫移至<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>，讓它緊接在後面的呼叫平台叫用方法。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 安全地隱藏此規則的警告，如果平台之間的程式碼叫用方法呼叫和<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>方法呼叫不明確或隱含的方式會導致的錯誤程式碼變更。  
  
## <a name="example"></a>範例  
 下列範例顯示違反規則的方法和滿足規則的方法。  
  
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA1060： 將 P/Invokes 到 NativeMethods 類別](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400: P/Invoke 進入點應該要存在](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)  
  
 [CA1401: P/Invokes 不應該為可見](../code-quality/ca1401-p-invokes-should-not-be-visible.md)  
  
 [Ca2101： 必須指定 P/Invoke 字串引數的封送處理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
 [CA2205：必須使用 Win32 API 的 Managed 對應項](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)