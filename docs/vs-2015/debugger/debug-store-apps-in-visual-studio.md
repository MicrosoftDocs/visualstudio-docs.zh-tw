---
title: Debug Store 應用程式
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 48a85bcf-290b-4390-9993-f6f9dd73ad03
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6bc2d05c6b6aae4b2f33d135c6859da7b17de963
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533155"
---
# <a name="debug-store-apps-in-visual-studio"></a>在 Visual Studio 中偵錯市集應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 偵錯工具讓您能控制程式的執行，以及檢查其狀態。 您可以使用偵錯工具，找出 Windows 市集應用程式的缺失原因，以及了解您應用程式的確切工作情形。 當您在偵錯工具裡暫停 (中斷) 執行時，Visual Studio 會顯示包含執行中程式碼的原始程式檔，並反白顯示執行中的陳述式。 您可以查看變數的值、執行中函式的呼叫堆疊，以及程式狀態的其他層面。 您可以一次一個陳述式地繼續執行 (逐步執行) 程式，查看陳述式如何變更程式的值。 在以 JavaScript 撰寫的應用程式中，您可以檢查和操作頁面的 DOM。

## <a name="in-this-section"></a>本節內容

|Title|描述|
|-|-|
|[啟動偵錯工作階段 (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md)|如何開始偵錯工作階段，說明設定和開始 JavaScript 應用程式偵錯工作階段的不同選項。|
|[在偵錯工作階段中控制執行 (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)|偵錯工具巡覽帶領您完成簡單的應用程式，示範如何開始和停止偵錯、如何在程式碼中巡覽，以及如何檢視程式狀態。|
|[快速入門：偵錯 HTML 和 CSS](../debugger/quickstart-debug-html-and-css.md)|偵錯 HTML 和 CSS 顯示如何使用即時 DOM 檢查工具檢視和修改 HTML 和 CSS，以便互動式地偵錯 JavaScript 應用程式。|
|[快速入門：偵錯 JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md)|使用主控台的 Debug JavaScript 會示範如何使用[JAVAscript 主控台命令](../debugger/javascript-console-commands.md)，以互動方式進行 javascript 應用程式的偵錯工具。|
|[啟動偵錯工作階段 (VB、C#、C++ 和 XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)|如何開始偵錯工作階段 (Visual C++、Visual C# 和 Visual Basic)，說明設定和開始使用 Visual C++、Visual C# 或 Visual Basic 撰寫之應用程式偵錯工作階段的不同選項。|
|[巡覽偵錯工作階段 (Xaml 和 C#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)|偵錯工具巡覽帶領您完成簡單的應用程式，示範如何開始和停止偵錯、如何在程式碼中巡覽，以及如何檢視和變更程式狀態。|
|[觸發 Microsoft Store 的暫止、繼續和背景事件](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)|偵錯工具會停用暫停、繼續和終止應用程式的 Windows 處理程序生命週期管理 (PLM) 事件。 您可以從 [偵錯工具] 工具列觸發這些事件。<br /><br /> 背景工作可讓您執行重要的作業 (即使您的應用程式已暫停也無妨)。 偵錯工具讓您能開始這些背景工作和對它們進行偵錯。|

## <a name="see-also"></a>另請參閱
 [在 Visual Studio 中偵錯 (MSDN Library 中)](https://msdn.microsoft.com/library/sc65sadd(VS.110).aspx)
