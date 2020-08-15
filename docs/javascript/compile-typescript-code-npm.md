---
title: 使用 npm 編譯和建立 TypeScript 程式碼
description: 瞭解如何在 Visual Studio 中編譯和建立 TypeScript。
ms.date: 7/23/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 58603db021d7aeebe3272711e5ba92d96eb22075
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2020
ms.locfileid: "88250178"
---
# <a name="compile-typescript-code-nodejs"></a>編譯 TypeScript 程式碼 ( # A0) 

您可以使用 TypeScript SDK （在 Visual Studio 安裝程式中預設提供）或使用 npm，將 TypeScript 支援新增至您的專案。 對於在 Visual Studio 2019 中開發的專案，我們鼓勵您使用 TypeScript npm 套件，以在不同的平臺和環境之間獲得更高的可攜性。

針對 ASP.NET Core 專案，建議您改為使用 [NuGet 套件](../javascript/compile-typescript-code-nuget.md) 。

## <a name="add-typescript-support-using-npm"></a>使用 npm 新增 TypeScript 支援

[Typescript npm 套件](https://www.npmjs.com/package/typescript)會新增 typescript 支援。 將 TypeScript 2.1 或更高版本的 npm 套件安裝到您的專案中時，會在編輯器中載入對應版本的 TypeScript 語言服務。

1. [依照指示](/visualstudio/ide/quickstart-nodejs?toc=/visualstudio/javascript/toc.json) 安裝 Node.js 開發工作負載和 Node.js 執行時間。

   如需與 Visual Studio 的最簡單整合，請使用其中一個 Node.js TypeScript 範本來建立專案，例如「空白 Node.js Web 應用程式」範本。 否則，請使用 Visual Studio 隨附的 Node.js JavaScript 範本，並遵循這裡的指示，或使用 [開啟的資料夾](../javascript/develop-javascript-code-without-solutions-projects.md) 專案。

1. 如果您的專案尚未包含它，請安裝 [TypeScript npm 套件](https://www.npmjs.com/package/typescript)。

   從方案總管 (右窗格) 中，開啟專案根目錄中的 *package.js* 。 列出的套件會對應至方案總管中 npm-節點下的封裝。 如需詳細資訊，請參閱 [管理 npm 套件](../javascript/npm-package-management.md)。

   針對 Node.js 專案，您可以使用命令列或 IDE 來安裝 TypeScript npm 封裝。 若要使用 IDE 進行安裝，請以滑鼠右鍵按一下方案總管中的 [npm] 節點，選擇 [ **安裝新的 npm 套件**]，搜尋 **TypeScript**，然後安裝封裝。

   檢查 [**輸出**] 視窗中的 [ **npm** ] 選項，以查看封裝安裝進度。 已安裝的套件會顯示在方案總管的 [ **npm** ] 節點底下。

1. 如果您的專案尚未包含它，請將 *tsconfig* 檔案新增至您的專案根目錄。 若要加入檔案，請以滑鼠右鍵按一下專案節點，然後選擇 [ **加入 > 新專案**]。 選擇 [ **TYPESCRIPT JSON 設定檔**]，然後按一下 [ **新增**]。

   Visual Studio 會將檔案 *tsconfig.js* 新增至專案根目錄。 您可以使用這個檔案來 [設定](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) TypeScript 編譯器的選項。

1. 開啟 [tsconfig.js]，然後 * 按* [更新] 以設定您想要的編譯器選項。

   以下是簡單 *tsconfig.js* 檔案的範例。

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "dist"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   在此範例中：
   - *包含* 告訴編譯器在何處尋找 TypeScript ( *. ts) 檔案。
   - *outDir* 選項會指定 TypeScript 編譯器所轉換之一般 JavaScript 檔案的輸出檔案夾。
   - *sourceMap* 選項指出編譯器是否會產生 *sourceMap* 檔案。

   先前的設定僅提供設定 TypeScript 的基本簡介。 如需其他選項的詳細資訊，請參閱 [ 上的tsconfig.js](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)。

## <a name="build-the-application"></a>建置應用程式

1. 將 TypeScript (*. ts*) 或 typescript JSX (的 *tsx*) 檔案新增至您的專案，然後新增 typescript 程式碼。 如需 TypeScript 的簡單範例，請使用下列程式：

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. 在的 *package.js*中，使用下列腳本新增對 Visual Studio 組建和清除命令的支援。

   ```json
   "scripts": {
     "build": "tsc --build",
     "clean": "tsc --build --clean"
   },
   ```

   如果您需要使用協力廠商工具（例如 webpack）來建立，您可以將命令列組建腳本新增至檔案 * 中的package.js* ：

   ```json
   "scripts": {
      "build": "webpack-cli app.tsx --config webpack-config.js"
   }
   ```

   如需使用 webpack 與回應和 webpack 設定檔的範例，請參閱 [使用 Node.js 和回應建立 web 應用程式](../javascript/tutorial-nodejs-with-react-and-jsx.md)。

   如需搭配使用 Vue.js 與 TypeScript 的範例，請參閱 [建立 Vue.js 應用程式](/javascript/create-application-with-vuejs)。

1. 如果您需要設定選項，例如 [啟動] 頁面、[Node.js 執行時間]、[應用程式埠] 或 [執行時間引數] 的路徑，請以滑鼠右鍵按一下方案總管中的專案節點，然後選擇 [ **屬性**]。

   >[!NOTE]
   > 設定協力廠商工具時，Node.js 專案不會使用 [**工具**] [選項] [專案] 和 [方案] [  >  **Options**  >  **Projects and solutions**  >  **web 套件管理**  >  **外部 Web 工具**] 下所設定的路徑。 這些設定會用於其他專案類型。

1. 選擇 [ **組建 > 組建方案**]。

   雖然應用程式會在您執行時自動建立，但我們想要查看在建立過程中發生的事情：

   如果您產生來源對應，請開啟 [ *outDir* ] 選項中指定的資料夾，您會發現產生的 \* .js 檔案 (s) 連同產生的 \* js 檔案 (s) 。

   需要來源對應檔案才能進行 [調試](../javascript/debug-nodejs.md)程式。

## <a name="automate-build-tasks"></a>自動化組建工作

您可以使用 Visual Studio 中的 [工作執行器]，協助將協力廠商工具（例如 npm 和 webpack）的工作自動化。

- [NPM](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.NPMTaskRunner) 工作執行器-新增在 *package.js*中定義之 NPM 腳本的支援。 支援 yarn。
- [Webpack](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebPackTaskRunner) 工作執行器-新增 Webpack 的支援。
