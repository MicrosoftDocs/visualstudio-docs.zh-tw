---
title: 使用 TypeScript 建立 ASP.NET Core 應用程式
description: 在本教學課程中，您會使用 ASP.NET Core 和 TypeScript 來建立應用程式
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
ms.openlocfilehash: ef287616f5b214566a273817c229d9105bf253c5
ms.sourcegitcommit: cd7f122c6850cf442a4ca42d51d05c7a8fe9038d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/12/2021
ms.locfileid: "98129480"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>教學課程：在 Visual Studio 中建立具有 TypeScript 的 ASP.NET Core 應用程式

在本教學課程中 Visual Studio 開發 ASP.NET Core 和 TypeScript，您會建立簡單的 web 應用程式、新增一些 TypeScript 程式碼，然後執行應用程式。

::: moniker range="vs-2017"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2019"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads)頁面免費進行安裝。

::: moniker-end

在本教學課程中，您會了解如何：
> [!div class="checklist"]
> * 建立 ASP.NET Core 專案
> * 新增 TypeScript 支援的 NuGet 套件
> * 新增一些 TypeScript 程式碼
> * 執行應用程式
> * 使用 npm 新增協力廠商程式庫

## <a name="prerequisites"></a>Prerequisites

* 您必須安裝 Visual Studio，以及 ASP.NET 網頁程式開發工作負載。

    ::: moniker range=">=vs-2019"
    如果您尚未安裝 Visual Studio 2019，請移至 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/) 頁面，免費進行安裝。
    ::: moniker-end
    ::: moniker range="vs-2017"
    如果您尚未安裝 Visual Studio 2017，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)頁面免費進行安裝。
    ::: moniker-end

    如果您需要安裝工作負載，但已有 Visual Studio，請移至 [**工具**  >  **取得工具和功能**]，這會開啟 Visual Studio 安裝程式。 選擇 [ASP.NET 與網頁程式開發] 工作負載，然後選擇 [修改]。

## <a name="create-a-new-aspnet-core-mvc-project"></a>建立新的 ASP.NET Core MVC 專案

Visual Studio 可在「專案」中管理單一應用程式的檔案。 專案包含原始程式碼、資源和組態檔。

