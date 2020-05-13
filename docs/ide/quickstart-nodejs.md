---
title: 快速入門：使用 Visual Studio 建立您的第一個 Node.js 應用程式
description: 在此快速入門中，您會在 Visual Studio 中建立 Node.js 應用程式
ms.date: 06/27/2018
ms.technology: vs-javascript
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: f716421da3b9f888dbb7656c55db6814de88332b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "78235050"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>快速入門：使用 Visual Studio 建立您的第一個 Node.js 應用程式

在這個 5-10 分鐘的 Visual Studio 整合式開發環境 (IDE) 簡介中，您將建立簡單的 Node.js Web 應用程式。

## <a name="prerequisites"></a>必要條件

* 您必須安裝 Visual Studio 和 Node.js 開發工作負載。

    ::: moniker range=">=vs-2019"
    如果您尚未安裝 Visual Studio 2019，請轉到 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads) 頁面免費安裝它。
    ::: moniker-end
    ::: moniker range="vs-2017"
    如果您尚未安裝 Visual Studio 2017，請轉到 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 頁面免費安裝它。
    ::: moniker-end

    如果您需要安裝工作負載，但已經擁有視覺化工作室，請轉到 **"工具** > **獲取工具和功能..."，** 這將打開視覺化工作室安裝程式。 選擇 [Node.js 開發]**** 工作負載，然後選擇 [修改]****。

    ![VS 安裝程式中的 Node.js 工作負載](../ide/media/quickstart-nodejs-workload.png)

* 您必須安裝 Node.js 執行階段。

    如果您沒有安裝它，我們建議您從[Node.js](https://nodejs.org/en/download/)網站安裝 LTS 版本，以便與外部框架和庫進行最佳相容性。 Node.js 是為 32 位和 64 位體系結構構建的。 Visual Studio 中的 Node.js 工具（包含在 Node.js 工作負荷中）支援這兩個版本。 只需要一個，Node.js 安裝程式一次只支援安裝一個。
    
    一般而言，Visual Studio 會自動偵測已安裝的 Node.js 執行階段。 如果未檢測到已安裝的運行時，則可以將專案配置為引用屬性頁中的已安裝運行時（在創建專案後，按右鍵專案節點，選擇**屬性**，並設置**Node.exe 路徑**）。 您可以使用 Node.js 的全域安裝，也可以在每個 Node.js 專案中指定本地解譯器的路徑。 

## <a name="create-a-project"></a>建立專案

首先，您將建立 Node.js Web 應用程式專案。

1. 如果您尚未安裝 Node.js 執行階段，請從 [Node.js](https://nodejs.org/en/download/) 網站安裝 LTS 版本。

    有關詳細資訊，請參閱先決條件。

1. 開啟 Visual Studio。

1. 建立新專案。

    ::: moniker range=">=vs-2019"
    按 **Esc** 關閉開始視窗。 鍵入 **Ctrl + Q** 開啟 [搜尋] 方塊，鍵入 **Node.js**，然後選擇 [Create new Blank Node.js Web application project] \(建立新的空白 Node.js Web 應用程式專案\)**** (JavaScript)。 在出現的對話方塊中選擇 [建立]****。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從頂部功能表列中，選擇 **"檔** > **新專案** > **"。** 在 [新增專案]**** 對話方塊的左窗格中，展開 **JavaScript**，然後選擇 **Node.js**。 在中間窗格中，選擇 [Blank Node.js Web application] (空白的 Node.js Web 應用程式)****，然後選擇 [確定]****。
    ::: moniker-end
    如果您看不到 [空白的 Node.js Web 應用程式]**** 專案範本，則必須新增 **Node.js 開發**工作負載。 如需詳細指示，請參閱[必要條件](#prerequisites)。

    Visual Studio 會建立新的方案並開啟專案。 *server.js* 會在左窗格的編輯器中開啟。

## <a name="explore-the-ide"></a>探索 IDE

1. 查看方案總管**** 的右窗格。

   ![方案總管](../ide/media/quickstart-nodejs-solution-explorer.png)

   - 以粗體反白顯示的項目就是您的專案，並使用您在 [新增專案]**** 對話方塊中所指定的名稱。 在磁片上，此專案由專案資料夾中的 *.njsproj*檔表示。

   - 最上層是方案，預設其名稱會與專案相同。 方案 (以磁碟上的 *.sln* 檔案呈現) 是一或多個相關專案的容器。

   - npm 節點會顯示任何已安裝的 npm 套件。 您可以使用滑鼠右鍵按一下 npm 節點，以使用對話方塊來搜尋並安裝 npm 套件。

1. 如果要從命令提示符安裝 npm 包或 Node.js 命令，請按右鍵專案節點並在此處選擇 **"打開命令提示器**"。

   ![Node.js 命令提示字元](../ide/media/quickstart-nodejs-command-prompt.png)

1. 在編輯器 (左窗格) 的 *server.js* 檔案中，選擇 `http.createServer`，然後按 **F12**，或選擇操作 (右鍵) 功能表中的 [移至定義]****。 此命令將帶您到`createServer`*index.d.ts*中函數的定義。

   ![移至定義操作功能表](../ide/media/quickstart-nodejs-gotodefinition.png)

1. 移回至 *server.js*，然後將游標置於 `res.end('Hello World\n');` 這行程式碼的字串結尾，並進行修改，讓它看起來如下：

    `res.end('Hello World\n' + res.connection.`

    如果您鍵入 `connection.`，則 IntelliSense 會提供自動完成程式碼項目的選項。

   ![IntelliSense 自動完成](../ide/media/quickstart-nodejs-intellisense.png)

1. 選擇 [localPort]****，然後鍵入 `);` 以完成陳述式，讓它看起來如下：

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>執行應用程式

1. 按**Ctrl**+**F5（** 或**調試>無需調試即可啟動**）以運行應用程式。 應用程式會在瀏覽器中開啟。

1. 在瀏覽器視窗中，您會看到 "Hello World" 以及本機連接埠號碼。

1. 關閉網頁瀏覽器。

恭喜您完成本快速入門，其中，您已開始使用 Visual Studio IDE 和 Node.js。 如果您想要更深入地鑽研其功能，請繼續目錄的 [教學課程]**** 一節中的教學課程。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [將應用程式部署至 Linux App Service](../javascript/publish-nodejs-app-azure.md)

- [Node.js 和 Express 的教學課程](../javascript/tutorial-nodejs.md)
- [Node.js 和 React 的教學課程](../javascript/tutorial-nodejs-with-react-and-jsx.md)