---
title: 使用 DebuggerTypeProxy 顯示自訂類型 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerTypeProxyAttribute class
- DebuggerTypeProxy attribute
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 091619353adacaeb9c6996653ac64a0bcd84bb5c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72568964"
---
# <a name="tell-the-debugger-what-type-to-show-using-debuggertypeproxy-attribute-c-visual-basic-ccli"></a>使用 DebuggerTypeProxy 屬性（C#，Visual Basic， C++/cli）告訴偵錯工具要顯示的類型

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> 會指定類型的 Proxy (或替代)，並且變更在偵錯工具視窗中顯示類型的方式。 當您檢視有 Proxy 的變數時，Proxy 會替代 [顯示] 中的原始類型。 偵錯工具變數視窗只會顯示 proxy 型別的 Public 成員。 私用成員不會顯示。

這個屬性可以套用至：

- 結構
- 類別
- 組件

> [!NOTE]
> 針對機器碼，只有C++/cli 程式碼才支援這個屬性。

類型 Proxy 類別必須具有建構函式，才能接受 Proxy 將取代之類型的引數。 每次需要顯示目標類型的變數時，偵錯工具都會建立類型 Proxy 類別的新執行個體。 這種行為可能會影響效能。 因此，除非絕對必要，否則不要在建構函式中再執行任何作業。

為了將效能的負面影響降到最低，除非使用者在偵錯工具視窗中按一下 + 符號展開類型或使用 <xref:System.Diagnostics.DebuggerBrowsableAttribute>，否則運算式評估工具不會檢查類型顯示 Proxy 的屬性。 因此，您不應該將屬性放在顯示類型本身上， 屬性可以而且應該用於顯示類型的主體中。

讓類型 Proxy 成為做為屬性目標之類別內的私用巢狀類別，會是較理想的做法。 這樣就可方便它存取內部成員。

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> 可以被繼承，所以如果在基類上指定了型別 proxy，它會套用至任何衍生的類別，除非這些衍生類別指定自己的型別 proxy。

如果在組件層級使用 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>，則 `Target` 參數會指定 Proxy 將要取代的類型。

如需如何搭配 <xref:System.Diagnostics.DebuggerDisplayAttribute> 和 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 使用此屬性的範例，請參閱[使用 DebuggerDisplay 屬性](../debugger/using-the-debuggerdisplay-attribute.md)。

## <a name="using-generics-with-debuggertypeproxy"></a>使用泛型搭配 DebuggerTypeProxy

對泛型僅提供有限的支援。 對 C# 來說，`DebuggerTypeProxy` 只支援開啟類型。 開啟類型也稱為未建構類型，是尚未使用其型別參數的引數具現化的泛型類型。 不支援封閉類型 (也稱為建構類型)。

開啟類型的語法如下所示：

`Namespace.TypeName<,>`

如果您在 `DebuggerTypeProxy` 中使用泛型類型做為目標，就必須使用此語法。 `DebuggerTypeProxy` 機制會自動推斷型別參數。

如需有關中C#的開啟和關閉類型的詳細資訊，請參閱[ C#語言規格](/dotnet/csharp/language-reference/language-specification)的

Visual Basic 沒有開放類型語法，因此無法在 Visual Basic 中執行相同的動作。 您必須改用開放類型名稱的字串表示。

`"Namespace.TypeName'2"`

## <a name="see-also"></a>請參閱

- [使用 DebuggerDisplay 屬性](../debugger/using-the-debuggerdisplay-attribute.md)
- [建立 Managed 物件的自訂檢視](../debugger/create-custom-views-of-managed-objects.md)
- [使用偵錯工具顯示屬性增強偵錯功能](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
