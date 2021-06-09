---
title: 建立 Node.js 與 Express 應用程式
description: 在本教學課程中，您將瞭解如何在 Visual Studio 中使用 Express web 應用程式架構建立簡單的 Node.js 應用程式。
ms.date: 03/25/2021
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 5433ae0e84396f3c16dc5ed50f51ce7e9eb7056f
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760974"
---
# <a name="tutorial-create-a-nodejs-and-express-app-in-visual-studio"></a>教學課程：在 Visual Studio 中建立 Node.js 和 Express 應用程式

在使用 Node.js 和 Express 進行 Visual Studio 開發的這個教學課程中，您將建立簡單的 Node.js Web 應用程式、新增一些程式碼、探索 IDE 的一些功能，以及執行應用程式。 

::: moniker range="vs-2017"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。

::: moniker-end

::: moniker range=">=vs-2019"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads)頁面免費進行安裝。

::: moniker-end

在本教學課程中，您會了解如何：
> [!div class="checklist"]
> * 建立 Node.js 專案
> * 新增一些程式碼
> * 使用 IntelliSense 來編輯程式碼
> * 執行應用程式
> * 叫用偵錯工具中的中斷點

## <a name="before-you-begin"></a>開始之前

以下快速常見問題集介紹一些重要概念。

### <a name="what-is-nodejs"></a>什麼是 Node.js？

Node.js 是執行 JavaScript 伺服器端的伺服器端 JavaScript 執行階段環境。

### <a name="what-is-npm"></a>什麼是 npm？

npm 是 Node.js 的預設套件管理員。 套件管理員可讓程式設計人員能夠發佈並共用 Node.js 程式庫的原始程式碼，其設計目的是為了簡化程式庫的安裝、更新及解除安裝。

### <a name="what-is-express"></a>什麼是 express？

Express 是一種 Web 應用程式架構，用作 Node.js 的伺服器架構以建置 Web 應用程式。 Express 可讓您選擇不同的前端架構來建立 UI，例如 Pug (先前稱為 Jade) 。 本教學課程中使用 Pug。

## <a name="prerequisites"></a>必要條件

* 您必須安裝 Visual Studio 和 Node.js 開發工作負載。

    ::: moniker range=">=vs-2019"
    如果您尚未安裝 Visual Studio 2019，請移至 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/) 頁面，免費進行安裝。
    ::: moniker-end
    ::: moniker range="vs-2017"
    如果您尚未安裝 Visual Studio 2017，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)頁面免費進行安裝。
    ::: moniker-end

    如果您需要安裝工作負載，但已有 Visual Studio，請移至 [**工具**  >  **取得工具和功能**]，這會開啟 Visual Studio 安裝程式。 選擇 [Node.js 開發] 工作負載，然後選擇 [修改]。

    ![VS 安裝程式中的 Node.js 工作負載](../ide/media/quickstart-nodejs-workload.png)

