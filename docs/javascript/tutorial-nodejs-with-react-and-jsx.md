---
title: 建立 Node.js 與 React 應用程式
description: 在本教學課程中，您會使用適用於 Visual Studio 的 Node.js 工具來建立應用程式
ms.custom: ''
ms.date: 4/21/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: c6813e0ad482bb211269c9da3950842dda7f6abd
ms.sourcegitcommit: a7f781d5a089e6aab6b073a07f3d4d2967af8aa6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81760095"
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>教學課程：在 Visual Studio 中建立 Node.js 和 React 應用程式

Visual Studio 可讓您輕鬆地建立 Node.js 專案，體驗 IntelliSense 和其他支援 Node.js 的內建功能。 在適用於 Visual Studio 的本教學課程中，請從 Visual Studio 範本建立 Node.js Web 應用程式專案。 然後，請使用 React 建立簡單的應用程式。

在本教學課程中，您會了解如何：
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
    如果您尚未安裝 Visual Studio 2019,請轉到 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/) 頁面免費安裝它。
    ::: moniker-end
    ::: moniker range="vs-2017"
    如果您尚未安裝 Visual Studio 2017,請轉到 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/) 頁面免費安裝它。
    ::: moniker-end

    如果您需要安裝工作負載,但已經擁有可視化工作室,請轉到 **「工具** > **獲取工具和功能...",** 這將打開可視化工作室安裝程式。 選擇 [Node.js 開發]**** 工作負載，然後選擇 [修改]****。

    ![VS 安裝程式中的 Node.js 工作負載](../ide/media/quickstart-nodejs-workload.png)

