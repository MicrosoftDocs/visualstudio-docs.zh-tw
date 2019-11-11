---
title: 對 JavaScript 或 TypeScript 應用程式進行偵錯
description: Visual Studio 支援在其中對 JavaScript 和 TypeScript 進行偵錯
ms.date: 11/01/2019
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 0405488f6f456f22711498e81789881ffc5a0a8a
ms.sourcegitcommit: 308a2bdbea81df78bffc3a01afce4ab13131fabc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913006"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>在 Visual Studio 中對 JavaScript 和 TypeScript 進行偵錯

您可以使用 Visual Studio 來偵錯 JavaScript 和 TypeScript 程式碼。 您可以設定和叫用中斷點、附加偵錯工具、檢查變數、檢視呼叫堆疊，以及使用其他偵錯功能。

> [!TIP]
> 如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)頁面免費進行安裝。 根據您執行的應用程式開發類型，您可能需要安裝 Visual Studio 隨附的 **Node.js 開發工作負載**。

## <a name="debug-server-side-script"></a>偵錯伺服器端指令碼

1. 當您的專案在 Visual Studio 中開啟時，開啟伺服器端 JavaScript 檔案 (例如 *server.js*)，然後按一下左側的裝訂邊以設定中斷點：

    ![設定中斷點](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    中斷點是可靠偵錯最基本也最重要的功能。 中斷點會指出 Visual Studio 應暫停程式碼執行的地方，如此一來您可以查看變數的值或記憶體的行為，或查看程式碼分支是否正在執行。

1. 若要執行您的應用程式，請按 **F5** ([偵錯] > [開始偵錯])。

    偵錯工具會在您設定的中斷點處暫停 (目前的陳述式以黃色標示)。 現在，您可以將滑鼠指標停留在目前位於範圍內的變數上，並使用偵錯工具視窗 (如 [區域變數] 和 [監看式] 視窗)，藉以檢查應用程式狀態。

1. 按 **F5** 繼續執行應用程式。

1. 如果您想要使用 Chrome Developer Tools 或 F12 工具，請按 **F12**。 您可以使用這些工具來檢查 DOM，並使用 JavaScript 主控台與應用程式互動。

## <a name="debug-client-side-script"></a>偵錯用戶端指令碼

::: moniker range=">=vs-2019"
Visual Studio 僅提供適用于 Chrome 和 Microsoft Edge （Chromium）的用戶端偵錯工具支援。 在某些情節中，偵錯工具會自動叫用 JavaScript 和 TypeScript 程式碼以及 HTML 檔案內嵌指令碼的中斷點。 如需在 ASP.NET apps 中進行用戶端腳本的偵錯工具，請參閱[Microsoft Edge 中的偵錯工具 JavaScript](https://devblogs.microsoft.com/visualstudio/debug-javascript-in-microsoft-edge-from-visual-studio/)和此[適用于 Google Chrome 的文章](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome)。
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 僅提供 Chrome 和 Internet Explorer 的用戶端偵錯工具支援。 在某些情節中，偵錯工具會自動叫用 JavaScript 和 TypeScript 程式碼以及 HTML 檔案內嵌指令碼的中斷點。 如需在 ASP.NET apps 中進行用戶端腳本的偵錯工具，請參閱[Google Chrome 中 ASP.NET 專案的用戶端偵錯工具](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/)的 blog 文章。
::: moniker-end

針對 ASP.NET 以外的應用程式，請遵循這裡所述的步驟。

### <a name="prepare-your-app-for-debugging"></a>準備您的應用程式以進行調試

如果您的原始檔是由 TypeScript 或 Babel 等轉換器縮減或建立，則必須使用[來源對應](#generate_source_maps)以獲得最佳的偵錯體驗。 若沒有來源對應，您仍可將偵錯工具附加至執行中的用戶端指令碼。 不過，您只能在已縮減或轉換的檔案中設定和叫用中斷點，而不能在來源檔案中進行。 例如，在 Vue.js 應用程式中，已縮減的指令碼會以字串形式傳遞至 `eval` 陳述式，除非使用來源對應，否則無法使用 Visual Studio 偵錯工具有效地逐步執行此程式碼。 在複雜的偵錯工具案例中，您也可以改為使用 Chrome 開發人員工具或 Microsoft Edge 的 F12 工具。

如需產生來源對應的說明，請參閱[產生來源對應以進行偵錯工具](#generate_source_maps)。

### <a name="prepare_the_browser_for_debugging"></a>準備瀏覽器以進行偵錯工具

::: moniker range=">=vs-2019"
針對此案例，請使用 Microsoft Edge （Chromium），其目前在 IDE 或 Chrome 中名為**Microsoft Edge Beta** 。
::: moniker-end
::: moniker range="vs-2017"
針對此案例，請使用 Chrome。
::: moniker-end

1. 關閉目標瀏覽器的所有視窗。

   其他瀏覽器實例可能會防止瀏覽器開啟並啟用偵測。 （瀏覽器延伸模組可能正在執行，且無法進行完整的 debug 模式，因此您可能需要開啟 [工作管理員] 來尋找非預期的 Chrome 實例。）

   ::: moniker range=">=vs-2019"
   針對 Microsoft Edge （Chromium），也會關閉 Chrome 的所有實例。 因為這兩個瀏覽器都使用 chromium 程式碼基底，所以這會產生最佳結果。
   ::: moniker-end

2. 啟動瀏覽器並啟用偵錯工具。

    ::: moniker range=">=vs-2019"
    從 Visual Studio 2019 開始，您可以在瀏覽器啟動時設定 `--remote-debugging-port=9222` 旗標，方法是從 [**調試**程式] 工具列選取 **[流覽方式 ...]** >，然後選擇 [**新增**]，然後在 [**引數**] 欄位中設定旗標。 為瀏覽器使用不同的易記名稱，例如**具有**具有偵錯工具之偵錯工具或**Chrome**的邊緣。 如需詳細資訊，請參閱[版本資訊](/visualstudio/releases/2019/release-notes-v16.2)。

    ![將瀏覽器設定為開啟並啟用偵測](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    或者，從 Windows [**開始**] 按鈕開啟 [執行] 命令（**以**滑鼠右鍵按一下並選擇 [**執行**]），然後輸入下列命令：

    `msedge --remote-debugging-port=9222`

    或

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    從 Windows [開始] 按鈕開啟 [執行] 命令 (按一下滑鼠右鍵，並選擇 [執行])，然後輸入下列命令：

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    這會啟動您的瀏覽器並啟用偵錯工具。

    應用程式尚未執行，因此您會看到空白的瀏覽器頁面。

### <a name="attach-the-debugger-to-client-side-script"></a>將偵錯工具附加至用戶端腳本

若要從 Visual Studio 附加偵錯工具，並叫用用戶端程式代碼中的中斷點，偵錯工具需要協助來識別正確的進程。 以下是啟用此功能的其中一種方式。

1. 切換至 Visual Studio，然後在您的原始程式碼中設定中斷點，這可能是 JavaScript 檔案、TypeScript 檔案或 JSX 檔。 （在允許中斷點的程式程式碼中設定中斷點，例如 return 語句或 var 宣告）。

    ![設定中斷點](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    若要在轉換檔案中尋找特定程式碼，請使用**Ctrl**+**F** （**編輯** > **尋找並取代** > **快速尋找**）。

    針對用戶端程式代碼，若要在 TypeScript 檔案或 JSX 檔中叫用中斷點，通常需要使用[來源對應](#generate_source_maps)。 來源對應必須正確設定，才能支援 Visual Studio 中的調試。

2. 在 Visual Studio 中選取您的目標瀏覽器做為 debug 目標，然後按下**Ctrl**+**F5** （**debug** > **啟動但不進行調試**程式），以在瀏覽器中執行應用程式。

    ::: moniker range=">=vs-2019"
    如果您已建立具有易記名稱的瀏覽器設定，請選擇作為您的 debug 目標。
    ::: moniker-end

    應用程式會在新的瀏覽器索引標籤中開啟。

3. 選擇 [偵錯] > [附加至處理序]。

    > [!TIP]
    > 從 Visual Studio 2017 開始，一旦您依照下列步驟第一次附加至進程，您可以選擇 [ **Debug** ] > [重新**附加至進程**]，快速地重新附加至相同的進程。

4. 在 [**附加至進程**] 對話方塊中，取得您可以附加至之瀏覽器實例的篩選清單。

    ::: moniker range=">=vs-2019"
    在 Visual Studio 2019 中，于 [**附加至**] 欄位中選擇目標瀏覽器、 **javascript （Chrome）** 或**JAVAscript （Microsoft Edge-Chromium）** 的正確偵錯工具，在篩選方塊中輸入**Chrome**或**Edge**以篩選搜尋結果。
    ::: moniker-end
    ::: moniker range="vs-2017"
    在 Visual Studio 2017 中，選擇 [**附加至**] 欄位中的 [ **Webkit 程式碼**]，在 [篩選] 方塊中輸入**chrome**以篩選搜尋結果。
    ::: moniker-end

5. 選取具有正確主機埠（在此範例中為 localhost）的瀏覽器進程，然後選取 [**附加**]。

    埠（例如，1337）可能也會出現在 [**標題**] 欄位中，協助您選取正確的瀏覽器實例。

    ::: moniker range=">=vs-2019"
    下列範例顯示如何尋找 Microsoft Edge （Chromium）瀏覽器。

    ![附加至處理序](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![附加至處理序](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    當 [DOM 總管] 和 JavaScript 主控台在 Visual Studio 中開啟時，您就知道偵錯工具已正確附加。 這些偵錯工具類似適用於 Microsoft Edge 的 Chrome Developer Tools 和 F12 工具。
    ::: moniker-end

    > [!TIP]
    > 如果偵錯工具未附加，而且您看到「無法啟動偵錯工具介面卡」或「無法附加至進程」的訊息。 作業在目前狀態中不合法。」，請使用 Windows 工作管理員關閉目標瀏覽器的所有實例，然後再以「偵錯工具」模式啟動瀏覽器。 瀏覽器延伸模組可能正在執行，且無法進行完整的 debug 模式。

6. 因為具有中斷點的程式碼可能已經執行，請重新整理您的瀏覽器頁面。 如有必要，請採取動作，讓具有中斷點的程式碼執行。

    在偵錯工具中暫停時，您可以將滑鼠指標停留在變數上，並使用偵錯工具視窗，藉以檢查應用程式狀態。 您可以逐步執行程式碼 (**F5**、**F10** 和 **F11**) 來推進偵錯工具。 如需基本偵錯工具功能的詳細資訊，請參閱[偵錯工具的第一次](../debugger/debugger-feature-tour.md)查看。

    根據您的應用程式類型、您先前遵循的步驟，以及瀏覽器狀態之類的其他因素，您可能會*在轉換的*檔案或來源檔案中叫用中斷點。 不論哪一種方式，您都可以逐步執行程式碼並檢查變數。

   * 如果您需要在 TypeScript、JSX 或*vue*原始程式檔中中斷程式碼，但無法這麼做，請確定您的環境已正確設定，如[疑難排解](#troubleshooting_source_maps)一節中所述。

   * 如果您需要在轉換 JavaScript 檔案（例如*app-bundle.js.map*）中中斷程式碼，但無法這麼做，請移除來源對應檔（*檔案名 .js*）。

### <a name="troubleshooting_source_maps"></a>疑難排解中斷點和來源對應

如果您需要在 TypeScript 或 JSX 原始程式檔中中斷程式碼，但無法這麼做，請使用先前步驟中所述的 [**附加至進程**] 來附加偵錯工具。 請確定您的環境已正確設定：

* 您關閉了所有的瀏覽器實例，包括 Chrome 延伸模組（使用工作管理員），讓您可以在 [偵錯工具] 模式中執行瀏覽器。
      
* 請確定您[是在 [調試] 模式下啟動瀏覽器](#prepare_the_browser_for_debugging)。

* 請確定您的來源對應檔案包含原始程式檔的正確相對路徑，而且它不包含不支援的前置詞，例如*webpack:///* ，這會導致 Visual Studio 偵錯工具無法尋找來源檔案。 例如， *webpack:///.app.tsx*之類的參考可能會更正為 */app.tsx*。 您可以在來源對應檔（這有助於測試）或透過自訂群組建設定中，手動執行此動作。 如需詳細資訊，請參閱[產生來源對應以進行調試](#generate_source_maps)程式。

或者，如果您需要中斷原始程式檔（例如 app.config）中的*程式*代碼，但無法這麼做，請嘗試使用原始程式檔中的 `debugger;` 語句，或在 Chrome 開發人員工具（或 Microsoft Edge 的 F12 工具）中設定中斷點。

## <a name="generate_source_maps"></a> 產生來源對應以進行偵錯

Visual Studio 能夠在 JavaScript 來源檔案上使用及產生來源對應。 如果您的原始檔是由 TypeScript 或 Babel 等轉換器縮減或建立，通常需要這項功能。 可用選項取決於專案類型。

* Visual Studio 中的 TypeScript 專案預設會為您產生來源對應。 如需詳細資訊，請參閱[使用 tsconfig 來設定來源對應](#configure_source_maps)。

* 在 JavaScript 專案中，您可以使用搭配程式（例如 webpack）和像是 TypeScript 編譯器（或 Babel）之類的編譯器來產生來源對應，您可以將其新增至專案。 針對 TypeScript 編譯器，您也必須新增 tsconfig 的*json*檔案，並設定 `sourceMap` 編譯器選項。 如需示範如何使用基本 webpack 組態來執行這項作業的範例，請參閱[使用 React 建立 Node.js 應用程式](../javascript/tutorial-nodejs-with-react-and-jsx.md)。

> [!NOTE]
> 如果您不熟悉來源對應，請閱讀 [Introduction to JavaScript Source Maps](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) (JavaScript 來源對應簡介) 再繼續進行。 

若要設定來源對應的進階設定，請使用 *tsconfig.json* 或 TypeScript 專案的專案設定，但不要同時使用這兩者。

若要使用 Visual Studio 來啟用偵錯工具，您必須確定所產生來源對應中的來源檔案參考是否正確（這可能需要測試）。 例如，如果您使用 webpack，則來源對應檔中的參考會包含*webpack:///* 前置詞，這可防止 Visual Studio 尋找 TYPESCRIPT 或 JSX 原始程式檔。 具體來說，當您修正此問題以進行調試時，必須將來源檔案（例如*app.config*）的參考從*webpack:///./app.tsx*之類的專案變更為類似 */app.tsx*，以啟用偵錯工具（path 是相對於您的原始程式檔）。 下列範例示範如何在 webpack 中設定來源對應，這是最常見的 browserify 之一，因此可與 Visual Studio 搭配使用。

（僅限 Webpack）如果您要在 JSX 檔案的 TypeScript 中設定中斷點（而不是轉換 JavaScript 檔案），則必須更新您的 webpack 設定。 例如，在*webpack-config.js*中，您可能需要取代下列程式碼：

```javascript
  output: {
    filename: "./app-bundle.js", // This is an example of the filename in your project
  },
```

取代為此程式碼：

```javascript
  output: {
    filename: "./app-bundle.js", // Replace with the filename in your project
    devtoolModuleFilenameTemplate: '[resource-path]'  // Removes the webpack:/// prefix
  },
```

這是僅限開發的設定，可在 Visual Studio 中啟用用戶端程式代碼的偵錯工具。

針對複雜的案例，瀏覽器工具（**F12**）有時最適合用於偵錯工具，因為它們不需要變更自訂前置詞。

### <a name="configure_source_maps"></a>使用 tsconfig json 檔案設定來源對應

如果您將 *tsconfig.json* 檔案新增至專案，則 Visual Studio 會將根目錄視為 TypeScript 專案。 若要加入檔案，請在方案總管中的專案上按一下滑鼠右鍵，然後選擇 [**加入 > 新專案] > [TYPESCRIPT JSON 設定檔**]。 這會將類似如下的 *tsconfig.json* 檔案新增至您的專案。

```json
{
  "compilerOptions": {
    "noImplicitAny": false,
    "noEmitOnError": true,
    "removeComments": false,
    "sourceMap": true,
    "target": "es5"
  },
  "exclude": [
    "node_modules",
    "wwwroot"
  ]
}
```

#### <a name="compiler-options-for-tsconfigjson"></a>tsconfig.json 的編譯器選項

* **inlineSourceMap**：發出具有來源對應的單一檔案，而不是為每個原始程式檔建立個別的來源對應。
* **inlineSources**：在單一檔案中的來源對應旁發出來源;需要設定*inlineSourceMap*或*sourceMap* 。
* **mapRoot**：指定偵錯工具應尋找來源對應（ *.map*）檔案的位置，而不是預設位置。 如果執行階段 *.map* 檔案必須與 *.js* 檔案位於不同的位置，請使用此旗標。 指定的位置會內嵌於來源對應，以將偵錯工具導向至 *.map* 檔案的位置。
* **sourceMap**：產生對應的 *.map*檔案。
* **sourceRoot**：指定偵錯工具應尋找 TypeScript 檔案的位置，而不是來源位置。 如果執行階段原始檔所在位置必須不同於設計階段時的位置，請使用此旗標。 指定的位置會內嵌於來源對應，以將偵錯工具導向至來源檔案所在的位置。

如需編譯器選項的詳細資料，請參閱 TypeScript 手冊上的 [Compiler Options](https://www.typescriptlang.org/docs/handbook/compiler-options.html) (編譯器選項) 頁面。

### <a name="configure-source-maps-using-project-settings-typescript-project"></a>使用專案設定來設定來源對應（TypeScript 專案）

您也可以使用專案屬性來設定來源對應設定，方法是以滑鼠右鍵按一下專案，然後選擇 [專案] > [屬性] > [TypeScript 建置] > [偵錯]。

您可以使用下列專案設定。

* **產生來源**對應（相當於*Tsconfig*中的**sourceMap** ）：產生對應*的 .map*檔案。
* **指定來源對應的根目錄**（相當於*Tsconfig*中的**mapRoot** ）：指定偵錯工具應該尋找對應檔案的位置，而不是所產生的位置。 如果執行階段 *.map* 檔案必須與 .js 檔案位於不同的位置，請使用此旗標。 指定的位置會內嵌於來源對應，以將偵錯工具導向至對應檔案所在的位置。
* **指定 typescript 檔案的根目錄**（相當於*Tsconfig*中的**sourceRoot** ）：指定偵錯工具應尋找 TypeScript 檔案的位置，而不是來源位置。 如果執行階段原始檔所在位置必須不同於設計階段時的位置，請使用此旗標。 指定的位置會內嵌於來源對應，以將偵錯工具導向至來源檔案所在的位置。

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>使用 Razor (ASP.NET) 偵錯動態檔案中的 JavaScript

::: moniker range=">=vs-2019"
從 Visual Studio 2019 開始，Visual Studio 僅提供適用于 Chrome 和 Microsoft Edge （Chromium）的偵錯工具支援。
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 僅提供 Chrome 和 Internet Explorer 的偵錯支援。
::: moniker-end

不過，您無法在使用 Razor 語法（cshtml，vbhtml）產生的檔案上自動叫用中斷點。 偵錯這類檔案時有兩種方法可供使用：

* **將 `debugger;` 語句放在您要中斷的位置**：這會導致動態腳本停止執行，並在建立時立即開始進行調試。
* **載入頁面，並在 Visual Studio 上開啟動態**檔：您必須在進行偵錯工具時開啟動態檔案、設定中斷點，然後重新整理頁面，此方法才能正常執行。 您可以根據使用的是 Chrome 或 Internet Explorer，利用下列其中一個策略來尋找檔案：

   針對 Chrome，請移至 [方案總管] > [指令碼文件] > [您的頁面名稱]。

    > [!NOTE]
    > 使用 Chrome 時，您可能會收到訊息，指出**在 \<指令碼 > 標籤之間沒有可用的來源**。 這是正常的，您可以繼續偵錯。

   ::: moniker range=">=vs-2019"
   若為 Microsoft Edge （Chromium），請使用與 Chrome 相同的程式。
   ::: moniker-end

   ::: moniker range="vs-2017"
   針對 Internet Explorer，請移至 [方案總管] > [指令碼文件] > [Windows Internet Explorer] > [您的頁面名稱]。
   ::: moniker-end

如需詳細資訊，請參閱 [Client-side debugging of ASP.NET projects in Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/) (Google Chrome 中 ASP.NET 專案的用戶端偵錯)。
