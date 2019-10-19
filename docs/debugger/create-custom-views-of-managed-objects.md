---
title: 建立受控物件的自訂視圖 |Microsoft Docs
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3d75193368188efc660391d1e80c562ed881324b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578038"
---
# <a name="create-custom-views-of-managed-objects-c-visual-basic-f-ccli"></a>建立受控物件的自訂視圖C#（、Visual Basic F#、 C++、/cli）
您可以自訂 Visual Studio 在偵錯工具變數視窗中顯示資料型別的方式。

## <a name="attributes"></a>屬性

在C#中，Visual Basic F#、和C++ （C++僅限/cli 程式碼），您可以使用 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>、<xref:System.Diagnostics.DebuggerDisplayAttribute> 和 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 來新增自訂資料的擴充。

在 .NET Framework 2.0 程式碼中，Visual Basic 不支援 DebuggerBrowsable 屬性。 這項限制已在較新版本的 .NET 中移除。

## <a name="visualizers"></a>視覺化工具

您可以撰寫視覺化檢視以顯示任何 Managed 資料型別。 如需詳細資訊，請參閱[如何：撰寫視覺化](/visualstudio/debugger/create-custom-visualizers-of-data)程式。

> [!NOTE]
> 針對C++程式碼，您可以使用 Natvis 架構來加入自訂資料類型擴充，如在[偵錯工具中C++建立物件的自訂視圖](/visualstudio/debugger/create-custom-views-of-native-objects)中所述。

## <a name="see-also"></a>請參閱

- [使用 DebuggerDisplay 屬性告訴偵錯工具要顯示的內容](../debugger/using-the-debuggerdisplay-attribute.md)
- [使用 DebuggerTypeProxy 屬性告訴偵錯工具要顯示的類型](../debugger/using-debuggertypeproxy-attribute.md)
- [監看式及快速監看式視窗](../debugger/watch-and-quickwatch-windows.md)
- [使用偵錯工具顯示屬性增強偵錯功能](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
