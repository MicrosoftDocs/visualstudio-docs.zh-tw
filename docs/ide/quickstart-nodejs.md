---
title: "快速入門：使用 Visual Studio 建立您的第一個 Node.js 應用程式 | Microsoft Docs"
ms.custom: 
ms.date: 11/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: ghogen
dev_langs: JavaScript
ms.workload: nodejs
ms.openlocfilehash: 12c848797b167038b02106ca3392cac50171f699
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>快速入門：使用 Visual Studio 建立您的第一個 Node.js 應用程式
在這個 5-10 分鐘的 Visual Studio 整合式開發環境 (IDE) 簡介中，您將建立簡單的 Node.js Web 應用程式。 如果您尚未安裝 Visual Studio，請在[這裡](http://www.visualstudio.com)免費安裝它。  

## <a name="create-a-project"></a>建立專案
首先，您將建立 Node.js Web 應用程式專案。

1. 開啟 Visual Studio 2017。  

2. 從頂端功能表列中，選擇 [檔案] > [新增] > [專案]。  

3. 在 [新增專案] 對話方塊的左窗格中，展開 [JavaScript]，然後選擇 [Node.js]。 在中間窗格中，選擇 [Blank Node.js Web application] (空白的 Node.js Web 應用程式)，然後選擇 [確定]。   

     如果您看不到 [Blank Node.js Web application] (空白的 Node.js Web 應用程式) 專案範本，請在 [新增專案] 對話方塊的左窗格中，按一下 [開啟 Visual Studio 安裝程式] 連結。 Visual Studio 安裝程式即會啟動。 選擇 [Node.js 開發] 工作負載，然後選擇 [修改]。  

     ![VS 安裝程式中的 Node.js 工作負載](../ide/media/quickstart-nodejs-workload.png)  

    Visual Studio 會建立新的方案並開啟專案。 **server.js** 會在編輯器中開啟。

## <a name="explore-the-ide"></a>探索 IDE  

1. 查看方案總管的右窗格。

   ![底下提供說明，包括方案總管](../ide/media/quickstart-nodejs-solution-explorer.png)  

  - 以粗體反白顯示的項目就是您的專案，並使用您在 [新增專案] 對話方塊中所指定的名稱。 在磁碟上，此專案是由專案資料夾中的 .njsproj 檔案所呈現。

  - 最上層是方案，預設其名稱會與專案相同。 方案 (以磁碟上的 .sln 檔案呈現) 是一或多個相關專案的容器。

  - npm 節點會顯示任何已安裝的 npm 套件。 您可以使用滑鼠右鍵按一下 npm 節點，以使用對話方塊來搜尋並安裝 npm 套件。

1. 如果您想要從命令提示字元安裝 npm 套件或 node.js 命令，請以滑鼠右鍵按一下專案節點，然後選擇 [在這裡開啟命令提示字元]。

   ![Node.js 命令提示字元](../ide/media/quickstart-nodejs-command-prompt.png) 

1. 在編輯器 (左窗格) 的 **server.js** 檔案中，選擇 `http.createServer`，然後按 **F12**，或選擇操作 (右鍵) 功能表中的 [移至定義]。 此命令會將您帶到 index.d.ts 中 `createServer` 函式的定義。  

   ![移至定義操作功能表](../ide/media/quickstart-nodejs-gotodefinition.png)  

1. 將游標置於 `res.end('Hello World\n');` 這行程式碼的字串結尾，並進行修改，讓它看起來如下：

    `res.end('Hello World\n' + res.connection.`

    如果您鍵入 `connection.`，則 IntelliSense 會提供自動完成程式碼項目的選項。

   ![IntelliSense 自動完成](../ide/media/quickstart-nodejs-intellisense.png)  

1. 選擇 [localPort]，然後鍵入 `);` 以完成陳述式，讓它看起來如下：

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>執行應用程式
1. 按 **Ctrl+F5** (或 [偵錯] > [啟動但不偵錯])，以執行應用程式。 應用程式會在瀏覽器中開啟。  

1. 在瀏覽器視窗中，您會看到 "Hello World" 以及本機連接埠號碼。

1. 關閉網頁瀏覽器。  

恭喜您完成此快速入門！ 我們希望您更了解 Visual Studio IDE。 如果您想要更深入地鑽研其功能，請繼續目錄的 [教學課程] 一節中的教學課程。  

## <a name="next-steps"></a>後續步驟 

- 逐步進行 [Node.js 教學課程](../nodejs/tutorial-nodejs.md)  
- 深入了解 [Visual Studio IDE](../ide/visual-studio-ide.md)  
- 深入了解[適用於 Visual Studio 的 Node.js 工具](https://github.com/Microsoft/nodejstools/wiki)