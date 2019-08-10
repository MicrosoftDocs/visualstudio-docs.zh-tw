---
title: CA1404:必須在 P-Invoke 之後立即呼叫 GetLastError
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 03add1625c4d59bb180f9f0f08692e67bee8047b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922070"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404:必須在 P/Invoke 之後立即呼叫 GetLastError

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|分類|Microsoft.Interoperability|
|中斷變更|不中斷|

## <a name="cause"></a>原因

對<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName>方法或對等的 Win32 `GetLastError`函式進行呼叫, 而緊接在前面的呼叫不是平台叫用方法。

## <a name="rule-description"></a>規則描述
平台叫用方法會存取未受管理的程式碼, 並`Declare`使用中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]的關鍵字<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>或屬性來定義。 一般來說, 在失敗時, 非受控函式`SetLastError`會呼叫 Win32 函數來設定與失敗相關聯的錯誤碼。 Failed 函式的呼叫端會呼叫 Win32 `GetLastError`函式來抓取錯誤碼, 並判斷失敗的原因。 錯誤碼是以每個執行緒為基礎進行維護, 並會在下一次呼叫`SetLastError`時覆寫。 呼叫失敗的平台叫用方法之後, managed 程式碼就可以藉由呼叫<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>方法來捕獲錯誤碼。 由於錯誤碼可以由其他 managed 類別庫方法的內部呼叫覆寫, `GetLastError`因此應該在平台叫用方法呼叫之後立即呼叫或<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>方法。

當呼叫平台叫用方法與呼叫<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>時, 此規則會忽略下列 managed 成員的呼叫。 這些成員不會變更錯誤碼, 而且適用于判斷某些平台叫用方法呼叫是否成功。

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規, 請將呼叫移<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>至, 使其緊接在呼叫平台叫用方法之後。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
如果平台叫用方法呼叫和<xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>方法呼叫之間的程式碼無法明確或隱含地導致錯誤碼變更, 就可以放心地隱藏此規則的警告。

## <a name="example"></a>範例
下列範例顯示違反規則的方法, 以及符合規則的方法。

[!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
[!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]

## <a name="related-rules"></a>相關規則
[CA1060將 P/Invoke 移至 NativeMethods 類別](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

[CA1400P/Invoke 進入點應該存在](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

[CA1401P/Invoke 不應為可見](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

[CA2101 必須指定 P/Invoke 字串引數的封送處理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

[CA2205 必須使用 WIN32 API 的受控對等專案](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)