* 您必須安裝 Node.js 執行階段。

    如果您沒有安裝它，建議您從 [Node.js](https://nodejs.org/en/download/) 網站安裝 LTS 版本，以提供與外部架構和程式庫的最佳相容性。 Node.js 是針對32位和64位架構所建立。 Visual Studio 中的 Node.js 工具（包含在 Node.js 工作負載中）支援兩種版本。 只有一個是必要的，而且 Node.js 安裝程式只支援一次安裝一個。
    
    一般而言，Visual Studio 會自動偵測已安裝的 Node.js 執行階段。 如果未偵測到已安裝的執行時間，您可以在建立專案之後，將專案設定為參考已安裝的執行時間 (在專案節點上按一下滑鼠右鍵，選擇 [ **屬性**]，然後設定 **Node.exe 路徑**) 。 您可以使用 Node.js 的全域安裝，也可以在每個 Node.js 專案中指定本機解譯器的路徑。 

    本教學課程使用 Node.js 8.10.0 來進行測試。

## <a name="create-a-new-nodejs-project"></a>建立新的 Node.js 專案

Visual Studio 可在「專案」中管理單一應用程式的檔案。 專案包含原始程式碼、資源和組態檔。

在本教學課程中，您會從包含 Node.js 和 express 應用程式之程式碼的簡單專案開始。

1. 開啟 Visual Studio。

1. 建立新專案。

    ::: moniker range=">=vs-2019"
    按 **Esc** 關閉開始視窗。 鍵入 **Ctrl + Q** 開啟 [搜尋] 方塊，鍵入 **Node.js**，然後選擇 [Create a new Basic Azure Node.js Express 4 application] \(建立新的基礎 Azure Node.js Express 4 應用程式\) (JavaScript)。 在出現的對話方塊中選擇 [建立]。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從頂端功能表列中 **，選擇 [** 檔案  >  **新增**  >  **專案**]。 在 [新增專案] 對話方塊的左窗格中，展開 **JavaScript**，然後選擇 **Node.js**。 在中間窗格中，選擇 [ **基本 Azure Node.js Express 4 應用程式**]，然後選擇 **[確定]**。
    ::: moniker-end
    如果您看不到 [基本的 Azure Node.js Express 4 應用程式] 專案範本，則必須新增 **Node.js 開發** 工作負載。 如需詳細指示，請參閱[必要條件](#prerequisites)。

    Visual Studio 會建立新的方案，並在右窗格中開啟專案。 *app.js* 專案檔會在編輯器 (左窗格) 中開啟。

    ![專案結構](../javascript/media/tutorial-project-structure.png)

    (1) 以 **粗體** 反白顯示的項目就是您的專案，並使用您在 [新增專案] 對話方塊中所指定的名稱。 在檔案系統中，此專案是由專案資料夾中的 *.njsproj* 檔案所呈現。 您可以設定與專案建立關聯的屬性和環境變數，方法是以滑鼠右鍵按一下專案，然後選擇 [屬性]。 因為專案檔不會對 Node.js 專案來源進行自訂變更，所以您可以使用其他開發工具執行來回行程。

    (2) 最上層是方案，其名稱預設會與專案相同。 方案 (以磁碟上的 *.sln* 檔案呈現) 是一或多個相關專案的容器。

    (3) npm 節點會顯示任何已安裝的 npm 套件。 您可以用滑鼠右鍵按一下 npm 節點，使用對話方塊來搜尋及安裝 npm 套件，或者使用 *package.json* 中的設定來安裝及更新套件，並以滑鼠右鍵按一下 npm 節點中的選項。

    (4) *package.json* 是 npm 用來管理本機安裝套件之套件相依性和套件版本的檔案。 如需詳細資訊，請參閱 [管理 npm 封裝](../javascript/npm-package-management.md)。

    (5) *app.js* 之類的專案檔會顯示在專案節點下。 *app.js* 是專案啟動檔案，這也是它會以 **粗體** 顯示的原因。 以滑鼠右鍵按一下專案中的檔案，然後選取 [設定為 Node.js 啟動檔案]，即可設定啟動檔案。

1. 開啟 **npm** 節點，並確定所有必要的 npm 套件都存在。

    如果遺漏任何套件 (驚嘆號圖示) ，您可以在 [ **npm** ] 節點上按一下滑鼠右鍵，然後選擇 [ **安裝 npm 套件**]。

## <a name="add-some-code"></a>新增一些程式碼

應用程式使用 Pug 作為前端 JavaScript 架構。 Pug 則使用編譯成 HTML 的簡單標記程式碼。 (Pug 會設定為 *app.js* 中的檢視引擎。 設定 *app.js* 檢視引擎的程式碼為 `app.set('view engine', 'pug');`。)

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

    上述程式碼會用來動態產生一個具有標題和歡迎訊息的 HTML 頁面。 此頁面也包含了程式碼，以顯示每次按下按鈕就會隨之變更的影像。

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

    此程式碼會建立資料物件，您要將它傳送至動態產生的 HTML 頁面。

1. 將 `router.get` 函式呼叫取代為下列程式碼：

    ```js
    router.get('/', function (req, res) {
        res.render('index', { title: 'Express', "data" });
    });
    ```

    上述程式碼會使用 Express 路由器物件來設定目前的頁面，然後轉譯頁面，其中會將標題和資料物件傳遞給頁面。 *Index.pug* 檔案在這裡指定為執行 *index.js* 時要載入的頁面。 *index.js* 設定為 *app.js* 程式碼中的預設路由 (未顯示)。

    為了示範 Visual Studio 的數個功能，我們故意在包含 `res.render` 的程式碼行中犯了一個錯誤。 您要先修正此錯誤，應用程式才能執行，這是您在下一節中要執行的作業。

## <a name="use-intellisense"></a>使用 IntelliSense

IntelliSense 是一種 Visual Studio 工具，可協助您撰寫程式碼。

1. 在 *index.js* 中，移至包含 `res.render` 的行。

1. 將您的游標放在 `data` 字串後面，鍵入 `: get`，IntelliSense 將會顯示稍早在程式碼中定義的 `getData` 函式。 選取 `getData`。

    ![使用 IntelliSense](../javascript/media/tutorial-nodejs-intellisense.png)

1. 新增括弧，使其成為函式呼叫 `getData()` 。

1. 移除 `"data"` 前面的逗號 (`,`)，而且您會看到運算式上的綠色語法醒目提示。 將滑鼠停留在語法醒目提示上方。

    ![檢視語法錯誤](../javascript/media/tutorial-nodejs-syntax-checking.png)

    此訊息的最後一行告訴您：JavaScript 解譯器必須要有逗號 (`,`)。

1. 在下方窗格中，按一下 [ **錯誤清單** ] 索引標籤，然後針對所報告的問題類型，選取 [ **組建 + IntelliSense** ]。

    您會看到警告和描述以及檔案名稱和行號。

    ![檢視錯誤清單](../javascript/media/tutorial-nodejs-error-list.png)

1. 在 `"data"` 前面新增逗號 (`,`)，以修正程式碼。

    更正後，程式碼行應該如下所示：`res.render('index', { title: 'Express', "data": getData() });`

## <a name="set-a-breakpoint"></a>設定中斷點

您接著要執行附加了 Visual Studio 偵錯工具的應用程式。 執行這項作業之前，您需要設定中斷點。

1. 在 *index.js* 中，按一下下列程式碼行前面的左裝訂邊，以設定中斷點：

    `res.render('index', { title: 'Express', "data": getData() });`

    中斷點是可靠偵錯最基本也最重要的功能。 中斷點會指出 Visual Studio 應暫停程式碼執行的地方，如此一來您可以查看變數的值或記憶體的行為，或查看程式碼分支是否正在執行。

    ![設定中斷點](../javascript/media/tutorial-nodejs-set-breakpoint.png)

## <a name="run-the-application"></a>執行應用程式

1. 在 Debug 工具列中選取 [debug] 目標，例如 [ **Web server (Google Chrome)** 或 [ **web 伺服器 (Microsoft Edge)**]。

    ::: moniker range=">=vs-2019"
    ![選取偵錯目標](../javascript/media/vs-2019/tutorial-nodejs-deploy-target.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![選取偵錯目標](../javascript/media/tutorial-nodejs-deploy-target.png)
    ::: moniker-end

    如果您的電腦中有 Chrome 可供使用，但未顯示為選項，請從偵錯目標下拉式清單中選擇 [瀏覽方式]，並選取 Chrome 作為預設瀏覽器目標 (選擇 [設為預設值])。

1. 按 **F5** ([偵錯] > [開始偵錯]) 以執行應用程式。

    偵錯工具會在您設定的中斷點處暫停。 現在，您可以檢查您的應用程式狀態。

1. 將滑鼠停留 `getData` 上方，以在 DataTip 中查看其屬性

    ![檢查變數](../javascript/media/tutorial-nodejs-inspect-variables.png)

1. 按 **F5** ([偵錯] > [繼續]) 以繼續。

    應用程式會在瀏覽器中開啟。

    在瀏覽器視窗中，您會看到標題為 "Express"，而第一個段落中有 "Welcome to Express"。

1. 按一下按鈕，以顯示不同的影像。

    ![瀏覽器中執行的應用程式](../javascript/media/tutorial-nodejs-running-in-browser.png)

1. 關閉網頁瀏覽器。

## <a name="optional-publish-to-azure-app-service"></a>(選擇性) 發行至 Azure App Service

1. 在方案總管中，以滑鼠右鍵按一下專案，然後選擇 [ **發行**]。

   ![發佈至 Azure App Service](../javascript/media/tutorial-nodejs-publish-to-azure.png)

1. 選擇 [Microsoft Azure App Service]。

    在 [App Service] 對話方塊中，您可以登入 Azure 帳戶，並連線至現有 Azure 訂用帳戶。

1. 遵循其餘步驟來選取訂用帳戶、選擇或建立資源群組、選擇或建立應用程式服務平面，然後在系統提示發行至 Azure 時遵循步驟。 如需詳細指示，請參閱 [使用 web Deploy 發佈至 Azure 網站](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy)。

1. [輸出] 視窗會顯示部署到 Azure 的進度。

    部署成功時，您的應用程式會在執行 Azure App Service 的瀏覽器中開啟。 按一下按鈕以顯示影像。

   ![執行 Azure App Service 的應用程式](../javascript/media/tutorial-nodejs-running-in-azure.png)

恭喜您完成此教學課程！

## <a name="next-steps"></a>下一步

> [!div class="nextstepaction"]
> [將應用程式部署至 Linux App Service](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [AngularJS 語言服務延伸模組](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio)
