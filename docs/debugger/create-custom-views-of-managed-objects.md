---
title: 建立受控物件的自訂視圖 |Microsoft Docs
description: Visual Studio 偵錯工具會在變數視窗中顯示資料。 學習自訂如何顯示資料類型（包括自訂類型）。
ms.custom: SEO-VS-2020
ms.date: 01/08/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data types, custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c054d3bcfbb06d0093f04190ab8b4825b5cbf20f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865796"
---
# <a name="create-custom-views-of-managed-objects-c-visual-basic-f-ccli"></a>建立 managed 物件的自訂視圖 (c #、Visual Basic、F #、c + +/CLI) 
您可以自訂 Visual Studio 在偵錯工具變數視窗中顯示資料型別的方式。

## <a name="attributes"></a>屬性

在 c #、Visual Basic、F # 和 c + + 中 (c + +/CLI 程式碼僅) ，您可以使用、和來加入自訂資料的擴充 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> <xref:System.Diagnostics.DebuggerDisplayAttribute> <xref:System.Diagnostics.DebuggerBrowsableAttribute> 。

在 .NET Framework 2.0 程式碼中，Visual Basic 不支援 DebuggerBrowsable 屬性。 這項限制已在較新版本的 .NET 中移除。

## <a name="visualizers"></a>視覺化工具

您可以撰寫視覺化檢視以顯示任何 Managed 資料型別。 如需詳細資訊，請參閱 how [to：撰寫視覺化](create-custom-visualizers-of-data.md)程式。

> [!NOTE]
> 針對 c + + 程式碼，您可以使用 Natvis 架構加入自訂資料類型展開，如在 [偵錯工具中建立 c + + 物件的自訂視圖](create-custom-views-of-native-objects.md)所述。

## <a name="see-also"></a>另請參閱

- [使用 DebuggerDisplay 屬性告訴偵錯工具要顯示的內容](../debugger/using-the-debuggerdisplay-attribute.md)
- [使用 DebuggerTypeProxy 屬性告訴偵錯工具要顯示的類型](../debugger/using-debuggertypeproxy-attribute.md)
- [監看式及快速監看式視窗](../debugger/watch-and-quickwatch-windows.md)
- [使用偵錯工具顯示屬性增強偵錯功能](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
