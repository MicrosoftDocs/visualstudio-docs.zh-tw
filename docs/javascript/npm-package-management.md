---
title: 管理 npm 套件
description: Visual Studio 可協助您使用 Node.js 套件管理員 (npm) 來管理套件
ms.custom: seodec18
ms.date: 04/16/2020
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 0b4b699c01522878d83e59aadb2c6a54e9d7517f
ms.sourcegitcommit: a7f781d5a089e6aab6b073a07f3d4d2967af8aa6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81760175"
---
# <a name="manage-npm-packages-in-visual-studio"></a>管理 Visual Studio 中的 npm 套件

npm 可讓您安裝和管理要在 Node.js 應用程式中使用的套件。 Visual Studio 可讓您輕鬆地與 npm 互動，並透過 UI 或直接發出 npm 命令。 如果您不熟悉 npm，而且想要深入了解，請移至 [npm 文件](https://docs.npmjs.com/)。

可視化工作室與 npm 的集成因項目類型而異。
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [開啟資料夾(Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> npm 期望專案根中*node_modules*資料夾和*包.json。* 如果應用的資料夾結構不同,則應修改資料夾結構,如果要使用 Visual Studio 管理 npm 包。

## <a name="nodejs-projects"></a>Node.js 專案

對於 Node.js 專案,您可以執行以下任務:
* [從 [方案總管] 安裝套件](#npmInstallWindow)
* [從 [方案總管] 管理已安裝的套件](#solutionExplorer)
* [在 Node.js 互動式視窗中使用 `.npm` 命令](#interactive)

這些功能會一起運作，並與專案系統和專案中的 package.json** 檔案同步處理。

### <a name="prerequisites"></a>Prerequisites

您需要安裝**Node.js 開發**工作負荷和 Node.js 執行時,以便向專案添加 npm 支援。 有關詳細步驟,請參閱[創建 Node.js 專案](/visualstudio/ide/quickstart-nodejs?toc=/visualstudio/javascript/toc.json)。

> [!NOTE]
> 對於現有的 Node.js 專案,請使用**來自現有 Node.js 代碼**解決方案範本或[Open 資料夾 (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)專案類型在專案中啟用 npm。

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a>從解決方案資源管理員(Node.js)安裝套件

對於 Node.js 專案,安裝 npm 包的最簡單方法是通過 npm 包安裝視窗。 若要存取此視窗，請以滑鼠右鍵按一下專案中的 [npm]**** 節點，然後選取 [安裝新的 npm 套件]****。

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="從 [方案總管] 安裝新的 npm 套件" border="true":::

在此視窗中，您可以搜尋套件、指定選項，並安裝。

![搜尋 npm 套件](../javascript/media/search-package.png)

* **相依性類型** - 選擇 [標準]****、[開發]**** 和 [選擇性]**** 套件。 [標準] 指定套件是執行階段相依性，而 [開發] 指定只有在開發期間才需要套件。
* **添加到包.json** - 推薦。 此可配置選項被棄用。
* **選取的版本** - 選取您要安裝的套件版本。
* **其他 npm 引數** - 指定其他標準 npm 引數。 例如，您可以輸入版本值 (例如 `@~0.8`) 來安裝不在版本清單中的特定版本。

您可以在 **「輸出」** 視窗中的**npm**輸出中查看安裝進度。 這可能需要一些時間。

![npm 輸出](../javascript/media/npm-output.png)

> [!TIP]
> 您可以在搜尋查詢前面加上感興趣範圍來搜尋範圍套件；例如，鍵入 `@types/mocha` 尋找 mocha 的 TypeScript 定義檔案。 此外,在為 TypeScript 安裝類型定義時,可以通過在 npm`@ts2.6`參數位段中添加 來指定要定位的 TypeScript 版本。

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>在解決方案資源管理員(Node.js)中管理已安裝的套件

npm 套件會顯示在 [方案總管] 中。 **npm** 節點下的項目會模擬 package.json** 檔案中的相依性。

![搜尋 npm 套件](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>套件狀態

* ![已安裝的套件](../javascript/media/installed-npm.png) - 已安裝，並列在 package.json 中
* ![無直接關聯的套件](../javascript/media/extraneous-npm.png) - 已安裝，但未明確列在 package.json 中
* ![遺漏套件](../javascript/media/missing-npm.png) - 未安裝，但列在 package.json 中

::: moniker range=">=vs-2019"
右鍵按**下 npm**節點以執行以下操作之一:

* **安裝新的 npm 套件**打開 UI 以安裝新包。
* **安裝 npm 套件**運行 npm 安裝命令以安裝*套件*中列出的所有包。 (執行`npm install`.)
* **更新 npm 套件**根據*包.json*中指定的 semver 範圍,將包更新到最後一個版本。 (運行`npm update --save`.)。 通常使用"*"或"*"指定Semver範圍。 有關詳細資訊[,package.json 設定](../javascript/configure-packages-with-package-json.md)。

右鍵按下套件節點以執行以下操作之一:

* **安裝 npm 套件**執行 npm 安裝指令以安裝套件中列出的*套件*版本. (執行`npm install`.)
* **更新 npm 套件**根據*包.json*中指定的 semver 範圍,將包更新為最後一個版本。 (執行`npm update --save`.)通常使用"*"或"*"指定Semver範圍。
* **卸載 npm 套件**卸載套件並將其從*包中刪除.* `npm uninstall --save`
::: moniker-end
::: moniker range="vs-2017"
以滑鼠右鍵按一下套件節點或 **npm** 節點，來採取下列其中一個動作：
* **安裝缺少的套件**，而這些套件列在 package.json** 中
* **將 npm 套件更新**到最新版本
* **解除安裝套件**，並從 package.json** 中移除
::: moniker-end

>[!NOTE]
> 有關解決 npm 包問題,請參閱[故障排除](#troubleshooting-npm-packages)。

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>在 Node.js 互動式視窗 (Node.js) 中使用 .npm 命令

您也可以在 Node.js 互動式視窗中使用 `.npm` 命令來執行 npm 命令。 若要開啟此視窗，請以滑鼠右鍵按一下 [方案總管] 中的專案，然後選擇 [開啟 Node.js 互動式視窗]****。

在此視窗中，您可以使用下列這類命令來安裝套件：

`.npm install azure@4.2.3`

 > [!Tip]
 > npm 預設會在您專案的主目錄中執行。 如果您的方案中有多個專案，則請指定以括弧括住的專案名稱或路徑。
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > 如果您的專案未包含 package.json 檔案，請使用 `.npm init -y`來以預設項目建立新的 package.json 檔案。

 ## <a name="aspnet-core-projects"></a>ASP.NET核心專案

對於ASP.NET核心專案等專案,您可以將npm支援整合到專案中,並使用npm安裝包。
* [新增專案加入 npm 支援](#npmAdd)
* [使用套件安裝套件.json](#npmInstallPackage)

>[!NOTE]
> 對於ASP.NET核心專案,您還可以使用[庫管理器](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1)或紗線,而不是 npm 來安裝用戶端 JavaScript 和 CSS 檔。

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a>新增專案(ASP.NET核心)新增 npm 支援

如果專案尚未包含*包.json*檔案,則可以通過將*包.json*檔添加到專案中來添加一個檔以啟用 npm 支援。

1. 如果您沒有安裝 Node.js,我們建議您從[Node.js](https://nodejs.org/en/download/)網站安裝 LTS 版本,以便與外部框架和庫進行最佳相容性。

   npm 需要 Node.js。

1. 要添加*包.json*檔,請右鍵單擊解決方案資源管理器中的項目**Add** > ,然後 選擇「**添加新項**」。 選擇**npm 設定檔**,使用預設名稱,然後按下「**新增**」 。

   ![新增到您的項目](../javascript/media/npm-add-package-json.png)

   如果未看到列出的 npm 配置檔,則未安裝 Node.js 開發工具。 您可以使用視覺化工作室安裝程式添加**Node.js 開發**工作負荷。 然後重複上一步。

1. 在套件的`dependencies``devDependencies`或 部分包含一個或多個 npm*套件*。 例如,您可以將以下內容加入檔案中:

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

保存檔時,Visual Studio 會在解決方案資源管理器中的**依賴項/npm**節點下添加包。 如果看不到節點,請右鍵單擊**包.json**並選擇 **「還原包**」。。

>[!NOTE]
> 在某些情況下,解決方案資源管理器可能不會顯示已安裝 npm 包的正確狀態。 如需詳細資訊，請參閱[疑難排解](#troubleshooting-npm-packages)。

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>使用套件安裝套件.json(ASP.NET核心)

對於包含 npm 的專案,您可以使用`package.json`配置 npm 包。 右鍵按一下解決方案資源管理程式中的 npm 節點,然後選擇 **「開啟包.**

![搜尋 npm 套件](../javascript/media/npm-add-package.png)

*在包.json*中,IntelliSense 可説明您選擇 npm 包的特定版本。

:::image type="content" source="../javascript/media/npm-add-package-intellisense.png" alt-text="選擇 npm 套件版本" border="true":::

保存檔時,Visual Studio 會在解決方案資源管理器中的**依賴項/npm**節點下添加包。 如果看不到節點,請右鍵單擊**包.json**並選擇 **「還原包**」。。

安裝包可能需要幾分鐘時間。 通過在 **「輸出」** 視窗中切換到**npm**輸出來檢查套件安裝的進度。

![npm 輸出](../javascript/media/npm-output.png)

## <a name="troubleshooting-npm-packages"></a>容錯排除 npm 套件

* npm 需要 Node.js 如果您沒有安裝 Node.js,我們建議您從[Node.js](https://nodejs.org/en/download/)網站安裝 LTS 版本,以便與外部框架和庫進行最佳相容性。

* 對於 Node.js 專案,您必須安裝**Node.js 開發**工作負載以進行 npm 支援。

* 在某些情況下,解決方案資源管理器可能不會顯示已安裝 npm 包的正確狀態,因為[此處](https://github.com/aspnet/Tooling/issues/479)描述了已知問題。 例如,安裝包時,該程式可能顯示為未安裝。 在大多數情況下,您可以通過刪除*包.json、* 重新啟動 Visual Studio 以及重新添加*包.json*檔來更新解決方案資源管理器,如本文前面所述。 或者,安裝包時,可以使用 npm 輸出視窗來驗證安裝狀態。

* 如果在建置應用或洩漏 TypeScript 代碼時看到任何錯誤,請檢查 npm 包不相容,作為潛在的錯誤來源。 為了説明識別錯誤,請在安裝包時檢查 npm 輸出視窗,如本文前面所述。 例如,如果一個或多個 npm 包版本已棄用並導致錯誤,則可能需要安裝較新版本來修復錯誤。 如需使用 *package.json*控制 npm 套件版本的資訊，請參閱 [package.json 組態](../javascript/configure-packages-with-package-json.md)。

