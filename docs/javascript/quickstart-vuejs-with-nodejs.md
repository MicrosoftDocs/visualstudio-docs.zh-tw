---
title: 快速入門:建立您的第一個 Vue.js 應用程式
description: 在本快速入門中，您會在 Visual Studio 中使用適用於 Visual Studio 的 Node.js 工具建立 Vue.js 應用程式
ms.custom: ''
ms.date: 10/31/2019
ms.topic: quickstart
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 882c3a148164ab88412a817abd72d0608fadf9b2
ms.sourcegitcommit: 5c804c42d24d35dcf2ba195aba9ce07031743f62
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81744986"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>快速入門：使用 Visual Studio 建立您的第一個 Vue.js 應用程式

在這個 5-10 分鐘的 Visual Studio 整合式開發環境 (IDE) 簡介中，您將建立並執行簡單的 Vue.js Web 應用程式。

> [!IMPORTANT]
> 本文需要 Vue.js 範本，該範本是從 Visual Studio 2017 15.8 版開始提供。

## <a name="prerequisites"></a>Prerequisites

* 您必須安裝 Visual Studio 和 Node.js 開發工作負載。

    ::: moniker range=">=vs-2019"
    如果您尚未安裝 Visual Studio 2019,請轉到 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/) 頁面免費安裝它。
    ::: moniker-end
    ::: moniker range="vs-2017"
    如果您尚未安裝 Visual Studio 2017,請轉到 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/) 頁面免費安裝它。
    ::: moniker-end

    如果您需要安裝工作負載,但已經擁有可視化工作室,請轉到 **「工具** > **獲取工具和功能...",** 這將打開可視化工作室安裝程式。 選擇 [Node.js 開發]**** 工作負載，然後選擇 [修改]****。

    ![VS 安裝程式中的 Node.js 工作負載](../ide/media/quickstart-nodejs-workload.png)