>[!NOTE]
> 若要開始使用空白 ASP.NET Core 專案並新增 TypeScript 前端，請改為參閱 [與 typescript ASP.NET Core](https://www.typescriptlang.org/docs/handbook/asp-net-core.html) 。

在本教學課程中，您會從包含 ASP.NET Core MVC 應用程式程式碼的簡單專案開始。

1. 開啟 Visual Studio。

1. 建立新專案。

    ::: moniker range=">=vs-2019"
    如果 [開始] 視窗未開啟，請 **選擇 [** 檔案  >  **開始視窗]**。 在 [開始] 視窗中，選擇 [ **建立新專案**]。 在 [語言] 下拉式清單中，選擇 [ **c #**]。 在 [搜尋] 方塊中，輸入 **ASP.NET**，然後選擇 [ **ASP.NET Core Web 應用程式**]。 選擇 [下一步]。

    輸入專案的名稱，然後選擇 [ **建立**]。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從頂端功能表列中 **，選擇 [** 檔案  >  **新增**  >  **專案**]。 在 [ **新增專案** ] 對話方塊的左窗格中，展開 [ **Visual c #**]，然後選擇 [ **.net Core**]。 在中間窗格中，選擇 [ **ASP.NET Core Web 應用程式-c #**]，然後選擇 **[確定]**。
    ::: moniker-end
    如果您沒有看到 [ **ASP.NET Core Web 應用程式** ] 專案範本，則必須加入 **ASP.NET 和網頁程式開發** 工作負載。 如需詳細指示，請參閱[必要條件](#prerequisites)。

1. 在出現的對話方塊中，選取對話方塊中的 [ **Web 應用程式 (模型-視圖控制器)** ]，然後選擇 [ **建立** (**] 或 [確定]**) 。

   ![選擇 MVC 範本](../javascript/media/aspnet-core-ts-mvc-template.png)

    Visual Studio 會建立新的方案，並在右窗格中開啟專案。

## <a name="add-some-code"></a>新增一些程式碼

1. 在方案總管 (右窗格) 。 以滑鼠右鍵按一下專案節點，然後選擇 [ **管理 NuGet 套件**]。 在 [ **流覽** ] 索引標籤中，搜尋 [ **Microsoft**]，然後按一下右邊的 [ **安裝** ] 以安裝套件。

   ![新增 NuGet 套件](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio 會在方案總管的 [相依性 **]** 節點下新增 NuGet 套件。

1. 以滑鼠右鍵按一下專案節點，然後選擇 [ **加入 > 新專案**]。 選擇 **TYPESCRIPT JSON 設定檔**，然後按一下 [ **新增**]。

   Visual Studio 將檔案 *tsconfig.js* 加入至專案根目錄。 您可以使用這個檔案來 [設定](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) TypeScript 編譯器的選項。

1. 開啟 *tsconfig.js開啟* ，並將預設程式碼取代為下列程式碼：

   ```json
   {
     "compileOnSave": true,
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "wwwroot/js"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   *OutDir* 選項會指定 TypeScript 編譯器所轉換之一般 JavaScript 檔案的輸出檔案夾。

   此設定提供使用 TypeScript 的基本簡介。 在其他情況下（例如，使用 [gulp 或 webpack](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)），您可能會想要有不同的轉換 JavaScript 檔案中繼位置，視您的工具和設定喜好設定而定，而不是 *wwwroot/js*。

1. 在方案總管中，以滑鼠右鍵按一下專案節點，然後選擇 [ **加入 > 新資料夾**]。 使用新資料夾的名稱 *腳本* 。

1. 以滑鼠右鍵按一下 [ *腳本* ] 資料夾，然後選擇 [ **加入 > 新專案**]。 選擇 **TypeScript** 檔案，輸入名稱為 *app.config* 的檔案名，然後按一下 [ **新增**]。

   Visual Studio 將 *app.config* 新增至 *scripts* 資料夾。

1. 開啟 *app.config* ，並新增下列 TypeScript 程式碼。

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

    若要測試此功能，請從函式中移除 `.lastName` `greeter` ，然後重新輸入 "."，然後您會看到 IntelliSense。

    ![觀看 IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    選取 `lastName` 即可將姓氏新增回程序代碼。

1. 開啟 *Views/Home* 資料夾，然後開啟 *Index. cshtml*。

1. 將下列 HTML 程式碼新增至檔案結尾。

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. 開啟 [ *Views]/[共用* ] 資料夾，然後開啟 *_Layout*]。

1. 在呼叫之前，加入下列腳本參考 `@RenderSection("Scripts", required: false)` ：

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>建置應用程式

1. 選擇 [ **組建 > 組建方案**]。

   雖然應用程式會在您執行應用程式時自動建立，但我們想要查看在建立程式期間所發生的問題。

1. 開啟 *wwwroot/js* 資料夾，您會發現兩個新檔案， *app.js* 和來源對應檔， *app.js 對應*。 這些檔案是由 TypeScript 編譯器所產生。

   需要來源對應檔案才能進行偵錯工具。

## <a name="run-the-application"></a>執行應用程式

1. 按 **F5** ([偵錯] > [開始偵錯]) 以執行應用程式。

    應用程式會在瀏覽器中開啟。

    在瀏覽器視窗中，您會看到 [ **歡迎使用** ] 標題和 [ **按一下我** 的] 按鈕。

    ![使用 TypeScript ASP.NET Core](../javascript/media/aspnet-core-ts-running-app.png)

1. 按一下按鈕以顯示我們在 TypeScript 檔案中指定的訊息。

## <a name="debug-the-application"></a>偵錯應用程式

1. 在的函 `greeter` 式中設定中斷點 `app.ts` ，方法是在程式碼編輯器的左邊界中按一下。

    ![設定中斷點](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. 按 **F5** 執行應用程式。

   您可能需要回應訊息，才能啟用腳本的調試。

   應用程式會在中斷點暫停。 現在，您可以檢查變數並使用偵錯工具功能。

## <a name="add-typescript-support-for-a-third-party-library"></a>新增協力廠商程式庫的 TypeScript 支援

1. 依照 [npm 套件管理](../javascript/npm-package-management.md#aspnet-core-projects) 中的指示，將檔案新增 `package.json` 至您的專案。 這會將 npm 支援新增至您的專案。

   >[!NOTE]
   > 針對 ASP.NET Core 專案，您也可以使用連結 [庫管理員](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1&preserve-view=true) 或 yarn 而不是 npm 來安裝用戶端 JAVASCRIPT 和 CSS 檔案。

1. 在此範例中，將 jQuery 的 TypeScript 定義檔新增至您的專案。 在檔案的 *package.js* 中包含下列各項。

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   這會為 jQuery 新增 TypeScript 支援。 JQuery 程式庫本身已包含在 MVC 專案範本中 (在方案總管) 中的 wwwroot/lib 下查看。 如果您使用不同的範本，您可能也需要包含 jquery npm 封裝。

1. 如果未安裝方案總管中的封裝，請以滑鼠右鍵按一下 [npm] 節點，然後選擇 [ **還原套件**]。

   >[!NOTE]
   > 在某些案例中，方案總管可能表示 npm 套件因為 [此處](https://github.com/aspnet/Tooling/issues/479)所述的已知問題而與 *package.js* 不同步。 例如，封裝可能會在安裝時顯示為未安裝。 在大部分的情況下，您可以刪除 *package.js*、重新開機 Visual Studio，然後重新新增 *package.js* 檔案，以更新方案總管，如本文稍早所述。

1. 在方案總管中，以滑鼠右鍵按一下 [腳本] 資料夾，然後選擇 [**加入**  >  **新專案**]。

1. 選擇 [ **TypeScript** 檔案]，輸入 [連結 *庫*]，然後選擇 [ **新增**]。

1. 在 [連結 *庫*] 中，新增下列程式碼。

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

   為了簡單起見，此程式碼會使用 jQuery 和警示來顯示訊息。

   加入 jQuery 的 TypeScript 類型定義之後，當您在 jQuery 物件後面輸入 "." 時，就會取得 jQuery 物件的 IntelliSense 支援，如下所示。

   ![jquery IntelliSense](../javascript/media/aspnet-core-ts-jquery-intellisense.png)

1. 在 _Layout 的 cshtml 中，更新要包含的腳本參考 `library.js` 。

   ```html
   <script src="~/js/app.js"></script>
   <script src="~/js/library.js"></script>
   ```

1. 在 [索引] 中，將下列 HTML 加入至檔案結尾。

   ```html
   <div>
      <p id="ts-example-2">jQuery version is:</p>
   </div>
   ```

1. 按 **F5** ([偵錯] > [開始偵錯]) 以執行應用程式。

    應用程式會在瀏覽器中開啟。

    按一下警示中的 **[確定]** ，以查看更新為 **jQuery 版本的頁面是：3.3.1！！**。

    ![jquery 範例](../javascript/media/aspnet-core-ts-jquery-example.png)

## <a name="next-steps"></a>後續步驟

您可能會想要深入瞭解搭配 ASP.NET Core 使用 TypeScript 的詳細資料。

> [!div class="nextstepaction"]
> [ASP.NET Core 和 TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
