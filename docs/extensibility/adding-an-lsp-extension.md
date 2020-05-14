---
title: 新增語言伺服器協定擴展 |微軟文件
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef2093915538f09f425fc961420c4a3078043c91
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740228"
---
# <a name="add-a-language-server-protocol-extension"></a>新增語言伺服器通訊協定延伸模組

語言伺服器協定 (LSP) 是一種通用協定,其形式為 JSON RPC v2.0,用於向各種代碼編輯器提供語言服務功能。 使用該協定,開發人員可以編寫一個語言伺服器,向支援 LSP 的各種代碼編輯器提供語言服務功能,如 IntelliSense、錯誤診斷、查找所有引用等。 傳統上,可以使用 TextMate 語法檔提供語法突出顯示等基本功能,或者編寫使用全套 Visual Studio 擴展 API 提供更豐富數據的自定義語言服務來添加 Visual Studio 中的語言服務。 借助 Visual Studio 對 LSP 的支援,有第三個選項。

![視覺化工作室中的語言伺服器協定服務](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>語言伺服器通訊協定

![語言伺服器協定實現](media/lsp-implementation.png)

本文介紹如何創建使用基於 LSP 的語言伺服器的 Visual Studio 擴展。 它假定您已經開發了基於 LSP 的語言伺服器,並且只想將其集成到 Visual Studio 中。

為了在 Visual Studio 中提供支援,語言伺服器可以透過任何基於串流的傳輸機制與用戶端(Visual Studio) 通訊,例如:

* 標準輸入/輸出串流
* 具名管道
* Socket(僅限 TCP)

LSP 和 Visual Studio 中支援它的目的是將不屬於 Visual Studio 產品的語言服務載入。 它不打算擴展視覺工作室中的現有語言服務(如 C#)。 要延伸現有語言,請參閱語言服務的擴充性指南(例如[,"Roslyn".NET 編譯器平臺](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)),或請參閱[擴展編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)。

有關協定本身的詳細資訊,請參閱[此處](https://github.com/Microsoft/language-server-protocol)的文檔。

有關如何創建範例語言伺服器或如何將現有語言伺服器整合到 Visual Studio Code 中的詳細資訊,請參閱[此處](https://code.visualstudio.com/docs/extensions/example-language-server)的文檔。

## <a name="language-server-protocol-supported-features"></a>語言伺服器協定支援功能

下表顯示了可視化工作室中支援哪些 LSP 功能:

訊息 | 在視覺工作室中提供支援
--- | ---
initialize | 是
初始化 | 是
shutdown | 是
exit | 是
$/取消請求 | 是
視窗/顯示訊息 | 是
視窗/顯示訊息要求 | 是
視窗/記錄訊息 | 是
遙測/事件 |
用戶端/寄存器能力 |
用戶端/取消註冊功能 |
工作區/已更改設定 | 是
工作區/已更改監視檔 | 是
工作區/符號 | 是
工作區/執行命令 | 是
工作區/應用編輯 | 是
文字文件/發佈診斷 | 是
文字文件/已開啟 | 是
文字文件/已變更 | 是
文字文件/儲存 |
文字文件/將儲存等待,直到 |
文字文件/已儲存 | 是
文字文件/關閉 | 是
文字文件/完成 | 是
完成/解決 | 是
文字文件/懸停 | 是
文字文件/簽署說明 | 是
文字文件/引用 | 是
文字文件/文件突顯 | 是
文字文件/文件符號 | 是
文字文件/格式 | 是
文字文件/範圍格式 | 是
文字文件/開啟類型格式 |
文字文件/定義 | 是
文字文件/代碼操作 | 是
文字文件/代碼鏡頭 |
代碼鏡頭/解析 |
文字文件/文件連結 |
文件連結/解析 |
文字文件/重新命名 | 是

## <a name="get-started"></a>開始使用

> [!NOTE]
> 從 Visual Studio 2017 版本 15.8 開始,對通用語言伺服器協定的支援內置於可視化工作室中。 如果您已使用預覽[語言伺服器用戶端 VSIX](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)版本構建 LSP 擴展,則升級至版本 15.8 或更高版本後,它們將停止工作。 您需要執行以下操作才能讓 LSP 延伸再次工作:
>
> 1. 卸載微軟可視化工作室語言伺服器協定預覽 VSIX。
>
>    從版本 15.8 開始,每次在 Visual Studio 中執行升級時,將自動檢測並刪除預覽 VSIX。
>
> 2. 更新您的 Nuget 引用到[LSP 套件](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)的最新非預覽版本。
>
> 3. 刪除 VSIX 清單中對 Microsoft 視覺化工作室語言伺服器協定預覽 VSIX 的依賴項。
>
> 4. 確保 VSIX 指定 Visual Studio 2017 版本 15.8 預覽 3 作為安裝目標的下限。
>
> 5. 重建並重新部署。

### <a name="create-a-vsix-project"></a>建立 VSIX 專案

要使用基於 LSP 的語言伺服器創建語言服務擴展,首先請確保為 VS 實例安裝了**Visual Studio 擴充開發**工作負載。

接下來,透過瀏覽**到檔案** > **新項目** > **視覺化 C_** > **擴充性** > VSIX 專案建立新的**VSIX 專案**:

![建立 vsix 專案](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>語言伺服器與執行時安裝

預設情況下,為支援 Visual Studio 中基於 LSP 的語言伺服器而創建的擴展不包含語言伺服器本身或執行它們所需的執行時。 擴展開發人員負責分發語言伺服器和所需的運行時。 有幾種方法可以做到這一點:

* 語言伺服器可以作為內容檔嵌入到 VSIX 中。
* 創建 MSI 以安裝語言伺服器和/或所需的執行時。
* 在應用商店上提供說明,告知使用者如何獲取運行時和語言伺服器。

### <a name="textmate-grammar-files"></a>文字Mate語法檔

LSP 不包括有關如何為語言提供文本著色的規範。 要為 Visual Studio 中的語言提供自訂著色,擴展開發人員可以使用 TextMate 語法檔。 要新增自訂 TextMate 語法或主題檔,請按照以下步驟操作:

1. 在延伸室內建立名為「語法」的資料夾(也可以是您選擇的任何名稱)。

2. 在*語法*資料夾中,包括任何*\*.tm 語言**\***\*、.plist、.tmtheme*或*\*.json*檔,您希望提供自定義著色。

   > [!TIP]
   > *.tmtheme*檔案定義作用域如何映射到 Visual Studio 分類(命名顏色鍵)。 有關指導,您可以在 *%程式檔 (x86)%_Microsoft\\\<Visual Studio\\\<版本>SKU>_Common7_IDE_共同扩展\Microsoft_TextMate_starterkit_Themesg*目錄中引用全域 *.tmtheme*檔。

3. 建立 *.pkgdef*檔案並新增類似於此行:

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. 右鍵按下檔案並選擇**屬性**。 將 **'產生'** 操作**變更為內容**,並將**VSIX 屬性中的「 包含」** 變更為**true**。

完成上述步驟後,*語法*文件夾將作為名為"MyLang"的儲存庫源添加到包的安裝目錄中("MyLang"只是消除歧義的名稱,可以是任何唯一的字串)。 此目錄中的所有語法 *(.tm語言*檔)和主題檔 *(.tmtheme*檔案)都作為潛在內容被拾起,它們取代了 TextMate 提供的內置語法。 如果語法檔的聲明副檔名與正在打開的文件的副檔名匹配,TextMate 將介入。

## <a name="create-a-simple-language-client"></a>建立簡單的語言客戶端

### <a name="main-interface---ilanguageclient"></a>主介面 - [I語言用戶端](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

建立 VSIX 專案後,向專案新增以下 NuGet 套件:

* [微軟.VisualStudio.語言伺服器.用戶端](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> 完成上述步驟后依賴 NuGet 包時,牛頓軟.Json 和 StreamJsonRpc 包也添加到您的專案中。 **不要更新這些套件,除非您確定這些新版本將安裝在您的擴展目標 Visual Studio 版本上**。 程式集將不包含在 VSIX 中;因此,這些程式集將不包含在 VSIX 中。相反,它們將從可視化工作室安裝目錄中拾取。 如果引用的程式集版本較用戶電腦上安裝的程式集版本要大,則擴展將不起作用。

然後,您可以創建實現[I語言用戶端](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)介面的新類,該介面是連接到基於 LSP 的語言伺服器的語言用戶端所需的主介面。

以下是範例︰

```csharp
namespace MockLanguageExtension
{
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
        public string Name => "Bar Language Extension";

        public IEnumerable<string> ConfigurationSections => null;

        public object InitializationOptions => null;

        public IEnumerable<string> FilesToWatch => null;

        public event AsyncEventHandler<EventArgs> StartAsync;
        public event AsyncEventHandler<EventArgs> StopAsync;

        public async Task<Connection> ActivateAsync(CancellationToken token)
        {
            await Task.Yield();

            ProcessStartInfo info = new ProcessStartInfo();
            info.FileName = Path.Combine(Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location), "Server", @"MockLanguageServer.exe");
            info.Arguments = "bar";
            info.RedirectStandardInput = true;
            info.RedirectStandardOutput = true;
            info.UseShellExecute = false;
            info.CreateNoWindow = true;

            Process process = new Process();
            process.StartInfo = info;

            if (process.Start())
            {
                return new Connection(process.StandardOutput.BaseStream, process.StandardInput.BaseStream);
            }

            return null;
        }

        public async Task OnLoadedAsync()
        {
            await StartAsync.InvokeAsync(this, EventArgs.Empty);
        }

        public Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

需要實現的主要方法是[「上載Async」](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017)和[「啟動Async」。](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) 當 Visual Studio 載入了擴展並準備好啟動語言伺服器時,將調用[OnLoadedAsync。](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) 在此方法中,您可以立即調用[StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017)委託以發出語言伺服器應啟動的訊號,或者可以執行其他邏輯並在以後調用[StartAsync。](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) **要啟動語言伺服器,您必須在某個時間點調用 StartAsync。**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017)是最終調用[StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017)委託調用的方法。 它包含啟動語言伺服器並建立與它連接的邏輯。 必須返回包含用於寫入伺服器和從伺服器讀取的流的連接物件。 此處引發的任何異常都通過 Visual Studio 中的資訊列消息捕獲並顯示給使用者。

### <a name="activation"></a>啟用

實現語言用戶端類後,需要為其定義兩個屬性,以定義如何將其載入到 Visual Studio 並啟動:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio 使用[MEF(](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md)託管擴充性框架)來管理其擴展點。 ["導出"](/dotnet/api/system.componentmodel.composition.exportattribute)屬性指示 Visual Studio 應作為擴展點選取此類並在適當的時間載入。

要使用 MEF,還必須在 VSIX 清單中將 MEF 定義為資產。

開啟 VSIX 清單設計器並瀏覽到「**資產**」選項卡:

![新增 MEF 資產](media/lsp-add-asset.png)

按下 **'新增**'建立新資產:

![定義 MEF 資產](media/lsp-define-asset.png)

* **型態**: 微軟.VisualStudio.Mef 元件
* **來源**: 目前解決方案中的項目
* **專案**: [您的項目]

### <a name="content-type-definition"></a>內容類型定義

目前,載入基於 LSP 的語言伺服器擴展名的唯一方法是按檔內容類型。 也就是說,在定義語言用戶端類(實現[I語言用戶端](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017))時,您需要定義檔案類型,這些檔在打開時將導致載入擴展名。 如果未打開與您的定義的內容類型匹配的檔,則不會載入副檔名。

這是透過定義一個或多個`ContentTypeDefinition`類別完成的:

```csharp
namespace MockLanguageExtension
{
    public class BarContentDefinition
    {
        [Export]
        [Name("bar")]
        [BaseDefinition(CodeRemoteContentDefinition.CodeRemoteContentTypeName)]
        internal static ContentTypeDefinition BarContentTypeDefinition;

        [Export]
        [FileExtension(".bar")]
        [ContentType("bar")]
        internal static FileExtensionToContentTypeDefinition BarFileExtensionDefinition;
    }
}
```

在前面的範例中,為以 *.bar*檔案副檔名結尾的文件創建內容類型定義。 內容類型定義的名稱為"bar",必須派生自[代碼遠端內容類型名稱](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017)。

新增內容型態定義後,可以定義何時在語言用戶端類別中載入語言客戶端延伸:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

添加對 LSP 語言伺服器的支援不需要您在 Visual Studio 中實現自己的項目系統。 客戶可以在 Visual Studio 中打開單個檔案或資料夾,以開始使用您的語言服務。 事實上,對 LSP 語言伺服器的支援設計僅在打開的資料夾/檔案方案中工作。 如果實現了自定義項目系統,則某些功能(如設置)將不起作用。

## <a name="advanced-features"></a>進階功能

### <a name="settings"></a>設定

支援自定義語言伺服器特定的設置,但仍處於改進過程中。 設置特定於語言伺服器支援的內容,通常控制語言伺服器如何發出數據。 例如,語言伺服器可能具有報告的最大錯誤數設置。 擴展作者將定義一個預設值,使用者可以更改特定專案。

依以下步驟向 LSP 語言服務擴展新增對設定的支援:

1. 包含設定及其預設值的專案添加 JSON 檔(例如 *,Mock語言副檔設定.json)。* 例如：

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. 右鍵按下 JSON 檔並選擇**屬性**。 將**產生**操作變更為「內容」,將「包含在 VSIX」 屬性變更為**true**。

3. 實現設定節並傳回 JSON 檔中定義的設定的前置字串清單(在可視化工作室代碼中,這將映射到包.json 中的設定節名稱):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. 加入專案加入 .pkgdef 檔(新增新文字檔並將檔副檔名更改為 .pkgdef)。 pkgdef 檔案應包含此資訊:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    範例：

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. 右鍵按下 .pkgdef 檔案並選擇**屬性**。 將 **'產生****'''變更為'內容**',將**VSIX 屬性中的' 變更**為**true**。

6. 開啟*source.延伸.vsix清單*檔,並在 **「資產**」選項卡中新增資產:

   ![編輯與套件資產](media/lsp-add-vspackage-asset.png)

   * **型態**: 微軟.VisualStudio.Vs 包
   * **來源**: 檔案系統上的檔案
   * **路徑**: [對 *.pkgdef*檔案的路徑]

### <a name="user-editing-of-settings-for-a-workspace"></a>使用者編輯工作區的設定

1. 用戶打開一個工作區,其中包含伺服器擁有的檔。
2. 使用者在名為*VSWorkspaceSettings.json*的 *.vs*資料夾中添加一個檔。
3. 使用者為伺服器提供的設置向*VSWorkspaceSettings.json*檔添加一行。 例如：

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>開啟診斷追蹤

可以啟用診斷追蹤以在用戶端和伺服器之間輸出所有消息,這在調試問題時非常有用。 要啟用診斷追蹤,可以執行以下操作:

1. 打開或創建工作區設定檔*VSWorkspaceSettings.json(* 請參閱"工作區設置的使用者編輯")。
2. 在設定 json 檔中添加以下行:

```json
{
    "foo.trace.server": "Off"
}
```

追蹤詳細性有三個可能的值:

* 關閉「:」% 關閉
* "消息":已打開但僅跟蹤方法名稱和响應 ID。
* "詳細":已打開跟蹤;跟蹤整個 rpc 消息。

開啟追蹤後,內容將寫入 *%temp%_VisualStudio_LSP*目錄中的檔案。 紀錄遵循命名格式 *[語言用戶端名稱] -[日期時間戳]日誌*。 目前,只能為打開的資料夾方案啟用跟蹤。 打開單個檔以啟動語言伺服器沒有診斷跟蹤支援。

### <a name="custom-messages"></a>自訂訊息

有 API 用於方便將訊息傳遞到非標準語言伺服器協定一部分的語言伺服器和接收消息。 要處理自訂訊息,請在語言用戶端類別中實現[I語言用戶端訊息介面](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)。 [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md)庫用於在語言用戶端和語言伺服器之間傳輸自定義消息。 由於 LSP 語言用戶端擴展與任何其他 Visual Studio 擴展類似,因此您可以透過自訂訊息決定在擴展中向 Visual Studio(使用其他 Visual Studio API)添加其他功能(LSP 不支援)。

#### <a name="receive-custom-messages"></a>接收自訂訊息

要從語言伺服器接收自定義消息,請在[I語言ClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)上實現[自訂MessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017)屬性,並返回知道如何處理自訂郵件的物件。 以下範例:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public object CustomMessageTarget
    {
        get;
        set;
    }

    public class CustomTarget
    {
        public void OnCustomNotification(JToken arg)
        {
            // Provide logic on what happens OnCustomNotification is called from the language server
        }

        public string OnCustomRequest(string test)
        {
            // Provide logic on what happens OnCustomRequest is called from the language server
        }
    }
}
```

#### <a name="send-custom-messages"></a>傳送自訂訊息

要向語言伺服器發送自訂訊息,請在[I語言用戶端自訂訊息](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)上實現[附加ForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017)方法。 當您的語言伺服器啟動並準備接收消息時,將調用此方法。 [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs)物件作為參數傳遞,然後您可以保留該參數,使用[VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) API 將消息發送到語言伺服器。 以下範例:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public async Task AttachForCustomMessageAsync(JsonRpc rpc)
    {
        await Task.Yield();

        this.customMessageRpc = rpc;
    }

    public async Task SendServerCustomNotification(object arg)
    {
        await this.customMessageRpc.NotifyWithParameterObjectAsync("OnCustomNotification", arg);
    }

    public async Task<string> SendServerCustomMessage(string test)
    {
        return await this.customMessageRpc.InvokeAsync<string>("OnCustomRequest", test);
    }
}
```

### <a name="middle-layer"></a>中介層

有時,擴展開發人員可能想要攔截發送到語言伺服器並從語言伺服器接收的 LSP 消息。 例如,擴展開發人員可能希望更改為特定 LSP 消息發送的消息參數,或修改從語言伺服器返回的 LSP 功能的結果(例如完成)。 必要時,擴展開發人員可以使用中間層 API 攔截 LSP 消息。

每個 LSP 消息都有自己的中間層介面進行攔截。 要攔截特定消息,請創建一個類,該類為該消息實現中間層介面。 然後,在語言用戶端類中實現[I語言ClientCustomMessage介面](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017),並在[「中間層」](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017)屬性中返回物件的實例。 以下範例:

```csharp
public class MockLanguageClient: ILanguageClient, ILanguageClientCustomMessage
{
    public object MiddleLayer => MiddleLayerProvider.Instance;

    private class MiddleLayerProvider : ILanguageClientWorkspaceSymbolProvider
    {
        internal readonly static MiddleLayerProvider Instance = new MiddleLayerProvider();

        private MiddleLayerProvider()
        {
        }

        public async Task<SymbolInformation[]> RequestWorkspaceSymbols(WorkspaceSymbolParams param, Func<WorkspaceSymbolParams, Task<SymbolInformation[]>> sendRequest)
        {
            // Send along the request as given
            SymbolInformation[] symbols = await sendRequest(param);

            // Only return symbols that are "files"
            return symbols.Where(sym => string.Equals(new Uri(sym.Location.Uri).Scheme, "file", StringComparison.OrdinalIgnoreCase)).ToArray();
        }
    }
}
```

中間層特徵仍在開發中,尚未全面。

## <a name="sample-lsp-language-server-extension"></a>範例 LSP 語言伺服器延伸

要檢視 Visual Studio 中使用 LSP 用戶端 API 的範例延伸的原始碼,請參閱 VSSDK-可擴充性-範例[LSP 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol)。

## <a name="faq"></a>常見問題集

**我想構建一個自定義專案系統來補充我的 LSP 語言伺服器,在 Visual Studio 中提供更豐富的功能支援,我該怎麼做?**

Visual Studio 中基於 LSP 的語言伺服器的支援依賴於[打開的資料夾功能](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/),並且設計為不需要自定義專案系統。 您可以[按照此處](https://github.com/Microsoft/VSProjectSystem)的說明構建自己的自定義專案系統,但某些功能(如設置)可能無法正常工作。 LSP 語言伺服器的預設初始化邏輯是傳遞當前打開的資料夾的根資料夾位置,因此,如果您使用自定義專案系統,則可能需要在初始化期間提供自定義邏輯,以確保語言伺服器可以正確啟動。

**如何添加調試器支援?**

我們將在將來的版本中為[通用調試協定](https://code.visualstudio.com/docs/extensionAPI/api-debugging)提供支援。

**如果已經安裝了 VS 支援的語言服務(例如 JavaScript),我是否仍可以安裝提供其他功能(如 linting)的 LSP 語言伺服器擴展?**

可以,但並非所有功能都正常工作。 LSP 語言伺服器擴展的最終目標是啟用 Visual Studio 不支援的本機語言服務。 您可以使用 LSP 語言伺服器創建提供其他支援的擴展,但某些功能(如 IntelliSense)不會是流暢的體驗。 通常,建議使用 LSP 語言伺服器擴展來提供新的語言體驗,而不是擴展現有語言體驗。

**在哪裡發佈已完成的 LSP 語言伺服器 VSIX?**

在此處查看[市場說明。](walkthrough-publishing-a-visual-studio-extension.md)

## <a name="see-also"></a>另請參閱

- [新增其他語言的 Visual Studio 編輯器支援](../ide/adding-visual-studio-editor-support-for-other-languages.md)
