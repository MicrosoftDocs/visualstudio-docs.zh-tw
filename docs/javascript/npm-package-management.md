---
title: 管理 npm 套件
description: Visual Studio 可協助您使用 Node.js 套件管理員 (npm) 來管理套件
ms.custom: seodec18
ms.date: 03/12/2020
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: dba657d30eedef26337c708e7ede6c5ab85ed4cc
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "79549992"
---
# <a name="manage-npm-packages-in-visual-studio"></a>管理 Visual Studio 中的 npm 套件

npm 可讓您安裝和管理要在 Node.js 應用程式中使用的套件。 Visual Studio 可讓您輕鬆地與 npm 互動，並透過 UI 或直接發出 npm 命令。 如果您不熟悉 npm，而且想要深入了解，請移至 [npm 文件](https://docs.npmjs.com/)。

視覺化工作室與 npm 的集成因專案類型而異。
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [打開資料夾（Node.js）](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> npm 期望專案根中*node_modules*資料夾和*包.json。* 如果應用的資料夾結構不同，則應修改資料夾結構，如果要使用 Visual Studio 管理 npm 包。

> [!NOTE]
> 對於現有的 Node.js 專案，請使用**來自現有 Node.js 代碼**解決方案範本在專案中啟用 npm。

## <a name="nodejs-projects"></a>Node.js 專案

對於 Node.js 專案，請使用以下方法之一：
* [從 [方案總管] 安裝套件](#npmInstallWindow)
* [從 [方案總管] 管理已安裝的套件](#solutionExplorer)
* [在 Node.js 互動式視窗中使用 `.npm` 命令](#interactive)

這些功能會一起運作，並與專案系統和專案中的 package.json** 檔案同步處理。

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a>從解決方案資源管理器（Node.js）安裝包

對於 Node.js 專案，安裝 npm 包的最簡單方法是通過 npm 包安裝視窗。 若要存取此視窗，請以滑鼠右鍵按一下專案中的 [npm]**** 節點，然後選取 [安裝新的 npm 套件]****。

![從 [方案總管] 安裝新的 npm 套件](../javascript/media/solution-explorer-install-package.png)

在此視窗中，您可以搜尋套件、指定選項，並安裝。

![搜尋 npm 套件](../javascript/media/search-package.png)

* **相依性類型** - 選擇 [標準]****、[開發]**** 和 [選擇性]**** 套件。 [標準] 指定套件是執行階段相依性，而 [開發] 指定只有在開發期間才需要套件。
* **新增到 package.json** - 已淘汱此選項
* **選取的版本** - 選取您要安裝的套件版本。
* **其他 npm 引數** - 指定其他標準 npm 引數。 例如，您可以輸入版本值 (例如 `@~0.8`) 來安裝不在版本清單中的特定版本。

您可以在 **"輸出"** 視窗中的**npm**輸出中查看安裝進度。 這可能需要一些時間。

![npm 輸出](../javascript/media/npm-output.png)

> [!TIP]
> 您可以在搜尋查詢前面加上感興趣範圍來搜尋範圍套件；例如，鍵入 `@types/mocha` 尋找 mocha 的 TypeScript 定義檔案。 此外，在為 TypeScript 安裝類型定義時，可以通過在 npm 參數欄位中添加`@ts2.6`來指定要定位的 TypeScript 版本。

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>在解決方案資源管理器（Node.js）中管理已安裝的包

npm 套件會顯示在 [方案總管] 中。 **npm** 節點下的項目會模擬 package.json** 檔案中的相依性。

![搜尋 npm 套件](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>套件狀態

* ![已安裝的套件](../javascript/media/installed-npm.png) - 已安裝，並列在 package.json 中
* ![無直接關聯的套件](../javascript/media/extraneous-npm.png) - 已安裝，但未明確列在 package.json 中
* ![遺漏套件](../javascript/media/missing-npm.png) - 未安裝，但列在 package.json 中

以滑鼠右鍵按一下套件節點或 **npm** 節點，來採取下列其中一個動作：
* **安裝缺少的套件**，而這些套件列在 package.json** 中
* **更新套件**至最新版本
* **解除安裝套件**，並從 package.json** 中移除

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>在 Node.js 互動式視窗 （Node.js） 中使用 .npm 命令

您也可以在 Node.js 互動式視窗中使用 `.npm` 命令來執行 npm 命令。 若要開啟此視窗，請以滑鼠右鍵按一下 [方案總管] 中的專案，然後選擇 [開啟 Node.js 互動式視窗]****。

在此視窗中，您可以使用下列這類命令來安裝套件：

`.npm install azure@4.2.3`

 > [!Tip]
 > npm 預設會在您專案的主目錄中執行。 如果您的方案中有多個專案，則請指定以括弧括住的專案名稱或路徑。
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > 如果您的專案未包含 package.json 檔案，請使用 `.npm init -y`來以預設項目建立新的 package.json 檔案。

 ## <a name="aspnet-core-projects"></a>ASP.NET核心專案

對於ASP.NET核心專案等專案，您可以將 npm 支援集成到專案中，並使用 npm 安裝包。
* [向專案添加 npm 支援](#npmAdd)
* [使用包安裝包.json](#npmInstallPackage)

>[!NOTE]
> 對於ASP.NET核心專案，您還可以使用[庫管理器](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1)或紗線，而不是 npm 來安裝用戶端 JavaScript 和 CSS 檔。

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a>向專案（ASP.NET核心）添加 npm 支援

如果專案尚未包含*包.json*檔，則可以通過將包.json 檔添加到專案中添加一個啟用 npm 支援檔。

1. 要添加檔，請按右鍵解決方案資源管理器中的專案，然後選擇**Add** > "**添加新項**"。 選擇**npm 設定檔**，使用預設名稱，然後按一下"**添加**"。

   ![將包.json 添加到您的專案](../javascript/media/npm-add-package-json.png)

1. 在包的`dependencies`或`devDependencies`部分包括一個或多個 npm*包*。 例如，您可以將以下內容添加到檔中：

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

保存檔時，Visual Studio 會在解決方案資源管理器中的**依賴項/npm**節點下添加包。 如果看不到節點，請按右鍵**包.json**並選擇 **"還原包**"。

>[!NOTE]
> 在某些情況下，解決方案資源管理器可能指示 npm 包與*包.json*不同步，因為[此處](https://github.com/aspnet/Tooling/issues/479)描述了一個已知問題。 例如，安裝包時，該程式可能顯示為未安裝。 在大多數情況下，您可以通過刪除*包.json、* 重新開機 Visual Studio 以及重新添加*包.json*檔來更新解決方案資源管理器，如本文前面所述。

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>使用包安裝包.json（ASP.NET核心）

對於包含 npm 的專案，您可以使用 配置 npm`package.json`包。 按右鍵解決方案資源管理器中的 npm-節點，然後選擇 **"打開包.**

![搜尋 npm 套件](../javascript/media/npm-add-package.png)

*在包.json*中，IntelliSense 可説明您選擇 npm 包的特定版本。

![搜尋 npm 套件](../javascript/media/npm-add-package-intellisense.png)

保存檔時，Visual Studio 會在解決方案資源管理器中的**依賴項/npm**節點下添加包。 如果看不到節點，請按右鍵**包.json**並選擇 **"還原包**"。

安裝包可能需要幾分鐘時間。 通過在 **"輸出"** 視窗中切換到**npm**輸出來檢查包安裝的進度。

![npm 輸出](../javascript/media/npm-output.png)

