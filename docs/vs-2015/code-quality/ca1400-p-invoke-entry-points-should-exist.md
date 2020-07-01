---
title: CA1400： P-Invoke 進入點應該存在 |Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 15b63e49f89e17db631772c48765cc610f47ed29
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548300"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400：P/Invoke 進入點應該要存在
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|類別|Microsoft. 互通性|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 公用或受保護的方法會以標記 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 。 有可能是找不到 Unmanaged 程式庫，或是方法不符合程式庫中的函式。 如果規則找不到完全依照指定的方法名稱，它會藉由使用 ' A ' 或 ' W ' suffixing 方法名稱，尋找該方法的 ANSI 或寬字元版本。 如果找不到相符的結果，規則會嘗試使用 __stdcall 名稱格式（ _MyMethod@12 ，其中12代表引數的長度）來尋找函式。 如果找不到相符的，而且方法名稱是以 ' # ' 開頭，此規則就會搜尋函數做為序數參考，而不是名稱參考。

## <a name="rule-description"></a>規則描述
 沒有任何編譯時間檢查可確保以標記的方法 <xref:System.Runtime.InteropServices.DllImportAttribute> 位於參考的非受控 DLL 中。 如果程式庫中沒有具有指定名稱的函式，或方法的引數不符合函式引數，則 common language runtime 會擲回例外狀況。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請更正具有屬性的方法 <xref:System.Runtime.InteropServices.DllImportAttribute> 。 請確定非受控程式庫存在，而且與包含方法的元件位於相同的目錄中。 如果程式庫存在且正確地參考，請確認方法名稱、傳回類型和引數簽章是否符合程式庫函式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當非受控程式庫位於與參考它的 managed 元件相同的目錄中時，請勿隱藏此規則的警告。 在找不到非受控程式庫的情況下，可能可以安全地隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的類型。 未命名的函式 `DoSomethingUnmanaged` 會在 kernel32.dll 中發生。

 [!code-csharp[FxCop.Interoperability.DLLExists#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DLLExists/cs/FxCop.Interoperability.DLLExists.cs#1)]

## <a name="see-also"></a>另請參閱
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>
