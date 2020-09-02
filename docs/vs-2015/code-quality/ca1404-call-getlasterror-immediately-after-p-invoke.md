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
ms.openlocfilehash: 54ac9a4d56136d9e981ae038a0b219aa4cb4774e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544491"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404：必須在 P/Invoke 之後立即呼叫 GetLastError
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|類別|Microsoft. 互通性|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 對 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> 方法或對等的 Win32 函式進行呼叫 `GetLastError` ，而緊接在之前的呼叫不是平台叫用方法。

## <a name="rule-description"></a>規則描述
 平台叫用方法會存取非受控碼，而且是使用 `Declare` 中的關鍵字 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 或屬性來定義 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 。 一般來說，當失敗時，非受控函 `SetLastError` 式會呼叫 Win32 函數來設定與失敗相關聯的錯誤碼。 失敗函式的呼叫端會呼叫 Win32 函式 `GetLastError` 來取得錯誤碼，並判斷失敗的原因。 錯誤碼是依每個執行緒來維護，並且會在下一次呼叫時覆寫 `SetLastError` 。 呼叫失敗的平台叫用方法之後，managed 程式碼可以藉由呼叫方法來取得錯誤碼 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> 。 由於錯誤碼可由其他 managed 類別庫方法的內部呼叫覆寫，因此應該在 `GetLastError` <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> 平台叫用方法呼叫之後立即呼叫或方法。

 當呼叫平台叫用方法與呼叫時，規則會忽略下列 managed 成員的呼叫 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> 。 這些成員不會變更錯誤碼，而且很適合用來判斷某些平台叫用方法呼叫是否成功。

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將呼叫移至， <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> 使其緊接在對平台叫用方法的呼叫之後。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果平台叫用方法呼叫和方法呼叫之間的程式碼 <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> 無法明確或隱含地導致錯誤碼變更，則可以放心地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的方法，以及滿足規則的方法。

 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/cs/FxCop.Interoperability.LastErrorPInvoke.cs#1)]
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/vb/FxCop.Interoperability.LastErrorPInvoke.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1060：將 P/Invoke 移至 NativeMethods 類別](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400： P/Invoke 進入點應該存在](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401： P/Invoke 不應該為可見的](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101 必須：指定 P/Invoke 字串引數的封送處理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205:必須使用 Win32 API 的受控對應項](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)
