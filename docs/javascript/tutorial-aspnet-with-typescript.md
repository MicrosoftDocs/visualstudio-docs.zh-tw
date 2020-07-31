---
title: 使用 TypeScript 建立 ASP.NET Core 應用程式
description: 在本教學課程中，您會使用 ASP.NET Core 和 TypeScript 建立應用程式
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
ms.openlocfilehash: e8a12c16c4c53ab2d0850bf5b768488160fa729a
ms.sourcegitcommit: b8ec700fc4c14c68c6ce280f29c19870261990d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2020
ms.locfileid: "87453700"
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
> * 使用 npm 新增協力廠商程式庫

## <a name="prerequisites"></a>先決條件

* 您必須安裝 Visual Studio 和 ASP.NET 網頁程式開發工作負載。

    ::: moniker range=">=vs-2019"
    如果您尚未安裝 Visual Studio 2019，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)]   頁面免費進行安裝。
    ::: moniker-end
    ::: moniker range="vs-2017"
    如果您尚未安裝 Visual Studio 2017，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/)]   頁面免費進行安裝。
    ::: moniker-end

    如果您需要安裝工作負載，但已經有 Visual Studio，請移至 [**工具**]  >  [**取得工具和功能 ...**]，這會開啟 Visual Studio 安裝程式。 選擇 [ASP.NET 與網頁程式開發]**** 工作負載，然後選擇 [修改]****。

## <a name="create-a-new-aspnet-core-mvc-project"></a>建立新的 ASP.NET Core MVC 專案

Visual Studio 可在「專案」** 中管理單一應用程式的檔案。 專案包含原始程式碼、資源和組態檔。

