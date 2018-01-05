---
title: "Ca2205： 必須使用受管理的 Win32 API 的對等項目 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: ea1c408e524614009c8c12bda85afad397faf607
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205：必須使用 Win32 API 的 Managed 對應項
|||  
|-|-|  
|TypeName|UseManagedEquivalentsOfWin32Api|  
|CheckId|CA2205|  
|分類|Microsoft.Usage|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 平台叫用方法定義，且具有對等功能的方法有在[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]類別庫。  
  
## <a name="rule-description"></a>規則描述  
 平台叫用方法用於呼叫 unmanaged 的 DLL 函式，並使用定義<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>屬性，或`Declare`在 Visual Basic 中的關鍵字。 定義不正確的平台叫用方法可能會導致執行階段例外狀況因為有問題，例如命名函數，故障的參數和傳回的數值資料類型和不正確的欄位規格，例如呼叫慣例和字元對應設定。 如果有的話，通常是比較簡單且較少出錯呼叫比定義並直接呼叫 unmanaged 的方法等的 managed 的方法。 呼叫平台叫用的方法也會造成需要處理的額外的安全性問題。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請呼叫 unmanaged 函式取代其受管理的對等的呼叫。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 如果建議的取代方法未提供必要的功能，則隱藏此規則的警告。  
  
## <a name="example"></a>範例  
 下列範例顯示的平台叫用違反規則的方法定義。 此外，呼叫平台叫用方法，並顯示對等的 managed 的方法。  
  
 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]  
  
## <a name="related-rules"></a>相關的規則  
 [Ca1404： 必須在 P/Invoke 之後立即呼叫 GetLastError](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)  
  
 [CA1060： 將 P/Invokes 到 NativeMethods 類別](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400: P/Invoke 進入點應該要存在](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)  
  
 [CA1401: P/Invokes 不應該為可見](../code-quality/ca1401-p-invokes-should-not-be-visible.md)  
  
 [Ca2101： 必須指定 P/Invoke 字串引數的封送處理](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)