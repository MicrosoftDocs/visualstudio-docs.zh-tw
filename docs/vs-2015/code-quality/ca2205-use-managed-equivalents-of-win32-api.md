---
title: CA2205 必須：使用 WIN32 API 的受控對等專案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 85e27ab04ca81f5513a0b09bc41548f4a7c2430d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547676"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205:必須使用 Win32 API 的受控對應項
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|類別|Microsoft。使用方式|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 已定義平台叫用方法，且類別庫中存在具有對等功能的方法 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 。

## <a name="rule-description"></a>規則描述
 平台叫用方法是用來呼叫非受控 DLL 函式，並使用 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 屬性（attribute）或 `Declare` 中的關鍵字（在 Visual Basic 中）來定義。 定義不正確的平台叫用方法可能會導致執行時間例外狀況，因為有 misnamed 函式、錯誤的參數和傳回值資料類型對應，以及不正確的欄位規格（例如呼叫慣例和字元集）等問題。 如果可用，通常比直接定義和呼叫非受控方法更簡單，而且呼叫對等 managed 方法的錯誤較少。 呼叫平台叫用方法也可能導致需要解決的其他安全性問題。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將非受控函式的呼叫取代為其受管理的對等的呼叫。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果建議的取代方法未提供所需的功能，請隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的平台叫用方法定義。 此外，也會顯示平台叫用方法和對等 managed 方法的呼叫。

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/cs/FxCop.Usage.ManagedEquivalents.cs#1)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/vb/FxCop.Usage.ManagedEquivalents.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1404 必須：在 P/Invoke 之後立即呼叫 GetLastError](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060：將 P/Invoke 移至 NativeMethods 類別](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400： P/Invoke 進入點應該存在](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401： P/Invoke 不應為可見](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101 必須：指定 P/Invoke 字串引數的封送處理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)
