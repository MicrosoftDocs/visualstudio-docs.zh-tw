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
ms.openlocfilehash: 3f8fa8fcd859a7464d471972689728dc556a79bd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75678970"
---
# <a name="debug-a-javascript-or-typescript-app-in-visual-studio"></a>在 Visual Studio 中對 JavaScript 和 TypeScript 進行偵錯

您可以使用 Visual Studio 來偵錯 JavaScript 和 TypeScript 程式碼。 您可以設定和叫用中斷點、附加偵錯工具、檢查變數、檢視呼叫堆疊，以及使用其他偵錯功能。

> [!TIP]
> 如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)頁面免費進行安裝。 根據您執行的應用程式開發類型，您可能需要安裝 Visual Studio 隨附的 **Node.js 開發工作負載**。

## <a name="debug-server-side-script"></a>偵錯伺服器端指令碼

1. 當您的專案在 Visual Studio 中開啟時，開啟伺服器端 JavaScript 檔案 (例如 *server.js*)，然後按一下左側的裝訂邊以設定中斷點：

    ![設定中斷點](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    中斷點是可靠偵錯最基本也最重要的功能。 中斷點會指出 Visual Studio 應暫停程式碼執行的地方，如此一來您可以查看變數的值或記憶體的行為，或查看程式碼分支是否正在執行。

1. 若要執行您的應用程式，請按 **F5** ([偵錯]**** > [開始偵錯]****)。

    偵錯工具會在您設定的中斷點處暫停 (目前的陳述式以黃色標示)。 現在，您可以將滑鼠指標停留在目前位於範圍內的變數上，並使用偵錯工具視窗 (如 [區域變數]**** 和 [監看式]**** 視窗)，藉以檢查應用程式狀態。

1. 按 **F5** 繼續執行應用程式。

1. 如果您想要使用 Chrome Developer Tools 或 F12 工具，請按 **F12**。 您可以使用這些工具來檢查 DOM，並使用 JavaScript 主控台與應用程式互動。

## <a name="debug-client-side-script"></a>偵錯用戶端指令碼

::: moniker range=">=vs-2019"
Visual Studio 僅為 Chrome 和微軟邊緣（鉻）提供用戶端調試支援。 在某些情節中，偵錯工具會自動叫用 JavaScript 和 TypeScript 程式碼以及 HTML 檔案內嵌指令碼的中斷點。 有關在ASP.NET應用程式中調試用戶端腳本，請參閱 Microsoft Edge[中的"調試 JavaScript"](https://devblogs.microsoft.com/visualstudio/debug-javascript-in-microsoft-edge-from-visual-studio/)博客文章和[Google Chrome 的此帖子](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome)。 有關在 ASP.NET 核心中調試 TypeScript，請參閱[使用 TypeScript 創建ASP.NET核心應用](tutorial-aspnet-with-typescript.md)。
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 僅為 Chrome 和 IE 瀏覽器提供用戶端調試支援。 在某些情節中，偵錯工具會自動叫用 JavaScript 和 TypeScript 程式碼以及 HTML 檔案內嵌指令碼的中斷點。 有關在ASP.NET應用程式中調試用戶端腳本，請參閱 Google Chrome[中ASP.NET專案的博客文章用戶端調試](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/)。
::: moniker-end

對於ASP.NET以外的應用程式，請按照此處介紹的步驟操作。

### <a name="prepare-your-app-for-debugging"></a>準備應用進行調試

如果您的原始檔是由 TypeScript 或 Babel 等轉換器縮減或建立，則必須使用[來源對應](#generate_source_maps)以獲得最佳的偵錯體驗。 若沒有來源對應，您仍可將偵錯工具附加至執行中的用戶端指令碼。 不過，您只能在已縮減或轉換的檔案中設定和叫用中斷點，而不能在來源檔案中進行。 例如，在 Vue.js 應用程式中，已縮減的指令碼會以字串形式傳遞至 `eval` 陳述式，除非使用來源對應，否則無法使用 Visual Studio 偵錯工具有效地逐步執行此程式碼。 在複雜的調試方案中，您也可以使用 Chrome 開發人員工具或 F12 工具進行 Microsoft 邊緣。

有關生成源映射的説明，請參閱[生成源映射以進行調試](#generate_source_maps)。

### <a name="prepare-the-browser-for-debugging"></a><a name="prepare_the_browser_for_debugging"></a>準備瀏覽器進行調試

::: moniker range=">=vs-2019"
對於此方案，請使用當前在 IDE 中命名為 Microsoft**邊緣測試版的**Microsoft 邊緣（鉻）或 Chrome。
::: moniker-end
::: moniker range="vs-2017"
對於此方案，請使用 Chrome。
::: moniker-end

1. 關閉目標瀏覽器的所有視窗。

   其他瀏覽器實例可能會阻止瀏覽器在啟用調試後打開。 （瀏覽器延伸程式可能正在運行並阻止完全偵錯模式，因此您可能需要打開工作管理員才能查找 Chrome 的意外實例。

   ::: moniker range=">=vs-2019"
   對於微軟邊緣（鉻），也關閉所有Chrome實例。 由於兩個瀏覽器都使用鉻代碼庫，因此這可提供最佳結果。
   ::: moniker-end

2. 啟用調試後啟動瀏覽器。

    ::: moniker range=">=vs-2019"
    從 Visual Studio 2019 開始，`--remote-debugging-port=9222`您可以通過從 **"調試"** 工具列中選擇 **"流覽與...** >，然後選擇 **"添加**"，然後在 **"參數"** 欄位中設置標誌，從而在瀏覽器啟動時設置標誌。 對瀏覽器使用不同的易記名稱，如 **"使用調試邊緣"** 或 **"使用調試的 Chrome"。** 如需詳細資訊，請參閱[版本資訊](/visualstudio/releases/2019/release-notes-v16.2)。

    ![將瀏覽器設置為啟用調試後打開](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    或者，從 Windows**開始**按鈕打開 **"運行"** 命令（按右鍵並選擇 **"運行**"），然後輸入以下命令：

    `msedge --remote-debugging-port=9222`

    或者，

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    從 Windows [開始]**** 按鈕開啟 [執行]**** 命令 (按一下滑鼠右鍵，並選擇 [執行]****)，然後輸入下列命令：

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    這將在啟用調試後啟動瀏覽器。

    該應用程式尚未運行，因此您將獲得一個空瀏覽器頁面。

### <a name="attach-the-debugger-to-client-side-script"></a>將調試器附加到用戶端腳本

要從 Visual Studio 附加調試器並在用戶端代碼中命中中斷點，調試器需要幫助確定正確的過程。 以下是啟用此功能的其中一種方式。

1. 切換到 Visual Studio，然後在原始程式碼中設置中斷點，該中斷點可能是 JavaScript 檔、TypeScript 檔或 JSX 檔。 （在允許中斷點（如返回語句或 var 聲明）的程式碼中設置中斷點。

    ![設定中斷點](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    要查找轉頁檔中的特定代碼，請使用**Ctrl**+**F（****編輯** > **查找和替換** > **快速查找**）。

    對於用戶端代碼，要在 TypeScript 檔中命中中斷點 *，.vue*或 JSX 檔通常需要使用[源映射](#generate_source_maps)。 必須正確配置源映射，以支援視覺化工作室中的調試。

2. 選擇目標瀏覽器作為 Visual Studio 中的調試目標，然後按**Ctrl**+**Debug** > **F5（****調試啟動而不調試**）在瀏覽器中運行應用。

    ::: moniker range=">=vs-2019"
    如果創建具有易記名稱的瀏覽器配置，請選擇該配置作為調試目標。
    ::: moniker-end

    應用程式會在新的瀏覽器索引標籤中開啟。

3. 選擇**調試** > **附加到進程**。

    > [!TIP]
    > 從 Visual Studio 2017 開始，一旦您第一次通過執行這些步驟附加到流程，您可以通過選擇**調試** > **重新附加到進程**來快速重新附加到同一進程。

4. 在 **"附加到進程"** 對話方塊中，獲取可附加到的瀏覽器實例的篩選清單。
    ::: moniker range=">=vs-2019"
    在 Visual Studio 2019 中，在"附加到欄位"中為目標瀏覽器選擇正確的調試器，在 **"附加到**欄位"中為**JavaScript（Chrome）** 或**JavaScript（微軟邊緣 - 鉻）** 選擇，在篩選器框中鍵入**鑲邊**或**邊緣**以篩選搜尋結果。
    ::: moniker-end
    ::: moniker range="vs-2017"
    在 Visual Studio 2017 中，在 **"附加到**欄位"中選擇**Webkit 代碼**，在篩選器框中鍵入**鑲邊**以篩選搜尋結果。
    ::: moniker-end

5. 選擇具有正確主機埠（本示例中的本地主機）的瀏覽器進程，然後選擇**附加**。

    埠（例如 1337）也可能顯示在 **"標題"** 欄位中，以説明您選擇正確的瀏覽器實例。

    ::: moniker range=">=vs-2019"
    下面的示例顯示了 Microsoft 邊緣（鉻）瀏覽器的外觀。

    ![附加至處理序](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![附加至處理序](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    當 [DOM 總管] 和 JavaScript 主控台在 Visual Studio 中開啟時，您就知道偵錯工具已正確附加。 這些偵錯工具類似適用於 Microsoft Edge 的 Chrome Developer Tools 和 F12 工具。
    ::: moniker-end

    > [!TIP]
    > 如果調試器未附加，並且您看到消息"無法啟動調試配接器"或"無法附加到進程"。 在目前狀態下操作不合法。" 在以偵錯模式啟動瀏覽器之前，使用 Windows 工作管理員關閉目標瀏覽器的所有實例。 瀏覽器延伸可能正在運行並阻止完全偵錯模式。

6. 由於具有中斷點的代碼可能已執行，因此刷新瀏覽器頁面。 如有必要，請採取措施，使具有中斷點的代碼執行。

    在偵錯工具中暫停時，您可以將滑鼠指標停留在變數上，並使用偵錯工具視窗，藉以檢查應用程式狀態。 您可以逐步執行程式碼 (**F5**、**F10** 和 **F11**) 來推進偵錯工具。 有關基本調試功能的詳細資訊，請參閱[首先查看調試器](../debugger/debugger-feature-tour.md)。

    您可能會在轉貼*的 .js*檔或原始檔案中命中中斷點，具體取決於你的應用類型、以前遵循的步驟以及其他因素（如瀏覽器狀態）。 不論哪一種方式，您都可以逐步執行程式碼並檢查變數。

   * 如果需要在 TypeScript、JSX 或 *.vue*原始檔案中侵入代碼，但無法執行，請確保環境設置正確，如[故障排除](#troubleshooting_source_maps)部分所述。

   * 如果需要在轉貼的 JavaScript 檔中（例如 *，app-bundle.js）* 中侵入代碼，並且無法執行此操作，請刪除源映射檔*filename.js.map*。

### <a name="troubleshooting-breakpoints-and-source-maps"></a><a name="troubleshooting_source_maps"></a>故障排除中斷點和源映射

如果需要在 TypeScript 或 JSX 原始檔案中侵入代碼，但無法做到這一點，請使用"**附加到進程**"，如前面的步驟所述，可以附加調試器。 確保環境設置正確：

* 您關閉了所有瀏覽器實例，包括 Chrome 副檔名（使用工作管理員），以便您可以在偵錯模式下運行瀏覽器。
      
* 請確保[在偵錯模式下啟動瀏覽器](#prepare_the_browser_for_debugging)。

* 確保源映射檔包含原始檔案的正確相對路徑，並且不包含不支援的首碼，如*webpack:///*，這阻止 Visual Studio 調試器查找原始檔案。 例如 *，webpack:///.app.tsx*等引用可能會更正為 *./app.tsx*。 您可以在源映射檔（對測試有説明）或通過自訂組建組態手動執行此操作。 有關詳細資訊，請參閱[生成用於調試的源映射](#generate_source_maps)。

或者，如果您需要在原始檔案中（例如 *，app.tsx*）中侵入代碼，但無法做到這一點，請嘗試在原始檔案中使用`debugger;`語句，或者在 Chrome 開發人員工具（或適用于 Microsoft Edge 的 F12 工具）中設置中斷點。

## <a name="generate-source-maps-for-debugging"></a><a name="generate_source_maps"></a> 產生來源對應以進行偵錯

Visual Studio 能夠在 JavaScript 來源檔案上使用及產生來源對應。 如果您的原始檔是由 TypeScript 或 Babel 等轉換器縮減或建立，通常需要這項功能。 可用選項取決於專案類型。

* Visual Studio 中的 TypeScript 專案預設會為您產生來源對應。 有關詳細資訊，請參閱使用[tsconfig.json 檔配置源映射](#configure_source_maps)。

* 在 JavaScript 專案中，可以使用 Webpack 等捆綁包和類型腳本編譯器（或 Babel）等編譯器生成源映射，您可以將其添加到專案中。 對於 TypeScript 編譯器，還必須添加*tsconfig.json*檔並設置`sourceMap`編譯器選項。 如需示範如何使用基本 webpack 組態來執行這項作業的範例，請參閱[使用 React 建立 Node.js 應用程式](../javascript/tutorial-nodejs-with-react-and-jsx.md)。

> [!NOTE]
> 如果您不熟悉來源對應，請閱讀 [Introduction to JavaScript Source Maps](https://www.html5rocks.com/en/tutorials/developertools/sourcemaps/) (JavaScript 來源對應簡介) 再繼續進行。 

若要設定來源對應的進階設定，請使用 *tsconfig.json* 或 TypeScript 專案的專案設定，但不要同時使用這兩者。

要使用 Visual Studio 啟用調試，您需要確保生成源映射中對原始檔案的引用正確（這可能需要測試）。 例如，如果您使用的是 Webpack，則源映射檔中的引用包括*webpack:///* 首碼，這阻止 Visual Studio 查找 TypeScript 或 JSX 原始檔案。 具體來說，當您出於調試目的更正此問題時，對原始檔案的引用（如*app.tsx）* 必須從*類似webpack:///./app.tsx*更改為啟用調試的 *./app.tsx*之類的內容（路徑相對於原始檔案）。 下面的示例演示如何在 Webpack 中配置源映射，Webpack 是最常見的捆綁包組合之一，以便它們與 Visual Studio 一起工作。

（僅限網路包）如果要在 JSX 檔的 TypeScript（而不是轉裝的 JavaScript 檔）中設置中斷點，則需要更新 Webpack 配置。 例如，在*Webpack-config.js*中，您可能需要替換以下代碼：

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

這是一個僅開發設置，用於在 Visual Studio 中啟用用戶端代碼的調試。

對於複雜的方案，瀏覽器工具 **（F12**） 有時最適合調試，因為它們不需要更改自訂首碼。

### <a name="configure-source-maps-using-a-tsconfigjson-file"></a><a name="configure_source_maps"></a>使用 tsconfig.json 檔配置源映射

如果您將 *tsconfig.json* 檔案新增至專案，則 Visual Studio 會將根目錄視為 TypeScript 專案。 要添加檔，請在解決方案資源管理器中按右鍵專案，然後選擇 **"添加>新專案> TypeScript JSON 設定檔**。 這會將類似如下的 *tsconfig.json* 檔案新增至您的專案。

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

* **內聯SourceMap**：使用源映射發出單個檔，而不是為每個原始檔案創建單獨的源映射。
* **內聯源**： 在單個檔中將源映射與源映射一起發出;需要設置*內聯源映射*或*源映射*。
* **mapRoot**： 指定調試器應查找源映射 （*.map*） 檔的位置，而不是預設位置。 如果執行階段 *.map* 檔案必須與 *.js* 檔案位於不同的位置，請使用此旗標。 指定的位置會內嵌於來源對應，以將偵錯工具導向至 *.map* 檔案的位置。
* **源映射**：生成相應的 *.map*檔。
* **sourceRoot**： 指定調試器應查找 TypeScript 檔的位置，而不是源位置。 如果執行階段原始檔所在位置必須不同於設計階段時的位置，請使用此旗標。 指定的位置會內嵌於來源對應，以將偵錯工具導向至原始檔所在的位置。

如需編譯器選項的詳細資料，請參閱 TypeScript 手冊上的 [Compiler Options](https://www.typescriptlang.org/docs/handbook/compiler-options.html) (編譯器選項) 頁面。

### <a name="configure-source-maps-using-project-settings-typescript-project"></a>使用專案設置配置源映射（TypeScript 專案）

您也可以使用專案屬性來設定來源對應設定，方法是以滑鼠右鍵按一下專案，然後選擇 [專案] > [屬性] > [TypeScript 建置] > [偵錯]****。

您可以使用下列專案設定。

* **生成源映射**（等效于*tsconfig.json*中的**源映射**）：生成相應的 *.map*檔。
* **指定源映射的根目錄**（等效于*tsconfig.json*中的**mapRoot）：** 指定調試器應查找地圖檔的位置，而不是生成的位置。 如果執行階段 *.map* 檔案必須與 .js 檔案位於不同的位置，請使用此旗標。 指定的位置會內嵌於來源對應，以將偵錯工具導向至對應檔案所在的位置。
* **指定 TypeScript 檔的根目錄**（等效于*tsconfig.json*中的**sourceRoot）：** 指定調試器應查找 TypeScript 檔而不是源位置的位置。 如果執行階段原始檔所在位置必須不同於設計階段時的位置，請使用此旗標。 指定的位置會內嵌於來源對應，以將偵錯工具導向至原始檔所在的位置。

## <a name="debug-javascript-in-dynamic-files-using-razor-aspnet"></a>使用 Razor (ASP.NET) 偵錯動態檔案中的 JavaScript

::: moniker range=">=vs-2019"
從 Visual Studio 2019 開始，Visual Studio 僅為 Chrome 和 Microsoft 邊緣（鉻）提供調試支援。
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 僅提供 Chrome 和 Internet Explorer 的偵錯支援。
::: moniker-end

但是，您不能在使用 Razor 語法生成的檔（cshtml、vbhtml）上自動命中中斷點。 偵錯這類檔案時有兩種方法可供使用：

* **將`debugger;`語句放在要中斷的位置**：這將導致動態腳本在創建動態腳本時停止執行並立即開始調試。
* **載入頁面並在 Visual Studio 上打開動態文檔**：您需要在調試時打開動態檔、設置中斷點並刷新頁面，以便此方法正常工作。 您可以根據使用的是 Chrome 或 Internet Explorer，利用下列其中一個策略來尋找檔案：

   針對 Chrome，請移至 [方案總管] > [指令碼文件] > [您的頁面名稱]****。

    > [!NOTE]
    > 使用 Chrome 時，您可能會收到訊息，指出**在 \<指令碼 > 標籤之間沒有可用的來源**。 這是正常的，您可以繼續偵錯。

   ::: moniker range=">=vs-2019"
   對於 Microsoft 邊緣（鉻），請使用與 Chrome 相同的過程。
   ::: moniker-end

   ::: moniker range="vs-2017"
   針對 Internet Explorer，請移至 [方案總管] > [指令碼文件] > [Windows Internet Explorer] > [您的頁面名稱]****。
   ::: moniker-end

如需詳細資訊，請參閱 [Client-side debugging of ASP.NET projects in Google Chrome](https://devblogs.microsoft.com/aspnet/client-side-debugging-of-asp-net-projects-in-google-chrome/) (Google Chrome 中 ASP.NET 專案的用戶端偵錯)。
