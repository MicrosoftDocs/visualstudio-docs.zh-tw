---
title: 對 JavaScript 或 TypeScript 應用程式進行偵錯
description: Visual Studio 支援在其中對 JavaScript 和 TypeScript 進行偵錯
ms.date: 12/03/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: b6bc2aa2dff6a1d71428041e17bffe39c7d624e9
ms.sourcegitcommit: 5dc74b4fdff1357df43a19f6e8a51d7bf706abd6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2019
ms.locfileid: "55768401"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>在 Visual Studio 中對 JavaScript 和 TypeScript 進行偵錯

您可以使用 Visual Studio 來偵錯 JavaScript 和 TypeScript 程式碼。 您可以設定和叫用中斷點、附加偵錯工具、檢查變數、檢視呼叫堆疊，以及使用其他偵錯功能。

> [!TIP]
> 如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)頁面免費進行安裝。 根據您執行的應用程式開發類型，您可能需要安裝 Visual Studio 隨附的 **Node.js 開發工作負載**。

## <a name="debug-server-side-script"></a>偵錯伺服器端指令碼

1. 當您的專案在 Visual Studio 中開啟時，開啟伺服器端 JavaScript 檔案 (例如 *server.js*)，然後按一下左側的裝訂邊以設定中斷點：

    ![設定中斷點](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    中斷點是可靠偵錯最基本也最重要的功能。 中斷點會指出 Visual Studio 應暫停程式碼執行的地方，如此一來您可以查看變數的值或記憶體的行為，或查看程式碼分支是否正在執行。

1. 若要執行您的應用程式，請按 **F5** ([偵錯] > [開始偵錯])。

    偵錯工具會在您設定的中斷點處暫停 (目前的陳述式以黃色標示)。 現在，您可以將滑鼠指標停留在目前位於範圍內的變數上，並使用偵錯工具視窗 (如 [區域變數] 和 [監看式] 視窗)，藉以檢查應用程式狀態。

1. 按 **F5** 繼續執行應用程式。

1. 如果您想要使用 Chrome Developer Tools 或 F12 工具，請按 **F12**。 您可以使用這些工具來檢查 DOM，並使用 JavaScript 主控台與應用程式互動。

## <a name="debug-client-side-script"></a>偵錯用戶端指令碼

Visual Studio 僅提供 Chrome 和 Internet Explorer 的偵錯支援。 在某些情節中，偵錯工具會自動叫用 JavaScript 和 TypeScript 程式碼以及 HTML 檔案內嵌指令碼的中斷點。

如果您的原始檔是由 TypeScript 或 Babel 等轉換器縮減或建立，則必須使用[來源對應](#generate_sourcemaps)以獲得最佳的偵錯體驗。 若沒有來源對應，您仍可將偵錯工具附加至執行中的用戶端指令碼。 不過，您只能在已縮減或轉換的檔案中設定和叫用中斷點，而不能在來源檔案中進行。 例如，在 Vue.js 應用程式中，已縮減的指令碼會以字串形式傳遞至 `eval` 陳述式，除非使用來源對應，否則無法使用 Visual Studio 偵錯工具有效地逐步執行此程式碼。 在某些複雜的偵錯情節中，您也可以使用適用於 Microsoft Edge 的 Chrome Developer Tools 或 F12 工具。

若要從 Visual Studio 附加偵錯工具，並叫用用戶端程式碼的中斷點，偵錯工具通常需要協助以識別正確的處理序。 以下是使用 Chrome 啟用此功能的其中一種方式。

### <a name="attach-the-debugger-to-client-side-script-using-chrome"></a>使用 Chrome 將偵錯工具附加至用戶端指令碼

1. 關閉所有 Chrome 視窗。

    您必須完成此動作，才能在偵錯模式中執行 Chrome。

2. 從 Windows [開始] 按鈕開啟 [執行] 命令 (按一下滑鼠右鍵，並選擇 [執行])，然後輸入下列命令：

    `chrome.exe --remote-debugging-port=9222`

    此命令會啟動 Chrome 並啟用偵錯。

3. 切換至 Visual Studio，然後在原始程式碼中設定中斷點 (在允許中斷點的程式碼行中設定中斷點，例如 `return` 陳述式或 `var` 宣告)。

    ![設定中斷點](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    如果您需要在產生的大型檔案中尋找特定程式碼，請使用 **Ctrl**+**F** ([編輯] > [尋找和取代] > [快速尋找])。

4. 將 Chrome 選取為 Visual Studio 的偵錯目標後，請按 **Ctrl**+**F5** ([偵錯] > [啟動但不偵錯]) 以在瀏覽器中執行應用程式。

    應用程式會在新的瀏覽器索引標籤中開啟。

    如果您的電腦中有 Chrome 可供使用，但未顯示為選項，請從偵錯目標下拉式清單中選擇 [瀏覽方式]，並選取 Chrome 作為預設瀏覽器目標 (選擇 [設為預設值])。

5. 選擇 [偵錯] > [附加至處理序]。

6. 在 [附加至處理序] 對話方塊中，於 [附加至] 欄位中選擇 [WebKit 程式碼]，然後在篩選方塊中鍵入 **chrome** 以篩選搜尋結果。

    [WebKit 程式碼] 是 Webkit 型瀏覽器 Chrome 的必要值。

7. 選取具有正確主機連接埠 (在此圖中為 1337) 的 Chrome 處理序，然後選取 [附加]。

    ![附加至處理序](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    當 [DOM 總管] 和 JavaScript 主控台在 Visual Studio 中開啟時，您就知道偵錯工具已正確附加。 這些偵錯工具類似適用於 Microsoft Edge 的 Chrome Developer Tools 和 F12 工具。

    > [!NOTE]
    > 如果偵錯工具未附加，而且您看到訊息「無法附加到處理序。 作業在目前狀態中不合法」，請先使用工作管理員關閉 Chrome 的所有執行個體，再於偵錯模式中啟動 Chrome。 Chrome 擴充功能可能會執行，並防止完整的偵錯模式。

8. 如果已執行具有中斷點的程式碼，請重新整理瀏覽器頁面以叫用中斷點。

    在偵錯工具中暫停時，您可以將滑鼠指標停留在變數上，並使用偵錯工具視窗，藉以檢查應用程式狀態。 您可以逐步執行程式碼 (**F5**、**F10** 和 **F11**) 來推進偵錯工具。

    針對已縮減或轉換的 JavaScript，根據您的環境和瀏覽器狀態而定，您可能會叫用已轉換 JavaScript 或它在 TypeScript 檔案中對應位置 (使用來源對應) 的中斷點。 不論哪一種方式，您都可以逐步執行程式碼並檢查變數。

    * 如果您需要在 TypeScript 檔案內中斷程式碼，但無法這麼做，請使用上一步中所述的 [附加至處理序] 來附加偵錯工具。 然後藉由從 [方案總管] 開啟 [指令碼文件] > [filename.tsx] 來開啟動態產生的 TypeScript 檔案，接著設定中斷點並在瀏覽器中重新整理頁面 (在允許中斷點的程式碼行中設定中斷點，例如 `return` 陳述式或 `var` 宣告)。

        或者，如果您需要在 TypeScript 檔案內中斷程式碼，但無法這麼做，請嘗試在 TypeScript 檔案中使用 `debugger;` 陳述式，或改為在 Chrome Developer Tools 中設定中斷點。

    * 如果您需要在已轉換的 JavaScript 檔案 (例如 *app-bundle.js*) 內中斷程式碼，但無法這麼做，請移除來源對應檔案 (*filename.js.map*)。

     > [!TIP]
     > 依照下列步驟第一次附加至處理序之後，在 Visual Studio 2017 中選擇 [偵錯] > [重新附加至處理序]，即可快速地重新附加至相同的處理序。

## <a name="generate_sourcemaps"></a> 產生來源對應以進行偵錯

Visual Studio 能夠在 JavaScript 來源檔案上使用及產生來源對應。 如果您的原始檔是由 TypeScript 或 Babel 等轉換器縮減或建立，通常需要這項功能。 可用選項取決於專案類型。

* Visual Studio 中的 TypeScript 專案預設會為您產生來源對應。

* 在 JavaScript 專案中，您需要使用搭配程式 (例如 webpack) 和編譯器 (例如 TypeScript 編譯器或 Babel) 來產生來源對應。您可以將這些工具新增至專案。 針對 TypeScript 編譯器，您還必須新增 *tsconfig.json* 檔案。 如需示範如何使用基本 webpack 組態來執行這項作業的範例，請參閱[使用 React 建立 Node.js 應用程式](../javascript/tutorial-nodejs-with-react-and-jsx.md)。

> [!NOTE]
> 如果您不熟悉來源對應，請閱讀 [Introduction to JavaScript Source Maps](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) (JavaScript 來源對應簡介) 再繼續進行。

若要設定來源對應的進階設定，請使用 *tsconfig.json* 或 TypeScript 專案的專案設定，但不要同時使用這兩者。

### <a name="configure-source-maps-using-a-tsconfigjson-file"></a>使用 tsconfig.json 檔案設定來源對應

如果您將 *tsconfig.json* 檔案新增至專案，則 Visual Studio 會將根目錄視為 TypeScript 專案。 若要新增檔案，請以滑鼠右鍵按一下 [方案總管] 中的專案，然後選擇 [新增] > [新增項目] > [Web] > [指令碼] > [TypeScript JSON 組態檔]。 這會將類似如下的 *tsconfig.json* 檔案新增至您的專案。

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

* **inlineSourceMap**：發出具有來源對應的單一檔案，而不是針對每個來源檔案建立個別來源對應。
* **inlineSources**：發出原始檔及單一檔案的來源對應；必須設定 *inlineSourceMap* 或 *sourceMap*。
* **mapRoot**：指定偵錯工具應尋找來源對應 (*.map*) 檔案的位置，而不是預設位置。 如果執行階段 *.map* 檔案必須與 *.js* 檔案位於不同的位置，請使用此旗標。 指定的位置會內嵌於來源對應，以將偵錯工具導向至 *.map* 檔案的位置。
* **sourceMap**：產生對應的 *.map* 檔案。
* **sourceRoot**：指定偵錯工具應尋找 TypeScript 檔案的位置，而不是原始檔位置。 如果執行階段原始檔所在位置必須不同於設計階段時的位置，請使用此旗標。 指定的位置會內嵌於來源對應，以將偵錯工具導向至原始檔所在的位置。

如需編譯器選項的詳細資料，請參閱 TypeScript 手冊上的 [Compiler Options](https://www.typescriptlang.org/docs/handbook/compiler-options.html) (編譯器選項) 頁面。

### <a name="configure-source-maps-using-project-settings"></a>使用專案設定設定來源對應

您也可以使用專案屬性來設定來源對應設定，方法是以滑鼠右鍵按一下專案，然後選擇 [專案] > [屬性] > [TypeScript 建置] > [偵錯]。

您可以使用下列專案設定。

* **產生來源對應** (相當於 *tsconfig.json* 中的 **sourceMap**)：產生對應的 *.map* 檔案。
* **指定來源對應的根目錄** (相當於 *tsconfig.json* 中的 **mapRoot**)：指定偵錯工具應尋找對應檔案的位置，而不是產生的位置。 如果執行階段 *.map* 檔案必須與 .js 檔案位於不同的位置，請使用此旗標。 指定的位置會內嵌於來源對應，以將偵錯工具導向至對應檔案所在的位置。
* **指定 TypeScript 檔案的根目錄** (相當於 *tsconfig.json* 中的 **sourceRoot**)：指定偵錯工具應尋找 TypeScript 檔案的位置，而不是原始檔位置。 如果執行階段原始檔所在位置必須不同於設計階段時的位置，請使用此旗標。 指定的位置會內嵌於來源對應，以將偵錯工具導向至來源檔案所在的位置。

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>使用 Razor (ASP.NET) 偵錯動態檔案中的 JavaScript

Visual Studio 僅提供 Chrome 和 Internet Explorer 的偵錯支援。 它會自動將中斷點附加至 JavaScript/TypeScript 和 HTML 檔案內嵌指令碼。

無法自動偵錯動態產生的檔案。 您無法自動叫用透過 Razor 語法 (cshtml、vbhtml) 所產生檔案的中斷點。 偵錯這類檔案時有兩種方法可供使用：

* **將 `debugger;` 陳述式放在您要中斷的位置**：這會導致正在建立的動態指令碼停止執行並立即開始偵錯。
* **在 Visual Studio 中載入頁面並開啟動態文件**：您需要在偵錯時開啟動態檔案、設定您的中斷點，然後重新整理頁面，才能運作此方法。 您可以根據使用的是 Chrome 或 Internet Explorer，利用下列其中一個策略來尋找檔案：

   針對 Chrome，請移至 [方案總管] > [指令碼文件] > [您的頁面名稱]。

    > [!NOTE]
    > 使用 Chrome 時，您可能會收到訊息 `no source is available between `<script>` tags.` This is OK, just continue debugging.

   針對 Internet Explorer，請移至 [方案總管] > [指令碼文件] > [Windows Internet Explorer] > [您的頁面名稱]。

如需詳細資訊，請參閱 [Client-side debugging of ASP.NET projects in Google Chrome](https://blogs.msdn.microsoft.com/webdev/2016/11/21/client-side-debugging-of-asp-net-projects-in-google-chrome/) (Google Chrome 中 ASP.NET 專案的用戶端偵錯)。
