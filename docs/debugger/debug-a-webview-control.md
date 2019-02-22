---
title: 偵錯 WebView 控制項 (UWP) |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 4945515def65a0a1a363e6ba6cd76ca411dc6d6f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009036"
---
# <a name="debug-a-webview-control-in-a-uwp-app"></a>偵錯 WebView 控制項在 UWP 應用程式
  
 若要在 Windows 執行階段應用程式中檢查及偵錯 `WebView` 控制項，您可以設定 Visual Studio 在您啟動應用程式時附加指令碼偵錯工具。 您有兩種方式可互動`WebView`控制使用偵錯工具：  
  
-   開啟 `WebView` 執行個體的 [DOM 總管][](../debugger/quickstart-debug-html-and-css.md)，然後檢查 DOM 元素、調查 CSS 樣式問題，並測試動態呈現的樣式變更。  
  
-   選取 `WebView` 執行個體中顯示的網頁或 `iFrame`，作為 [JavaScript Console][](../debugger/javascript-console-commands.md) 視窗中的目標，然後使用主控台命令與網頁互動。 主控台提供對於目前指令碼執行內容的存取。  
  
### <a name="attach-the-debugger-c-visual-basic-c"></a>附加偵錯工具 (C#、Visual Basic、C++)  
  
1.  在 Visual Studio 中，將 `WebView` 控項項加入 Windows 執行階段元件。  
  
2.  在 [方案總管] 中，從專案的捷徑功能表選擇 [屬性]，即可開啟專案的屬性。  
  
3.  選擇 [偵錯]。 在 [應用程式程序] 清單中，選擇 [指令碼]。  
  
     ![附加 script 偵錯工具](../debugger/media/js_dom_webview_script_debugger.png "JS_DOM_WebView_Script_Debugger")  
  
4.  (選擇性) 若為非 Express 版本的 Visual Studio，依序選擇 [工具] > [選項] > [偵錯] > [Just-In-Time]，然後停用指令碼的 Just-In-Time (JIT) 偵錯，以停用 JIT 偵錯。  
  
    > [!NOTE]
    >  藉由停用 JIT 偵錯，您可以隱藏在部分網頁上發生之未處理例外的對話方塊。 在 Visual Studio Express 中，一律停用 JIT 偵錯。  
  
5.  按 F5 鍵啟動偵錯作業。  
  
### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>使用 [DOM 總管] 檢查及偵錯 WebView 控制項  
  
1.  (C#、Visual Basic、C++) 將指令碼偵錯工具附加到應用程式。 請參閱第一節裡的指示。  
  
2.  如果您尚未這麼做，請將 `WebView` 控制項加入到應用程式，然後按 F5 開始偵錯。  
  
3.  巡覽到包含 `Webview` 控制項的頁面。  
  
4.  開啟的 DOM 總管 視窗`WebView`選擇的控制項**偵錯**， **Windows**， **DOM 總管**，然後選擇 URL`WebView`您要檢查。  
  
     ![開啟 [DOM 總管]](../debugger/media/js_dom_webview.png "JS_DOM_WebView")  
  
     與 `WebView` 相關的 [DOM 總管] 會顯示為 Visual Studio 中的新索引標籤。  
  
5.  檢視及修改動態 DOM 項目和 CSS 樣式中所述[使用 DOM 總管偵錯 CSS 樣式](/visualstudio/debugger/quickstart-debug-html-and-css)。  
  
### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>使用 [JavaScript 主控台] 視窗檢查及偵錯 WebView 控制項  
  
1.  (C#、Visual Basic、C++) 將指令碼偵錯工具附加到應用程式。 請參閱第一節裡的指示。  
  
2.  如果您尚未這麼做，請將 `WebView` 控制項加入到應用程式，然後按 F5 開始偵錯。  
  
3.  開啟 [JavaScript 主控台] 視窗，如`WebView`選擇的控制項**偵錯**， **Windows**， **JavaScript 主控台**。  
  
     隨即顯示 [JavaScript 主控台] 視窗。  
  
4.  巡覽到包含 `Webview` 控制項的頁面。  
  
5.  在主控台視窗中，選取 網頁或`iFrame`來顯示`WebView`控制中**目標**清單。  
  
     ![目標 [JavaScript 主控台] 視窗中的選取項目](../debugger/media/js_console_target.png "JS_Console_Target")  
  
    > [!NOTE]
    >  使用主控台，您可以一次與單一 `WebView`、`iFrame`、共用連絡人或 Web 背景工作互動。 每個項目需要個別的 Web 平台主機 (WWAHost.exe) 執行個體。 您一次可以與一個主機互動。  
  
6.  檢視及修改您的應用程式中的變數或使用主控台命令中所述[快速入門：偵錯 JavaScript](../debugger/quickstart-debug-javascript-using-the-console.md)並[JavaScript Console commands](../debugger/javascript-console-commands.md)。  
  
## <a name="see-also"></a>請參閱  
 [快速入門：對 HTML 和 CSS 進行偵錯](../debugger/quickstart-debug-html-and-css.md)