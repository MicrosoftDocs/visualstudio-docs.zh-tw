---
title: 新增語言伺服器通訊協定延伸模組 |Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d328eb525767205eeedc5781bb93129d5b2eb7f7
ms.sourcegitcommit: 3e74ec49a54e5c3da7631f4466128cdf4384af6b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2019
ms.locfileid: "68711241"
---
# <a name="add-a-language-server-protocol-extension"></a>新增語言伺服器通訊協定延伸模組

語言伺服器通訊協定 (LSP) 是一種常見的通訊協定, 其格式為 JSON RPC v2.0, 用來提供語言服務功能給各種程式碼編輯器。 開發人員可以使用此通訊協定, 撰寫單一語言伺服器來提供語言服務功能, 例如 IntelliSense、錯誤診斷、尋找所有參考等等, 以及支援 LSP 的各種程式碼編輯器。 傳統上, 您可以使用 TextMate 文法檔案來新增 Visual Studio 中的語言服務, 以提供基本功能 (例如語法醒目提示) 或撰寫自訂語言服務 (使用一組完整的 Visual Studio 擴充性 Api 來提供)更豐富的資料。 有了 LSP 的 Visual Studio 支援, 還有第三個選項。

![Visual Studio 中的語言伺服器通訊協定服務](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>語言伺服器通訊協定

![語言伺服器通訊協定執行](media/lsp-implementation.png)

本文說明如何建立使用以 LSP 為基礎之語言伺服器的 Visual Studio 延伸模組。 它假設您已開發一台以 LSP 為基礎的語言伺服器, 而且只想要將它整合到 Visual Studio 中。

如需 Visual Studio 內的支援, 語言伺服器可以透過任何以資料流程為基礎的傳輸機制與用戶端 (Visual Studio) 通訊, 例如:

* 標準輸入/輸出資料流程
* 具名管道
* 通訊端 (僅限 TCP)

在 Visual Studio 中, LSP 和支援的目的是要將不屬於 Visual Studio 產品的語言服務上架。 其目的不在 Visual Studio 中擴充現有的語言服務C#(例如)。 若要擴充現有的語言, 請參閱語言服務的擴充性指南 (例如, ["Roslyn" .NET Compiler Platform](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)), 或參閱[擴充編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)。

如需有關通訊協定本身的詳細資訊, 請參閱[這裡](https://github.com/Microsoft/language-server-protocol)的檔。

如需有關如何建立範例語言伺服器, 或如何將現有的語言伺服器整合到 Visual Studio Code 的詳細資訊, 請參閱[這裡](https://code.visualstudio.com/docs/extensions/example-language-server)的檔。

## <a name="language-server-protocol-supported-features"></a>語言伺服器通訊協定支援的功能

下表顯示 Visual Studio 支援的 LSP 功能:

訊息 | 具有 Visual Studio 的支援
--- | ---
格式化 | 是
初始化 | 是
關機 | 是
退出 | 是
$/cancelRequest | 是
window/showMessage | 是
window/showMessageRequest | 是
window/logMessage | 是
遙測/事件 |
client/registerCapability |
client/unregisterCapability |
workspace/didChangeConfiguration | 是
workspace/didChangeWatchedFiles | 是
工作區/符號 | 是
workspace/executeCommand | 是
workspace/applyEdit | 是
textDocument/publishDiagnostics | 是
textDocument/didOpen | 是
textDocument/didChange | 是
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | 是
textDocument/didClose | 是
textDocument/completion | 是
completion/resolve | 是
textDocument/hover | 是
textDocument/signatureHelp | 是
textDocument/references | 是
textDocument/documentHighlight | 是
textDocument/documentSymbol | 是
textDocument/formatting | 是
textDocument/rangeFormatting | 是
textDocument/onTypeFormatting |
textDocument/definition | 是
textDocument/codeAction | 是
textDocument/codeLens |
codeLens/resolve |
textDocument/documentLink |
documentLink/resolve |
textDocument/rename | 是

## <a name="get-started"></a>開始使用

> [!NOTE]
> 從 Visual Studio 2017 15.8 版開始, 通用語言伺服器通訊協定的支援內建于 Visual Studio 中。 如果您已使用 preview[語言伺服器用戶端 VSIX](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)版本來建立 LSP 延伸模組, 一旦升級至15.8 版或更高版本, 它們就會停止運作。 您必須執行下列動作, 才能讓 LSP 擴充功能再次運作:
>
> 1. 卸載 Microsoft Visual Studio 語言伺服器通訊協定預覽 VSIX。
>
>    從15.8 版開始, 每次在中執行升級時, 都會自動偵測並移除 preview VSIX Visual Studio。
>
> 2. 將您的 Nuget 參考更新為[LSP 套件](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)的最新非預覽版本。
>
> 3. 在 VSIX 資訊清單中移除對 Microsoft Visual Studio 語言伺服器通訊協定預覽 VSIX 的相依性。
>
> 4. 請確定您的 VSIX 指定 Visual Studio 2017 15.8 版 Preview 3 做為安裝目標的下限。
>
> 5. 重建並重新部署。

### <a name="create-a-vsix-project"></a>建立 VSIX 專案

若要使用以 LSP 為基礎的語言伺服器建立語言服務延伸模組, 請先確定您已針對您的實例安裝**Visual Studio 延伸模組開發**工作負載。

接下來, 流覽至 [檔案] [**新增專案** >   > ] [  > **視覺C#**   > 擴充性**VSIX 專案**] 來建立新的 VSIX 專案:

![建立 vsix 專案](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>語言伺服器和執行時間安裝

根據預設, 為了在 Visual Studio 中支援 LSP 語言伺服器所建立的擴充功能, 不包含執行這些伺服器所需的語言伺服器本身或執行時間。 延伸模組開發人員負責散發語言伺服器和所需的執行時間。 有數種方式可以執行這項操作:

* 語言伺服器可以內嵌在 VSIX 中做為內容檔案。
* 建立 MSI 以安裝語言伺服器和/或所需的執行時間。
* 提供 Marketplace 通知使用者如何取得執行時間和語言伺服器的指示。

### <a name="textmate-grammar-files"></a>TextMate 文法檔案

LSP 不包含如何為語言提供文字顏色標示的規格。 為了在 Visual Studio 中提供語言的自訂顏色標示, 延伸模組開發人員可以使用 TextMate 文法檔案。 若要新增自訂 TextMate 文法或主題檔案, 請遵循下列步驟:

1. 在您的延伸模組中建立名為 "文法" 的資料夾 (或您選擇的任何名稱)。

2. 在 [文法] 資料夾內, 包括您想要提供自訂顏色標示的任何 *\*tmlanguage*、  *\*plist*、  *\*. tmtheme*或 *\*json*檔案。

   > [!TIP]
   > *Tmtheme*檔案會定義範圍如何對應至 Visual Studio 分類 (命名色彩索引鍵)。 如需指引, 您可以參考 *% ProgramFiles (x86)% \ Microsoft Visual Studio\\ \<版本 >\\ \<SKU > \Common7\IDE\CommonExtensions\Microsoft\ 中的 tmtheme 檔案。TextMate\Starterkit\Themesg*目錄。

3. 建立 *.pkgdef*檔案, 並新增類似以下的一行:

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. 以滑鼠右鍵按一下檔案, 然後選取 [**屬性**]。 將 [**建立**] 動作變更為 [**內容**], 然後將 [**在 VSIX 中包含**] 屬性變更為**true**。

完成上述步驟之後, 會將文法資料夾新增至套件的安裝目錄, 做為名為 ' MyLang ' 的存放庫來源 (' MyLang ' 只是用來去除混淆的名稱, 而且可以是任何唯一的字串)。 此目錄中的所有文法 ( *. tmlanguage*檔案) 和主題檔案 ( *. tmtheme*檔案) 都會被視為潛力, 而且它們會取代 TextMate 所提供的內建文法。 如果文法檔案的宣告延伸符合要開啟之檔案的副檔名, 則 TextMate 會逐步執行。

## <a name="create-a-simple-language-client"></a>建立簡單的語言用戶端

### <a name="main-interface---ilanguageclientdotnetapimicrosoftvisualstudiolanguageserverclientilanguageclientviewvisualstudiosdk-2017"></a>主要介面- [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

建立 VSIX 專案之後, 將下列 NuGet 套件新增至您的專案:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> 當您完成上述步驟之後, 當您在 NuGet 套件上進行相依性時, 也會將 Newtonsoft 和 StreamJsonRpc 套件新增至您的專案。 **除非您確定這些新版本將會安裝在您的延伸模組目標 Visual Studio 版本上, 否則請勿更新這些套件**。 元件不會包含在您的 VSIX 中;相反地, 它們會從 Visual Studio 安裝目錄中挑選。 如果您參考的元件版本比使用者電腦上安裝的還新, 則您的擴充功能將無法使用。

接著, 您可以建立新的類別來執行[ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)介面, 這是連接到 LSP 型語言伺服器的語言用戶端所需的主要介面。

以下是範例:

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

需要實作為[OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017)和[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017)的主要方法。 當 Visual Studio 載入您的擴充功能, 而且您的語言伺服器已準備好開始時, 就會呼叫[OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) 。 在此方法中, 您可以立即叫用[StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017)委派, 以表示應該啟動語言伺服器, 或者您也可以執行其他邏輯, 並在稍後叫用[StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) 。 **若要啟用您的語言伺服器, 您必須在某個時間點呼叫 StartAsync。**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017)是最後藉由呼叫[StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017)委派來叫用的方法。 其中包含啟動語言伺服器並建立其連接的邏輯。 必須傳回連線物件, 其中包含要寫入伺服器和從伺服器讀取的資料流程。 此處擲回的任何例外狀況都會透過 Visual Studio 中的資訊列訊息來攔截並向使用者顯示。

### <a name="activation"></a>啟用

在您的語言用戶端類別完成後, 您必須定義兩個屬性, 以定義如何將它載入 Visual Studio 並啟用:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio 使用[MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) 來管理其擴充點。 [Export](/dotnet/api/system.componentmodel.composition.exportattribute)屬性會指出應該將此類別視為擴充點, 並在適當的時間載入, 以 Visual Studio。

若要使用 MEF, 您也必須在 VSIX 資訊清單中將 MEF 定義為資產。

開啟您的 VSIX 資訊清單設計工具, 然後流覽至 [**資產**] 索引標籤:

![新增 MEF 資產](media/lsp-add-asset.png)

按一下 [**新增**] 以建立新的資產:

![定義 MEF 資產](media/lsp-define-asset.png)

* **類型**:Microsoft.VisualStudio.MefComponent
* **來源**:目前方案中的專案
* **專案**: [您的專案]

### <a name="content-type-definition"></a>內容類型定義

目前, 載入以 LSP 為基礎的語言伺服器擴充功能的唯一方式是依檔案內容類型。 也就是說, 在定義您的語言用戶端類別 (它會執行[ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)) 時, 您必須定義檔案的類型, 當開啟時, 就會載入擴充功能。 如果未開啟任何符合您定義之內容類型的檔案, 則不會載入您的延伸模組。

這項作業是透過定義一或`ContentTypeDefinition`多個類別來完成:

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

在上述範例中, 會針對結尾為 *. bar*副檔名的檔案建立內容類型定義。 內容類型定義的名稱為 "bar", 且必須衍生自[CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017)。

新增內容類型定義之後, 您可以接著定義何時要在 language client 類別中載入語言用戶端擴充功能:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

新增 LSP 語言伺服器的支援時, 您不需要在 Visual Studio 中執行自己的專案系統。 客戶可以在 Visual Studio 中開啟單一檔案或資料夾, 以開始使用您的語言服務。 事實上, 對 LSP 語言伺服器的支援是設計成隻在開啟資料夾/檔案案例中使用。 如果已執行自訂專案系統, 某些功能 (例如設定) 將無法使用。

## <a name="advanced-features"></a>進階功能

### <a name="settings"></a>設定

提供對自訂語言伺服器特定設定的支援, 但仍在改善過程中。 設定專屬於語言伺服器所支援的內容, 而且通常會控制語言伺服器發出資料的方式。 例如, 語言伺服器可能會有回報的錯誤最大數目的設定。 延伸模組作者會定義預設值, 可供使用者針對特定專案進行變更。

請遵循下列步驟, 將設定的支援新增至您的 LSP 語言服務延伸模組:

1. 將 JSON 檔案 (例如*MockLanguageExtensionSettings*) 新增至您的專案, 其中包含設定和其預設值。 例如：

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. 以滑鼠右鍵按一下 JSON 檔案, 然後選取 [**屬性**]。 將 [**建立**] 動作變更為 [內容], 並將 [在 VSIX 中包含] 屬性設為 [ **true**]。

3. 執行 ConfigurationSections, 並傳回 JSON 檔案中定義之設定的首碼清單 (在 Visual Studio Code 中, 這會對應至 package. JSON 中的設定區段名稱):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. 將 .pkgdef 檔案新增至專案 (加入新的文字檔, 並將副檔名變更為. .pkgdef)。 .Pkgdef 檔案應該包含下列資訊:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    範例：

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. 以滑鼠右鍵按一下 .pkgdef 檔案, 然後選取 [**屬性**]。 將 [**建立**動作] 變更為 [**內容**], 並將 [**在 VSIX 中包含**] 屬性變更為**true**

6. 開啟*extension.vsixmanifest*檔案, 並在 [**資產**] 索引標籤中新增資產:

   ![編輯 vspackage 資產](media/lsp-add-vspackage-asset.png)

   * **類型**:Microsoft.VisualStudio.VsPackage
   * **來源**:檔案系統上的檔案
   * **Path**: [path to a *.pkgdef* file]

### <a name="user-editing-of-settings-for-a-workspace"></a>使用者編輯工作區的設定

1. 使用者開啟包含您的伺服器所擁有之檔案的工作區。
2. 使用者在 *. vs*資料夾中新增名為*vsworkspacesettings.json*的檔案。
3. 使用者會針對伺服器提供的設定, 將一行新增至*vsworkspacesettings.json*檔案。 例如：

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>啟用診斷追蹤

診斷追蹤可以啟用以輸出用戶端與伺服器之間的所有訊息, 這在偵測問題時可能很有用。 若要啟用診斷追蹤, 請執行下列動作:

1. 開啟或建立工作區設定檔*vsworkspacesettings.json* (請參閱「使用者編輯工作區的設定」)。
2. 在設定 json 檔案中新增下列程式程式碼:

```json
{
    "foo.trace.server": "Off"
}
```

追蹤詳細資訊有三個可能的值:

* 「關閉」: 完全關閉追蹤
* 「訊息」: 追蹤已開啟, 但是只會追蹤方法名稱和回應識別碼。
* 「詳細資訊」: 追蹤已開啟;追蹤整個 rpc 訊息。

開啟追蹤時, 會將內容寫入 *%temp%\VisualStudio\LSP*目錄中的檔案。 記錄檔會遵循命名格式 *[LanguageClientName]-[Datetime 戳記] .log*。 目前, 只能針對開啟資料夾案例啟用追蹤。 開啟單一檔案以啟用語言伺服器並不支援診斷追蹤。

### <a name="custom-messages"></a>自訂訊息

有一些 Api 可協助您將訊息傳遞至不屬於標準語言伺服器通訊協定的語言伺服器, 以及從中接收訊息。 若要處理自訂訊息, 請在您的 language client 類別中執行[ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)介面。 [VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md)程式庫是用來在您的語言用戶端和語言伺服器之間傳輸自訂訊息。 由於您的 LSP 語言用戶端擴充功能就像任何其他 Visual Studio 延伸模組一樣, 因此您可以決定新增額外的功能 (不受 LSP 支援), 以透過自訂訊息在您的延伸模組中 Visual Studio (使用其他 Visual Studio Api)。

#### <a name="receive-custom-messages"></a>接收自訂訊息

若要從語言伺服器接收自訂訊息, 請在[ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)上執行[CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017)屬性, 並傳回知道如何處理自訂訊息的物件。 範例如下:

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

若要將自訂訊息傳送到語言伺服器, 請在[ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)上執行[AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017)方法。 當您的語言伺服器啟動並準備好接收訊息時, 就會叫用這個方法。 系統會將[JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs)物件當做參數來傳遞, 然後您就可以繼續使用[VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) api 將訊息傳送到語言伺服器。 範例如下:

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

有時候延伸模組開發人員可能會想要攔截從語言伺服器傳送和接收的 LSP 訊息。 例如, 延伸模組開發人員可能會想要改變針對特定 LSP 訊息所傳送的訊息參數, 或修改從語言伺服器針對 LSP 功能傳回的結果 (例如完成)。 當此為必要時, 延伸模組開發人員可以使用 MiddleLayer API 來攔截 LSP 訊息。

每個 LSP 訊息都有它自己的中介層介面來攔截。 若要攔截特定的訊息, 請建立一個類別, 它會針對該訊息執行中介層介面。 然後, 在您的 language client 類別中執行[ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)介面, 並在[MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017)屬性中傳回物件的實例。 範例如下:

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

中介層功能仍在開發中, 而且尚未全面提供。

## <a name="sample-lsp-language-server-extension"></a>範例 LSP 語言伺服器擴充功能

若要使用 Visual Studio 中的 LSP 用戶端 API 查看範例延伸模組的原始程式碼, 請參閱 VSSDK-擴充性-範例[LSP 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol)。

## <a name="faq"></a>常見問題集

**我想要建立自訂的專案系統來補充我的 LSP 語言伺服器, 以在 Visual Studio 中提供更豐富的功能支援, 我該怎麼做呢？**

Visual Studio 中以 LSP 為基礎的語言伺服器支援依賴 [[開啟資料夾] 功能](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/), 並設計為不需要自訂專案系統。 您可以遵循[這裡](https://github.com/Microsoft/VSProjectSystem)的指示, 建立您自己的自訂專案系統, 但某些功能 (例如設定) 可能無法使用。 LSP 語言伺服器的預設初始化邏輯是傳入目前開啟之資料夾的根資料夾位置, 因此, 如果您使用自訂的專案系統, 您可能需要在初始化期間提供自訂邏輯, 以確保您的語言伺服器可以正常啟動。

**如何? 新增偵錯工具支援嗎？**

我們將在未來的版本中提供[一般偵錯工具通訊協定](https://code.visualstudio.com/docs/extensionAPI/api-debugging)的支援。

**如果已安裝 VS 支援的語言服務 (例如 JavaScript), 我是否仍然可以安裝可提供其他功能 (例如 linting) 的 LSP 語言伺服器延伸模組？**

是, 但並非所有功能都能正常運作。 LSP 語言伺服器擴充功能的最終目標是要啟用 Visual Studio 原本不支援的語言服務。 您可以使用 LSP 語言伺服器來建立提供額外支援的延伸模組, 但某些功能 (例如 IntelliSense) 將不會是順暢的體驗。 一般來說, 我們會建議使用 LSP 語言伺服器擴充功能來提供新的語言體驗, 而不是擴充現有的。

**我要在哪裡發行已完成的 LSP 語言伺服器 VSIX？**

請參閱[這裡](walkthrough-publishing-a-visual-studio-extension.md)的 Marketplace 指示。

## <a name="see-also"></a>另請參閱

- [新增其他語言的 Visual Studio 編輯器支援](../ide/adding-visual-studio-editor-support-for-other-languages.md)
