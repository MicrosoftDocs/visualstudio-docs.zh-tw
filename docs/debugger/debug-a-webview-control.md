---
title: " (UWP) 的 Web 工作控制項進行 Debug 錯 |Microsoft Docs"
description: 瞭解如何檢查和偵測 Windows 執行階段應用程式中所使用的 Web 程式控制項。 您可以使用 [DOM 總管] 和 [JavaScript 主控台] 視窗。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 7d105907-8b39-4d07-8762-5c5ed74c7f21
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: 5439f9f253126e159df5dd9ea58bad04c3f6c649
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560547"
---
# <a name="debug-a-webview-control-in-a-uwp-app"></a>在 UWP 應用程式中將 Web 程式控制項進行偵錯工具

 若要在 Windows 執行階段應用程式中檢查及偵錯 `WebView` 控制項，您可以設定 Visual Studio 在您啟動應用程式時附加指令碼偵錯工具。 您有兩種方式可以 `WebView` 使用偵錯工具與控制項互動：

- 開啟 `WebView` 執行個體的 [DOM 總管](../debugger/quickstart-debug-html-and-css.md)，然後檢查 DOM 元素、調查 CSS 樣式問題，並測試動態呈現的樣式變更。

- 選取 `WebView` 執行個體中顯示的網頁或 `iFrame`，作為 [JavaScript Console](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true) 視窗中的目標，然後使用主控台命令與網頁互動。 主控台提供對於目前指令碼執行內容的存取。

### <a name="attach-the-debugger-c-visual-basic-c"></a>附加偵錯工具 (C#、Visual Basic、C++)

1. 在 Visual Studio 中，將 `WebView` 控項項加入 Windows 執行階段元件。

2. 在 [方案總管] 中，從專案的捷徑功能表選擇 [屬性]，即可開啟專案的屬性。

3. 選擇 [偵錯]。 在 [應用程式程序] 清單中，選擇 [指令碼]。

     ![附加 Script 偵錯工具](../debugger/media/js_dom_webview_script_debugger.png "JS_DOM_WebView_Script_Debugger")

4. (選擇性) 若為非 Express 版本的 Visual Studio，依序選擇 [工具] > [選項] > [偵錯] > [Just-In-Time]，然後停用指令碼的 Just-In-Time (JIT) 偵錯，以停用 JIT 偵錯。

    > [!NOTE]
    > 藉由停用 JIT 偵錯，您可以隱藏在部分網頁上發生之未處理例外的對話方塊。 在 Visual Studio Express 中，一律停用 JIT 偵錯。

5. 按 F5 開始偵錯作業。

### <a name="use-the-dom-explorer-to-inspect-and-debug-a-webview-control"></a>使用 [DOM 總管] 檢查及偵錯 WebView 控制項

1. (C#、Visual Basic、C++)  將指令碼偵錯工具附加到應用程式。 請參閱第一節裡的指示。

2. 如果您尚未這麼做，請將 `WebView` 控制項加入到應用程式，然後按 F5 開始偵錯。

3. 巡覽到包含 `Webview` 控制項的頁面。

4. `WebView`選擇 [ **Debug**]、[ **Windows**]、[ **DOM 總管**]，然後選擇您想要檢查的 URL，以開啟控制項的 DOM 總管視窗 `WebView` 。

     ![開啟 DOM 總管](../debugger/media/js_dom_webview.png "JS_DOM_WebView")

     與 `WebView` 相關的 [DOM 總管] 會顯示為 Visual Studio 中的新索引標籤。

5. 如 [使用 DOM 總管的 DEBUG CSS 樣式](quickstart-debug-html-and-css.md)中所述，請參閱和修改即時 DOM 元素和 css 樣式。

### <a name="use-the-javascript-console-window-to-inspect-and-debug-a-webview-control"></a>使用 [JavaScript 主控台] 視窗檢查及偵錯 WebView 控制項

1. (C#、Visual Basic、C++)  將指令碼偵錯工具附加到應用程式。 請參閱第一節裡的指示。

2. 如果您尚未這麼做，請將 `WebView` 控制項加入到應用程式，然後按 F5 開始偵錯。

3. `WebView`選擇 [ **Debug**]、[ **Windows**]、[ **javascript 主控台**]，開啟控制項的 [JavaScript 主控台] 視窗。

     隨即顯示 [JavaScript 主控台] 視窗。

4. 巡覽到包含 `Webview` 控制項的頁面。

5. 在主控台視窗中，選取 [ `iFrame` `WebView` **目標** ] 清單中控制項所顯示的網頁或。

     ![JavaScript 主控台視窗中的目標選項](../debugger/media/js_console_target.png "JS_Console_Target")

    > [!NOTE]
    > 使用主控台，您可以一次與單一 `WebView`、`iFrame`、共用連絡人或 Web 背景工作互動。 每個項目需要個別的 Web 平台主機 (WWAHost.exe) 執行個體。 您一次可以與一個主機互動。

6. 在您的應用程式中查看及修改變數，或使用主控台命令（如 [快速入門： Debug javascript](../debugger/quickstart-debug-javascript-using-the-console.md) 和 [javascript 主控台命令](../debugger/javascript-console-commands.md?view=vs-2017&preserve-view=true)中所述）。

## <a name="see-also"></a>另請參閱

- [快速入門：偵錯 HTML 和 CSS](../debugger/quickstart-debug-html-and-css.md)