---
title: 快速入門：建立您的第一個 Vue.js 應用程式
description: 在本快速入門中，您會在 Visual Studio 中使用適用於 Visual Studio 的 Node.js 工具建立 Vue.js 應用程式
ms.custom: seodec18
ms.date: 09/24/2018
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
ms.openlocfilehash: a3bd2c65ccca172eca46eb5d935ef7735734a608
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58069589"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>快速入門：使用 Visual Studio 建立您的第一個 Vue.js 應用程式

在這個 5-10 分鐘的 Visual Studio 整合式開發環境 (IDE) 簡介中，您將建立並執行簡單的 Vue.js Web 應用程式。

> [!IMPORTANT]
> 此文章需要 Vue.js 範本，該範本是從 Visual Studio 2017 15.8 版開始提供。

## <a name="prerequisites"></a>必要條件

* 您必須安裝 Visual Studio 和 Node.js 開發工作負載。

    ::: moniker range=">=vs-2019"
    如果您尚未安裝 Visual Studio 2019，請前往  [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/) 頁面免費進行安裝。
    ::: moniker-end
    ::: moniker range="vs-2017"
    如果您尚未安裝 Visual Studio 2017，請前往  [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/) 頁面免費進行安裝。
    ::: moniker-end

    如果您需要安裝工作負載，但已安裝 Visual Studio，請移至 [工具] > [取得工具與功能...]，以開啟 Visual Studio 安裝程式。 選擇 [Node.js 開發] 工作負載，然後選擇 [修改]。

    ![VS 安裝程式中的 Node.js 工作負載](../ide/media/quickstart-nodejs-workload.png)

* 您必須安裝 Node.js 執行階段。

    如果您沒有安裝，請從 [Node.js](https://nodejs.org/en/download/) 網站安裝 LTS 版本。 一般而言，Visual Studio 會自動偵測已安裝的 Node.js 執行階段。 如果偵測不到已安裝的執行階段，您可以在屬性頁面中將專案設定為參考已安裝的執行階段 (建立專案之後，以滑鼠右鍵按一下專案節點，然後選擇 [屬性])。

## <a name="create-a-project"></a>建立專案

首先，您將建立 Vue.js Web 應用程式專案。

1. 如果您尚未安裝 Node.js 執行階段，請從 [Node.js](https://nodejs.org/en/download/) 網站安裝 LTS 版本。

    一般而言，Visual Studio 會自動偵測已安裝的 Node.js 執行階段。 如果偵測不到已安裝的執行階段，您可以在屬性頁面中將專案設定為參考已安裝的執行階段 (建立專案後，以滑鼠右鍵按一下專案節點，然後選擇 [屬性])。

1. 開啟 Visual Studio。

1. 從頂端功能表列中，選擇 [檔案] > [新增] > [專案]。

1. 建立新的專案。

    ::: moniker range=">=vs-2019"
    在 [建立新專案] 對話方塊中，於搜尋方塊中輸入 **javascript** 或 **typescript** 以篩選結果，然後依序選擇 [基本 Vue.js Web 應用程式] 和 [下一步]。 接著，選擇 [建立]。
    ::: moniker-end
    ::: moniker range="vs-2017"
    在 [新增專案] 對話方塊的左窗格中，展開 [JavaScript]，然後選擇 [Node.js]。 在中間窗格中，選擇 [基本 Vue.js Web 應用程式]，然後選擇 [確定]。
    ::: moniker-end
    如果您看不到 [基本 Vue.js Web 應用程式] 專案範本，則必須新增 **Node.js 開發**工作負載。 如需詳細指示，請參閱[必要條件](#prerequisites)。

    ![Vue.js 範本](../javascript/media/vuejs-template.png)

    Visual Studio 會建立新專案。 隨即在 [方案總管] 右窗格中開啟新專案。

1. 檢查 [輸出] 視窗 (下方窗格)，以取得安裝應用程式所需 npm 套件的進度。

1. 在 [方案總管] 中，開啟 **npm** 節點，並確定已安裝所有列出的 npm 套件。

    如果遺漏任何套件 (驚嘆號圖示)，您可以用滑鼠右鍵按一下 **npm** 節點，然後選擇 [安裝遺漏的 npm 套件]。

## <a name="explore-the-ide"></a>探索 IDE

1. 查看方案總管的右窗格。

     ![Vue.js 方案](../javascript/media/vuejs-solution.png)

   - 以粗體反白顯示的項目就是您的專案，並使用您在 [新增專案] 對話方塊中所指定的名稱。 在磁碟上，此專案是由專案資料夾中的 .*njsproj* 檔案所呈現。

   - 最上層是方案，預設其名稱會與專案相同。 方案 (以磁碟上的 .*sln* 檔案呈現) 是一或多個相關專案的容器。

   - **npm** 節點會顯示任何已安裝的 npm 套件。 您可以使用滑鼠右鍵按一下 npm 節點，以使用對話方塊來搜尋並安裝 npm 套件。

2. 如果您想要從命令提示字元安裝 npm 套件或執行 Node.js 命令，請以滑鼠右鍵按一下專案節點，然後選擇 [在這裡開啟命令提示字元]。

## <a name="add-a-vue-file-to-the-project"></a>將 .vue 檔案新增至專案

1. 在 [方案總管] 中，以滑鼠右鍵按一下任何資料夾 (例如 *src/components* 資料夾)，然後選擇 [新增] > [新增項目]。

1. 選取 [JavaScript Vue 單一檔案元件] 或 [TypeScript Vue 單一檔案元件]，然後按一下 [新增]。

    Visual Studio 隨即將新檔案新增至專案。

## <a name="build-the-project"></a>建置專案

1. (僅限 TypeScript 專案) 從 Visual Studio 中，選擇 [建置] > [清除方案]。

1. 接著，選擇 [建置] > [建置方案] 來建置專案。 請檢查 [輸出] 視窗查看建置結果，然後從 [顯示輸出來源] 清單選擇 [建置]。

    Vue.js 專案範本會設定建置後事件來使用 `build` npm 指令碼。 如果您想要修改此設定，請從 Windows 檔案總管中開啟專案檔 (*\<專案名稱\>.njsproj*)，並找出這行程式碼：

    ```xml
    <PostBuildEvent>npm run build</PostBuildEvent>
    ```

## <a name="run-the-application"></a>執行應用程式

1. 按 **Ctrl**+**F5** (或 [偵錯] > [啟動但不偵錯])，以執行應用程式。

   在主控台中，您會看到一則訊息：「正在啟動程式開發伺服器」。

   接著，應用程式會在瀏覽器中開啟。

   ![在瀏覽器中執行的 Vue.js 應用程式](../javascript/media/vuejs-running-app.png)

1. 關閉網頁瀏覽器。

恭喜您完成此快速入門！ 我們希望您更了解如何搭配使用 Visual Studio IDE 與 Vue.js。 如果您想要更深入地鑽研其功能，請繼續目錄的 [教學課程] 一節中的教學課程。

## <a name="next-steps"></a>後續步驟

- 逐步進行 [Node.js 和 Express 的教學課程](../nodejs/tutorial-nodejs.md)
- 逐步進行 [Node.js 和 React 的教學課程](/visualstudio/javascript/tutorial-nodejs-with-react-and-jsx)
- [將應用程式部署至 Linux App Service](../javascript/publish-nodejs-app-azure.md)