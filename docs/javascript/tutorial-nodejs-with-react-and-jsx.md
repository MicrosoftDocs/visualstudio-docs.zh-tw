---
title: 建立 Node.js 與 React 應用程式
description: 在本教學課程中，您會使用適用於 Visual Studio 的 Node.js 工具來建立應用程式
ms.custom: mvc
ms.date: 11/01/2019
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 2f14a5f2255f7ba1b077ead60147a6df407970fc
ms.sourcegitcommit: f9f389e72787de30eb869a55ef7725a10a4011f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2019
ms.locfileid: "73636560"
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

## <a name="before-you-begin"></a>開始之前

以下快速常見問題集介紹一些重要概念。

### <a name="what-is-nodejs"></a>什麼是 Node.js？

Node.js 是執行 JavaScript 伺服器端的伺服器端 JavaScript 執行階段環境。

### <a name="what-is-npm"></a>什麼是 npm？

npm 是 Node.js 的預設套件管理員。 套件管理員可讓程式設計人員能夠發佈並共用 Node.js 程式庫的原始程式碼，其設計目的是為了簡化程式庫的安裝、更新及解除安裝。

### <a name="what-is-react"></a>什麼是 React？

React 是前端架構，用來建立 UI。

### <a name="what-is-jsx"></a>什麼是 JSX？

JSX 是 JavaScript 語法延伸模組，通常搭配 React 使用以描述 UI 項目。 JSX 程式碼必須轉換為純文字 JavaScript，才可以在瀏覽器中執行。

### <a name="what-is-webpack"></a>什麼是 webpack？

Webpack 搭配 JavaScript 檔案，讓它們可以在瀏覽器中執行。 它也可以轉換或封裝其他資源和資產。 它經常用來指定編譯器，例如 Babel 或 TypeScript，將 JSX 或 TypeScript 程式碼轉換為純文字 JavaScript。

## <a name="prerequisites"></a>Prerequisites

* 您必須安裝 Visual Studio 和 Node.js 開發工作負載。

    ::: moniker range=">=vs-2019"
    如果您尚未安裝 Visual Studio 2019，請前往  [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/) 頁面免費進行安裝。
    ::: moniker-end
    ::: moniker range="vs-2017"
    如果您尚未安裝 Visual Studio 2017，請前往  [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/) 頁面免費進行安裝。
    ::: moniker-end

    如果您需要安裝工作負載，但已安裝 Visual Studio，請移至 [工具] > [取得工具與功能...]，以開啟 Visual Studio 安裝程式。 選擇 [Node.js 開發] 工作負載，然後選擇 [修改]。

    ![VS 安裝程式中的 Node.js 工作負載](../ide/media/quickstart-nodejs-workload.png)

