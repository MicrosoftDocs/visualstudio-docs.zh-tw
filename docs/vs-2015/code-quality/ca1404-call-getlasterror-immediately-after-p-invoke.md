---
title: CA1404 必須：在 P-Invoke 之後立即呼叫 GetLastError |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2664837c17894f7ca336d650a7e08e21c45d955f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661317"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404：必須在 P/Invoke 之後立即呼叫 GetLastError
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Category|Microsoft. 互通性|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 對 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> 方法或對等的 Win32 `GetLastError` 函式進行呼叫，而緊接在前面的呼叫不是平台叫用方法。

## <a name="rule-description"></a>規則描述
 平台叫用方法會存取未受管理的程式碼，並使用 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 中的 `Declare` 關鍵字或 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 屬性來定義。 一般來說，在失敗時，非受控函式會呼叫 Win32 `SetLastError` 函數來設定與失敗相關聯的錯誤碼。 Failed 函式的呼叫端會呼叫 Win32 `GetLastError` 函數來取得錯誤碼，並判斷失敗的原因。 錯誤碼是以每個執行緒為基礎進行維護，並會在下一次呼叫 `SetLastError` 時覆寫。 呼叫失敗的平台叫用方法之後，managed 程式碼可以藉由呼叫 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> 方法來抓取錯誤碼。 由於錯誤碼可以由其他 managed 類別庫方法的內部呼叫覆寫，因此應該在平台叫用方法呼叫之後立即呼叫 `GetLastError` 或 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> 方法。

 此規則會在呼叫平台叫用方法與 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> 的呼叫之間發生時，忽略下列 managed 成員的呼叫。 這些成員不會變更錯誤碼，而且適用于判斷某些平台叫用方法呼叫是否成功。

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請將呼叫移至 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>，讓它緊接在呼叫平台叫用方法之後。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果平台叫用方法呼叫和 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> 方法呼叫之間的程式碼無法明確或隱含地導致錯誤碼變更，則隱藏此規則的警告是安全的。

## <a name="example"></a>範例
 下列範例顯示違反規則的方法，以及符合規則的方法。

 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/cs/FxCop.Interoperability.LastErrorPInvoke.cs#1)]
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/vb/FxCop.Interoperability.LastErrorPInvoke.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1060：將 P/Invokes 移到 NativeMethods 類別](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400：P/Invoke 進入點應該存在](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401：不應顯示 P/Invokes](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101：指定 P/Invoke 字串引數的封送處理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205：必須使用 Win32 API 的 Managed 對應項](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)
