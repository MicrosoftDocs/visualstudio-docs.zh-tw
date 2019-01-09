---
title: 管理 npm 套件
description: Visual Studio 可協助您使用 Node.js 套件管理員 (npm) 來管理套件
ms.custom: seodec18
ms.date: 06/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: bae9beac69daf78bfd6a8604c4364af857dff0a6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845950"
---
# <a name="manage-npm-packages-in-visual-studio"></a>管理 Visual Studio 中的 npm 套件

npm 可讓您安裝和管理要在 Node.js 應用程式中使用的套件。 如果您不熟悉 npm，而且想要深入了解，請移至 [npm 文件](https://docs.npmjs.com/)。

Visual Studio 可讓您輕鬆地與 npm 互動，並透過 UI 或直接發出 npm 命令。 您可以使用下列方法：
* [從 [方案總管] 安裝套件](#npmInstallWindow)
* [從 [方案總管] 管理已安裝的套件](#solutionExplorer)
* [在 Node.js 互動式視窗中使用 `.npm` 命令](#interactive)

這些功能會一起運作，並與專案系統和專案中的 package.json 檔案同步處理。

## <a name="npmInstallWindow"></a> 從 [方案總管] 安裝套件

安裝 npm 套件的最簡單方式是透過 npm 套件安裝視窗。 若要存取此視窗，請以滑鼠右鍵按一下專案中的 [npm] 節點，然後選取 [安裝新的 npm 套件]。

![從 [方案總管] 安裝新的 npm 套件](../javascript/media/solution-explorer-install-package.png)

在此視窗中，您可以搜尋套件、指定選項，並安裝。 

![搜尋 npm 套件](../javascript/media/search-package.png)

* **相依性類型** - 選擇 [標準]、[開發] 和 [選擇性] 套件。 [標準] 指定套件是執行階段相依性，而 [開發] 指定只有在開發期間才需要套件。
* **新增到 package.json** - 已淘汱此選項
* **選取的版本** - 選取您要安裝的套件版本。
* **其他 npm 引數** - 指定其他標準 npm 引數。 例如，您可以輸入版本值 (例如 `@~0.8`) 來安裝不在版本清單中的特定版本。

您可以在 [輸出] 視窗的 [npm] 索引標籤中看到安裝進度。 這可能需要一些時間。

> [!TIP]
> 您可以在搜尋查詢前面加上感興趣範圍來搜尋範圍套件；例如，鍵入 `@types/mocha` 尋找 mocha 的 TypeScript 定義檔案。 而且，安裝 TypeScript 的類型定義時，您可以在 npm 引數欄位中新增 `@ts2.6`，以指定設為目標的 TypeScript 版本。

## <a name="solutionExplorer"></a> 在 [方案總管] 中管理已安裝的套件

npm 套件會顯示在 [方案總管] 中。 **npm** 節點下的項目會模擬 package.json 檔案中的相依性。

![搜尋 npm 套件](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>套件狀態
* ![已安裝的套件](../javascript/media/installed-npm.png) - 已安裝，並列在 package.json 中
* ![無直接關聯的套件](../javascript/media/extraneous-npm.png) - 已安裝，但未明確列在 package.json 中
* ![遺漏套件](../javascript/media/missing-npm.png) - 未安裝，但列在 package.json 中

以滑鼠右鍵按一下套件節點或 **npm** 節點，來採取下列其中一個動作：
* **安裝缺少的套件**，而這些套件列在 package.json 中
* **更新套件**至最新版本
* **解除安裝套件**，並從 package.json 中移除

## <a name="interactive"></a> 在 Node.js 互動式視窗中使用 .npm 命令

您也可以在 Node.js 互動式視窗中使用 `.npm` 命令來執行 npm 命令。 若要開啟此視窗，請以滑鼠右鍵按一下 [方案總管] 中的專案，然後選擇 [開啟 Node.js 互動式視窗]。

在此視窗中，您可以使用下列這類命令來安裝套件：

`.npm install azure@4.2.3`
 
 > [!Tip]
 > npm 預設會在您專案的主目錄中執行。 如果您的方案中有多個專案，則請指定以括弧括住的專案名稱或路徑。 
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > 如果您的專案未包含 package.json 檔案，請使用 `.npm init -y`來以預設項目建立新的 package.json 檔案。 