* 您必須安裝 Node.js 執行階段。

    本教學課程已使用 10.16.0 版進行測試。

    如果您沒有安裝，請從 [Node.js](https://nodejs.org/en/download/) 網站安裝 LTS 版本。 一般而言，Visual Studio 會自動偵測已安裝的 Node.js 執行階段。 如果偵測不到已安裝的執行階段，您可以在屬性頁面中將專案設定為參考已安裝的執行階段 (建立專案之後，以滑鼠右鍵按一下專案節點，然後選擇 [屬性])。

## <a name="create-a-project"></a>建立專案

首先，請建立 Node.js Web 應用程式專案。

1. 開啟 Visual Studio。

1. 建立新的專案。

    ::: moniker range=">=vs-2019"
    按 **Esc** 關閉開始視窗。 鍵入 **Ctrl + Q** 開啟 [搜尋] 方塊，再鍵入 **Node.js**，然後選擇 [空白的 Node.js Web 應用程式] (JavaScript)。 在出現的對話方塊中，選擇 [建立]。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從頂端功能表列中，選擇 [檔案] > [新增] > [專案]。 在 [新增專案] 對話方塊的左窗格中，展開 **JavaScript**，然後選擇 **Node.js**。 在中間窗格中，選擇 [空白的 Node.js Web 應用程式]、輸入名稱 **NodejsWebAppBlank**，然後選擇 [確定]。
    ::: moniker-end
    如果您看不到 [空白的 Node.js Web 應用程式] 專案範本，則必須新增 **Node.js 開發**工作負載。 如需詳細指示，請參閱[必要條件](#prerequisites)。

    Visual Studio 會建立新的方案，並開啟專案。

    ![[方案總管] 中的 Node.js 專案](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1) 以**粗體**反白顯示的項目就是您的專案，並使用您在 [新增專案] 對話方塊中所指定的名稱。 在檔案系統中，此專案是由專案資料夾中的 *.njsproj* 檔案所呈現。 您可以設定與專案建立關聯的屬性和環境變數，方法是以滑鼠右鍵按一下專案，然後選擇 [屬性]。 因為專案檔不會對 Node.js 專案來源進行自訂變更，所以您可以使用其他開發工具執行來回行程。

    (2) 最上層是方案，其名稱預設會與專案相同。 方案 (以磁碟上的 *.sln* 檔案呈現) 是一或多個相關專案的容器。

    (3) npm 節點會顯示任何已安裝的 npm 套件。 您可以用滑鼠右鍵按一下 npm 節點，使用對話方塊來搜尋及安裝 npm 套件，或者使用 *package.json* 中的設定來安裝及更新套件，並以滑鼠右鍵按一下 npm 節點中的選項。

    (4) *package.json* 是 npm 用來管理本機安裝套件之套件相依性和套件版本的檔案。 如需這個檔案的詳細資訊，請參閱 [package.json 組態](../javascript/configure-packages-with-package-json.md)

    (5) *server.js* 之類的專案檔會顯示在專案節點下。 *server.js* 是專案啟動檔案，這也是它會以**粗體**顯示的原因。 以滑鼠右鍵按一下專案中的檔案，然後選取 [設定為 Node.js 啟動檔案]，即可設定啟動檔案。

## <a name="add-npm-packages"></a>新增 npm 套件

此應用程式需要 npm 模組的數目才能正確執行。

* react
* react-dom
* express
* path
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

1. 請將下列程式碼貼入 *package.json*，而不是使用 UI 來搜尋其餘的套件並一次新增一個。 若要這樣做，請新增具有下列程式碼的 `dependencies` 區段：

    ```json
    "dependencies": {
      "express": "~4.16.4",
      "path": "~0.12.7",
      "react": "~16.6.0",
      "react-dom": "~16.6.0",
      "ts-loader": "~5.3.0",
      "typescript": "~3.1.5",
      "webpack": "~4.23.1",
      "webpack-cli": "~3.1.2"
    }
    ```

    如果在您的空白範本版本中已經有 `dependencies` 區段，只需將它取代為上述 JSON 程式碼。 如需使用此檔案的詳細資訊，請參閱[package. json configuration](../javascript/configure-packages-with-package-json.md)。

1. 儲存變更。

1. 以滑鼠右鍵按一下專案中的 [npm] 節點，然後選擇 [更新 npm 套件]。

    在下方窗格中，選取 [輸出] 視窗以查看套件安裝進度。 安裝可能需要幾分鐘的時間，您可能無法立即查看結果。 若要查看輸出，請務必選取 [輸出] 視窗中 [顯示輸出來源] 欄位中的 [Npm]。

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

1. 在 [**加入新專案**] 對話方塊中，選擇 [ **TypeScript JSX**檔案]，輸入*app.config*的名稱，然後選取 [**新增** **] 或 [確定]** 。

1. 重複這些步驟來新增 *webpack-config.js*。 選擇 [JavaScript 檔案]，而非 TypeScript JSX 檔案。

1. 重複相同的步驟，以將 *index.html* 新增至專案。 請選擇 [HTML 檔案]，而不是 JavaScript 檔案。

1. 重複相同的步驟，以將 *tsconfig.json* 新增至專案。 請選擇 [TypeScript JSON 組態檔]，而不是 JavaScript 檔案。

## <a name="add-app-code"></a>新增應用程式程式碼

1. 開啟 *server.js*，並以下列程式碼取代現有的程式碼：

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

    export class Hello extends React.Component {
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

    Webpack 組態程式碼會指示 Webpack 使用 TypeScript 載入器來轉換 JSX。

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

    如果看到任何錯誤，而不是上述的輸出，您必須在應用程式運作之前解決這些錯誤。 如果您的 npm 套件版本與本教學課程中顯示的版本不同，這可能是錯誤的來源。 修正錯誤的其中一種方法是使用先前步驟中所顯示的確切版本。 此外，如果這些套件版本的其中一或多個版本已遭取代而導致錯誤，您可能需要安裝較新的版本來修正錯誤。 如需使用 *package.json*控制 npm 套件版本的資訊，請參閱 [package.json 組態](../javascript/configure-packages-with-package-json.md)。

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案節點，並選擇 [新增] > [現有資料夾]，然後選擇 *dist* 資料夾，並選擇 [選取資料夾]。

    Visual Studio 會將 *dist* 資料夾新增至專案，其中包含 *app-bundle.js* 和 *app-bundle.js.map*。

1. 開啟 *app-bundle.js* 以查看轉換的 JavaScript 程式碼。

1. 如果系統提示您重新載入外部修改的檔案，請選取 [全部皆是]。

    ![載入已修改的檔案](../javascript/media/tutorial-nodejs-react-reload-files.png)

每次變更 *app.tsx* 時，您必須重新執行 webpack 命令。 若要將此步驟自動化，請新增組建指令碼來轉換 JSX。

## <a name="add-a-build-script-to-transpile-the-jsx"></a>新增組建指令碼來轉換 JSX

從 Visual Studio 2019 開始，需要組建指令碼。 您可以在從 Visual Studio 建置時轉換 JSX，而不是在命令列上轉譯 JSX (如上一節中所示)。

* 開啟 *package.json*，並在 `dependencies` 區段之後新增下列區段：

   ```json
   "scripts": {
    "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

## <a name="run-the-app"></a>執行應用程式

1. 選取 [Microsoft Edge] 或 [Chrome] 做為目前的「調試目標」。

    ::: moniker range=">=vs-2019"
    ![選取 Chrome 作為偵錯目標](../javascript/media/vs-2019/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![選取 Chrome 作為偵錯目標](../javascript/media/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end

    ::: moniker range=">=vs-2019"
    如果您的電腦上有 Chrome 可用，但未顯示為選項，請選擇 [**網頁瀏覽器（browsername）** ] > 從 [偵錯工具目標] 下拉式清單中**選取 [網頁瀏覽器**]，然後選取 [ **Chrome** ] 做為預設瀏覽器目標。
    ::: moniker-end
    ::: moniker range="vs-2017"
    如果您的電腦上有 Chrome 可用，但未顯示為選項，請從 [偵錯工具目標] 下拉式清單中選擇 [ **Web 瀏覽器（browsername）** ] > **Google Chrome** ，然後選取 [ **Chrome** ] 做為預設瀏覽器目標。
    ::: moniker-end

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

1. 如果您想要使用適用于 Microsoft Edge 的 Chrome 開發人員工具或 F12 工具，請按**F12**。 您可以使用這些工具來檢查 DOM，並使用 JavaScript 主控台與應用程式互動。

1. 關閉網頁瀏覽器和主控台。

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>設定和叫用用戶端 React 程式碼的中斷點

在上一節中，您已將偵錯工具附加到伺服器端 Node.js 程式碼。 若要從 Visual Studio 附加偵錯工具，並叫用用戶端 React 程式碼的中斷點，偵錯工具必須協助識別正確的處理序。 以下是啟用此功能的其中一種方式。

### <a name="prepare-the-browser-for-debugging"></a>準備瀏覽器以進行偵錯工具

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

1. 切換至 Visual Studio，然後在您的原始程式碼中設定中斷點，可以是*app-bundle.js.map*或*app.config*。

    針對*app-bundle.js.map*，在 `render()` 函式中設定中斷點，如下圖所示：

    ![設定中斷點](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    若要在轉換*app-bundle.js.map*檔案中尋找 `render()` 函式，請使用**Ctrl**+**F** （**編輯** > 尋找**和 取代** > **快速尋找**）。

    針對*app.config*，請在 `return` 語句上的 `render()` 函式內設定中斷點。

    ![設定中斷點](../javascript/media/tutorial-nodejs-react-set-breakpoint-in-tsx-file.png)

2. 如果您要在*tsx*檔案中設定中斷點（而不是*app-bundle.js.map*），則必須更新*webpack-config.js*。 取代下列程式碼：

    ```javascript
    output: {
        filename: "./app-bundle.js",
    },
    ```

    取代為此程式碼：

    ```javascript
    output: {
        filename: "./app-bundle.js",
        devtoolModuleFilenameTemplate: '[resource-path]'  // removes the webpack:/// prefix
    },
    ```

    這是僅限開發的設定，可在 Visual Studio 中啟用調試。 此設定可讓您在建立應用程式時，覆寫來源對應檔（ *app-bundle.js.map*）中產生的參考。 根據預設，來源對應檔案中的 webpack 參考包含*webpack:///* 前置詞，這可防止 Visual Studio 尋找原始程式檔（ *tsx*）。 具體來說，當您進行這種變更時，會將來源檔案（app.config）的參考從*webpack:///./app.tsx*變更為 *./app.tsx*，這會啟用調試*程式*。

3. 在 Visual Studio 中選取您的目標瀏覽器做為 debug 目標，然後按下**Ctrl**+**F5** （**debug** > **啟動但不進行調試**程式），以在瀏覽器中執行應用程式。

    ::: moniker range=">=vs-2019"
    如果您已建立具有易記名稱的瀏覽器設定，請選擇作為您的 debug 目標。
    ::: moniker-end

    應用程式會在新的瀏覽器索引標籤中開啟。

4. 選擇 [偵錯] > [附加至處理序]。

    > [!TIP]
    > 從 Visual Studio 2017 開始，一旦您依照下列步驟第一次附加至進程，您可以選擇 [ **Debug** ] > [重新**附加至進程**]，快速地重新附加至相同的進程。

5. 在 [**附加至進程**] 對話方塊中，取得您可以附加至之瀏覽器實例的篩選清單。

    ::: moniker range=">=vs-2019"
    在 Visual Studio 2019 中，于 [**附加至**] 欄位中選擇目標瀏覽器、 **javascript （Chrome）** 或**JAVAscript （Microsoft Edge-Chromium）** 的正確偵錯工具，在篩選方塊中輸入**Chrome**或**Edge**以篩選搜尋結果。
    ::: moniker-end
    ::: moniker range="vs-2017"
    在 Visual Studio 2017 中，選擇 [**附加至**] 欄位中的 [ **Webkit 程式碼**]，在 [篩選] 方塊中輸入**chrome**以篩選搜尋結果。
    ::: moniker-end

6. 選取具有正確主機埠（在此範例中為 localhost）的瀏覽器進程，然後選取 [**附加**]。

    埠（1337）可能也會出現在 [**標題**] 欄位中，協助您選取正確的瀏覽器實例。

    ::: moniker range=">=vs-2019"
    下列範例顯示如何尋找 Microsoft Edge （Chromium）瀏覽器。

    ![附加至處理序](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![附加至處理序](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    當 [DOM 總管] 和 JavaScript 主控台在 Visual Studio 中開啟時，您就知道偵錯工具已正確附加。 這些偵錯工具類似適用於 Microsoft Edge 的 Chrome Developer Tools 和 F12 工具。
    ::: moniker-end

    > [!TIP]
    > 如果偵錯工具未附加，而且您看到訊息「無法附加到處理序。 作業在目前狀態中不合法。」，請使用工作管理員關閉目標瀏覽器的所有實例，然後再以「偵錯工具」模式啟動瀏覽器。 瀏覽器延伸模組可能正在執行，且無法進行完整的 debug 模式。

7. 因為已執行具有中斷點的程式碼，所以請重新整理瀏覽器頁面以叫用中斷點。

    在偵錯工具中暫停時，您可以將滑鼠指標停留在變數上，並使用偵錯工具視窗，藉以檢查應用程式狀態。 您可以逐步執行程式碼 (**F5**、**F10** 和 **F11**) 來推進偵錯工具。 如需基本偵錯工具功能的詳細資訊，請參閱[偵錯工具的第一次](../debugger/debugger-feature-tour.md)查看。

    您可以在*app-bundle.js.map*中叫用中斷點或其對應*位置，視*您先前遵循的步驟而定，以及您的環境和瀏覽器狀態。 不論哪一種方式，您都可以逐步執行程式碼並檢查變數。

   * 如果您需要在 *app.tsx* 內中斷程式碼，但無法這麼做，請使用上一步中所述的 [附加至處理序] 來附加偵錯工具。 請確定您的環境已正確設定：

      * 您關閉了所有的瀏覽器實例，包括 Chrome 延伸模組（使用工作管理員），讓您可以在 [偵錯工具] 模式中執行瀏覽器。 請確定您是在 [調試] 模式下啟動瀏覽器。

      * 請確定您的來源對應檔案包含 */app.tsx*的參考，而不是*webpack:///./app.tsx*，這可防止 Visual Studio 偵錯工具尋找*應用程式的 tsx*。

       或者，如果您需要中斷 app.config 中的*程式*代碼，但無法這麼做，請嘗試在*app.config*中使用 `debugger;` 語句，或在 Chrome 開發人員工具（或適用于 Microsoft Edge 的 F12 工具）中設定中斷點。

   * 如果您需要在*app-bundle.js.map*中中斷程式碼，但無法這麼做，請移除來源對應檔*app-bundle.js.map*。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [將應用程式部署至 Linux App Service](../javascript/publish-nodejs-app-azure.md)
