---
title: CA1404：必須在 P/Invoke 之後立即呼叫 GetLastError
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4e9a339a4b665f892c3e3e63c77ba0dee5891df8
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45552038"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404：必須在 P/Invoke 之後立即呼叫 GetLastError

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|類別|Microsoft.Interoperability|
|中斷變更|非重大|

## <a name="cause"></a>原因

進行呼叫，以<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName>方法或對等的 Win32`GetLastError`函式，並且出現前立即呼叫不到平台叫用方法。

## <a name="rule-description"></a>規則描述
 平台叫用方法存取 unmanaged 程式碼，並使用定義`Declare`中的關鍵字[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]或<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>屬性。 通常，發生錯誤時，unmanaged 函式會呼叫 Win32`SetLastError`函式來設定失敗相關聯的錯誤碼。 呼叫端的失敗函式會呼叫 Win32`GetLastError`函式來擷取錯誤碼，並判斷失敗的原因。 會維護每個執行緒為基礎的錯誤碼，以及下一個呼叫會覆寫`SetLastError`。 Managed 程式碼的呼叫失敗的平台叫用方法之後，可以呼叫來擷取錯誤碼<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>方法。 因為內部呼叫其他 managed 的類別程式庫方法，將會覆寫的錯誤碼`GetLastError`或<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>方法應該在平台叫用方法呼叫之後立即呼叫。

 此規則會忽略下列呼叫受管理的成員，在平台的呼叫之間發生時叫用方法，並呼叫<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>。 這些成員不會變更錯誤程式碼，而且有助於決定成功的某些平台叫用方法呼叫。

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，呼叫移到<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>，讓它緊接在後面的呼叫平台叫用方法。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可安全地隱藏此規則的警告，如果平台之間的程式碼叫用方法呼叫和<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>方法呼叫不明確或隱含的方式會導致錯誤程式碼變更。

## <a name="example"></a>範例
 下列範例顯示違反規則方法，並符合規則的方法。

 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]

## <a name="related-rules"></a>相關的規則
 [CA1060：將 P/Invokes 移到 NativeMethods 類別](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400：P/Invoke 進入點應該存在](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401：不應顯示 P/Invokes](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101：指定 P/Invoke 字串引數的封送處理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205：必須使用 Win32 API 的 Managed 對應項](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)