---
title: 建立 Node.js 與 React 應用程式
description: 在本教學課程中，您會使用適用於 Visual Studio 的 Node.js 工具來建立應用程式
ms.custom: mvc
ms.date: 05/23/2018
ms.technology: vs-nodejs
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 88810c2e4958e96bd5487ce1a5b059897b725b45
ms.sourcegitcommit: 7a11a094a353f2e2a2077ad863ca4c0fb97f7ec5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2018
ms.locfileid: "39132229"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>教學課程：在 Visual Studio 中建立 Node.js 和 React 應用程式

Visual Studio 可讓您輕鬆地建立 Node.js 專案，體驗 IntelliSense 和其他支援 Node.js 的內建功能。 在適用於 Visual Studio 的本教學課程中，請從 Visual Studio 範本建立 Node.js Web 應用程式專案。 然後，請使用 React 建立簡單的應用程式。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> * 建立 Node.js 專案
> * 新增 npm 套件
> * 將 React 程式碼新增至您的應用程式
> * 轉換 JSX
> * 附加偵錯工具

## <a name="prerequisites"></a>必要條件

* 您必須安裝 Visual Studio 2017 和 Node.js 開發工作負載。

    如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)頁面免費進行安裝。

    如果您需要安裝工作負載，但已擁有 Visual Studio，請在 [新增專案] 對話方塊的左窗格中，選取 [開啟 Visual Studio 安裝程式]。 Visual Studio 安裝程式即會啟動。 選擇 [Node.js 開發] 工作負載，然後選擇 [修改]。

