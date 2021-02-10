---
title: 使用 Node.js 建立 Vue.js 應用程式
description: 您可以使用 Vue.js 架構在 Visual Studio 中建立 Node.js 應用程式
ms.custom: seodec18
ms.date: 07/06/2018
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 52281c403ceb0f2708aa546cbd73559593c419be
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942824"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>使用適用於 Visual Studio 的 Node.js 工具建立 Vue.js 應用程式

Visual Studio 支援使用 JavaScript 或 TypeScript 搭配 [Vue.js](https://vuejs.org/) 架構進行應用程式開發。

下列新功能支援 Visual Studio 中的 Vue.js 應用程式開發：

* 支援 *.vue* 檔案中的指令碼、樣式和範本區塊
* 辨識 *.vue* 檔案上的 `lang` 屬性
* Vue.js 專案和檔案範本

## <a name="prerequisites"></a>必要條件

* 您必須安裝 Visual Studio 2017 15.8 版或更新版本，以及 **Node.js 開發** 工作負載。

    > [!IMPORTANT]
    > 此文章需要的功能是從 Visual Studio 2017 15.8 版開始提供。

    ::: moniker range=">=vs-2019"
    如果尚未安裝必要版本，請安裝 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)。
    ::: moniker-end
    ::: moniker range="vs-2017"
    如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。
    ::: moniker-end

    如果您需要安裝工作負載，但已有 Visual Studio，請移至 [**工具**  >  **取得工具和功能**]，這會開啟 Visual Studio 安裝程式。 選擇 [Node.js 開發] 工作負載，然後選擇 [修改]。

* 若要建立 ASP.NET Core 專案，您必須安裝 ASP.NET 與網頁程式開發工作負載，以及 .NET Core 跨平台開發工作負載。