* 您必須安裝 Node.js 執行階段。

    本教程已使用版本 12.6.2 進行了測試。

    如果您沒有安裝它,我們建議您從[Node.js](https://nodejs.org/en/download/)網站安裝 LTS 版本,以便與外部框架和庫進行最佳相容性。 Node.js 是為 32 位元和 64 位體系結構構建的。 Visual Studio 中的 Node.js 工具(包含在 Node.js 工作負荷中)支援這兩個版本。 只需要一個,Node.js 安裝程式一次只支援安裝一個。
    
    一般而言，Visual Studio 會自動偵測已安裝的 Node.js 執行階段。 如果未檢測到已安裝的運行時,則可以將專案配置為引用屬性頁中的已安裝運行時(在創建專案後,右鍵單擊專案節點,選擇**屬性**,並設置**Node.exe 路徑**)。 您可以使用 Node.js 的全域安裝,也可以在每個 Node.js 專案中指定本地解釋器的路徑。 

## <a name="create-a-project"></a>建立專案

首先，請建立 Node.js Web 應用程式專案。

1. 開啟 Visual Studio。

1. 建立新專案。

    ::: moniker range=">=vs-2019"
    按 **Esc** 關閉開始視窗。 鍵入**Ctrl + Q**以開啟搜尋框,鍵入**Node.js,** 然後選擇**空白 Node.js Web 應用程式 - JAvaScript**。 (儘管本教程使用 TypeScript 編譯器,但這些步驟要求您從**JAvaScript**範本開始。
    
    在出現的對話方塊中選擇 [建立]****。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從頂部功能表欄中,選擇 **「檔** > **新專案** > **」。。** 在 [新增專案]**** 對話方塊的左窗格中，展開 **JavaScript**，然後選擇 **Node.js**。 在中間窗格中，選擇 [空白的 Node.js Web 應用程式]****、輸入名稱 **NodejsWebAppBlank**，然後選擇 [確定]****。
    ::: moniker-end
    如果看不到**空白 Node.js Web 應用程式**專案範本,則必須添加**Node.js 開發**工作負荷。 如需詳細指示，請參閱[必要條件](#prerequisites)。

    Visual Studio 會建立新的方案，並開啟專案。

    ![[方案總管] 中的 Node.js 專案](../javascript/media/tutorial-nodejs-react-project-structure.png)

    (1) 以**粗體**反白顯示的項目就是您的專案，並使用您在 [新增專案]**** 對話方塊中所指定的名稱。 在檔案系統中，此專案是由專案資料夾中的 *.njsproj* 檔案所呈現。 您可以設定與專案建立關聯的屬性和環境變數，方法是以滑鼠右鍵按一下專案，然後選擇 [屬性]****。 因為專案檔不會對 Node.js 專案來源進行自訂變更，所以您可以使用其他開發工具執行來回行程。

    (2) 最上層是方案，其名稱預設會與專案相同。 方案 (以磁碟上的 *.sln* 檔案呈現) 是一或多個相關專案的容器。

    (3) npm 節點會顯示任何已安裝的 npm 套件。 您可以用滑鼠右鍵按一下 npm 節點，使用對話方塊來搜尋及安裝 npm 套件，或者使用 *package.json* 中的設定來安裝及更新套件，並以滑鼠右鍵按一下 npm 節點中的選項。

    (4) *package.json* 是 npm 用來管理本機安裝套件之套件相依性和套件版本的檔案。 有關詳細資訊,請參閱管理[npm 包](../javascript/npm-package-management.md)。

    (5) *server.js* 之類的專案檔會顯示在專案節點下。 *server.js* 是專案啟動檔案，這也是它會以**粗體**顯示的原因。 以滑鼠右鍵按一下專案中的檔案，然後選取 [設定為 Node.js 啟動檔案]****，即可設定啟動檔案。

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

1. 在 [方案總管] (右窗格) 中，以滑鼠右鍵按一下專案中的 [npm]**** 節點，然後選擇 [安裝新的 npm 套件]****。

    在 [安裝新的 npm 套件]**** 對話方塊中，您可以選擇安裝最新的套件版本或指定版本。 如果選擇安裝這些包的當前版本,但稍後遇到意外錯誤,則可能需要安裝這些步驟後面介紹的確切包版本。

1. 在 [安裝新的 npm 套件]**** 對話方塊中，搜尋 react 套件，然後選取 [安裝套件]**** 來安裝它。

    ![安裝 npm 套件](../javascript/media/tutorial-nodejs-react-install-package.png)

    選取 [輸出]**** 視窗來查看安裝套件的進度 (選取 [顯示輸出來源]**** 欄位中的 [Npm]****)。 安裝後，套件會出現在 **npm** 節點下。

    專案的 *package.json* 檔案會以新的套件資訊 (包括套件版本) 進行更新。

1. 而不是使用 UI 來搜尋和添加套件的其餘部分一次一個,將以下代碼貼上到*套件.* 若要這樣做，請新增具有下列程式碼的 `dependencies` 區段：

    ```json
    "dependencies": {
      "express": "~4.17.1",
      "path": "~0.12.7",
      "react": "~16.13.1",
      "react-dom": "~16.13.1",
      "ts-loader": "~7.0.1",
      "typescript": "~3.8.3",
      "webpack": "~4.42.1",
      "webpack-cli": "~3.3.11"
    }
    ```

    如果在您的空白範本版本中已經有 `dependencies` 區段，只需將它取代為上述 JSON 程式碼。 有關使用此檔案的詳細資訊,請參閱[package.json 設定](../javascript/configure-packages-with-package-json.md)。

1. 儲存變更。

1. 右鍵按一下專案中**的 npm**節點,然後選擇 **「安裝 npm 包**」。

    此命令直接運行 npm 安裝命令。

    在下方窗格中，選取 [輸出]**** 視窗以查看套件安裝進度。 安裝可能需要幾分鐘的時間，您可能無法立即查看結果。 若要查看輸出，請務必選取 [輸出]**** 視窗中 [顯示輸出來源]**** 欄位中的 [Npm]****。

    以下是安裝後顯示在 [方案總管] 中的 npm 模組。

    ![npm 套件](../javascript/media/tutorial-nodejs-react-npm-modules-installed.png)

    > [!NOTE]
    > 如果您想要使用命令列來安裝 npm 套件，請以滑鼠右鍵按一下專案節點，然後選擇 [在這裡開啟命令提示字元]****。 使用標準的 Node.js 命令來安裝套件。

## <a name="add-project-files"></a>新增專案檔

在這些步驟中，您會將四個新的檔案新增至專案中。

* *app.tsx*
* *webpack-config.js*
* *索引.html*
* *tsconfig.json*

針對這個簡單的應用程式，您可以在專案根目錄中新增專案檔。 (在大部分的應用程式中，您通常會將檔案新增至子資料夾，並據以調整相對路徑參考。)

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案 **NodejsWebAppBlank**，然後選擇 [新增]**** > [新增項目]****。

1. 在 **「新增新項目」** 對話方塊中,選擇**TypeScript JSX 檔**,鍵入名稱*應用程式.tsx,* 然後選擇 **「添加**」**或「確定**」 。

1. 重複這些步驟來新增 *webpack-config.js*。 選擇 [JavaScript 檔案]****，而非 TypeScript JSX 檔案。

1. 重複相同的步驟，以將 *index.html* 新增至專案。 請選擇 [HTML 檔案]****，而不是 JavaScript 檔案。

1. 重複相同的步驟，以將 *tsconfig.json* 新增至專案。 請選擇 [TypeScript JSON 組態檔]****，而不是 JavaScript 檔案。

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

   上述程式碼會使用 Express 來啟動 Node.js 作為 Web 應用程式伺服器。 此程式碼會將連接埠設定為專案屬性中設定的連接埠號碼 (根據預設，連接埠在屬性中設定為 1337)。 若要開啟專案屬性，請以滑鼠右鍵按一下 [方案總管] 中的專案，然後選擇 [屬性]****。

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

    *app.tsx*被指定為源檔。

## <a name="transpile-the-jsx"></a>轉換 JSX

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案節點，然後選擇 [在這裡開命令提示字元]****。

1. 在命令提示字元中鍵入下列命令：

    `node_modules\.bin\webpack app.tsx --config webpack-config.js`

    [命令提示字元] 視窗會顯示結果。

    ![執行 webpack](../javascript/media/tutorial-nodejs-react-run-webpack-cmd.png)

    如果看到任何錯誤，而不是上述的輸出，您必須在應用程式運作之前解決這些錯誤。 如果您的 npm 套件版本與本教學課程中顯示的版本不同，這可能是錯誤的來源。 修正錯誤的其中一種方法是使用先前步驟中所顯示的確切版本。 此外，如果這些套件版本的其中一或多個版本已遭取代而導致錯誤，您可能需要安裝較新的版本來修正錯誤。 如需使用 *package.json*控制 npm 套件版本的資訊，請參閱 [package.json 組態](../javascript/configure-packages-with-package-json.md)。

1. 在「解決方案資源管理器」中,右鍵單擊專案節點並選擇 **「添加** > **現有資料夾**」,然後選擇 *「分離資料夾*」並選擇 **「選擇資料夾**」 。

    Visual Studio 會將 *dist* 資料夾新增至專案，其中包含 *app-bundle.js* 和 *app-bundle.js.map*。

1. 開啟 *app-bundle.js* 以查看轉換的 JavaScript 程式碼。

1. 如果系統提示您重新載入外部修改的檔案，請選取 [全部皆是]****。

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

1. 選擇**Web 伺服器(Google Chrome)** 或**Web 伺服器(微軟邊緣)** 作為當前調試目標。

    ::: moniker range=">=vs-2019"
    ![選取 Chrome 作為偵錯目標](../javascript/media/vs-2019/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![選取 Chrome 作為偵錯目標](../javascript/media/tutorial-nodejs-react-debug-target.png)
    ::: moniker-end

    如果您的電腦中有 Chrome 可供使用，但未顯示為選項，請從偵錯目標下拉式清單中選擇 [瀏覽方式]****，並選取 Chrome 作為預設瀏覽器目標 (選擇 [設為預設值]****)。

1. 若要執行應用程式，請按 **F5** ([偵錯]**** > [開始偵錯]****) 或綠色箭號按鈕。

    Node.js 主控台視窗隨即開啟，其中顯示偵錯工具正在接聽的通訊埠。

    Visual Studio 會啟動 *server.js* 這個啟動檔案，藉以啟動應用程式。

    ![在瀏覽器中執行 React](../javascript/media/tutorial-nodejs-react-running-react.png)

1. 關閉瀏覽器視窗。

1. 關閉主控台視窗。

## <a name="set-a-breakpoint-and-run-the-app"></a>設定中斷點並執行應用程式

1. 在 *server.js* 中，按一下 `staticPath` 宣告左側的裝訂邊，以設定中斷點：

    ![設定中斷點](../javascript/media/tutorial-nodejs-react-set-breakpoint.png)

    中斷點是可靠偵錯最基本也最重要的功能。 中斷點會指出 Visual Studio 應暫停程式碼執行的地方，如此一來您可以查看變數的值或記憶體的行為，或查看程式碼分支是否正在執行。

1. 若要執行應用程式，請按 **F5** ([偵錯]**** > [開始偵錯]****)。

    偵錯工具會在您設定的中斷點處暫停 (目前的陳述式以黃色標示)。 現在，您可以將滑鼠指標停留在目前位於範圍內的變數上，並使用偵錯工具視窗 (如 [區域變數]**** 和 [監看式]**** 視窗)，藉以檢查應用程式狀態。

1. 按 **F5** 繼續執行應用程式。

1. 如果您想使用 Chrome 開發人員工具或 F12 工具進行微軟邊緣,請按**F12**。 您可以使用這些工具來檢查 DOM，並使用 JavaScript 主控台與應用程式互動。

1. 關閉網頁瀏覽器和主控台。

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>設定和叫用用戶端 React 程式碼的中斷點

在上一節中，您已將偵錯工具附加到伺服器端 Node.js 程式碼。 若要從 Visual Studio 附加偵錯工具，並叫用用戶端 React 程式碼的中斷點，偵錯工具必須協助識別正確的處理序。 以下是啟用此功能的其中一種方式。

### <a name="prepare-the-browser-for-debugging"></a>準備瀏覽器進行除錯

::: moniker range=">=vs-2019"
對於此方案,請使用當前在IDE中命名為Microsoft**邊緣測試版的**Microsoft邊緣(鉻)或Chrome。
::: moniker-end
::: moniker range="vs-2017"
對於此方案,請使用 Chrome。
::: moniker-end

1. 關閉目標瀏覽器的所有視窗。

   其他瀏覽器實例可能會阻止瀏覽器在啟用調試后打開。 (瀏覽器擴展程式可能正在運行並阻止完全調試模式,因此您可能需要打開任務管理器才能查找 Chrome 的意外實例。

   ::: moniker range=">=vs-2019"
   對於微軟邊緣(鉻),也關閉所有Chrome實例。 由於兩個瀏覽器共用鉻代碼庫,因此可提供最佳結果。
   ::: moniker-end

2. 啟用調試後啟動瀏覽器。

    ::: moniker range=">=vs-2019"
    從 Visual Studio`--remote-debugging-port=9222`2019 開始, 您可以通過從 **「除錯」** 工具列中選擇 **「瀏覽與...** >,然後選擇 **「新增**」,然後在 **「參數」** 欄位中設定標誌,從而在瀏覽器啟動時設定標誌。 對瀏覽器使用不同的友好名稱,如 **「使用調試邊緣」** 或 **「使用調試的 Chrome」。。** 如需詳細資訊，請參閱[版本資訊](/visualstudio/releases/2019/release-notes-v16.2)。

    ![將瀏覽器設定為啟用除錯後開啟](../javascript/media/tutorial-nodejs-react-edge-with-debugging.png)

    或者,從 Windows**開始**按鈕打開 **「執行」** 命令(右鍵按一下並選擇 **」執行**「執行」」,然後輸入以下命令:

    `msedge --remote-debugging-port=9222`

    或者，

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    ::: moniker range="vs-2017"
    從 Windows [開始]**** 按鈕開啟 [執行]**** 命令 (按一下滑鼠右鍵，並選擇 [執行]****)，然後輸入下列命令：

    `chrome.exe --remote-debugging-port=9222`
    ::: moniker-end

    這將在啟用調試後啟動瀏覽器。

    該應用程式尚未運行,因此您將獲得一個空瀏覽器頁面。

### <a name="attach-the-debugger-to-client-side-script"></a>將除錯程式附加到客戶端文稿

1. 切換到 Visual Studio,然後在原始碼中設定斷點,無論是*應用捆綁.js*還是*app.tsx*。

    對於*應用捆綁.js*,設置函`render()`數中的 斷點,如下圖所示:

    ![設定中斷點](../javascript/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

    要在`render()`轉貼*應用 bundle.js*檔中尋找函數,請使用**Ctrl**+**F(****編輯** > **查找和替換** > **快速搜尋**)。

    對於*app.tsx*`render()``return`,在語句上設置函數內的斷點。

    ![設定中斷點](../javascript/media/tutorial-nodejs-react-set-breakpoint-in-tsx-file.png)

2. 如果要在 *.tsx*檔中設定斷點(而不是*套用 bundle.js),* 則需要更新*Webpack-config.js*。 將下列程式碼：

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

    這是一個僅開發設置,用於在 Visual Studio 中啟用調試。 此設定允許您在生成應用時覆蓋源映射檔*app-bundle.js.map*中的生成引用。 預設情況下,源地圖檔中的 Webpack 引用包含*webpack:///* 前置前置前置,這阻止 Visual Studio 尋找來源*檔案 app.tsx*。 具體而言,當您進行此更改時,對源檔的*引用 app.tsx*將從*webpack:///./app.tsx*更改為 *./app.tsx*,這支持調試。

3. 選擇目標瀏覽器作為 Visual Studio 中的調試目標,然後按**Ctrl**+**Debug** > **F5(****除錯啟動而不調試**)在瀏覽器中運行應用。

    ::: moniker range=">=vs-2019"
    如果建立具有友好名稱的瀏覽器配置,請選擇該配置作為調試目標。
    ::: moniker-end

    應用程式會在新的瀏覽器索引標籤中開啟。

4. 選擇**除錯** > **附加到行程**。

    > [!TIP]
    > 從 Visual Studio 2017 開始,一旦您第一次通過執行這些步驟附加到流程,您可以通過選擇**調試** > **重新附加到進程**來快速重新附加到同一進程。

5. 在 **「附加到行程」** 對話方塊中,獲取可附加到的瀏覽器實例的篩選清單。

    ::: moniker range=">=vs-2019"
    在 Visual Studio 2019 中,在「附加到欄位」中為目標瀏覽器選擇正確的調試器,在 **「附加到**欄位」中為**JAVAScript(Chrome)** 或**JavaScript(微軟邊緣 - 鉻)** 選擇,在篩選器框中鍵入**鑲邊**或**邊緣**以篩選搜尋結果。
    ::: moniker-end
    ::: moniker range="vs-2017"
    在 Visual Studio 2017 中,在 **『附加到**欄位』中選擇**Webkit 程式碼**,在篩選器框中鍵入**鑲邊**以篩選搜尋結果。
    ::: moniker-end

6. 選擇有正確主機連接埠(本範例的本地主機)的瀏覽器程序,然後選擇**附加**。

    埠 (1337) 也可能顯示在 **「標題」** 欄位中,以説明您選擇正確的瀏覽器實例。

    ::: moniker range=">=vs-2019"
    下面的示例顯示了 Microsoft 邊緣(鉻)瀏覽器的外觀。

    ![附加至處理序](../javascript/media/tutorial-nodejs-react-attach-to-process-edge.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![附加至處理序](../javascript/media/tutorial-nodejs-react-attach-to-process.png)

    當 [DOM 總管] 和 JavaScript 主控台在 Visual Studio 中開啟時，您就知道偵錯工具已正確附加。 這些偵錯工具類似適用於 Microsoft Edge 的 Chrome Developer Tools 和 F12 工具。
    ::: moniker-end

    > [!TIP]
    > 如果偵錯工具未附加，而且您看到訊息「無法附加到處理序。 操作在當前狀態下不合法。" 在以除錯模式啟動瀏覽器之前,使用任務管理器關閉目標瀏覽器的所有實例。 瀏覽器擴展可能正在運行並阻止完全除錯模式。

7. 因為已執行具有中斷點的程式碼，所以請重新整理瀏覽器頁面以叫用中斷點。

    在偵錯工具中暫停時，您可以將滑鼠指標停留在變數上，並使用偵錯工具視窗，藉以檢查應用程式狀態。 您可以逐步執行程式碼 (**F5**、**F10** 和 **F11**) 來推進偵錯工具。 有關基本除錯功能的詳細資訊,請參閱[首先檢視除錯器](../debugger/debugger-feature-tour.md)。

    您可以在*應用 bundle.js*中命中斷點,也可以在*app.tsx*中在其映射的位置命中斷點,具體取決於您之前遵循的步驟以及您的環境和瀏覽器狀態。 不論哪一種方式，您都可以逐步執行程式碼並檢查變數。

   * 如果您需要在 *app.tsx* 內中斷程式碼，但無法這麼做，請使用上一步中所述的 [附加至處理序]**** 來附加偵錯工具。 確保環境設定正確:

      * 您關閉了所有瀏覽器實例,包括 Chrome 擴展名(使用任務管理器),以便您可以在調試模式下運行瀏覽器。 請確保在除錯模式下啟動瀏覽器。

      * 請確保您的來源地圖檔包含對 *./app.tsx*的引用,而不是*webpack:///./app.tsx,* 這可以防止 Visual Studio 調試器尋找*app.tsx*。
       或者,如果您需要在*app.tsx*中侵入代碼,但無法做到這一點,請`debugger;`嘗試在*app.tsx*中使用 語句,或者在 Chrome 開發人員工具(或適用於 Microsoft 邊緣的 F12 工具)中設置斷點。

   * 如果需要在*app-bundle.js*中侵入代碼,但無法做到這一點,請刪除原始檔*app-bundle.js.map*。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [將應用程式部署至 Linux App Service](../javascript/publish-nodejs-app-azure.md)
