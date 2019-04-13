---
title: 建立物件的自訂檢視 |Microsoft Docs
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
ms.openlocfilehash: 733f3ec7573287e934f8a5f0167db89c0683759a
ms.sourcegitcommit: cd91a8a4f6086cda9ba6948be25864fc7d6b8e44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59537474"
---
# <a name="create-custom-views-of-objects-c-visual-basic-c"></a>建立自訂檢視的物件 (C#，Visual Basic 中， C++)
您可以自訂 Visual Studio 在偵錯工具變數視窗中顯示資料型別的方式。

## <a name="native-code"></a>機器碼

針對C++程式碼中，您可以新增使用 Natvis 架構中，自訂資料型別擴充，如中所述[建立的自訂檢視C++偵錯工具中的物件](/visualstudio/debugger/create-custom-views-of-native-objects)。 針對C++/CLI 程式碼中，您也可以使用此處所述，在這篇文章中的屬性。

## <a name="attributes"></a>屬性

在C#，Visual Basic 和C++(C++僅限 /CLI 程式碼)，您可以新增自訂資料使用的擴充<xref:System.Diagnostics.DebuggerTypeProxyAttribute>， <xref:System.Diagnostics.DebuggerDisplayAttribute>，和<xref:System.Diagnostics.DebuggerBrowsableAttribute>。

在 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] 程式碼中，Visual Basic 不支援 DebuggerBrowsable 屬性。 最新版的 .NET Framework 中已移除此限制。

## <a name="visualizers"></a>視覺化工具

您可以撰寫視覺化檢視以顯示任何 Managed 資料型別。 如需詳細資訊，請參閱[如何：撰寫視覺化檢視](/visualstudio/debugger/create-custom-visualizers-of-data)。

## <a name="see-also"></a>另請參閱

- [告知偵錯工具要顯示使用 DebuggerDisplay 屬性](../debugger/using-the-debuggerdisplay-attribute.md)
- [告知偵錯工具類型以顯示使用 DebuggerTypeProxy 屬性](../debugger/using-debuggertypeproxy-attribute.md)
- [監看式及快速監看式視窗](../debugger/watch-and-quickwatch-windows.md)
- [使用偵錯工具顯示屬性增強偵錯功能](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)