* 您必須安裝 Node.js 執行階段。

    本教學課程已使用 8.11.2 版進行測試。

    如果您沒有安裝，請從 [Node.js](https://nodejs.org/en/download/) 網站安裝 LTS 版本。 一般而言，Visual Studio 會自動偵測已安裝的 Node.js 執行階段。 如果偵測不到已安裝的執行階段，您可以在屬性頁面中將專案設定為參考已安裝的執行階段 (建立專案之後，以滑鼠右鍵按一下專案節點，然後選擇 [屬性])。

## <a name="create-a-project"></a>建立專案

首先，請建立 Node.js Web 應用程式專案。

1. 開啟 Visual Studio 2017。

1. 從頂端功能表列中，選擇 [檔案] > [新增] > [專案]。

1. 在 [新增專案] 對話方塊的左窗格中，展開 [JavaScript]，然後選擇 [Node.js]。 在中間窗格中，選擇 [空白的 Node.js Web 應用程式]，鍵入名稱 **NodejsWebAppBlank**，然後選擇 [確定]。

     如果沒有看到 [空白的 Node.js Web 應用程式] 專案範本，您必須先安裝 Node.js 開發工作負載。

    Visual Studio 會建立新的方案，並開啟專案。

    ![[方案總管] 中的 Node.js 專案](../javascript/media/tutorial-nodejs-react-project-structure.png)

    * 以粗體反白顯示的項目就是您的專案，並使用您在 [新增專案] 對話方塊中所指定的名稱。 在檔案系統中，此專案是由專案資料夾中的 *.njsproj* 檔案所呈現。 您可以設定與專案建立關聯的屬性和環境變數，方法是以滑鼠右鍵按一下專案，然後選擇 [屬性]。 因為專案檔不會對 Node.js 專案來源進行自訂變更，所以您可以使用其他開發工具執行來回行程。

    * 最上層是方案，預設其名稱會與專案相同。 方案 (以磁碟上的 *.sln* 檔案呈現) 是一或多個相關專案的容器。

    * npm 節點會顯示任何已安裝的 npm 套件。 您可以使用滑鼠右鍵按一下 npm 節點，以使用對話方塊來搜尋並安裝 npm 套件。

    * *server.js* 之類的專案檔會顯示在專案節點下。 *server.js* 是專案啟動檔案。

## <a name="add-npm-packages"></a>新增 npm 套件

此應用程式需要 npm 模組的數目才能正確執行。

* react
* react-dom
* express
* 路徑
* ts-loader
* typescript
* webpack
* webpack-cli

1. 在 [方案總管] (右窗格) 中，以滑鼠右鍵按一下專案中的 [npm] 節點，然後選擇 [安裝新的 npm 套件]。

    在 [安裝新的 npm 套件] 對話方塊中，您可以選擇安裝最新的套件版本或指定版本。 如果選擇安裝這些套件的目前版本，但稍後發生未預期的錯誤，您可能需要安裝這些步驟後面所述的確切套件版本。

1. 在 [安裝新的 npm 套件] 對話方塊中，搜尋 react 套件，然後選取 [安裝套件] 來安裝它。

    ![安裝 npm 套件](../javascript/media/tutorial-nodejs-react-install-packages.png)

    選取 [輸出] 視窗來查看安裝套件的進度 (選取 [顯示輸出來源] 欄位中的 [Npm])。 安裝後，套件會出現在 **npm** 節點下。

    專案的 *package.json* 檔案會以新的套件資訊 (包括套件版本) 進行更新。

1. 請將下列程式碼貼入 package.json，而不是使用 UI 來搜尋其餘的套件並一次新增一個。 以下列程式碼取代 `dependencies` 區段：

    ```js
    "dependencies": {
      "express": "4.16.2",
      "path": "0.12.7",
      "react": "16.4.0",
      "react-dom": "16.4.0",
      "ts-loader": "4.0.1",
      "typescript": "2.7.2",
      "webpack": "4.1.1",
      "webpack-cli": "2.0.11"
    }
    ```

1. 以滑鼠右鍵按一下專案中的 [npm] 節點，然後選擇 [更新 npm 套件]。

    選取 [輸出] 視窗以查看安裝套件的進度。 安裝可能需要幾分鐘的時間，您可能無法立即查看結果。

    以下是安裝後顯示在 [方案總管] 中的 npm 模組。

    ![npm 套件](../javascript/media/tutorial-nodejs-react-npm-modules.png)

    > [!NOTE]
    > 如果您想要使用命令列來安裝 npm 套件，請以滑鼠右鍵按一下專案節點，然後選擇 [在這裡開啟命令提示字元]。 使用標準的 Node.js 命令來安裝套件。

## <a name="add-project-files"></a>新增專案檔

在這些步驟中，您會將四個新的檔案新增至專案中。

* *app.tsx*
* *webpack-config.js*
* *index.html*
* *tsconfig.json*

針對這個簡單的應用程式，您可以在專案根目錄中新增專案檔。 (在大部分的應用程式中，您通常會將檔案新增至子資料夾，並據以調整相對路徑參考。)

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案 **NodejsWebAppBlank**，然後選擇 [新增] > [新增項目]。

1. 在 [新增項目] 對話方塊方塊中，選擇 [TypeScript JSX 檔案]，鍵入名稱 *app.tsx*，然後選取 [確定]。

1. 重複這些步驟來新增 *webpack-config.js*。 選擇 [JavaScript 檔案]，而非 TypeScript JSX 檔案。

1. 重複相同的步驟，以將 *index.html* 新增至專案。 請選擇 [HTML 檔案]，而不是 JavaScript 檔案。

1. 重複相同的步驟，以將 *tsconfig.json* 新增至專案。 請選擇 [TypeScript JSON 組態檔]，而不是 JavaScript 檔案。

## <a name="add-app-code"></a>新增應用程式程式碼

1. 開啟 *server.js*，並以下列程式碼取代此程式碼：

    ```javascript
    'use strict';
    var path = require('path');
    var express = require('express');

    var app = express();

    var staticPath = path.join(__dirname, '/');
    app.use(express.static(staticPath));

    // Allows you to set port in the project properties.
    app.set('port', process.env.PORT || 3000);

    var server = app.listen(app.get('port'), function() {
        console.log('listening');
    });
    ```

   上述程式碼會使用 Express 來啟動 Node.js 作為 Web 應用程式伺服器。 此程式碼會將連接埠設定為專案屬性中設定的連接埠號碼 (根據預設，連接埠在屬性中設定為 1337)。 若要開啟專案屬性，請以滑鼠右鍵按一下 [方案總管] 中的專案，然後選擇 [屬性]。

1. 開啟 *app.tsx*，並新增下列程式碼：

    ```javascript
    declare var require: any

    var React = require('react');
    var ReactDOM = require('react-dom');

    class Hello extends React.Component {
        render() {
            return (
                <h1>Welcome to React!!</h1>
            );
        }
    }

    ReactDOM.render(<Hello />, document.getElementById('root'));
    ```

    上述程式碼會使用 JSX 語法和 React 來顯示簡單的訊息。

1. 開啟 *index.html*，並將 **body** 區段取代為下列程式碼：

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    這個 HTML 網頁會載入 *app-bundle.js*，其中包含轉換為純文字 JavaScript 的 JSX 和 React 程式碼。 目前，*app-bundle.js* 是一個空白檔案。 在下一個區段中，您可以設定選項來轉換程式碼。

## <a name="configure-webpack-and-typescript-compiler-options"></a>設定 webpack 和 TypeScript 編譯器選項

在先前的步驟中，您已將 *webpack-config.js* 新增至專案。 接下來，您可以新增 webpack 組態程式碼。 您將新增一個簡單的 webpack 組態，其可指定輸入檔 (*app.tsx*) 和輸出檔 (*app-bundle.js*)，用來統合 JSX 並將其轉譯為純文字 JavaScript。 對於轉譯，您還可以設定一些 TypeScript 編譯器選項。 這個程式碼是基本組態，主要是用來簡介 webpack 和 TypeScript 編譯器。

1. 在 [方案總管] 中，開啟 *webpack-config.js*，然後新增下列程式碼。

    ```json
    module.exports = {
        devtool: 'source-map',
        entry: "./app.tsx",
        mode: "development",
        output: {
            filename: "./app-bundle.js"
        },
        resolve: {
            extensions: ['.Webpack.js', '.web.js', '.ts', '.js', '.jsx', '.tsx']
        },
        module: {
            rules: [
                {
                    test: /\.tsx$/,
                    exclude: /(node_modules|bower_components)/,
                    use: {
                        loader: 'ts-loader'
                    }
                }
            ]
        }
    }
    ```

    webpack 組態程式碼會指示 Webpack 使用 TypeScript 載入器來轉換 JSX。

1. 開啟 *tsconfig.json*，然後將預設程式碼取代為指定 TypeScript 編譯器選項的下列程式碼：

    ```json
    {
      "compilerOptions": {
        "noImplicitAny": false,
        "module": "commonjs",
        "noEmitOnError": true,
        "removeComments": false,
        "sourceMap": true,
        "target": "es5",
        "jsx": "react"
      },
      "exclude": [
        "node_modules"
      ],
      "files": [
        "app.tsx"
      ]
    }
    ```

    *app.tsx* 已指定為原始程式檔。

## <a name="transpile-the-jsx"></a>轉換 JSX

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案節點，然後選擇 [在這裡開命令提示字元]。

1. 在命令提示字元中鍵入下列命令：

    `node_modules\.bin\webpack app.tsx --config webpack-config.js`

    [命令提示字元] 視窗會顯示結果。

    ![執行 webpack](../javascript/media/tutorial-nodejs-react-run-webpack.png)

    如果看到任何錯誤，而不是上述的輸出，您必須在應用程式運作之前解決這些錯誤。 如果您的 npm 套件版本與本教學課程中顯示的版本不同，這可能是錯誤的來源。 修正錯誤的其中一種方法是使用先前步驟中所顯示的確切版本。 此外，如果這些套件版本的其中一或多個版本已遭取代而導致錯誤，您可能需要安裝較新的版本來修正錯誤。

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案節點，並選擇 [新增] > [現有資料夾]，然後選擇 *dist* 資料夾，並選擇 [選取資料夾]。

    Visual Studio 會將 *dist* 資料夾新增至專案，其中包含 *app-bundle.js* 和 *app-bundle.js.map*。

1. 開啟 *app-bundle.js* 以查看轉換的 JavaScript 程式碼。

1. 如果系統提示您重新載入外部修改的檔案，請選取 [全部皆是]。

    ![載入已修改的檔案](../javascript/media/tutorial-nodejs-react-reload-files.png)

每次變更 *app.tsx* 時，您必須重新執行 webpack 命令。

## <a name="run-the-app"></a>執行應用程式

1. 請確定已選取 Chrome 作為目前的偵錯目標。

    ![選取 Chrome 作為偵錯目標](../javascript/media/tutorial-nodejs-react-debug-target.png)

1. 若要執行應用程式，請按 **F5** ([偵錯] > [開始偵錯]) 或綠色箭號按鈕。

    Node.js 主控台視窗隨即開啟，其中顯示偵錯工具正在接聽的通訊埠。

    Visual Studio 會啟動 *server.js* 這個啟動檔案，藉以啟動應用程式。

    ![在瀏覽器中執行 React](../javascript/media/tutorial-nodejs-react-running-react.png)

1. 關閉瀏覽器視窗。

1. 關閉主控台視窗。

## <a name="set-a-breakpoint-and-run-the-app"></a>設定中斷點並執行應用程式

1. 在 *server.js* 中，按一下 `staticPath` 宣告左側的裝訂邊，以設定中斷點：

    ![設定中斷點](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    中斷點是可靠偵錯最基本也最重要的功能。 中斷點會指出 Visual Studio 應暫停程式碼執行的地方，如此一來您可以查看變數的值或記憶體的行為，或查看程式碼分支是否正在執行。

1. 若要執行應用程式，請按 **F5** ([偵錯] > [開始偵錯])。

    偵錯工具會在您設定的中斷點處暫停 (目前的陳述式以黃色標示)。 現在，您可以將滑鼠指標停留在目前位於範圍內的變數上，並使用偵錯工具視窗 (如 [區域變數] 和 [監看式] 視窗)，藉以檢查應用程式狀態。

1. 按 **F5** 繼續執行應用程式。

1. 如果您想要使用 Chrome Developer Tools，請按 **F12**。 您可以使用這些工具來檢查 DOM，並使用 JavaScript 主控台與應用程式互動。

1. 關閉網頁瀏覽器和主控台。

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>設定和叫用用戶端 React 程式碼的中斷點

在上一節中，您已將偵錯工具附加到伺服器端 Node.js 程式碼。 若要從 Visual Studio 附加偵錯工具，並叫用用戶端 React 程式碼的中斷點，偵錯工具必須協助識別正確的處理序。 以下是啟用此功能的其中一種方式。

1. 關閉所有 Chrome 視窗。

1. 從 Windows [開始] 按鈕開啟 [執行] 命令 (按一下滑鼠右鍵，並選擇 [執行])，然後輸入下列命令：

    `chrome.exe --remote-debugging-port=9222`

    這會啟動 Chrome 並啟用偵錯。

1. 切換至 Visual Studio，然後在 *app-bundle.js* 程式碼的 `render()` 函式中設定中斷點，如下圖所示：

    ![設定中斷點](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

1. 將 Chrome 選取為 Visual Studio 的偵錯目標後，請按 **Ctrl**+**F5** ([偵錯] > [啟動但不偵錯]) 以在瀏覽器中執行應用程式。

    應用程式會在新的瀏覽器索引標籤中開啟。

1. 選擇 [偵錯] > [附加至處理序]。

1. 在 [附加至處理序] 對話方塊中，於 [附加至] 欄位中選擇 [Webkit 程式碼]，在篩選方塊中鍵入 **chrome** 以篩選搜尋結果。

1. 選取具有正確主機通訊埠 (在此範例中為 1337) 的 Chrome 處理序，然後選取 [附加]。

    ![附加至處理序](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    當 [DOM 總管] 和 JavaScript 主控台在 Visual Studio 中開啟時，您就知道偵錯工具已正確附加。 這些偵錯工具類似於 Chrome Developer Tools 和 Edge 的 F12 工具。

    > [!NOTE]
    > 如果偵錯工具未附加，而且您看到訊息「無法附加到處理序。 作業在目前狀態中不合法。請在將 Chrome 啟動為偵錯模式之前，先使用工作管理員關閉 Chrome 的所有執行個體。 Chrome 擴充功能可能會執行，並防止完整的偵錯模式。

1. 因為已執行具有中斷點的程式碼，所以請重新整理瀏覽器頁面以叫用中斷點。

    在偵錯工具中暫停時，您可以將滑鼠指標停留在變數上，並使用偵錯工具視窗，藉以檢查應用程式狀態。 您可以逐步執行程式碼 (**F5**、**F10** 和 **F11**) 來推進偵錯工具。

    根據您的環境和瀏覽器狀態而定，您可能會叫用 *app-bundle.js* 的中斷點，或它在 *app.tsx* 中對應的位置。 不論哪一種方式，您都可以逐步執行程式碼並檢查變數。

    * 如果您需要在 *app.tsx* 內中斷程式碼，但無法這麼做，請使用上一步中所述的 [附加至處理序] 來附加偵錯工具。 然後藉由從 [方案總管] 開啟 [指令碼文件] > [app.tsx] 來開啟動態產生的 *app.tsx* 檔案，接著設定中斷點並在瀏覽器中重新整理頁面 (在允許中斷點的程式碼行中設定繼點，例如 `return` 陳述式或 `var` 宣告)。

        或者，如果您要在 *app.tsx* 內中斷程式碼，但而無法這樣做，請嘗試在 *app.tsx* 中使用 `debugger;` 陳述式，或改為在 Chrome 開發人員工具中設定中斷點。

    * 如果您要在 *app-bundle.js* 內中斷程式碼，但無法這麼做，請移除來源對應檔 (*app-bundle.js.map*)。

    > [!TIP]
    > 依照下列步驟第一次附加至處理序之後，在 Visual Studio 2017 中選擇 [偵錯] > [重新附加至處理序]，即可快速地重新附加至相同的處理序。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [將應用程式部署至 Linux App Service](../javascript/publish-nodejs-app-azure.md)