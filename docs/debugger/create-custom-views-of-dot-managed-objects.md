---
title: 建立受管理物件的自訂檢視 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data types [C#], custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6be491a5c7a0ceb0ed536416cdd3b273f96b4bb1
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="create-custom-views-of-managed-objects"></a>建立受管理物件的自訂檢視
您可以自訂 Visual Studio 在偵錯工具變數視窗中顯示資料型別的方式。  
  
## <a name="attributes"></a>屬性  
 在 C# 和 Visual Basic 中，您可以使用 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>、<xref:System.Diagnostics.DebuggerDisplayAttribute> 和 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 加入自訂資料的擴充功能。  
  
 在 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] 程式碼中，Visual Basic 不支援 DebuggerBrowsable 屬性。 最新版的 .NET Framework 中已移除此限制。  
  
## <a name="visualizers"></a>視覺化工具  
 您可以撰寫視覺化檢視以顯示任何 Managed 資料型別。 如需詳細資訊，請參閱[How to： 撰寫視覺化檢視](../debugger/how-to-write-a-visualizer.md)。  
  
## <a name="native-code"></a>機器碼  
 針對機器碼，您可以將自訂資料型別擴充功能加入至 autoexp.dat 檔，其位於 Program Files\Microsoft Visual Studio 11.0\Common7\Packages\Debugger 目錄中。 如何撰寫 `autoexp` 規則的指令位於檔案本身中。  
  
> [!CAUTION]
>  這個檔案的結構和 autoexp 規則語法可能因 Visual Studio 發行版本不同而有所差異。  
  
 您也可以透過撰寫運算式評估工具增益集來自訂原生型別檢視。 如需詳細資訊，請參閱[EEAddIn 範例： 偵錯運算式評估工具增益集](http://msdn.microsoft.com/en-us/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 DebuggerTypeProxy 屬性](../debugger/using-debuggertypeproxy-attribute.md)   
 [使用 DebuggerDisplay 屬性](../debugger/using-the-debuggerdisplay-attribute.md)   
 [監看式和快速監看式視窗](../debugger/watch-and-quickwatch-windows.md)   
 [使用偵錯工具顯示屬性增強偵錯功能](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)