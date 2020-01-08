---
title: 使用 TypeScript 建立 ASP.NET Core 應用程式
description: 在本教學課程中，您會使用 ASP.NET Core 和 TypeScript 建立應用程式
ms.date: 01/03/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 8d733c41e2833eeca2a8bf8c68f5e329f0af723c
ms.sourcegitcommit: 0d8488329263cc0743a89d43f6de863028e982ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2020
ms.locfileid: "75685304"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>教學課程：在 Visual Studio 中使用 TypeScript 建立 ASP.NET Core 應用程式

在 Visual Studio 開發 ASP.NET Core 和 TypeScript 的本教學課程中，您會建立簡單的 web 應用程式、新增一些 TypeScript 程式碼，然後執行應用程式。 

::: moniker range="vs-2017"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2019"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads)頁面免費進行安裝。

::: moniker-end

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> * 建立 ASP.NET Core 專案
> * 新增 TypeScript 支援的 NuGet 套件
> * 新增一些 TypeScript 程式碼
> * 執行應用程式

## <a name="prerequisites"></a>必要條件：

* 您必須安裝 Visual Studio 和 ASP.NET 網頁程式開發工作負載。

    ::: moniker range=">=vs-2019"
    如果您尚未安裝 Visual Studio 2019，請前往  [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/) 頁面免費進行安裝。
    ::: moniker-end
    ::: moniker range="vs-2017"
    如果您尚未安裝 Visual Studio 2017，請前往  [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/) 頁面免費進行安裝。
    ::: moniker-end

    如果您需要安裝工作負載，但已安裝 Visual Studio，請移至 [工具] > [取得工具與功能...]，以開啟 Visual Studio 安裝程式。 選擇 [ASP.NET 與網頁程式開發] 工作負載，然後選擇 [修改]。

## <a name="create-a-new-aspnet-core-mvc-project"></a>建立新的 ASP.NET Core MVC 專案

Visual Studio 可在「專案」中管理單一應用程式的檔案。 專案包含原始程式碼、資源和組態檔。

在本教學課程中，您會從簡單的專案開始，其中包含 ASP.NET Core MVC 應用程式的程式碼。

1. 開啟 Visual Studio。

