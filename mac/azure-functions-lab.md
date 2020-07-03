---
title: 教學課程：Azure Functions
description: 在 Visual Studio for Mac 中使用 Azure Functions。
author: sayedihashimi
ms.author: sayedha
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 38FD2070-5151-482E-B0A9-993715128736
ms.topic: tutorial
ms.openlocfilehash: 99373d7da8c7f83c8703b237ff83c63f9d1b6a53
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "85939088"
---
# <a name="tutorial-getting-started-with-azure-functions"></a>教學課程：開始使用 Azure Functions

在此實驗室中，您將了解如何開始使用 Visual Studio for Mac 建置 Azure 函式。 您也將與代表 Azure Functions 開發人員可用之多種繫結和觸發程序的其中一種 Azure 儲存體資料表進行整合。

## <a name="objectives"></a>目標

> [!div class="checklist"]
> * 建立及偵錯區域 Azure 函式
> * 與 Web 和 Azure 儲存體資源進行整合
> * 協調涉及多個 Azure 函式的工作流程

## <a name="requirements"></a>規格需求

- Visual Studio for Mac 7.5 或更高版本。
- Azure 訂用帳戶（免費提供 [https://azure.com/free](https://azure.com/free?ref=visualstudio) ）。

## <a name="exercise-1-creating-an-azure-functions-project"></a>練習 1：建立 Azure Functions 專案

1. 啟動**Visual Studio for Mac**。

2. 選取 [檔案] > [新增方案]****。

3. 從 [雲端] > [一般]**** 類別，選取 [Azure Functions]**** 範本。 您將使用 C# 建立 .NET 類別庫來裝載 Azure 函式。 按 [下一步] 。

    ![選取 [Azure Functions] 範本](media/azure-functions-lab-image1.png)

4. 將 [專案名稱]**** 設定為 **"AzureFunctionsLab"**，然後按一下 [建立]****。

    ![命名及建立您的 Azure Functions 專案](media/azure-functions-lab-image2.png)

5. 展開 **Solution Pad** 中的節點。 預設專案範本包含各種 Azure WebJobs 套件及 Newtonsoft.json 套件的 NuGet 參考。

     另外還有三個檔案： - **host.json** 用於描述主機的全域組態選項 - **local.settings.json** 用於進行服務設定。
        - 專案範本也會建立預設 HttpTrigger。 為了此實驗室，您應該從專案刪除 **HttpTrigger.cs** 檔案。

    開啟 **local.settings.json**。 預設會有兩個空的連接字串設定。

    ![Solution Pad 顯示 local.settings.json 檔案](media/azure-functions-lab-image3.png)

## <a name="exercise-2-creating-an-azure-storage-account"></a>練習 2：建立 Azure 儲存體帳戶

1. 在登入您的 Azure 帳戶 [https://portal.azure.com](https://portal.azure.com) 。

1. 在畫面左側的 [我的最愛]**** 區段下，選取 [儲存體帳戶]****：

    ![Azure 入口網站的 [我的最愛] 區段顯示 [儲存體帳戶] 項目](media/azure-functions-lab-image4.png)

1. 選取 [新增]**** 建立新的儲存體帳戶：

    ![新增儲存體帳戶的按鈕](media/azure-functions-lab-image5.png)

1. 在 [名稱]**** 中輸入全域唯一名稱，並在 [資源群組]**** 中重複使用。 您可以保留所有其他項目的預設值。

    ![新儲存體帳戶的詳細資料](media/azure-functions-lab-image6.png)

1. 按一下 [建立]。 建立儲存體帳戶可能需要幾分鐘的時間。 成功建立之後，您會收到通知。

    ![部署成功通知](media/azure-functions-lab-image7.png)

1. 從 [通知] 選取 [前往資源]**** 按鈕。

1. 選取 [存取金鑰]**** 索引標籤。

    ![存取金鑰設定](media/azure-functions-lab-image8.png)

1. 複製第一個**連接字串**。 此字串稍後將用來整合 Azure 儲存體與 Azure Functions。

    ![金鑰 1 的資訊](media/azure-functions-lab-image9.png)

1. 返回 **Visual Studio for Mac**，並貼入完整連接字串作為 **local.settings.json** 中的 **AzureWebJobsStorage** 設定。 現在您可以參考屬性中的設定名稱，來取得需要存取其資源的函式。

    ![輸入連接金鑰的本機設定檔案](media/azure-functions-lab-image10.png)

## <a name="example-3-creating-and-debugging-an-azure-function"></a>範例 3：建立及偵錯 Azure 函式

1. 您現在已準備好開始新增一些程式碼。 使用 .NET 類別庫時，Azure 函式會新增為靜態方法。 從 **Solution Pad**，以滑鼠右鍵按一下 [AzureFunctions]**** 專案節點，然後選取 [新增] > [新增函式]****：

    ![[新增函式] 選項](media/azure-functions-lab-image11.png)

1. 在 [新增 Azure 函式] 對話方塊中，選取 [Generic WebHook] \(一般 WebHook\) 範本。 將 [名稱]**** 設定為 **Add**，然後按一下 [確定]**** 建立您的函式：

    ![[新增 Azure 函式] 對話方塊](media/azure-functions-lab-image12.png)

1. 在新檔案頂端，新增下列 **using** 指示詞：

    ```csharp
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using System.Web;
    using Microsoft.WindowsAzure.Storage.Table;
    ```

1. 移除現有的 `Run` 方法，然後將下列方法新增至類別作為您的 Azure 函式：

    ```csharp
    [FunctionName("Add")]
    public static int Run(
    [HttpTrigger(AuthorizationLevel.Function, "get", Route = null)]
    HttpRequestMessage req,
    TraceWriter log)
    {
        int x = 1;
        int y = 2;

        return x + y;
    }
    ```

1. 讓我們逐步解說此方法定義。

    您首先會看到 **FunctionName** 屬性將此方法標示為 Azure 函式。 該屬性會指定函式的公用名稱。 屬性名稱不一定要與實際方法名稱相符。

    ![醒目提示 FunctionName 屬性的新 Run 方法](media/azure-functions-lab-image13.png)

1. 接下來，將此方法標示為 **public static** 方法，此為必要。 您也會注意到傳回值為**int**。除非另有使用方法屬性來指定，否則 Azure 函式的任何非 void 傳回值都會以文字形式傳給用戶端。 根據預設，它會以 **XML** 傳回，但可變更為 **JSON** (您將在稍後的實驗室中執行)。

    ![醒目提示初始設定方法的新 Run 方法](media/azure-functions-lab-image14.png)

1. 第一個參數以 **HttpTrigger** 屬性標示，表示此方法是由 HTTP 要求叫用。 該屬性也會指定方法的授權層級，以及其支援的動詞命令 (在本例中只支援 **"GET"**)。 您也可以選擇性地定義 **Route** 來覆寫方法的路徑，並提供方法來自動從路徑擷取變數。 由於 **Route** 在這裡為 Null，因此這個方法的路徑將預設為 **/api/Add**。

    ![醒目提示參數的新 Run 方法](media/azure-functions-lab-image15.png)

1. 此方法的最後一個參數是 **TraceWriter** ，可用來記錄診斷和錯誤訊息。

    ![醒目提示 TraceWriter 的新 Run 方法](media/azure-functions-lab-image16.png)

1. 按一下方法的 **return** 行邊界，在該行設定中斷點：

    ![在換行中設定中斷點](media/azure-functions-lab-image17.png)

1. 按 **F5** 鍵或選取 [執行] > [開始偵錯]****，在偵錯工作階段中建置並執行專案。 您也可以按一下 [執行]**** 按鈕。 這些選項都會執行相同的工作。 此實驗室的其餘部分參考 **F5**，但您可以使用最慣用的方法。

    ![建置並執行專案](media/azure-functions-lab-image18.png)

1. 執行專案會自動開啟終端機應用程式。

1. 該專案會根據方法屬性及本文稍後將涵蓋的檔案慣例，來偵測 Azure 函式。 在本例中，它會偵測單一 Azure 函式，並「產生」一個作業函式。

    ![終端機中的 Azure 函式輸出](media/azure-functions-lab-image19.png)

1. 在啟動訊息底部，Azure Functions 主機會列印任何 HTTP 觸發程序 API 的 URL。 應該只有一個。 複製該 URL，並將它貼到新的瀏覽器索引標籤中。

    ![Azure 函式 API URL](media/azure-functions-lab-image20.png)

1. 此中斷點應該會立即觸發。 Web 要求已路由傳送至函式，現在可進行偵錯。 將滑鼠移至 **x** 變數上方以查看其值。

    ![中斷點已觸發](media/azure-functions-lab-image21.png)

1. 使用稍早用來新增中斷點的相同方法來移除中斷點 (按一下邊界或選取該行，然後按 **F9** 鍵)。

1. 按**F5**繼續執行。

1. 在瀏覽器中，會呈現方法的 XML 結果。 如預期般，硬式編碼的加法運算會產生可能的總和。 請注意，如果您在 Safari 中只看到 "3"，請移至 [Safari] > [Preferences] \(喜好設定\) > [Advanced] \(進階\)****，然後勾選 [Show Develop menu in menu bar] \(在功能表列中顯示開發功能表\)**** 核取方塊並重新載入頁面。

1. 在 [Visual Studio for Mac]**** 中，按一下 [停止]**** 按鈕以結束偵錯工作階段。 為了確保套用新的變更，別忘了重新啟動 (停止後再執行) 偵錯工作階段。

    ![停止偵錯選項](media/azure-functions-lab-image22.png)

1. 在 **Run** 方法中，以下列程式碼取代 **x** 和 **y** 定義。 此程式碼會從 URL 的查詢字串擷取值，以便能夠動態地根據所提供的參數執行加法運算。

    ```csharp
    var query = HttpUtility.ParseQueryString(req.RequestUri.Query);

    int x = int.Parse(query["x"]);

    int y = int.Parse(query["y"]);

    return x + y;
    ```

1. 執行應用程式。

1. 返回瀏覽器視窗，然後將字串 `/?x=2&y=3` 附加至 URL。 整個 URL 現在應該是 `http://localhost:7071/api/Add?x=2&y=3`。 巡覽至新的 URL。

1. 此時，結果應該會反映新的參數。 您可以隨時使用不同的值來執行專案。 請注意，沒有任何錯誤檢查，因此參數無效或遺失都會擲回錯誤。

1. 停止偵錯工作階段。

## <a name="exercise-4-working-with-functionjson"></a>練習 4：使用 function.json

1. 在先前的練習中提到，Visual Studio for Mac 已為程式庫中定義的 Azure 函式「產生」作業函式。 這是因為 Azure Functions 不會真的在執行階段使用方法屬性，而是使用編譯時間檔案系統慣例來設定 Azure Functions 可供使用的位置及方式。 從 **Solution Pad**，以滑鼠右鍵按一下您的專案節點，然後選取 [在尋找工具中顯示]****。

     ![[在尋找工具中顯示] 功能表選項](media/azure-functions-lab-image23.png)

1. 向下巡覽檔案系統，直到您抵達 **bin/Debug/netstandard2.0**。 應該會有一個名為 **Add** 的資料夾。 此資料夾已建立，並對應至 C# 程式碼中的函式名稱屬性。 展開 Add 資料夾以顯示單一 **function.json** 檔案。 執行階段使用此檔案來裝載及管理 Azure 函式。 對於其他沒有編譯時間支援的語言模型 (例如 C# 指令碼或 JavaScript)，則必須手動建立及維護這些資料夾。 對於 C# 開發人員，則會在建置時自動從屬性中繼資料產生這些資料夾。 以滑鼠右鍵按一下 **function.json**，然後選擇在 Visual Studio 中開啟。

    ![檔案目錄中的 function.json](media/azure-functions-lab-image24.png)

1. 透過本教學課程的上述步驟，您應該對 C# 屬性有基本的了解。 考慮到這點，此 JSON 看起來應該很熟悉。 不過，有些項目並未涵蓋在先前的練習中。 例如，每個**繫結**必須已設定其**方向**。 您可能猜得到，**"in"** 表示參數為輸入，而 **"out"** 表示參數為傳回值 (透過 **$return**) 或方法的 **out** 參數。 您也必須指定組件中的 **scriptFile** (相對於此最終位置) 和 **entryPoint** 方法 (public static)。 在接下來幾個步驟中，您將使用此模型新增自訂函式路徑，因此請將此檔案內容複製到剪貼簿。

    ![Visual Studio for Mac 中開啟的 function.json 檔案](media/azure-functions-lab-image25.png)

1. 在 **Solution Pad** 中，以滑鼠右鍵按一下 **AzureFunctionsLab** 專案節點，然後選取 [新增] > [新增資料夾]****。 將新的資料夾命名為 **Adder**。 根據預設慣例，此資料夾的名稱會定義 API 的路徑，例如 **api/Adder**。

    ![[新增資料夾] 選項](media/azure-functions-lab-image26.png)

1. 以滑鼠右鍵按一下 **Adder** 資料夾，然後選取 [新增] > [新增檔案]****。

    ![[新增檔案] 選項](media/azure-functions-lab-image27.png)

1. 選取 [Web]**** 類別和 [空的 JSON 檔案]**** 範本。 將 [名稱]**** 設定為 **function**，然後按一下 [新增]****。

    ![[空的 JSON 檔案] 選項](media/azure-functions-lab-image28.png)

1. 貼入其他 **function.json** 的內容 (來自步驟 3)，以取代新建立檔案的預設內容。

1. 從 JSON 檔案頂端移除下列幾行：

    ```json
    "configurationSource":"attributes",
    "generatedBy":"Microsoft.NET.Sdk.Functions-1.0.13",
    ```

1. 在第一個繫結結尾 (**"name": "req"** 行之後)，新增下列屬性。 別忘了在前一行包含逗號。 此屬性會覆寫預設根目錄，因此它現在會從路徑擷取 **int** 參數，並放入名為 **x** 和 **y** 的方法參數。

    ```json
    "direction": "in",
    "route": "Adder/{x:int?}/{y:int?}"
    ```

1. 在第一個繫結底下新增另一個繫結。 此繫結會處理函式的傳回值。 別忘了在前一行包含逗號：

    ```json
    {
    "name": "$return",
    "type": "http",
    "direction": "out"
    }
    ```

1. 另請更新檔案底部的 **entryPoint** 屬性，以使用稱為 **"Add2"** 的方法，如下所示。 這是為了說明路徑 **api/Adder...** 可對應至任何名稱的適當方法 (此處為 **Add2**)。

    ```json
    "entryPoint": "<project-name>.<function-class-name>.Add2"
    ```

1. 您的最終 **function.json** 檔案看起來應該類似下列 JSON：

    ```json
    {
    "bindings": [
        {
        "type": "httpTrigger",
        "methods": [
            "get"
        ],
        "authLevel": "function",
        "direction": "in",
        "name": "req",
        "route": "Adder/{x:int?}/{y:int?}"
        },
        {
        "name": "$return",
        "type": "http",
        "direction": "out"
        }
    ],
    "disabled": false,
    "scriptFile": "../bin/AzureFunctionsProject.dll",
    "entryPoint": "AzureFunctionsProject.Add.Add2"
    }
    ```

1. 完成此工作的最後一個必要步驟，就是指示 Visual Studio for Mac 在每次這個檔案變更時，都將它複製到輸出目錄的同一個相對路徑。 選取檔案時，從右側導覽列選擇 [屬性] 索引標籤，然後針對 [複製到輸出目錄]**** 選取 [有更新時才複製]****：

    ![JSON 檔案的 [屬性] 選項](media/azure-functions-lab-image30.png)

1. 在 **Add.cs** 中，以下列方法取代 `Run` 方法 (包括屬性) 來完成預期的函式。 它與 `Run` 很類似，不同之處在於它未使用任何屬性，而且具有明確參數 **x** 和 **y**。

    ```csharp
    public static int Add2(
        HttpRequestMessage req,
        int x,
        int y,
        TraceWriter log)
    {
        return x + y;
    }
    ```

1. 按 **F5** 鍵建置並執行專案。

1. 當建置完成並啟動平台時，現在會指出要求有第二個可用的路由對應至最近新增的方法：

    ![HTTP 函式的 URL](media/azure-functions-lab-image31.png)

1. 返回瀏覽器視窗，並流覽至 **http://localhost:7071/api/Adder/3/5** 。

1. 此時，方法再次有效，可從路徑提取參數並產生總和。

1. 返回 **Visual Studio for Mac** 並結束偵錯工作階段。

## <a name="exercise-5-working-with-azure-storage-tables"></a>練習 5：使用 Azure 儲存體資料表

通常，您建置的服務可能會比我們目前為止所建置的服務更複雜，而且需要大量時間及/或基礎結構才能執行。 在此情況下，您可能會發現將要求排入佇列，再於 Azure Functions 提供支援的資源變成可用時進行處理，是很有效的做法。 在其他情況下，您會想要集中儲存資料。 Azure 儲存體資料表可讓您快速地執行此作業。

1. 將下列類別新增至 **Add.cs**。 它應該移至命名空間內，但在現有的類別之外。

    ```csharp
    public class TableRow : TableEntity
    {
        public int X { get; set; }
        public int Y { get; set; }
        public int Sum { get; set; }
    }
    ```

1. 在 **Add** 類別內，新增下列程式碼以引進另一個函式。 請注意，此作業是獨特的，到目前為止都未涉及 HTTP 回應。 最後一行會傳回新的 **TableRow**，並填入可讓您稍後輕鬆擷取的一些重要資訊 (**PartitionKey** 和 **RowKey**)，以及其參數與總和。 方法內的程式碼也會使用 **TraceWriter**，讓您更輕鬆地知道函式何時執行。

    ```csharp
    [FunctionName("Process")]
    [return: Table("Results")]
    public static TableRow Process(
        [HttpTrigger(AuthorizationLevel.Function, "get",
            Route = "Process/{x:int}/{y:int}")]
        HttpRequestMessage req,
        int x,
        int y,
        TraceWriter log)
    {
        log.Info($"Processing {x} + {y}");

        return new TableRow()
        {
            PartitionKey = "sums",
            RowKey = $"{x}_{y}",
            X = x,
            Y = y,
            Sum = x + y
        };
    }
    ```

1. 按 **F5** 鍵建置並執行專案。

1. 在 [瀏覽器] 索引標籤中，流覽至 **http://localhost:7071/api/Process/4/6** 。 這會將另一則訊息放入佇列，最後會導致將另一個資料列新增至資料表。

1. 返回**終端機**並留意 **4 + 6** 的連入要求。

    ![終端機輸出顯示加法要求](media/azure-functions-lab-image32.png)

1. 返回瀏覽器，將要求重新整理為相同的 URL。 此時，您會在 **Process** 方法之後看到錯誤。 這是因為程式碼嘗試使用已存在的分割區和資料列索引鍵組合，將資料列新增至 Azure 資料表儲存體資料表。

    ```
    System.Private.CoreLib: Exception while executing function: Process. Microsoft.Azure.WebJobs.Host: Error while handling parameter $return after function returned:. Microsoft.Azure.WebJobs.Host: The specified entity already exists.
    ```

1. 結束偵錯工作階段。

1. 為了減輕錯誤，請將下列參數新增至緊接在 **TraceWriter** 參數前面的方法定義。 此參數會指示 Azure Functions 平台從我們用來儲存結果之 **PartitionKey** 的 [結果]**** 資料表，嘗試擷取 **TableRow**。 不過，當您注意到 **RowKey** 根據相同方法的其他 **x** 和 **y** 參數動態產生時，才能體會一些真正的魅力。 如果該資料列已存在，則 **tableRow** 會在方法開始時就有該資料列，而不需要開發人員執行額外的工作。 如果該資料列不存在，則會為 Null。 這類效率可讓開發人員專注於重要的商務邏輯，而不是基礎結構。

    ```csharp
    [Table("Results", "sums", "{x}_{y}")]
    TableRow tableRow,
    ```

1. 將下列程式碼新增至方法的開頭。 如果 **tableRow** 不是 Null，則我們已有所要求之作業的結果，因此可以立即將它傳回。 否則，函式會如往常一般繼續執行。 雖然這可能不是傳回資料的最強固方式，但它指出您只要使用很少的程式碼，就可以在多個可擴充層之間協調非常複雜的作業。

    ```csharp
    if (tableRow != null)
    {
        log.Info($"{x} + {y} already exists");
        return null;
    }
    ```

1. 按 **F5** 鍵建置並執行專案。

1. 在 [瀏覽器] 索引標籤中，重新整理位於的 URL **http://localhost:7071/api/Process/4/6** 。 因為此記錄的資料表資料列存在，所以應該會立即傳回且不會發生錯誤。 由於沒有 HTTP 輸出，您可以在終端機中查看輸出。

    ![終端機輸出顯示資料表資料列已存在](media/azure-functions-lab-image33.png)

1. 更新 URL 以反映尚未測試的組合，例如 **http://localhost:7071/api/Process/5/7** 。 注意終端機中的訊息，其指出找不到資料表資料列 (符合預期)。

    ![終端機輸出顯示新的處理序](media/azure-functions-lab-image34.png)

1. 返回 **Visual Studio for Mac** 並結束偵錯工作階段。

<!--
1. Finally, let's take a look at what it's like to work with multiple input records. Rather than specify a specific **TableRow**, you can request an **IQueryable<TableRow>** using the same attributes, and the runtime will fill it with the appropriate resource you need. Add the code below to create a **List** function that lists all items that currently exist in the Azure table we've been working with. Also note that we're specifying that the MIME type of the response is **application/json**, so the runtime will automatically render as JSON.

    ```csharp
    [FunctionName("List")]
    public static HttpResponseMessage List(
        [HttpTrigger(AuthorizationLevel.Function, "get", Route = null)]
        HttpRequestMessage req,
        [Table("Results", "sums")]
        IQueryable<TableRow> table,
        TraceWriter log)
    {
        return req.CreateResponse(HttpStatusCode.OK, table, "application/json");
    }
    ```
1. Press **F5** to build and run the project.

1. In the browser tab, navigate to **http://localhost:7071/api/List**. This should pull down the list of all items in the Azure table and render it as JSON.

    ![](https://user-images.githubusercontent.com/3944468/29033725-be9d5a5e-7b4a-11e7-8b55-df0a200b6320.png)
-->

## <a name="summary"></a>摘要

在此實驗室中，您已了解如何開始使用 Visual Studio for Mac 建置 Azure 函式。
