---
title: 建立 Node.js 和 Express 應用程式 - Visual Studio | Microsoft Docs
description: 在本教學課程中，您會在 Visual Studio 中建立 Node.js 和 Express 應用程式
ms.custom: ''
ms.date: 03/13/2018
ms.technology: vs-nodejs
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 47bf06fabba9197029831382b6ad6e9068e7829c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>教學課程：在 Visual Studio 中建立 Node.js 和 Express 應用程式
在使用 Node.js 和 Express 進行 Visual Studio 開發的這個教學課程中，您將建立簡單的 Node.js Web 應用程式、新增一些程式碼、探索 IDE 的一些功能，以及執行應用程式。 如果您尚未安裝 Visual Studio，請在[這裡](http://www.visualstudio.com)免費安裝它。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> * 建立 Node.js 專案
> * 新增一些程式碼
> * 使用 IntelliSense
> * 執行應用程式
> * 叫用中斷點

## <a name="prerequisites"></a>必要條件

* 您必須安裝 Visual Studio 和 Node.js 開發工作負載。

    如果您尚未安裝 Visual Studio，請在[這裡](http://www.visualstudio.com)免費安裝它。

    如果您需要安裝工作負載，但已擁有 Visual Studio，請在 [新增專案] 對話方塊的左窗格中，按一下 [開啟 Visual Studio 安裝程式]。 Visual Studio 安裝程式即會啟動。 選擇 [Node.js 開發] 工作負載，然後選擇 [修改]。

* 您必須安裝 Node.js 執行階段。

    如果您沒有安裝，請從 [Node.js](https://nodejs.org/en/download/) 網站安裝 LTS 版本。 一般而言，Visual Studio 會自動偵測已安裝的 Node.js 執行階段。 如果偵測不到已安裝的執行階段，您可以在屬性頁面中將專案設定為參考已安裝的執行階段 (建立專案之後，以滑鼠右鍵按一下專案節點，然後選擇 [屬性])。

    本教學課程使用 Node.js 8.10.0 來進行測試。

## <a name="create-a-project"></a>建立專案
首先，您將建立 Node.js Web 應用程式專案。

1. 開啟 Visual Studio 2017。

1. 從頂端功能表列中，選擇 [檔案] > [新增] > [專案]。

1. 在 [新增專案] 對話方塊的左窗格中，展開 [JavaScript]，然後選擇 [Node.js]。 在中間窗格中，選取 [基本的 Azure Node.js Express 4 應用程式]，然後選擇 [確定]。

     如果沒有看到 [基本的 Azure Node.js Express 4 應用程式] 專案範本，您必須先安裝 [Node.js 開發] 工作負載。

    Visual Studio 會建立新的方案，並開啟專案。 *app.js* 專案檔會在編輯器 (左窗格) 中開啟。

    - 以粗體反白顯示的項目就是您的專案，並使用您在 [新增專案] 對話方塊中所指定的名稱。 在檔案系統中，此專案是由專案資料夾中的 *.njsproj* 檔案所呈現。 您可以設定與專案建立關聯的屬性和環境變數，方法是以滑鼠右鍵按一下專案，然後選擇 [屬性]。 因為專案檔不會對 Node.js 專案來源進行自訂變更，所以您可以使用其他開發工具執行來回行程。

    - 最上層是方案，預設其名稱會與專案相同。 方案 (以磁碟上的 *.sln* 檔案呈現) 是一或多個相關專案的容器。

    - npm 節點會顯示任何已安裝的 npm 套件。 您可以使用滑鼠右鍵按一下 npm 節點，以使用對話方塊來搜尋並安裝 npm 套件。

    - *app.js* 之類的專案檔會顯示在專案節點下。 *app.js* 是專案啟動檔案。

1. 開啟 **npm** 節點，並確定所有必要的 npm 套件都存在。

    如果遺漏任何項目 (驚嘆號圖示)，您可以用滑鼠右鍵按一下 **npm** 節點，然後選擇 [安裝遺漏的 npm 套件]。

## <a name="add-some-code"></a>新增一些程式碼

1. 在 [方案總管] (右窗格) 中，開啟 views 資料夾，然後開啟 *index.pug*。

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

1. 在 routes 資料夾中，開啟 *index.js*。

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

    包含 `res.render` 的程式碼行中有錯誤。 我們需要修正此錯誤，才能執行應用程式。 我們將在下節修正該錯誤。

## <a name="use-intellisense"></a>使用 IntelliSense

1. 在 *index.js* 中，移至包含 `res.render` 的行。

1. 在 `data` 字串後面鍵入 `: get`，而 IntelliSense 將會顯示 `getData` 函式。 選取 `getData`。

    ![使用 IntelliSense](../nodejs/media/tutorial-nodejs-intellisense.png)

1. 移除 `"data"` 前面的逗號 (`,`)，而且您會看到運算式上的綠色語法醒目提示。 將滑鼠停留在語法醒目提示上方。

    ![檢視語法錯誤](../nodejs/media/tutorial-nodejs-syntax-checking.png)

    此訊息的最後一行告訴您：JavaScript 解譯器必須要有逗號 (`,`)。

1. 按一下 [錯誤清單] 索引標籤。

    您會看到警告和描述以及檔案名稱和行號。

    ![檢視錯誤清單](../nodejs/media/tutorial-nodejs-error-list.png)

1. 在 `"data"` 前面新增逗號 (`,`)，以修正程式碼。

## <a name="set-a-breakpoint"></a>設定中斷點

1. 在 *index.js* 中，按一下下列程式碼行前面的左裝訂邊，以設定中斷點：

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

在本教學課程中，您已了解如何使用 Express 建立和執行 Node.js 應用程式，以及使用偵錯工具叫用中斷點。

> [!div class="nextstepaction"]
> [適用於 Visual Studio 的 Node.js 工具](https://github.com/Microsoft/nodejstools)