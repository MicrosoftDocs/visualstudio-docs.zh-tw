---
title: CA1400:-Invoke 進入點應該要存在 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0e5696689d0aa40f4af2e11970c81b47737a3d80
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200378"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400:P/Invoke 進入點應該要存在
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|分類|Microsoft.Interoperability|
|中斷變更|非重大|

## <a name="cause"></a>原因
 公用或受保護的方法會標示<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>。 有可能是找不到 Unmanaged 程式庫，或是方法不符合程式庫中的函式。 如果此規則在完全依照其指定找不到方法名稱，它會尋找 ANSI 或寬字元版本的方法上使用 'A' 或 'W' 的方法名稱的尾碼。 如果找到相符項目，此規則會嘗試尋找函式使用 __stdcall 名稱格式 (_MyMethod@12，其中 12 代表引數的長度)。 如果找到相符項目，並以 '#' 開頭的方法名稱，此規則會搜尋函式做為序數的參考，而非名稱參考。

## <a name="rule-description"></a>規則描述
 任何編譯時期檢查可確定方法標記著<xref:System.Runtime.InteropServices.DllImportAttribute>參考 unmanaged DLL 中。 如果沒有具有指定的名稱的函式中程式庫，或是方法的引數不相符的函式引數，common language runtime 會擲回例外狀況。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，更正方法<xref:System.Runtime.InteropServices.DllImportAttribute>屬性。 請確定 unmanaged 程式庫是否存在，且包含方法的組件相同的目錄中。 如果存在且正確地參考程式庫，請確認方法名稱、 傳回型別和引數簽章符合程式庫函式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 與參考它的 managed 組件相同的目錄中的 unmanaged 程式庫時，請勿隱藏此規則的警告。 它可能是安全地隱藏在案例中，unmanaged 程式庫找不到此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的型別。 名為沒有函數`DoSomethingUnmanaged`kernel32.dll 中發生。

 [!code-csharp[FxCop.Interoperability.DLLExists#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DLLExists/cs/FxCop.Interoperability.DLLExists.cs#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>
