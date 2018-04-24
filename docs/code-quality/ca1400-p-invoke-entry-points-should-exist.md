---
title: 'CA1400: P Invoke 進入點應該要存在'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 125a9d93085cd82e32dd08a053fdaa98cc1af5cf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400：P/Invoke 進入點應該要存在
|||
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|分類|Microsoft.Interoperability|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 公用或受保護的方法會標示<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>。 有可能是找不到 Unmanaged 程式庫，或是方法不符合程式庫中的函式。 如果規則在完全依照其指定找不到方法名稱，它會尋找 ANSI 或寬字元版本的方法所尾碼 'A' 或 'W' 的方法名稱。 如果找到相符項目，此規則會嘗試尋找函式使用 __stdcall 名稱格式 (_MyMethod@12，其中 12 代表引數的長度)。 如果沒有找到符合的而且以 '#' 開頭的方法名稱，此規則中搜尋函式做為序數的參考，而非名稱參考。

## <a name="rule-description"></a>規則描述
 不會產生編譯時期檢查可確定方法是，標示<xref:System.Runtime.InteropServices.DllImportAttribute>位於受參考的 unmanaged DLL。 如果沒有具有指定的名稱的函式程式庫，或方法的引數不相符的函式引數，common language runtime 會擲回例外狀況。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，更正方法<xref:System.Runtime.InteropServices.DllImportAttribute>屬性。 請確定將 unmanaged 程式庫存在且包含方法的組件相同的目錄中。 如果媒體櫃已存在且正確的參考，請確認的方法名稱、 傳回型別和引數簽章符合程式庫函式。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 Unmanaged 程式庫參考它的 managed 組件相同的目錄時，請勿隱藏此規則的警告。 它可能安全地隱藏在案例中，unmanaged 程式庫找不到此規則的警告。

## <a name="example"></a>範例
 下列範例顯示違反規則的類型。 函式，名為`DoSomethingUnmanaged`kernel32.dll 中發生。

 [!code-csharp[FxCop.Interoperability.DLLExists#1](../code-quality/codesnippet/CSharp/ca1400-p-invoke-entry-points-should-exist_1.cs)]

## <a name="see-also"></a>另請參閱
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>