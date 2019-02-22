---
title: 使用 Node.js 建立 Vue.js 應用程式
description: 您可以使用 Vue.js 架構在 Visual Studio 中建立 Node.js 應用程式
ms.custom: seodec18
ms.date: 07/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: a1c9de1c65c5f3f780e6ea4374fa7d96f436f514
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227757"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>使用適用於 Visual Studio 的 Node.js 工具建立 Vue.js 應用程式

Visual Studio 2017 包含改善的 [Vue.js](https://vuejs.org/) 架構支援，該架構可在使用 Vue.js、JavaScript 和 TypeScript 建立應用程式時改善開發體驗。

下列新功能支援 Visual Studio 中的 Vue.js 應用程式開發：

* 支援 *.vue* 檔案中的指令碼、樣式和範本區塊
* 辨識 *.vue* 檔案上的 `lang` 屬性
* Vue.js 專案和檔案範本

## <a name="prerequisites"></a>必要條件

* 您必須安裝 Visual Studio 2017 15.8 版 Preview 3 和 **Node.js 開發**工作負載。

    > [!IMPORTANT]
    > 本文需要的功能是從 Visual Studio 2017 15.8 版 Preview 3 開始提供。

    如果您尚未安裝 Visual Studio，請前往  [Visual Studio 下載](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) 頁面免費進行安裝。

    如果您需要安裝工作負載，但已擁有 Visual Studio，請在 [新增專案] 對話方塊 (選取 [檔案] > [新增] > [專案]) 的左窗格中，按一下 [開啟 Visual Studio 安裝程式]。 Visual Studio 安裝程式即會啟動。 選擇 [Node.js 開發] 工作負載，然後選擇 [修改]。

* 若要建立 ASP.NET Core 專案，您必須安裝 ASP.NET 與網頁程式開發工作負載，以及 .NET Core 跨平台開發工作負載。

* 您必須安裝 Node.js 執行階段。

    如果您沒有安裝，請從 [Node.js](https://nodejs.org/en/download/) 網站安裝 LTS 版本。 一般而言，Visual Studio 會自動偵測已安裝的 Node.js 執行階段。 如果它沒有偵測到已安裝的執行階段，您可以將專案設定為參考屬性頁面中已安裝的執行階段。 (建立專案之後，請以滑鼠右鍵按一下專案節點，然後選擇 [屬性])。

## <a name="create-a-vuejs-project-using-a-template"></a>使用範本建立 Vue.js 專案

您可以使用新的 Vue.js 範本來建立新專案。 使用範本是最簡單的使用者入門方式。 如需詳細步驟，請參閱[使用 Visual Studio 建立您的第一個 Vue.js 應用程式](../javascript/quickstart-vuejs-with-nodejs.md)。

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>使用 ASP.NET Core 和 Vue CLI 建立 Vue.js 專案

Vue.js 提供正式的 CLI 以快速 Scaffolding 專案。 如果您想要使用 CLI 來建立應用程式，請遵循本文中的步驟以設定您的開發環境。

> [!IMPORTANT]
> 這些步驟假設您已經有一些使用 Vue.js 架構的體驗。 如果沒有，請瀏覽 [Vue.js](https://vuejs.org/) 以深入了解此架構。

### <a name="create-a-new-aspnet-core-project"></a>建立新的 ASP.NET Core 專案

在此範例中，請使用空白的 ASP.NET Core 應用程式 (C#)。 不過，您可以從各種專案和程式設計語言中進行選擇。

#### <a name="create-an-empty-project"></a>建立空白專案

1. 開啟 Visual Studio，然後從主功能表選擇 [檔案] > [新增] > [專案]。

1. 在 [Visual C#] > [Web] 底下，選擇 [ASP.NET Core Web 應用程式]，然後按一下 [確定]。

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

1. 鍵入 `vue init webpack ClientApp`，並在系統提示您回答其他問題時遵循步驟。

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>修改 Webpack 組態以將建置的檔案輸出至 wwwroot

* 開啟檔案 *./ClientApp/config/index.js*，並將 `build.index` 和 `build.assetsRoot` 變更為 wwwroot 路徑：

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-clientapp-each-time-that-a-build-is-triggered"></a>表示專案會在每次觸發組建時建置 ClientApp

1. 在 Visual Studio 中，移至 [專案] > [屬性] > [建置事件]。

1. 在 [建置前事件命令列] 上鍵入 `npm --prefix ./ClientApp run build`。

#### <a name="configure-webpacks-output-module-names"></a>設定 Webpack 的輸出模組名稱

* 開啟檔案 *./ClientApp/build/webpack.base.conf.js*，並將下列屬性新增至 output 屬性：

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>使用 Vue CLI 新增 TypeScript 支援

這些步驟需要 vue-cli 3.0，它目前仍處於搶鮮版 (Beta) 階段。

1. 移至命令提示字元，並將目前的目錄變更為專案根資料夾。

1. 鍵入 `vue create ClientApp`，然後選擇 [手動選取功能]。

1. 選擇 [Typescript]，然後選取其他所需的選項。

1. 遵循其餘的步驟並回應問題。

#### <a name="configure-a-vuejs-project-for-typescript"></a>設定 TypeScript 的 Vue.js 專案

1. 開啟檔案 *./ClientApp/tsconfig.json*，並將 `noEmit:true` 新增至編譯器選項。

    藉由設定此選項，您可以避免每次在 Visual Studio 中建置時造成專案雜亂。

1. 接下來，在 *./ClientApp/* 中建立 *vue.config.js* 檔案，並新增下列程式碼。

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

vue-cli 3.0 的未知問題會阻止自動化建置流程。 每次嘗試重新整理 wwwroot 資料夾時，您都需要在 ClientApp 資料夾上執行命令 `npm run build`。

## <a name="limitations"></a>限制

* `lang` 屬性僅支援 JavaScript 和 TypeScript 語言。 接受的值包括：js、jsx、ts 和 tsx。
* `lang` 屬性不適用於範本或樣式標籤。
* 由於其前置處理本質，不支援對 *.vue* 檔案中的指令碼區塊進行偵錯。
* TypeScript 無法將 *.vue* 檔案辨識為模組。 您需要包含如下程式碼的檔案，以告知 TypeScript *.vue* 檔案的外觀 (vue-cli 3.0 範本已經包含此檔案)。

    ```js
    // ./ClientApp/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* 使用 vue-cli 3.0 時，執行命令 `npm run build` 作為專案屬性的建置前事件無法運作。

## <a name="see-also"></a>另請參閱

- [Vue 使用者入門指南](https://vuejs.org/v2/guide) \(英文\)。
- [Vue CLI project](https://github.com/vuejs/vue-cli)(Vue CLI 專案)。
- [Webpack 設定文件](https://webpack.js.org/configuration/) \(英文\)。
