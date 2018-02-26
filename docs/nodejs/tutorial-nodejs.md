---
title: "Visual Studio 中的 Node.js 使用者入門 | Microsoft Docs"
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: ghogen
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 1d91d46b20f82a1700c2d20639b3a8827c92bcb0
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2018
---
# <a name="getting-started-with-nodejs-in-visual-studio"></a>Visual Studio 中的 Node.js 使用者入門
在使用 Visual Studio 進行 Node.js 開發的這個教學課程中，您將建立簡單的 Node.js Web 應用程式、新增一些程式碼、探索 IDE 的一些功能，以及執行應用程式。 如果您尚未安裝 Visual Studio，請在[這裡](http://www.visualstudio.com)免費安裝它。  

## <a name="create-a-project"></a>建立專案
首先，您將建立 Node.js Web 應用程式專案。

1. 開啟 Visual Studio 2017。  

2. 從頂端功能表列中，選擇 [檔案] > [新增] > [專案]。  

3. 在 [新增專案] 對話方塊的左窗格中，展開 [JavaScript]，然後選擇 [Node.js]。 在中間窗格中，選擇 [基本的 Azure Node.js Express 4 應用程式]，然後選擇 [確定]。   

     如果您看不到 [B基本的 Azure Node.js Express 4 應用程式] 專案範本，請在 [新增專案] 對話方塊的左窗格中，按一下 [開啟 Visual Studio 安裝程式] 連結。 Visual Studio 安裝程式即會啟動。 選擇 [Node.js 開發] 工作負載，然後選擇 [修改]。 

    Visual Studio 會建立新的方案，並開啟專案。 **app.js** 專案檔會在編輯器 (左窗格) 中開啟。 如果您不熟悉 Visual Studio 方案和專案，請參閱[快速入門：使用 Visual Studio 建立您的第一個 Node.js 應用程式](../ide/quickstart-nodejs.md)。

4. 如果您尚未安裝 Node.js 執行階段，請從 [Node.js](https://nodejs.org/en/download/) \(英文\) 網站安裝它。

    一般而言，Visual Studio 會自動偵測已安裝的 Node.js 執行階段。 如果它沒有偵測到已安裝的執行階段，您可以將專案設定為參考已安裝的執行階段。

## <a name="add-some-code"></a>新增一些程式碼

1. 在方案總管 (右窗格) 中，開啟 views 資料夾，然後開啟 index.pug。

1. 將內容取代為下列標記。

    ```js
    extends layout

    block content
      h1= title
      p Welcome to #{title}
      script.
        var f1 = function() { document.getElementById('myImage').src='#{data.item1}' }
      script.
        var f2 = function() { document.getElementById('myImage').src='#{data.item2}' }
      script.
        var f3 = function() { document.getElementById('myImage').src='#{data.item3}' }

      button(onclick='f1()') One!
      button(onclick='f2()') Two!
      button(onclick='f3()') Three!
      p
      a: img(id='myImage' height='200' width='200' src='')
    ```

1. 在 routes 資料夾中，開啟 index.js。

1. 在 `router.get` 呼叫前面，新增下列程式碼：

    ```js
    var getData = function () {
        var data = {
            'item1': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg',
            'item2': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg',
            'item3': 'http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg'
        }
        return data;
    }
    ````

1. 將 `router.get` 函式呼叫取代為下列程式碼：

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

1. 在 `data` 後面，輸入 `: get`，而 IntelliSense 將會顯示 getData 顯示。 選取 `getData`。

    ![使用 IntelliSense](../nodejs/media/tutorial-nodejs-intellisense.png) 

1. 移除 `"data"` 前面的逗號 (`,`)，而且您會看到運算式上的綠色語法醒目提示。 將滑鼠停留在語法醒目提示上方。

    ![檢視語法錯誤](../nodejs/media/tutorial-nodejs-syntax-checking.png) 

    此訊息的最後一行告訴您：JavaScript 解譯器必須要有逗號 (`,`)。

1. 按一下 [錯誤清單] 索引標籤。

    您會看到警告和描述以及檔案名稱和行號。

    ![檢視錯誤清單](../nodejs/media/tutorial-nodejs-error-list.png)

1. 在 `"data"` 前面新增逗號 (`,`)，以修正程式碼。

## <a name="set-a-breakpoint"></a>設定中斷點

1. 在 index.js 中，按一下下列程式碼行前面的左裝訂邊，以設定中斷點：

    `res.render('index', { title: 'Express', "data": getData() });`

    中斷點是可靠偵錯最基本也最重要的功能。 中斷點會指出 Visual Studio 應暫停程式碼執行的地方，如此一來您可以查看變數的值或記憶體的行為，或查看程式碼分支是否正在執行。 

    ![設定中斷點](../nodejs/media/tutorial-nodejs-set-breakpoint.png) 

## <a name="run-the-application"></a>執行應用程式

1. 在 [偵錯] 工具列中選取偵錯目標。

    ![選取偵錯目標](../nodejs/media/tutorial-nodejs-deploy-target.png) 

1. 按 **F5** ([偵錯] > [開始偵錯]) 以執行應用程式。

    偵錯工具會在您設定的中斷點處暫停。 現在，您可以檢查您的應用程式狀態。

1. 將滑鼠停留 `getData` 上方，以在 DataTip 中查看其屬性

    ![檢查變數](../nodejs/media/tutorial-nodejs-inspect-variables.png)

1. 按 **F5** ([偵錯] > [繼續]) 以繼續。

    應用程式會在瀏覽器中開啟。

    在瀏覽器視窗中，您會看到標題為 "Express"，而第一個段落中有 "Welcome to Express"。

1. 按一下按鈕，以顯示不同的影像。

    ![瀏覽器中執行的應用程式](../nodejs/media/tutorial-nodejs-running-in-browser.png)  

1. 選取 [檢視] > [其他視窗] > [Node.js 互動式視窗]，以開啟 Node.js 互動式視窗。

   ![開啟 Node.js 互動式視窗](../nodejs/media/tutorial-nodejs-interactive-window.png)  

    互動式視窗支援您可以使用程式碼進行的所有事項，包含使用 `require()` 陳述式。 下列螢幕擷取畫面中的程式碼定義變數，並顯示 Node.js 解譯器的位置。

   ![Node.js 互動式視窗](../nodejs/media/tutorial-nodejs-interactive-window-example.png)  

1. 關閉網頁瀏覽器。  

## <a name="optional-publish-to-azure-app-service"></a>(選擇性) 發行至 Azure App Service

1. 在方案總管中，以滑鼠右鍵按一下專案，然後選擇 [發行]。

   ![發佈至 Azure App Service](../nodejs/media/tutorial-nodejs-publish-to-azure.png)  

1. 選擇 [Microsoft Azure App Service]。

    在 [App Service] 對話方塊中，您可以登入 Azure 帳戶，並連線至現有 Azure 訂用帳戶。

1. 遵循其餘步驟來選取訂用帳戶、選擇或建立資源群組、選擇或建立應用程式服務平面，然後在系統提示發行至 Azure 時遵循步驟。 如需詳細指示，請參閱[使用 Web Deploy 發行到 Azure 網站](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy)。

1. [輸出] 視窗會顯示部署到 Azure 的進度。

    部署成功時，您的應用程式會在執行 Azure App Service 的瀏覽器中開啟。 按一下按鈕以顯示影像。

   ![執行 Azure App Service 的應用程式](../nodejs/media/tutorial-nodejs-running-in-azure.png)  

恭喜您完成此教學課程！

## <a name="next-steps"></a>後續步驟 

- 深入了解[適用於 Visual Studio 的 Node.js 工具](https://github.com/Microsoft/nodejstools/wiki)  
- 深入了解 [Visual Studio IDE](../ide/visual-studio-ide.md)  