>[!NOTE]
> 若要開始使用空的 ASP.NET Core 專案並新增 TypeScript 前端，請改為參閱[使用 typescript ASP.NET Core](https://www.typescriptlang.org/docs/handbook/asp-net-core.html) 。

在本教學課程中，您會從簡單的專案開始，其中包含 ASP.NET Core MVC 應用程式的程式碼。

1. 開啟 Visual Studio。

1. 建立新專案。

    ::: moniker range=">=vs-2019"
    如果 [開始] 視窗未開啟，請**選擇 [** 檔案  >  **] [啟動視窗]**。 在 [開始] 視窗中，選擇 [**建立新專案**]。 在 [語言] 下拉式清單中，選擇 [ **c #**]。 在搜尋方塊中，輸入**ASP.NET**，然後選擇 [ **ASP.NET Core Web 應用程式**]。 選擇 [下一步]。

    輸入專案的名稱，然後選擇 [**建立**]。
    ::: moniker-end
    ::: moniker range="vs-2017"
    從頂端功能表列中 **，選擇 [** 檔案] [新增] [  >  **New**  >  **專案**]。 在 [**新增專案**] 對話方塊的左窗格中，展開 [ **Visual c #**]，然後選擇 [ **.net Core**]。 在中間窗格中，選擇 [ **ASP.NET Core Web 應用程式-c #**]，然後選擇 **[確定]**。
    ::: moniker-end
    如果您看不到 [ **ASP.NET Core Web 應用程式**] 專案範本，則必須新增 [ **ASP.NET 和 網頁程式開發**] 工作負載。 如需詳細指示，請參閱[必要條件](#prerequisites)。

1. 在出現的對話方塊中，選取對話方塊中的 [ **Web 應用程式（模型-視圖控制器）** ]，然後選擇 [**建立**] （或 **[確定]**）。

   ![選擇 MVC 範本](../javascript/media/aspnet-core-ts-mvc-template.png)

    Visual Studio 會建立新的方案，並在右窗格中開啟專案。

## <a name="add-some-code"></a>新增一些程式碼

1. 在方案總管（右窗格）。 以滑鼠右鍵按一下專案節點，然後選擇 [**管理 NuGet 封裝**]。 在 [**流覽**] 索引標籤中，搜尋 [ **Microsoft TypeScript**]，然後按一下右側的 [**安裝**] 以安裝封裝。

   ![新增 NuGet 套件](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio 會在方案總管的 [相依性 **]** 節點底下新增 NuGet 套件。

1. 以滑鼠右鍵按一下專案節點，然後選擇 [**加入 > 新專案**]。 選擇 [ **TYPESCRIPT JSON 設定檔**]，然後按一下 [**新增**]。

   Visual Studio 會將檔案*tsconfig.js*新增至專案根目錄。 您可以使用這個檔案來[設定](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)TypeScript 編譯器的選項。

1. 開啟*tsconfig.js* ，並將預設程式碼取代為下列程式碼：

   ```json
   {
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

   *OutDir*選項會指定 TypeScript 編譯器所轉換之一般 JavaScript 檔案的輸出檔案夾。

   此設定提供使用 TypeScript 的基本簡介。 在其他案例中，例如，使用[gulp 或 webpack](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)時，您可能會想要轉換 JavaScript 檔案有不同的中繼位置，視您的工具和設定喜好設定而定，而不是*wwwroot/js*。

1. 在方案總管中，以滑鼠右鍵按一下專案節點，然後選擇 [**加入 > 新增資料夾**]。 使用新資料夾的名稱*腳本*。

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

    若要測試這種情況，請從函式中移除 `.lastName` `greeter` ，然後重新輸入 "."，您就會看到 IntelliSense。

    ![View IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    選取 `lastName` 即可將姓氏加回程序代碼。

1. 開啟*Views/Home*資料夾，然後開啟*Index. cshtml*。

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

1. 在呼叫之前，新增下列腳本參考 `@RenderSection("Scripts", required: false)` ：

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>建置應用程式

1. 選擇 [**組建 > 組建方案**]。

   雖然應用程式會在您執行時自動建立，但我們想要查看在建立過程中發生的事情。

1. 開啟*wwwroot/js*資料夾，您會發現兩個新的檔案， *app.js*和來源對應檔， *app.js. map*。 這些檔案是由 TypeScript 編譯器所產生。

   需要來源對應檔案才能進行偵錯工具。

## <a name="run-the-application"></a>執行應用程式

1. 按 **F5** ([偵錯]**** > [開始偵錯]****) 以執行應用程式。

    應用程式會在瀏覽器中開啟。

    在瀏覽器視窗中，您會看到 [**歡迎**] 標題和 [**按一下我**] 按鈕。

    ![使用 TypeScript 的 ASP.NET Core](../javascript/media/aspnet-core-ts-running-app.png)

1. 按一下此按鈕，以顯示我們在 TypeScript 檔案中指定的訊息。

## <a name="debug-the-application"></a>偵錯應用程式

1. `greeter` `app.ts` 按一下程式碼編輯器中的左邊界，在的函式中設定中斷點。

    ![設定中斷點](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. 按**F5**執行應用程式。

   您可能需要回應訊息以啟用腳本的調試。

   應用程式會在中斷點暫停。 現在，您可以檢查變數，並使用偵錯工具功能。

## <a name="add-typescript-support-for-a-third-party-library"></a>新增協力廠商程式庫的 TypeScript 支援

1. 依照[npm 套件管理](../javascript/npm-package-management.md#aspnet-core-projects)中的指示，將檔案新增 `package.json` 至您的專案。 這會將 npm 支援新增至您的專案。

   >[!NOTE]
   > 針對 ASP.NET Core 專案，您也可以使用連結[庫管理員](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1)或 yarn，而不是 npm 來安裝用戶端 JAVASCRIPT 和 CSS 檔案。

1. 在此範例中，將 jQuery 的 TypeScript 定義檔新增至您的專案。 在檔案的*package.js*中包含下列資訊。

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   這會新增 jQuery 的 TypeScript 支援。 JQuery 程式庫本身已包含在 MVC 專案範本中（請查看方案總管中的 wwwroot/lib 底下）。 如果您使用不同的範本，您可能也需要包含 jquery npm 套件。

1. 如果未安裝方案總管中的封裝，請以滑鼠右鍵按一下 [npm] 節點，然後選擇 [**還原套件**]。

   >[!NOTE]
   > 在某些情況下，方案總管可能表示由於[這裡](https://github.com/aspnet/Tooling/issues/479)所述的已知問題，npm 封裝與*package.js*不同步。 例如，套件在安裝時可能會顯示為 [未安裝]。 在大部分情況下，您可以藉由刪除*package.json*、重新開機 Visual Studio，然後在檔案上重新加入*package.js* （如本文稍早所述）來更新方案總管。

1. 在方案總管中，以滑鼠右鍵按一下 [腳本] 資料夾，然後選擇 [**加入**  >  **新專案**]。

1. 選擇 [ **TypeScript**檔案]，輸入*library. ts*，然後選擇 [**新增**]。

1. 在 [連結*庫. ts*] 中，新增下列程式碼。

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

   新增 jQuery 的 TypeScript 類型定義之後，當您在 jQuery 物件後面輸入 "." 時，就會取得 jQuery 物件的 IntelliSense 支援，如下所示。

   ![jquery IntelliSense](../javascript/media/aspnet-core-ts-jquery-intellisense.png)

1. 在 _Layout. cshtml 中，更新要包含的腳本參考 `library.js` 。

   ```html
   <script src="~/js/app.js"></script>
   <script src="~/js/library.js"></script>
   ```

1. 在 [Index. cshtml] 中，將下列 HTML 新增至檔案結尾。

   ```html
   <div>
      <p id="ts-example-2">jQuery version is:</p>
   </div>
   ```

1. 按 **F5** ([偵錯]**** > [開始偵錯]****) 以執行應用程式。

    應用程式會在瀏覽器中開啟。

    按一下警示中的 **[確定]** ，以查看更新為**jQuery 版本的頁面是：3.3.1！！**。

    ![jquery 範例](../javascript/media/aspnet-core-ts-jquery-example.png)

## <a name="next-steps"></a>後續步驟

您可能想要深入瞭解搭配 ASP.NET Core 使用 TypeScript 的詳細資訊。

> [!div class="nextstepaction"]
> [ASP.NET Core 和 TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
