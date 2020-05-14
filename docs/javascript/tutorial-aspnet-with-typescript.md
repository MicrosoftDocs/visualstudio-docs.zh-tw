---
title: 使用 TypeScript 建立 ASP.NET Core 應用程式
description: 在本教程中，您將使用ASP.NET核心和 TypeScript 創建應用
ms.date: 03/16/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: e212aec6d2d3aa7e20cb0ca08c9ea604f32bb08c
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "79988554"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>教程：在視覺化工作室中使用 TypeScript 創建ASP.NET核心應用

在 Visual Studio 開發ASP.NET核心和 TypeScript 教程中，您將創建一個簡單的 Web 應用程式，添加一些 TypeScript 代碼，然後運行該應用程式。 

::: moniker range="vs-2017"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2019"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads)頁面免費進行安裝。

::: moniker-end

在本教學課程中，您會了解如何：
> [!div class="checklist"]
> * 創建ASP.NET核心專案
> * 添加 NuGet 包以進行 TypeScript 支援
> * 添加一些 TypeScript 代碼
> * 執行應用程式
> * 使用 npm 添加協力廠商庫

## <a name="prerequisites"></a>必要條件

* 您必須安裝 Visual Studio 並ASP.NET Web 開發工作負載。

    ::: moniker range=">=vs-2019"
    如果您尚未安裝 Visual Studio 2019，請轉到 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/) 頁面免費安裝它。
    ::: moniker-end
    ::: moniker range="vs-2017"
    如果您尚未安裝 Visual Studio 2017，請轉到 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/) 頁面免費安裝它。
    ::: moniker-end

    如果您需要安裝工作負載，但已經擁有視覺化工作室，請轉到 **"工具** > **獲取工具和功能..."，** 這將打開視覺化工作室安裝程式。 選擇 [ASP.NET 與網頁程式開發]**** 工作負載，然後選擇 [修改]****。

## <a name="create-a-new-aspnet-core-mvc-project"></a>創建新ASP.NET核心 MVC 專案

Visual Studio 可在「專案」** 中管理單一應用程式的檔案。 專案包含原始程式碼、資源和組態檔。

>[!NOTE]
> 要從空ASP.NET核心專案開始並添加 TypeScript 前端，請參閱[使用 TypeScript ASP.NET核心](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)。

在本教程中，您首先介紹了一個簡單的專案，其中包含ASP.NET酷睿 MVC 應用的代碼。

1. 開啟 Visual Studio。

