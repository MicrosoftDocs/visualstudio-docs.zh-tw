---
title: 建立您的第一個 Node.js 應用程式
ms.custom: SEO-VS-2020
description: 在此快速入門中，您會在 Visual Studio 中建立 Node.js 應用程式
ms.date: 03/25/2021
ms.technology: vs-javascript
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: ecd65c0348ac16a2097061726e3896961ae04482
ms.sourcegitcommit: 00e16b9afe6b22ba0591e4d0d92690544e6d4357
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2021
ms.locfileid: "105617048"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>快速入門：使用 Visual Studio 建立您的第一個 Node.js 應用程式

在這個 5-10 分鐘的 Visual Studio 整合式開發環境 (IDE) 簡介中，您將建立簡單的 Node.js Web 應用程式。

## <a name="prerequisites"></a>必要條件

* 您必須安裝 Visual Studio 和 Node.js 開發工作負載。

    ::: moniker range=">=vs-2019"
    如果您尚未安裝 Visual Studio 2019，請移至 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads) 頁面，免費進行安裝。
    ::: moniker-end
    ::: moniker range="vs-2017"
    如果您尚未安裝 Visual Studio 2017，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。
    ::: moniker-end

    如果您需要安裝工作負載，但已有 Visual Studio，請移至 [**工具**  >  **取得工具和功能**]，這會開啟 Visual Studio 安裝程式。 選擇 [Node.js 開發] 工作負載，然後選擇 [修改]。

    ![VS 安裝程式中的 Node.js 工作負載](../ide/media/quickstart-nodejs-workload.png)

* 您必須安裝 Node.js 執行階段。

    如果您沒有安裝它，建議您從 [Node.js](https://nodejs.org/en/download/) 網站安裝 LTS 版本，以提供與外部架構和程式庫的最佳相容性。 Node.js 是針對32位和64位架構所建立。 Visual Studio 中的 Node.js 工具（包含在 Node.js 工作負載中）支援兩種版本。 只有一個是必要的，而且 Node.js 安裝程式只支援一次安裝一個。
    
    一般而言，Visual Studio 會自動偵測已安裝的 Node.js 執行階段。 如果未偵測到已安裝的執行時間，您可以在建立專案之後，將專案設定為參考已安裝的執行時間 (在專案節點上按一下滑鼠右鍵，選擇 [ **屬性**]，然後設定 **Node.exe 路徑**) 。 您可以使用 Node.js 的全域安裝，也可以在每個 Node.js 專案中指定本機解譯器的路徑。 

## <a name="create-a-project"></a>建立專案

首先，您將建立 Node.js Web 應用程式專案。

1. 如果您尚未安裝 Node.js 執行階段，請從 [Node.js](https://nodejs.org/en/download/) 網站安裝 LTS 版本。

    如需詳細資訊，請參閱必要條件。

1. 開啟 Visual Studio。

1. 建立新專案。

    ::: moniker range=">=vs-2019"
    按 **Esc** 關閉開始視窗。 鍵入 **Ctrl + Q** 開啟 [搜尋] 方塊，鍵入 **Node.js**，然後選擇 [Create new Blank Node.js Web application project] \(建立新的空白 Node.js Web 應用程式專案\) (JavaScript)。 在出現的對話方塊中選擇 [建立]。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從頂端功能表列中 **，選擇 [** 檔案  >  **新增**  >  **專案**]。 在 [新增專案] 對話方塊的左窗格中，展開 **JavaScript**，然後選擇 **Node.js**。 在中間窗格中，選擇 [Blank Node.js Web application] (空白的 Node.js Web 應用程式)，然後選擇 [確定]。
    ::: moniker-end
    如果您看不到 [空白的 Node.js Web 應用程式] 專案範本，則必須新增 **Node.js 開發** 工作負載。 如需詳細指示，請參閱[必要條件](#prerequisites)。

    Visual Studio 會建立新的方案並開啟專案。 *server.js* 會在左窗格的編輯器中開啟。

## <a name="explore-the-ide"></a>探索 IDE

1. 查看方案總管的右窗格。

   ![方案總管](../ide/media/quickstart-nodejs-solution-explorer.png)

   - 以粗體反白顯示的項目就是您的專案，並使用您在 [新增專案] 對話方塊中所指定的名稱。 在磁片上，此專案是由專案資料夾中的 *>.njsproj* 檔案表示。

   - 最上層是方案，預設其名稱會與專案相同。 方案 (以磁碟上的 *.sln* 檔案呈現) 是一或多個相關專案的容器。

   - npm 節點會顯示任何已安裝的 npm 套件。 您可以使用滑鼠右鍵按一下 npm 節點，以使用對話方塊來搜尋並安裝 npm 套件。

1. 如果您想要從命令提示字元安裝 npm 套件或 Node.js 命令，請以滑鼠右鍵按一下專案節點，然後選擇 [ **在這裡開啟命令提示** 字元]。

   ![Node.js 命令提示字元](../ide/media/quickstart-nodejs-command-prompt.png)

1. 在編輯器 (左窗格) 的 *server.js* 檔案中，選擇 `http.createServer`，然後按 **F12**，或選擇操作 (右鍵) 功能表中的 [移至定義]。 此命令會將您帶到在 node.js `createServer` *. ts* 中的函式定義。

   ![移至定義操作功能表](../ide/media/quickstart-nodejs-gotodefinition.png)

1. 移回至 *server.js*，然後將游標置於 `res.end('Hello World\n');` 這行程式碼的字串結尾，並進行修改，讓它看起來如下：

    `res.end('Hello World\n' + res.connection.`

    如果您鍵入 `connection.`，則 IntelliSense 會提供自動完成程式碼項目的選項。

   ![IntelliSense 自動完成](../ide/media/quickstart-nodejs-intellisense.png)

1. 選擇 [localPort]，然後鍵入 `);` 以完成陳述式，讓它看起來如下：

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>執行應用程式

1. 按下 **Ctrl** + **F5** (或 **Debug > 啟動但不) 調試** 程式來執行應用程式。 應用程式會在瀏覽器中開啟。

1. 在瀏覽器視窗中，您會看到 "Hello World" 以及本機連接埠號碼。

1. 關閉網頁瀏覽器。

恭喜您完成本快速入門，其中，您已開始使用 Visual Studio IDE 和 Node.js。 如果您想要更深入地鑽研其功能，請繼續目錄的 [教學課程] 一節中的教學課程。

## <a name="next-steps"></a>下一步

> [!div class="nextstepaction"]
> [將應用程式部署至 Linux App Service](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [Node.js 和 Express 的教學課程](../javascript/tutorial-nodejs.md)

> [!div class="nextstepaction"]
> [Node.js 和 React 的教學課程](../javascript/tutorial-nodejs-with-react-and-jsx.md)