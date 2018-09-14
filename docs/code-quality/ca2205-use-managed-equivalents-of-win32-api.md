---
title: CA2205：必須使用 Win32 API 的 Managed 對應項
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 0d9ae35155009e43678aca89e388ebac721a5724
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551236"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205：必須使用 Win32 API 的 Managed 對應項

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|類別|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因

平台叫用方法定義，且具有對等功能的方法存在於[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]類別庫。

## <a name="rule-description"></a>規則描述

平台叫用的方法用來呼叫 unmanaged 的 DLL 函式，並使用<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>屬性，或`Declare`Visual Basic 中的關鍵字。 不正確地定義的平台叫用方法可能會導致執行階段例外狀況因為問題，例如命名函式，錯誤的參數和傳回數值資料類型，並不正確的欄位規格，例如呼叫慣例和字元對應設定。 如果有的話，就更簡單且較少出錯呼叫的對等的 managed 的方法，若要定義，並直接呼叫 unmanaged 的方法比。 呼叫平台叫用的方法也會造成需要處理的額外的安全性問題。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，以呼叫 unmanaged 函式的呼叫取代為其受管理的對等。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果建議的取代方法不會提供所需的功能，則隱藏此規則的警告。

## <a name="example"></a>範例

下列範例示範的平台叫用違反規則的方法定義。 此外，呼叫平台叫用方法，並顯示對等的 managed 的方法。

[!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
[!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]

## <a name="related-rules"></a>相關的規則

- [CA1404：在 P/Invoke 之後立即呼叫 GetLastError](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)
- [CA1060：將 P/Invokes 移到 NativeMethods 類別](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)
- [CA1400：P/Invoke 進入點應該存在](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)
- [CA1401：不應顯示 P/Invokes](../code-quality/ca1401-p-invokes-should-not-be-visible.md)
- [CA2101：指定 P/Invoke 字串引數的封送處理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)