1. 建立新專案。

    ::: moniker range=">=vs-2019"
    如果啟動視窗未打開，請選擇 **"檔** > **開始視窗**"。 在啟動視窗中，選擇 **"創建新專案**"。 在語言下拉清單中，選擇**C#**。 在搜索框中，鍵入**ASP.NET**，然後選擇**ASP.NET核心 Web 應用程式**。 選擇 [下一步]****。

    鍵入專案的名稱，然後選擇 **"創建**"。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從頂部功能表列中，選擇 **"檔** > **新專案** > **"。** 在 **"新專案**"對話方塊的左側窗格中，展開**Visual C#，** 然後選擇 **.NET Core**。 在中間窗格中，選擇**ASP.NET核心 Web 應用程式 - C#，** 然後選擇 **"確定**"。
    ::: moniker-end
    如果未看到**ASP.NET核心 Web 應用程式**專案範本，則必須添加**ASP.NET和 Web 開發**工作負荷。 如需詳細指示，請參閱[必要條件](#prerequisites)。

1. 在顯示的對話方塊中，在對話方塊中選擇**Web 應用程式（模型-視圖-控制器），** 然後選擇 **"創建**"（或 **"確定**"）。

   ![選擇 MVC 範本](../javascript/media/aspnet-core-ts-mvc-template.png)

    Visual Studio 會建立新的方案，並在右窗格中開啟專案。

## <a name="add-some-code"></a>新增一些程式碼

1. 在解決方案資源管理器（右窗格中）。 按右鍵專案節點並選擇 **"管理 NuGet 包**"。 在 **"流覽"** 選項卡中，搜索**Microsoft.TypeScript.MSBuild**，然後按一下"**右側安裝**"以安裝包。

   ![添加 NuGet 包](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio 在解決方案資源管理器中的**依賴項**節點下添加 NuGet 包。

   > [!NOTE]
   > 本教程需要 NuGet 包。 或者，在您自己的應用中，您可能需要使用[TypeScript npm 包](https://www.npmjs.com/package/typescript)。

1. 在"解決方案資源管理器"中，按右鍵專案節點並選擇"**添加>新資料夾**。 使用新資料夾的名稱*腳本*。

1. 按右鍵*腳本*資料夾並選擇"**添加>新專案**"。 選擇**TypeScript JSON 設定檔**，然後按一下"**添加**"。

   Visual Studio 將*tsconfig.json*檔添加到*腳本*資料夾中。 您可以使用此檔為 TypeScript 編譯器[配置選項](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)。

1. 打開*tsconfig.json*並將預設代碼替換為以下代碼：

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

   *outDir*選項指定由 TypeScript 編譯器轉置的計畫 JavaScript 檔的輸出檔案夾。

   此配置提供了使用 TypeScript 的基本介紹。 在其他方案中，例如使用[gulp 或 Webpack](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)時，您可能需要針對轉裝的 JavaScript 檔使用不同的中間位置，具體取決於您的工具和配置首選項，而不是 *。/wwwroot/js*.

1. 按右鍵*腳本*資料夾並選擇"**添加>新專案**"。 選擇**TypeScript 檔**，鍵入檔案名的名稱*應用.ts，* 然後按一下"**添加**"。

   視覺化工作室將*app.ts*添加到*腳本*資料夾。

1. 打開*應用.ts*並添加以下 TypeScript 代碼。

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

    Visual Studio 為您的 TypeScript 代碼提供 IntelliSense 支援。

    要測試此情況，`.lastName`請從`greeter`函數中刪除，然後重新鍵入"."，然後您將看到 IntelliSense。

    ![查看感知](../javascript/media/aspnet-core-ts-intellisense.png)

    選擇`lastName`該選擇可將姓氏添加回代碼。

1. 打開*視圖/主頁*資料夾，然後打開*索引.html*。

1. 將以下 HTML 代碼添加到檔的末尾。

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. 打開*視圖/共用*資料夾，然後打開 *_Layout.cshtml*。

1. 在調用 之前添加以下腳本引用到`@RenderSection("Scripts", required: false)`：

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>建置應用程式

1. 選擇**生成>生成解決方案**。

   儘管應用在運行時會自動生成，但我們希望查看生成過程中發生的情況。

1. 打開*wwwroot /js*資料夾，你會發現兩個新的檔 *，app.js*和源地圖檔 *，app.js.map*。 這些檔由 TypeScript 編譯器生成。

   調試需要源映射檔。

## <a name="run-the-application"></a>執行應用程式

1. 按 **F5** ([偵錯]**** > [開始偵錯]****) 以執行應用程式。

    應用程式會在瀏覽器中開啟。

    在瀏覽器視窗中，您將看到 **"歡迎"** 標題和 **"按一下我"** 按鈕。

    ![帶類型腳本的ASP.NET核心](../javascript/media/aspnet-core-ts-running-app.png)

1. 按一下該按鈕以顯示我們在 TypeScript 檔中指定的消息。

## <a name="debug-the-application"></a>偵錯應用程式

1. 通過按一下代碼編輯器中的左邊`greeter`距來`app.ts`設置 函數中的中斷點。

    ![設定中斷點](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. 按**F5**以運行應用程式。

   您可能需要回應訊息以啟用腳本調試。

   應用程式在中斷點處暫停。 現在，您可以檢查變數並使用調試器功能。

## <a name="add-typescript-support-for-a-third-party-library"></a>為協力廠商庫添加 TypeScript 支援

1. 按照[npm 包管理](../javascript/npm-package-management.md#aspnet-core-projects)中的說明將`package.json`檔添加到專案中。 這將為專案添加 npm 支援。

   >[!NOTE]
   > 對於ASP.NET核心專案，您還可以使用[庫管理器](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1)或紗線，而不是 npm 來安裝用戶端 JavaScript 和 CSS 檔。

1. 在此示例中，將 jQuery 的 TypeScript 定義檔添加到專案中。 在*包.json*檔中包括以下內容。

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   這為 jQuery 添加了 TypeScript 支援。 jQuery 庫本身已包含在 MVC 專案範本中（在解決方案資源管理器中的 wwwroot/lib 下查看）。 如果您使用的是其他範本，則可能需要包括 jquery npm 包。

1. 如果未安裝解決方案資源管理器中的包，請按右鍵 npm-節點並選擇 **"還原包**"。

   >[!NOTE]
   > 在某些情況下，解決方案資源管理器可能指示 npm 包與*包.json*不同步，因為[此處](https://github.com/aspnet/Tooling/issues/479)描述了一個已知問題。 例如，安裝包時，該程式可能顯示為未安裝。 在大多數情況下，您可以通過刪除*包.json、* 重新開機 Visual Studio 以及重新添加*包.json*檔來更新解決方案資源管理器，如本文前面所述。

1. 在解決方案資源管理器中，按右鍵腳本資料夾並選擇**Add** > "**添加新專案**"。

1. 選擇**TypeScript 檔**，鍵入*庫.ts，* 然後選擇 **"添加**"。

1. 在*庫.ts*中，添加以下代碼。

   ```ts
   var jqtest = {
      showMsg: function (): void {
         let v: any = jQuery.fn.jquery.toString();
         let content: any = $("#ts-example-2")[0].innerHTML;
         alert(content.toString());
         $("#ts-example-2")[0].innerHTML = content + " " + v + "!!";
      }
   };

   jqtest.showMsg();
   ```

   為簡單起見，此代碼顯示使用 jQuery 和警報的消息。

   添加了 jQuery 的 TypeScript 類型定義後，當您在 jQuery 物件之後鍵入"."時，您將獲得 IntelliSense 支援，如下所示。

   ![jquery IntelliSense](../javascript/media/aspnet-core-ts-jquery-intellisense.png)

1. 在 _Layout.cshtml 中，更新腳本引用`library.js`以包括 。

   ```html
   <script src="~/js/app.js"></script>
   <script src="~/js/library.js"></script>
   ```

1. 在 Index.cshtml 中，將以下 HTML 添加到檔的末尾。

   ```html
   <div>
      <p id="ts-example-2">jQuery version is:</p>
   </div>
   ```

1. 按 **F5** ([偵錯]**** > [開始偵錯]****) 以執行應用程式。

    應用程式將在瀏覽器中打開。

    按一下"**確定**"在警報中查看更新至**jQuery 版本的頁面：3.3.1！！**

    ![jquery 示例](../javascript/media/aspnet-core-ts-jquery-example.png)

## <a name="next-steps"></a>後續步驟

您可能需要瞭解有關將 TypeScript 與 ASP.NET 核心一起使用的詳細資訊。

> [!div class="nextstepaction"]
> [ASP.NET核心和類型腳本](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
