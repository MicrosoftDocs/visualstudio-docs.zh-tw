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
ms.openlocfilehash: 8a36986842cdac85a8a3e6ab474024b8db552ee7
ms.sourcegitcommit: ab5735d64a6ad7aecabf5d6df159888e3246bff5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2021
ms.locfileid: "111433710"
---
# <a name="quickstart-create-your-first-nodejs-app-with-visual-studio"></a>快速入門：使用 Visual Studio 建立您的第一個 Node.js 應用程式

在這項 Visual Studio 整合式開發環境 (IDE) 的5至10分鐘簡介中，您將建立一個簡單的 Node.js web 應用程式。

## <a name="prerequisites"></a>必要條件

開始之前，請先安裝 Visual Studio 並設定 Node.js 環境。

### <a name="install-visual-studio"></a>安裝 Visual Studio

::: moniker range=">=vs-2019"
如果您尚未安裝 Visual Studio 2019，請移至 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads) 頁面，免費進行安裝。
::: moniker-end
::: moniker range="vs-2017"
如果您尚未安裝 Visual Studio 2017，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。
::: moniker-end

### <a name="set-up-your-nodejs-environment"></a>設定您的 Node.js 環境

Visual Studio 可協助設定您的環境，包括安裝 Node.js 開發常見的工具。

1. 在 Visual Studio 中，移至 [**工具**  >  **取得工具及功能**]。

1. 在 [Visual Studio 安裝程式中，選擇 **Node.js 開發** 工作負載，然後選取 [ **修改** ] 以下載並安裝工作負載。

    ![Visual Studio 安裝程式中的 Node.js 工作負載](../ide/media/quickstart-nodejs-workload.png)

1. 安裝 [Node.js 運行](https://nodejs.org/en/download/)時間的 LTS 版本。 我們建議使用 LTS 版本，以取得與外部架構和程式庫的最佳相容性。

    雖然 Node.js 是針對32位和64位架構所建立，但 Node.js 安裝程式一次只支援安裝一個版本。

1. 如果 Visual Studio 未偵測到您已安裝的執行時間 (通常會) ，請將您的專案設定為參考已安裝的執行時間：

   1. [建立專案](#create-your-app-project)之後，以滑鼠右鍵按一下專案節點。

   1. 選取 [ **屬性** ]，並設定 **Node.exe 路徑**。 您可以使用 Node.js 的全域安裝，或指定每個 Node.js 專案中的本機解譯器路徑。

## <a name="create-your-app-project"></a>建立您的應用程式專案

1. 如果您還沒有這麼做，請安裝 LTS 版本的 [Node.js 運行](https://nodejs.org/en/download/)時間。 如需詳細資訊，請參閱 [必要條件](#prerequisites)。

1. 開啟 Visual Studio。

1. 建立新專案。

    ::: moniker range=">=vs-2019"

    1. 按 **Esc** 關閉開始視窗。

    1. 按 **Ctrl + Q** 開啟 [搜尋] 方塊，然後輸入 **Node.js**。

    1. 選擇 **空白 Node.js Web 應用程式 (JavaScript)**。 在對話方塊中，選取 [ **建立**]。

    ::: moniker-end

    ::: moniker range="vs-2017"
    1. 從頂端功能表列中 **，選擇 [** 檔案 > **新增** > **專案**]。

    1. 在 [ **新增專案** ] 對話方塊的左窗格中，展開 [ **JavaScript** ]，然後選擇 [ **Node.js**]。

    1. 在中間窗格中，選擇 [ **空白 Node.js Web 應用程式** ]，然後選取 **[確定]**。

    ::: moniker-end
    
    如果您看不到 [空白的 Node.js Web 應用程式] 專案範本，則必須新增 **Node.js 開發** 工作負載。 如需詳細指示，請參閱 [必要條件](#prerequisites)。

    Visual Studio 建立並開啟專案。 專案的 *server.js* 檔會在左邊的編輯器中開啟。

## <a name="explore-the-ide"></a>探索 IDE

1. 在右窗格中，查看 **方案總管**。

   ![方案總管](../ide/media/quickstart-nodejs-solution-explorer.png)

   - 以粗體反白顯示的是您的專案，使用您在設定專案時所提供的名稱。 在磁片上，此專案是由專案資料夾中的 *>.njsproj* 檔案表示。

   - 最上層是方案，預設其名稱會與專案相同。 方案 (以磁碟上的 *.sln* 檔案呈現) 是一或多個相關專案的容器。

   - **Npm** 節點會顯示已安裝的 npm 套件。 您可以用滑鼠右鍵按一下 [npm] 節點，以使用對話方塊搜尋和安裝 npm 套件。

1. 如果您想要從命令提示字元安裝 npm 套件或 Node.js 命令，請以滑鼠右鍵按一下專案節點，然後選擇 [ **在這裡開啟命令提示** 字元]。

   ![Node 點 j s 命令提示字元](../ide/media/quickstart-nodejs-command-prompt.png)

1. 如果您想要測試導覽至原始程式碼，請從開啟的 *server.js* 檔案中選取 [ **createServer** ]，然後按下 **F12** 鍵，或從內容中選擇 [ **移至定義** ] (以滑鼠右鍵按一下) 功能表。 此命令會帶您前往 `createServer` *HTTP.sys* 中的函式定義。

   ![移至定義操作功能表](../ide/media/quickstart-nodejs-gotodefinition.png)

1. 返回 *server.js* ，並找出這行程式碼： `res.end('Hello World\n');` 。 修改程式碼，如下所示：

    `res.end('Hello World\n' + res.connection.`

    當您輸入 **connection** 時，IntelliSense 會提供自動完成程式碼專案的選項。

   ![IntelliSense 自動完成](../ide/media/quickstart-nodejs-intellisense.png)

1. 選擇 [ **localPort** ]，然後輸入 **) ;** 以完成語句：

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-app"></a>執行應用程式

1. 按 **Ctrl + F5** (， 或  >  在 **不進行調試** 程式的情況下啟動 Debug) 來執行應用程式。 
 
   應用程式會在瀏覽器中開啟。

1. 在瀏覽器中，確認您看到「Hello World」訊息和本機埠號碼。

恭喜！ 您已使用 Visual Studio 建立簡單的 Node.js 應用程式。 若要深入瞭解，請繼續進行目錄的 [ **教學** 課程] 區段。

## <a name="next-steps"></a>下一步

> [!div class="nextstepaction"]
> [將應用程式部署至 Linux App Service](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [Node.js 和 Express 的教學課程](../javascript/tutorial-nodejs.md)

> [!div class="nextstepaction"]
> [Node.js 和 React 的教學課程](../javascript/tutorial-nodejs-with-react-and-jsx.md)
