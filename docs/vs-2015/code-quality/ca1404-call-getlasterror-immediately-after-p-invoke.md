---
title: CA1404:在 P-invoke 之後立即呼叫 GetLastError |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e33c724d2cebb9423f2e475d95bf42ac5e2cc966
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200308"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404:必須在 P/Invoke 之後立即呼叫 GetLastError
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|分類|Microsoft.Interoperability|
|中斷變更|非重大|

## <a name="cause"></a>原因
 進行呼叫，以<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName>方法或對等的 Win32`GetLastError`函式，並且出現前立即呼叫不到平台叫用方法。

## <a name="rule-description"></a>規則描述
 平台叫用方法存取 unmanaged 程式碼，並使用定義`Declare`中的關鍵字[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]或<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>屬性。 通常，發生錯誤時，unmanaged 函式會呼叫 Win32`SetLastError`函式來設定失敗相關聯的錯誤碼。 呼叫端的失敗函式會呼叫 Win32`GetLastError`函式來擷取錯誤碼，並判斷失敗的原因。 會維護每個執行緒為基礎的錯誤碼，以及下一個呼叫會覆寫`SetLastError`。 Managed 程式碼的呼叫失敗的平台叫用方法之後，可以呼叫來擷取錯誤碼<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>方法。 因為內部呼叫其他 managed 的類別程式庫方法，將會覆寫的錯誤碼`GetLastError`或<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>方法應該在平台叫用方法呼叫之後立即呼叫。

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

 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/cs/FxCop.Interoperability.LastErrorPInvoke.cs#1)]
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/vb/FxCop.Interoperability.LastErrorPInvoke.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA1060:將 P/Invokes 移到 NativeMethods 類別](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400:P/Invoke 進入點應該要存在](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401:P/Invokes 不應該為可見](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101： 必須指定的 P/Invoke 字串引數封送處理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205： 必須使用 Win32 API 的 managed 對等項目](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)
