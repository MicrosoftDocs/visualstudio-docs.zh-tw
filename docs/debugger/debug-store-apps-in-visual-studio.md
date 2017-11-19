---
title: "偵錯 Visual Studio 中的 UWP 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 48a85bcf-290b-4390-9993-f6f9dd73ad03
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3920bfbd5b1ddbddc3166118ead0c7d0fefff8d8
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2017
---
# <a name="debug-uwp-apps-in-visual-studio"></a>偵錯 Visual Studio 中的 UWP 應用程式
Visual Studio 偵錯工具讓您能控制程式的執行，以及檢查其狀態。 在 UWP 應用程式中尋找的缺失原因，以及了解只有您的應用程式的運作方式，您可以使用偵錯工具。 當您在偵錯工具裡暫停 (中斷) 執行時，Visual Studio 會顯示包含執行中程式碼的原始程式檔，並反白顯示執行中的陳述式。 您可以查看變數的值、執行中函式的呼叫堆疊，以及程式狀態的其他層面。 您可以一次一個陳述式地繼續執行 (逐步執行) 程式，查看陳述式如何變更程式的值。 在以 JavaScript 撰寫的應用程式中，您可以檢查和操作頁面的 DOM。  
  
## <a name="in-this-section"></a>本節內容  
  
|||  
|-|-|  
|[開始偵錯工作階段 (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md)|如何開始偵錯工作階段，說明設定和開始 JavaScript 應用程式偵錯工作階段的不同選項。|  
|[控制執行中的偵錯工作階段 (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)|偵錯工具巡覽帶領您完成簡單的應用程式，示範如何開始和停止偵錯、如何在程式碼中巡覽，以及如何檢視程式狀態。|  
|[快速入門：偵錯 HTML 和 CSS](../debugger/quickstart-debug-html-and-css.md)|偵錯 HTML 和 CSS 顯示如何使用即時 DOM 檢查工具檢視和修改 HTML 和 CSS，以便互動式地偵錯 JavaScript 應用程式。|  
|[快速入門： 偵錯 JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md)|使用主控台偵錯 JavaScript 顯示如何互動式地偵錯 JavaScript 應用程式使用[JavaScript 主控台命令](../debugger/javascript-console-commands.md)。|  
|[開始偵錯工作階段 （VB、 C#、 c + + 和 XAML）](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)|如何開始偵錯工作階段 (Visual C++、Visual C# 和 Visual Basic)，說明設定和開始使用 Visual C++、Visual C# 或 Visual Basic 撰寫之應用程式偵錯工作階段的不同選項。|  
|[巡覽偵錯工作階段 （Xaml 和 C#）](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)|偵錯工具巡覽帶領您完成簡單的應用程式，示範如何開始和停止偵錯、如何在程式碼中巡覽，以及如何檢視和變更程式狀態。|  
|[觸發暫停、 繼續及背景事件用於 UWP 應用程式)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)|偵錯工具會停用暫停、繼續和終止應用程式的 Windows 處理程序生命週期管理 (PLM) 事件。 您可以從 [偵錯工具] 工具列觸發這些事件。<br /><br /> 背景工作可讓您執行重要的作業 (即使您的應用程式已暫停也無妨)。 偵錯工具讓您能開始這些背景工作和對它們進行偵錯。|  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 偵錯](../debugger/index.md)  
 [偵錯工具功能的教學課程 (MSDN Library 中）](http://go.microsoft.com/fwlink/?LinkID=226896)