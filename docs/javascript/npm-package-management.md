---
title: 管理 npm 套件
description: Visual Studio 可協助您使用 Node.js 套件管理員 (npm) 來管理套件
ms.custom: seodec18
ms.date: 04/16/2020
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 26c750a11c2910a6c6f91e1207d731024af64a5f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962713"
---
# <a name="manage-npm-packages-in-visual-studio"></a>管理 Visual Studio 中的 npm 套件

npm 可讓您安裝和管理要在 Node.js 應用程式中使用的套件。 Visual Studio 可讓您輕鬆地與 npm 互動，並透過 UI 或直接發出 npm 命令。 如果您不熟悉 npm，而且想要深入了解，請移至 [npm 文件](https://docs.npmjs.com/)。

Visual Studio 與 npm 的整合會根據您的專案類型而有所不同。
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [開啟資料夾 ( # A0) ](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> npm 需要專案根目錄中的 *node_modules* 資料夾和 *package.js* 。 如果您的應用程式資料夾結構不同，如果您想要使用 Visual Studio 管理 npm 套件，則應該修改您的資料夾結構。

## <a name="nodejs-projects"></a>Node.js 專案

針對 Node.js 的專案，您可以執行下列工作：
* [從 [方案總管] 安裝套件](#npmInstallWindow)
* [從 [方案總管] 管理已安裝的套件](#solutionExplorer)
* [在 Node.js 互動式視窗中使用 `.npm` 命令](#interactive)

這些功能會一起運作，並與專案系統和專案中的 package.json 檔案同步處理。

### <a name="prerequisites"></a>必要條件

您需要安裝 **Node.js 開發** 工作負載及 Node.js 執行時間，才能將 npm 支援新增至您的專案。 如需詳細步驟，請參閱 [建立 Node.js 專案](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json)。

> [!NOTE]
> 針對現有的 Node.js 專案，請使用 [ **從現有的 Node.js 程式碼** ] 方案範本或 [ [開啟資料夾] ( # A2)](../javascript/develop-javascript-code-without-solutions-projects.md) 專案類型，在您的專案中啟用 npm。

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a> 從方案總管 ( # A0) 安裝套件

針對 Node.js 專案，安裝 npm 套件最簡單的方式是透過 npm 套件安裝視窗。 若要存取此視窗，請以滑鼠右鍵按一下專案中的 [npm] 節點，然後選取 [安裝新的 npm 套件]。

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="從 [方案總管] 安裝新的 npm 套件" border="true":::

在此視窗中，您可以搜尋套件、指定選項，並安裝。

![[安裝新的 npm 套件] 對話方塊的螢幕擷取畫面。 系統會選取 azure 2.2.1 預覽套件，並顯示該套件的詳細資料和選項。](../javascript/media/search-package.png)

* **相依性類型** - 選擇 [標準]、[開發] 和 [選擇性] 套件。 [標準] 指定套件是執行階段相依性，而 [開發] 指定只有在開發期間才需要套件。
* 依建議 **新增至 package.js** 。 這個可設定的選項已被取代。
* **選取的版本** - 選取您要安裝的套件版本。
* **其他 npm 引數** - 指定其他標準 npm 引數。 例如，您可以輸入版本值 (例如 `@~0.8`) 來安裝不在版本清單中的特定版本。

您可以在 [**輸出**] 視窗的 **npm** 輸出中看到安裝進度。 這可能需要一些時間。

![npm 輸出](../javascript/media/npm-output.png)

> [!TIP]
> 您可以在搜尋查詢前面加上感興趣範圍來搜尋範圍套件；例如，鍵入 `@types/mocha` 尋找 mocha 的 TypeScript 定義檔案。 此外，安裝 TypeScript 的型別定義時，您可以 `@ts2.6` 在 [npm 引數] 欄位中加入，藉以指定您要設為目標的 TypeScript 版本。

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>在方案總管 ( # A0) 中管理已安裝的套件

npm 套件會顯示在 [方案總管] 中。 **npm** 節點下的項目會模擬 package.json 檔案中的相依性。

![Npm 方案總管節點的螢幕擷取畫面，其中顯示 npm 封裝的安裝狀態。](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>套件狀態

* ![已安裝的套件](../javascript/media/installed-npm.png) - 已安裝，並列在 package.json 中
* ![無直接關聯的套件](../javascript/media/extraneous-npm.png) - 已安裝，但未明確列在 package.json 中
* ![遺漏套件](../javascript/media/missing-npm.png) - 未安裝，但列在 package.json 中

::: moniker range=">=vs-2019"
以滑鼠右鍵按一下 [ **npm** ] 節點，執行下列其中一個動作：

* **安裝新的 Npm 套件** 開啟 UI 以安裝新的套件。
* **安裝 Npm 套件** 執行 npm install 命令，以安裝 *package.js* 中列出的所有套件。  (執行 `npm install` 。 ) 
* **更新 Npm 套件** 根據 *package.json* 中指定 (SemVer) 範圍的語義版本設定，將封裝更新為最新版本。  (執行 `npm update --save` 。 ) 。 SemVer 範圍通常是使用 "~" 或 "^" 來指定。 如需詳細資訊，請 [package.js](../javascript/configure-packages-with-package-json.md)設定。

以滑鼠右鍵按一下封裝節點，執行下列其中一個動作：

* **安裝 Npm Package (s)** 執行 npm install 命令，以安裝 *package.js* 中列出的封裝版本。  (執行 `npm install` 。 ) 
* **更新 Npm 封裝 (s)** 根據 *package.js* 中指定的 SemVer 範圍，將封裝更新為最新版本。  (Run `npm update --save` . ) SemVer 範圍通常會使用 "~" 或 "^" 來指定。
* **卸載 Npm Package (s)** 卸載封裝，並將其從 (執行 *上的package.js* 中移除 `npm uninstall --save` 。 ) 
::: moniker-end
::: moniker range="vs-2017"
以滑鼠右鍵按一下套件節點或 **npm** 節點，來採取下列其中一個動作：
* **安裝缺少的套件**，而這些套件列在 package.json 中
* 將 **npm 套件更新** 為最新版本
* **解除安裝套件**，並從 package.json 中移除
::: moniker-end

>[!NOTE]
> 如需解決 npm 封裝問題的協助，請參閱 [疑難排解](#troubleshooting-npm-packages)。

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>在 Node.js 的互動式視窗中使用. npm 命令 ( # A1) 

您也可以在 Node.js 互動式視窗中使用 `.npm` 命令來執行 npm 命令。 若要開啟此視窗，請以滑鼠右鍵按一下 [方案總管] 中的專案，然後選擇 [開啟 Node.js 互動式視窗]。

在此視窗中，您可以使用下列這類命令來安裝套件：

`.npm install azure@4.2.3`

 > [!Tip]
 > npm 預設會在您專案的主目錄中執行。 如果您的方案中有多個專案，則請指定以括弧括住的專案名稱或路徑。
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > 如果您的專案未包含 package.json 檔案，請使用 `.npm init -y`來以預設項目建立新的 package.json 檔案。

 ## <a name="aspnet-core-projects"></a>ASP.NET Core 專案

針對 ASP.NET Core 專案之類的專案，您可以在專案中整合 npm 支援，並使用 npm 來安裝封裝。
* [將 npm 支援新增至專案](#npmAdd)
* [使用 package.js安裝套件](#npmInstallPackage)

>[!NOTE]
> 針對 ASP.NET Core 專案，您也可以使用連結 [庫管理員](/aspnet/core/client-side/libman/?view=aspnetcore-3.1&preserve-view=true) 或 yarn 而不是 npm 來安裝用戶端 JAVASCRIPT 和 CSS 檔案。

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a> 將 npm 支援新增至專案 (ASP.NET Core) 

如果您的專案尚未包含檔案 *上的package.js* ，您可以新增一個檔案 *package.js* 至專案，藉以啟用 npm 支援。

1. 如果您未安裝 Node.js，建議您從 [Node.js](https://nodejs.org/en/download/) 網站安裝 LTS 版本，以獲得與外部架構和程式庫的最佳相容性。

   npm 需要 Node.js。

1. 若要將 *package.js* 加入檔案，請以滑鼠右鍵按一下方案總管中的專案，然後選擇 [**加入**  >  **新專案**]。 選擇 **Npm 設定檔**，使用預設名稱，然後按一下 [ **新增**]。

   ![將 package.js新增至您的專案](../javascript/media/npm-add-package-json.png)

   如果您沒有看到列出的 npm 設定檔，則不會安裝 Node.js 的開發工具。 您可以使用 Visual Studio 安裝程式來新增 **Node.js 開發** 工作負載。 然後重複上一個步驟。

1. 在package.js的或區段中包含一或多個 npm 封裝 `dependencies` `devDependencies` 。  例如，您可以將下列內容新增至檔案：

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

當您儲存檔案時，Visual Studio 會在方案總管的 [相依性 **/Npm]** 節點下加入封裝。 如果您沒有看到節點，請以滑鼠右鍵按一下 **package.js** ，然後選擇 [ **還原套件**]。

>[!NOTE]
> 在某些情況下，方案總管可能不會顯示已安裝之 npm 套件的正確狀態。 如需詳細資訊，請參閱[疑難排解](#troubleshooting-npm-packages)。

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>在 (ASP.NET Core 上使用 package.js安裝套件) 

針對包含 npm 的專案，您可以使用設定 npm 封裝 `package.json` 。 在方案總管中的 [npm] 節點上按一下滑鼠右鍵，然後選擇 [ **開啟 package.js** 開啟]。

![已選取 [npm] 節點之方案總管的螢幕擷取畫面。 以滑鼠右鍵按一下內容功能表為開啟狀態，且已選取 [開啟 package.js開啟]。](../javascript/media/npm-add-package.png)

*package.js* 中的 IntelliSense 可協助您選取特定版本的 npm 套件。

:::image type="content" source="../javascript/media/npm-add-package-intellisense.png" alt-text="選取 npm 套件版本" border="true":::

當您儲存檔案時，Visual Studio 會在方案總管的 [相依性 **/Npm]** 節點下加入封裝。 如果您沒有看到節點，請以滑鼠右鍵按一下 **package.js** ，然後選擇 [ **還原套件**]。

安裝套件可能需要幾分鐘的時間。 切換至 [**輸出**] 視窗中的 [ **npm** 輸出]，檢查封裝安裝的進度。

![npm 輸出](../javascript/media/npm-output.png)

## <a name="troubleshooting-npm-packages"></a>針對 npm 套件進行疑難排解

* npm 需要 Node.js 如果您沒有安裝 Node.js，建議您從 [Node.js](https://nodejs.org/en/download/) 網站安裝 LTS 版本，以提供與外部架構和程式庫的最佳相容性。

* 針對 Node.js 的專案，您必須安裝 **Node.js 開發** 工作負載，以支援 npm。

* 在某些情況下，方案總管可能不會顯示已安裝 npm 套件的正確狀態，因為 [這裡](https://github.com/aspnet/Tooling/issues/479)有已知的問題。 例如，封裝可能會在安裝時顯示為未安裝。 在大部分的情況下，您可以刪除 *package.js*、重新開機 Visual Studio，然後重新新增 *package.js* 檔案，以更新方案總管，如本文稍早所述。 或者，在安裝封裝時，您可以使用 [npm 輸出] 視窗來確認安裝狀態。

* 如果您在建立應用程式或轉譯 TypeScript 程式碼時看到任何錯誤，請檢查 npm 套件不相容是否為可能的錯誤來源。 如本文先前所述，若要協助識別錯誤，請在安裝套件時檢查 [npm 輸出] 視窗。 例如，如果有一或多個 npm 套件版本已被取代，而導致錯誤，您可能需要安裝較新的版本來修正錯誤。 如需使用 *package.json* 控制 npm 套件版本的資訊，請參閱 [package.json 組態](../javascript/configure-packages-with-package-json.md)。