* 您必須安裝 Node.js 執行階段。

    如果您沒有安裝它,我們建議您從[Node.js](https://nodejs.org/en/download/)網站安裝 LTS 版本,以便與外部框架和庫進行最佳相容性。 Node.js 是為 32 位元和 64 位體系結構構建的。 Visual Studio 中的 Node.js 工具(包含在 Node.js 工作負荷中)支援這兩個版本。 只需要一個,Node.js 安裝程式一次只支援安裝一個。
    
    一般而言，Visual Studio 會自動偵測已安裝的 Node.js 執行階段。 如果未檢測到已安裝的運行時,則可以將專案配置為引用屬性頁中的已安裝運行時(在創建專案後,右鍵單擊專案節點,選擇**屬性**,並設置**Node.exe 路徑**)。 您可以使用 Node.js 的全域安裝,也可以在每個 Node.js 專案中指定本地解釋器的路徑。 

## <a name="create-a-project"></a>建立專案

首先，您將建立 Vue.js Web 應用程式專案。

1. 如果您尚未安裝 Node.js 執行階段，請從 [Node.js](https://nodejs.org/en/download/) 網站安裝 LTS 版本。

    有關詳細資訊,請參閱先決條件。

1. 開啟 Visual Studio。

1. 建立新專案。

    ::: moniker range=">=vs-2019"
    按 **Esc** 關閉開始視窗。 鍵入 **Ctrl + Q** 來開啟搜尋方塊，再鍵入**基本 Vue.js**，然後選擇 [基本 Vue.js Web 應用程式]**** (JavaScript 或 TypeScript)。 在出現的對話方塊中，鍵入名稱 **basic-vuejs**，然後選擇 [建立]****。

    ![Vue.js 範本](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    從頂部功能表欄中,選擇 **「檔** > **新專案** > **」。。** 在 [新增專案]**** 對話方塊的左窗格中，展開 **JavaScript** 或 **TypeScript**，然後選擇 **Node.js**。 在中間窗格中，選擇 [基本 Vue.js Web 應用程式]****，鍵入名稱 **basic-vuejs**，然後選擇 [確定]****。

    ![Vue.js 範本](../javascript/media/vuejs-template.png)
    ::: moniker-end
    如果您看不到 [基本 Vue.js Web 應用程式]**** 專案範本，則必須新增 **Node.js 開發**工作負載。 如需詳細指示，請參閱[必要條件](#prerequisites)。

    Visual Studio 會建立新專案。 隨即在 [方案總管] 右窗格中開啟新專案。

1. 檢查 [輸出] 視窗 (下方窗格)，以取得安裝應用程式所需 npm 套件的進度。

1. 在 [方案總管] 中，開啟 **npm** 節點，並確定已安裝所有列出的 npm 套件。

    如果遺漏任何套件 (驚嘆號圖示)，您可以用滑鼠右鍵按一下 **npm** 節點，然後選擇 [安裝遺漏的 npm 套件]****。

## <a name="explore-the-ide"></a>探索 IDE

1. 查看方案總管**** 的右窗格。

     ![Vue.js 方案](../javascript/media/vuejs-solution.png)

   - 以粗體反白顯示的項目就是您的專案，並使用您在 [新增專案]**** 對話方塊中所指定的名稱。 在磁碟上,此專案由表示。項目資料夾中的*njsproj*檔。

   - 最上層是方案，預設其名稱會與專案相同。 由表示的解決方案。磁碟上的*sln*檔案是一個或多個相關專案的容器。

   - **npm**節點顯示任何已安裝的 npm 包。 您可以使用滑鼠右鍵按一下 npm 節點，以使用對話方塊來搜尋並安裝 npm 套件。

2. 如果您想要從命令提示字元安裝 npm 套件或執行 Node.js 命令，請以滑鼠右鍵按一下專案節點，然後選擇 [在這裡開啟命令提示字元]****。

## <a name="add-a-vue-file-to-the-project"></a>將 .vue 檔案新增至專案

1. 在 [方案總管] 中，以滑鼠右鍵按一下任何資料夾 (例如 *src/components* 資料夾)，然後選擇 [新增]**** > [新增項目]****。

1. 選取 [JavaScript Vue 單一檔案元件]**** 或 [TypeScript Vue 單一檔案元件]****，然後按一下 [新增]****。

    Visual Studio 隨即將新檔案新增至專案。

## <a name="build-the-project"></a>建置專案

::: moniker range=">=vs-2019"
1. 接著，選擇 [建置]**[建置方案]** > **** 來建置專案。

1. 請檢查 [輸出]**** 視窗查看建置結果，然後從 [顯示輸出來源]**** 清單選擇 [建置]****。
::: moniker-end
::: moniker range="vs-2017"
1. (僅限 TypeScript 專案) 從 Visual Studio 中，選擇 [建置]**[清除方案]** > ****。

1. 接著，選擇 [建置]**[建置方案]** > **** 來建置專案。

1. 請檢查 [輸出]**** 視窗查看建置結果，然後從 [顯示輸出來源]**** 清單選擇 [建置]****。
::: moniker-end

JavaScript Vue.js 專案範本(TypeScript 範本的舊版本)`build`通過配置後期 生成事件來使用 npm 文稿。 如果要修改此設定,請從 Windows 資源管理員開啟專案檔 (*\<專案名稱\>.njsproj),* 然後找到這行碼:

```xml
<PostBuildEvent>npm run build</PostBuildEvent>
```

## <a name="run-the-application"></a>執行應用程式

1. 按**Ctrl**+**F5(** 或**除錯>無需除錯即可啟動**)以執行應用程式。

   在主控台中，您會看到一則訊息：「正在啟動程式開發伺服器」**。

   接著，應用程式會在瀏覽器中開啟。
   
   如果看不到正在運行的應用,請刷新頁面。

   ![在瀏覽器中執行的 Vue.js 應用程式](../javascript/media/vuejs-running-app.png)

1. 關閉網頁瀏覽器。

恭喜您完成此快速入門！ 我們希望您更了解如何搭配使用 Visual Studio IDE 與 Vue.js。 如果您想要更深入地鑽研其功能，請繼續目錄的 [教學課程]**** 一節中的教學課程。

## <a name="next-steps"></a>後續步驟

- 瀏覽[Vue.js](create-application-with-vuejs.md)的文章
- 逐步進行 [Node.js 和 Express 的教學課程](tutorial-nodejs.md)
- [將應用程式部署至 Linux App Service](../javascript/publish-nodejs-app-azure.md)