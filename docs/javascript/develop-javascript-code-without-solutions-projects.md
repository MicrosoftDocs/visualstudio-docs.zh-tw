---
title: 不使用方案或專案在 Visual Studio 中撰寫 JavaScript 程式碼
titleSuffix: ''
description: Visual Studio 提供建立程式碼的支援，而無需依賴專案檔或方案檔
ms.custom: seodec18
ms.date: 09/24/2018
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 9838cd39fe29f8233f82df00dda6a7392e3494cd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955485"
---
# <a name="develop-javascript-and-typescript-code-in-visual-studio-without-solutions-or-projects"></a>不使用方案或專案在 Visual Studio 中開發 JavaScript 和 TypeScript 程式碼

自 Visual Studio 2017 開始可以[不使用專案或解決方案來開發程式碼](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)，這讓您可以開啟程式碼的資料夾，並立即開始使用豐富的編輯器支援，例如 IntelliSense、搜尋、重構及偵錯等。 除了這些功能之外，適用於 Visual Studio 的 Node.js 工具還新增了建置 TypeScript 檔案、管理 npm 套件及執行 npm 指令碼的支援。

若要開始使用，**請**  >    >  從工具列選取 [開啟 **資料夾**]。 [方案總管] 顯示資料夾中的所有檔案，您可以開啟任何檔案以開始編輯。 在背景中，Visual Studio 會編製檔案的索引，以啟用 npm、建置功能，以及對功能進行偵錯。

> [!IMPORTANT]
> 本文中描述的許多功能，包括 npm 整合，都需要 Visual Studio 2017 15.8 版或更新版本。 必須安裝 Visual Studio **Node.js 開發** 工作負載。

## <a name="npm-integration"></a>npm 整合

如果開啟的資料夾中包含 *package.json* 檔案，您可以用滑鼠右鍵按一下 *package.json* 以顯示 npm 專用的操作功能表 (捷徑功能表)。

![[方案總管] 中的 npm 功能表](../javascript/media/solution-explorer-npm-ctx.png)

在捷徑功能表中，您可以利用與使用專案檔時[管理 npm 套件](npm-package-management.md)的相同方式來管理 npm 所安裝的套件。

此外，此功能表也可讓您執行 *package.json* 之 `scripts` 項目中定義的指令碼。 這些指令碼將使用 `PATH` 環境變數上可用的 Node.js 版本。 指令碼會在新視窗中執行。 這是用來執行組建或執行指令碼的絕佳方式。

## <a name="build-and-debug"></a>建置和偵錯

### <a name="packagejson"></a>package.json
如果資料夾中的 *package.json* 指定 `main` 項目，則 *package.json* 的滑鼠右鍵捷徑功能表將提供 [偵錯] 命令。
按一下此項目時，將以指定的指令碼作為其引數來啟動 *node.exe*。

### <a name="javascript-files"></a>JavaScript 檔案
您可以用滑鼠右鍵按一下檔案，然後從捷徑功能表中選取 [偵錯]，藉以對 JavaScript 檔案進行偵錯。 這會以該 JavaScript 檔案作為其引數來啟動 *node.exe*。

### <a name="typescript-files-and-tsconfigjson"></a>TypeScript 檔案和 tsconfig.json
如果資料夾中沒有任何的 *tsconfig.json*，您可以用滑鼠右鍵按一下 TypeScript 檔案，以查看用來建置該檔案並對其進行偵錯的捷徑功能表命令。 當您使用這些命令時，可以使用 *tsc.exe* 搭配預設選項進行建置或偵錯。 (您需要建置檔案，然後才能進行偵錯)。

> [!NOTE]
> 在建置 TypeScript 程式碼時，我們會使用 `C:\Program Files (x86)\Microsoft SDKs\TypeScript` 中安裝的最新版本。

如果資料夾中有 *tsconfig.json* 檔案，您可以用滑鼠右鍵按一下 TypeScript 檔案，以查看用來對該 TypeScript 檔案進行偵錯的功能表命令。 只有在 *tsconfig.json* 中未指定任何 `outFile` 時，才會顯示此選項。 如果指定了 `outFile`，您可以用滑鼠右鍵按一下 *tsconfig.json* ，然後選取正確的選項，對該檔案進行偵錯。 `tsconfig.json`　檔案也會為您提供組建選項，讓您指定編譯器選項。

> [!NOTE]
> 您可以在 [tsconfig.json TypeScript 手冊頁面](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)中找到 *tsconfig.json* 的詳細資訊。

## <a name="unit-tests"></a>單元測試
您可以藉由在 *package.json* 指定測試根，在 Visual Studio 中啟用單元測試整合：

```json
{
    // ...
    "vsTest":{
        "testRoot": "./tests"
    }
    // ...
}
```

測試執行器會列舉在本機上已安裝的套件，以判斷要使用哪個測試架構。
如果無法辨識任何支援的架構，測試執行器會預設為 *ExportRunner*。 其他支援的架構包括：
* Mocha ([mochajs.org](https://mochajs.org/))
* Jasmine ([Jasmine.github.io](https://jasmine.github.io/))
* Tape ([github.com/substack/tape](https://github.com/substack/tape))
* Jest ([jestjs.io](https://jestjs.io/))

開啟 test explorer 之後 (選擇 [**測試**  >  **Windows**  >  **test explorer**) ]，Visual Studio 探索並顯示測試。

> [!NOTE]
> 測試執行器只會列舉測試根目錄中的 JavaScript 檔案，如果您的應用程式以 TypeScript 撰寫，您需要先建置它們。
