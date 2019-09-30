---
title: CA2205:必須使用 Win32 API 的受控對應項
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ad26dcbbbef5a34796ca0aa134653c3c9df5d763
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253263"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205:必須使用 Win32 API 的受控對應項

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|分類|Microsoft.Usage|
|重大變更|不中斷|

## <a name="cause"></a>原因

已定義平台叫用方法，而且 .NET 中存在具有對等功能的方法。

## <a name="rule-description"></a>規則描述

平台叫用方法是用來呼叫非受控 DLL 函式，並使用<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>屬性（attribute）或中的`Declare`關鍵字（在 Visual Basic 中）來定義。 定義不正確的平台叫用方法可能會導致執行時間例外狀況，因為有 misnamed 函式、錯誤的參數和傳回值資料類型對應，以及不正確的欄位規格（例如呼叫慣例和字元）等問題設定. 如果有的話，呼叫對等的 managed 方法比直接定義和呼叫非受控方法更簡單且更少發生錯誤。 呼叫平台叫用方法也可能導致需要解決的其他安全性問題。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請將非受控函式的呼叫取代為其受管理的對等的呼叫。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果建議的取代方法未提供所需的功能，請隱藏此規則的警告。

## <a name="example"></a>範例

下列範例顯示違反規則的平台叫用方法定義。 此外，也會顯示平台叫用方法和對等 managed 方法的呼叫。

[!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
[!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]

## <a name="related-rules"></a>相關規則

- [CA1404 必須在 P/Invoke 之後立即呼叫 GetLastError](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)
- [CA1060將 P/Invoke 移至 NativeMethods 類別](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)
- [CA1400P/Invoke 進入點應該存在](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)
- [CA1401P/Invoke 不應為可見](../code-quality/ca1401-p-invokes-should-not-be-visible.md)
- [CA2101 必須指定 P/Invoke 字串引數的封送處理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)