1. 建立新的專案。

    ::: moniker range=">=vs-2019"
    按 **Esc** 關閉開始視窗。 輸入**Ctrl + Q**開啟 [搜尋] 方塊，輸入**ASP.NET**，然後選擇 [ **ASP.NET Core Web 應用C#程式-** ]。 在出現的對話方塊中選擇 [建立]。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從頂端功能表列中，選擇 [檔案] >  [新增] >  [專案]。 在 [新增專案] 對話方塊的左窗格中，展開 **JavaScript**，然後選擇 **Node.js**。 在中間窗格中，選擇 [ **ASP.NET Core Web 應用C#程式-** ]，然後選擇 **[確定]** 。
    ::: moniker-end
    如果您看不到 [ **ASP.NET Core Web 應用程式**] 專案範本，則必須新增 [ **ASP.NET 和 網頁程式開發**] 工作負載。 如需詳細指示，請參閱[必要條件](#prerequisites)。

1. 選擇 [**建立**] 之後，請選取對話方塊中的 [ **Web 應用程式（模型-視圖控制器）** ]，然後選擇 [**建立**]。

   ![選擇 MVC 範本](../javascript/media/aspnet-core-ts-mvc-template.png)

    Visual Studio 會建立新的方案，並在右窗格中開啟專案。

## <a name="add-some-code"></a>新增一些程式碼

1. 在方案總管（右窗格）。 以滑鼠右鍵按一下專案節點，然後選擇 [**管理 NuGet 封裝**]。 在 [**流覽**] 索引標籤中，搜尋 [ **Microsoft TypeScript**]，然後按一下右側的 [**安裝**] 以安裝封裝。

   ![新增 NuGet 套件](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio 會在方案總管的 [相依性 **]** 節點底下新增 NuGet 套件。

   > [!NOTE]
   > 本教學課程需要 NuGet 套件。 或者，在您自己的應用程式中，您可能會想要使用[TypeScript npm 套件](https://www.npmjs.com/package/typescript)。

1. 在方案總管中，以滑鼠右鍵按一下專案節點，然後選擇 [**加入 > 新增資料夾**]。 使用新資料夾的名稱*腳本*。

1. 以滑鼠右鍵按一下 [*腳本*] 資料夾，然後選擇 [**加入 > 新專案**]。 選擇 [ **TYPESCRIPT JSON 設定檔**]，然後按一下 [**新增**]。

   Visual Studio 將*tsconfig*新增至 [*腳本*] 資料夾。 您可以使用這個檔案來[設定](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)TypeScript 編譯器的選項。

1. 開啟*tsconfig* ，並將預設程式碼取代為下列程式碼：

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "../wwwroot/js"
     },
     "exclude": [
       "node_modules",
       "wwwroot"
     ]
   }
   ```

   *OutDir*選項會指定 TypeScript 編譯器所轉換之計畫 JavaScript 檔案的輸出檔案夾。

   此設定提供使用 TypeScript 的基本簡介。 在其他情況下，例如，使用[gulp 或 webpack](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)時，您可能會想要轉換 JavaScript 檔案有不同的中繼位置，視您的工具和設定喜好設定而定，而不是 *。/wwwroot/js*。

1. 以滑鼠右鍵按一下 [*腳本*] 資料夾，然後選擇 [**加入 > 新專案**]。 選擇**TypeScript**檔案，輸入檔案名為的*應用程式*名稱，然後按一下 [**新增**]。

   Visual Studio 會將*app. ts*新增至 [*腳本*] 資料夾。

1. 開啟*app. ts*並新增下列 TypeScript 程式碼。

    ```ts
    function TSButton() {
       let name: string = "Fred";
       document.getElementById("ts-example").innerHTML = greeter(user);
    }

    class Student {
       fullName: string;
       constructor(public firstName: string, public middleInitial: string, public lastName: string) {
           this.fullName = firstName + " " + middleInitial + " " + lastName;
       }
    }

    interface Person {
       firstName: string;
       lastName: string;
    }

    function greeter(person: Person) {
       return "Hello, " + person.firstName + " " + person.lastName;
    }

    let user = new Student("Fred", "M.", "Smith");
    ```

    Visual Studio 為您的 TypeScript 程式碼提供 IntelliSense 支援。

    若要測試這種情況，請從 `greeter` 函式中移除 `.lastName`，然後重新輸入 "."，您就會看到 IntelliSense。

    ![View IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    選取 [`lastName`]，將姓氏加回程序代碼。

1. 開啟*Views/Home*資料夾，然後開啟*index. html*。

1. 將下列 HTML 程式碼新增至檔案結尾。

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. 開啟*Views/Shared*資料夾，然後開啟 *_Layout. cshtml*。

1. 在 `@RenderSection("Scripts", required: false)`的呼叫之前，新增下列腳本參考：

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>建置應用程式

1. 選擇 [**組建 > 組建方案**]。

   雖然應用程式會在您執行時自動建立，但我們想要查看在建立過程中發生的事情。

1. 開啟*wwwroot/js*資料夾，您會發現兩個新的檔案，即*app.config*和來源對應檔*node.js. map*。 這些檔案是由 TypeScript 編譯器所產生。

   需要來源對應檔案才能進行偵錯工具。

## <a name="run-the-application"></a>執行應用程式

1. 按 **F5** ([偵錯] > [開始偵錯]) 以執行應用程式。

    應用程式會在瀏覽器中開啟。

    在瀏覽器視窗中，您會看到 [**歡迎**] 標題和 [**按一下我**] 按鈕。

    ![使用 TypeScript 的 ASP.NET Core](../javascript/media/aspnet-core-ts-running-app.png)

1. 按一下此按鈕，以顯示我們在 TypeScript 檔案中指定的訊息。

## <a name="debug-the-application"></a>進行應用程式偵錯

1. 在 [程式碼編輯器] 的左邊界中按一下，在 `app.ts` 的 `greeter` 函數中設定中斷點。

    ![設定中斷點](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. 按 **F5** 執行應用程式。

   您可能需要回應訊息以啟用腳本的調試。

   應用程式會在中斷點暫停。 現在，您可以檢查變數，並使用偵錯工具功能。

## <a name="next-steps"></a>後續步驟

您可能想要深入瞭解搭配 ASP.NET Core 使用 TypeScript 的詳細資訊。

> [!div class="nextstepaction"]
> [ASP.NET Core 和 TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