* 您必須安裝 Node.js 執行階段。

    如果您沒有安裝，請從 [Node.js](https://nodejs.org/en/download/) 網站安裝 LTS 版本。 一般而言，Visual Studio 會自動偵測已安裝的 Node.js 執行階段。 如果它沒有偵測到已安裝的執行階段，您可以將專案設定為參考屬性頁面中已安裝的執行階段。 (建立專案之後，請以滑鼠右鍵按一下專案節點，然後選擇 [屬性])。

## <a name="create-a-vuejs-project-using-nodejs"></a>使用 Node.js 建立 Vue.js 專案

您可以使用新的 Vue.js 範本來建立新專案。 使用範本是最簡單的使用者入門方式。 如需詳細步驟，請參閱[使用 Visual Studio 建立您的第一個 Vue.js 應用程式](../javascript/quickstart-vuejs-with-nodejs.md)。

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>使用 ASP.NET Core 和 Vue CLI 建立 Vue.js 專案

Vue.js 提供正式的 CLI 以快速 Scaffolding 專案。 如果您想要使用 CLI 來建立應用程式，請遵循本文中的步驟以設定您的開發環境。

> [!IMPORTANT]
> 這些步驟假設您已經有一些使用 Vue.js 架構的體驗。 如果沒有，請瀏覽 [Vue.js](https://vuejs.org/) 以深入了解此架構。

### <a name="create-a-new-aspnet-core-project"></a>建立新的 ASP.NET Core 專案

在此範例中，請使用空白的 ASP.NET Core 應用程式 (C#)。 不過，您可以從各種專案和程式設計語言中進行選擇。

#### <a name="create-an-empty-project"></a>建立空白專案

1. 開啟 Visual Studio 並建立新專案。

    ::: moniker range=">=vs-2019"
    按 **Esc** 關閉開始視窗。 鍵入 **Ctrl + Q** 來開啟搜尋方塊，鍵入 **asp.net**，然後選擇 [建立新的 ASP.NET Core Web 應用程式]。 在出現的對話方塊中，鍵入名稱 **client-app**，然後選擇 [建立]。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從頂端功能表列中 **，選擇 [** 檔案  >  **新增**  >  **專案**]。 在 [新增專案] 對話方塊的左窗格中，展開 [Visual C#]，然後選擇 [Web]。 在中間窗格中，選擇 [ASP.NET Core Web 應用程式]，鍵入名稱 **client-app**，然後選擇 [確定]。
    ::: moniker-end

    如果您看不到 [ASP.NET Core Web 應用程式] 專案範本，則必須先安裝 **ASP.NET 與網頁程式開發** 工作負載和 **.NET Core** 程式開發工作負載。 若要安裝工作負載，請在 [新增專案] 對話方塊 (選取 [檔案] > [新增] > [專案]) 的左窗格中，按一下 [開啟 Visual Studio 安裝程式]。 Visual Studio 安裝程式即會啟動。 選取所需的工作負載。

1. 選取 [空白]，然後按一下 [確定]。

    Visual Studio 隨即建立專案，而專案會在 [方案總管] (右窗格) 中開啟。

#### <a name="configure-the-project-startup-file"></a>設定專案啟動檔案

* 開啟檔案 *./Startup.cs*，並將下列幾行新增至 Configure 方法：

    ```csharp
    app.UseDefaultFiles(); // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a>安裝 vue CLI

若要安裝 vue-cli npm 模組，請開啟命令提示字元，並鍵入 `npm install --g vue-cli` 或 `npm install -g @vue/cli` (適用於 3.0 版，其目前處於搶鮮版 (Beta) 階段)。

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a>使用 vue CLI 來 Scaffold 新的用戶端應用程式

1. 移至命令提示字元，並將目前的目錄變更為專案根資料夾。

1. 鍵入 `vue init webpack client-app`，並在系統提示您回答其他問題時遵循步驟。

    > [!NOTE]
    > 針對 *.vue* 檔案，您需要使用 WebPack 或包含載入程式的類似架構來進行轉換。 TypeScript 和 Visual Studio 不知道如何編譯 *.vue* 檔案。 對於統合也是如此；TypeScript 不知道如何將 ES2015 模組 (也就是 `import` 和 `export` 陳述式) 轉換成單一的最終 *.js* 檔案，以載入瀏覽器中。 同樣地，WebPack 是最好的選擇。 若要使用 MSBuild 從 Visual Studio 中驅動此程序，您需要從 Visual Studio 範本執行啟動。 目前，沒有現成適用於 Vue.js 開發的 ASP.NET 樣板。

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>修改 Webpack 組態以將建置的檔案輸出至 wwwroot

* 開啟檔案 *./client-app/config/index.js*，然後將 `build.index` 和 `build.assetsRoot` 變更為 wwwroot 路徑：

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-client-app-each-time-that-a-build-is-triggered"></a>指出專案會在每次觸發建置時建置用戶端應用程式

1. 在 Visual Studio 中，移至 [**專案**  >  **屬性**]  >  **組建事件**。

1. 在 [建置前事件命令列] 上鍵入 `npm --prefix ./client-app run build`。

#### <a name="configure-webpacks-output-module-names"></a>設定 Webpack 的輸出模組名稱

* 開啟檔案 *./client-app/build/webpack.base.conf.js*，然後將下列屬性新增到輸出屬性：

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>使用 Vue CLI 新增 TypeScript 支援

這些步驟需要 vue-cli 3.0，它目前仍處於搶鮮版 (Beta) 階段。

1. 移至命令提示字元，並將目前的目錄變更為專案根資料夾。

1. 鍵入 `vue create client-app`，然後選擇 [手動選取功能]。

1. 選擇 [Typescript]，然後選取其他所需的選項。

1. 遵循其餘的步驟並回應問題。

#### <a name="configure-a-vuejs-project-for-typescript"></a>設定 TypeScript 的 Vue.js 專案

1. 開啟檔案 *./client-app/tsconfig.json*，然後將 `noEmit:true` 新增到編譯器選項。

    藉由設定此選項，您可以避免每次在 Visual Studio 中建置時造成專案雜亂。

1. 接下來，在 *./client-app/* 中建立 *vue.config.js* 檔案，並新增下列程式碼。

    ```js
    module.exports = {
        outputDir: '../wwwroot',

        configureWebpack: {
            output: {
                devtoolModuleFilenameTemplate: '[absolute-resource-path]',
                devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
            }
        }
    };
    ```

    上述程式碼會設定 Webpack，並設定 wwwroot 資料夾。

#### <a name="build-with-vue-cli-30"></a>使用 vue-cli 3.0 建置

與 vue-cli 3.0 相關的未知問題可能會阻止建置程序的自動化。 每次當您嘗試重新整理 wwwroot 資料夾時，您都需要在 client-app 資料夾上執行 `npm run build` 命令。

或者，您可以使用 ASP.NET 專案屬性將 vue-cli 3.0 專案建置為建置前事件。 以滑鼠右鍵按一下該專案，選擇 [屬性]，然後將下列命令包含在 [建置] 索引標籤的 [建置前事件命令列] 文字方塊中。

``` cmd
cd ./client-app
npm run build
cd ../
```

## <a name="limitations"></a>限制

* `lang` 屬性僅支援 JavaScript 和 TypeScript 語言。 接受的值包括：js、jsx、ts 和 tsx。
* `lang` 屬性不適用於範本或樣式標籤。
* 由於其前置處理本質，不支援對 *.vue* 檔案中的指令碼區塊進行偵錯。
* TypeScript 無法將 *.vue* 檔案辨識為模組。 您需要包含如下程式碼的檔案，以告知 TypeScript *.vue* 檔案的外觀 (vue-cli 3.0 範本已經包含此檔案)。

    ```js
    // ./client-app/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* 使用 vue-cli 3.0 時，執行命令 `npm run build` 作為專案屬性的建置前事件無法運作。

## <a name="see-also"></a>另請參閱

- [Vue 使用者入門指南](https://vuejs.org/v2/guide) \(英文\)。
- [VUE CLI 專案](https://github.com/vuejs/vue-cli)。
- [Webpack 設定文件](https://webpack.js.org/configuration/) \(英文\)。
