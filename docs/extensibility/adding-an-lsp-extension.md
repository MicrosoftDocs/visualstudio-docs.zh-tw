---
title: 新增語言伺服器通訊協定延伸模組 |Microsoft Docs
description: 瞭解如何建立 Visual Studio 擴充功能，以根據語言伺服器通訊協定 (LSP) 來整合語言伺服器。
ms.custom: SEO-VS-2020
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26f78be8708e61370be3256c8cde481d5c61c89d
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598142"
---
# <a name="add-a-language-server-protocol-extension"></a>新增語言伺服器通訊協定延伸模組

Language Server Protocol (LSP) 是一種通用的通訊協定，採用 JSON RPC v2.0 的形式，用來為各種程式碼編輯器提供語言服務功能。 開發人員可以使用此通訊協定撰寫單一語言伺服器，為支援 LSP 的各種程式碼編輯器提供語言服務功能，例如 IntelliSense、錯誤診斷、尋找所有參考等等。 傳統上，您可以使用 TextMate 文法檔來新增 Visual Studio 中的語言服務，以提供基本功能，例如語法醒目提示或撰寫自訂語言服務，以使用完整的 Visual Studio 擴充性 Api 來提供更豐富的資料。 有了 LSP 的 Visual Studio 支援，還有第三個選項。

![Visual Studio 中的語言伺服器通訊協定服務](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>語言伺服器通訊協定

![語言伺服器通訊協定實行](media/lsp-implementation.png)

本文說明如何建立使用以 LSP 為基礎之語言伺服器的 Visual Studio 延伸模組。 它假設您已經開發了 LSP 型語言伺服器，而且只想要將它整合到 Visual Studio 中。

針對 Visual Studio 內的支援，語言伺服器可以透過任何以資料流程為基礎的傳輸機制與用戶端 (Visual Studio) 進行通訊，例如：

* 標準輸入/輸出資料流程
* 具名管道
* 僅限通訊端 (TCP) 

在 Visual Studio 中，LSP 和支援的目的是要將不是 Visual Studio 產品一部分的語言服務上架。 它不是用來擴充現有的語言服務 (例如 Visual Studio 中的 c # ) 。 若要擴充現有的語言，請參閱 language service 的擴充性指南 (例如， ["Roslyn" .NET Compiler Platform](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)) 或參閱 [擴充編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)。

如需有關通訊協定本身的詳細資訊，請參閱 [此處](https://github.com/Microsoft/language-server-protocol)的檔。

如需有關如何建立範例語言伺服器，或如何將現有的語言伺服器整合到 Visual Studio Code 的詳細資訊，請參閱 [此處](https://code.visualstudio.com/docs/extensions/example-language-server)的檔。

## <a name="language-server-protocol-supported-features"></a>語言伺服器通訊協定支援的功能

下表顯示 Visual Studio 支援的 LSP 功能：

訊息 | 支援 Visual Studio
--- | ---
initialize | 是
初始化 | 是
shutdown | 是
exit | 是
$/cancelRequest | 是
window/showMessage | 是
window/showMessageRequest | 是
window/logMessage | 是
遙測/事件 |
用戶端/registerCapability |
用戶端/unregisterCapability |
工作區/didChangeConfiguration | 是
工作區/didChangeWatchedFiles | 是
工作區/符號 | 是
工作區/executeCommand | 是
工作區/applyEdit | 是
textDocument/publishDiagnostics | 是
textDocument/didOpen | 是
textDocument/didChange | 是
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | 是
textDocument/didClose | 是
textDocument/完成 | 是
完成/解決 | 是
textDocument/停留 | 是
textDocument/signatureHelp | 是
textDocument/參考 | 是
textDocument/documentHighlight | 是
textDocument/documentSymbol | 是
textDocument/格式化 | 是
textDocument/rangeFormatting | 是
textDocument/onTypeFormatting |
textDocument/定義 | 是
textDocument/codeAction | 是
textDocument/codeLens |
codeLens/解析 |
textDocument/documentLink |
documentLink/解析 |
textDocument/重新命名 | 是

## <a name="get-started"></a>開始使用

> [!NOTE]
> 從 Visual Studio 2017 15.8 版開始，Visual Studio 內建 common Language Server 通訊協定的支援。 如果您使用預覽 [語言伺服器用戶端 VSIX](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) 版本建立了 LSP 擴充功能，當您升級至15.8 版或更高版本時，它們將會停止運作。 您將需要執行下列動作，才能讓 LSP 延伸模組再次運作：
>
> 1. 卸載 Microsoft Visual Studio Language Server Protocol Preview VSIX。
>
>    從15.8 版開始，每次您在 Visual Studio 中執行升級時，就會自動偵測並移除 preview VSIX。
>
> 2. 針對 [LSP 套件](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)將 Nuget 參考更新為最新的非預覽版本。
>
> 3. 移除 VSIX 資訊清單中 Microsoft Visual Studio Language Server Protocol Preview VSIX 的相依性。
>
> 4. 請確定您的 VSIX 指定 Visual Studio 2017 15.8 版 Preview 3 作為安裝目標的下限。
>
> 5. 重建並重新部署。

### <a name="create-a-vsix-project"></a>建立 VSIX 專案

若要使用以 LSP 為基礎的語言伺服器來建立語言服務延伸模組，請先確定您已針對 VS 的實例安裝 **Visual Studio 延伸模組開發** 工作負載。

接下來，**流覽至 [**  >  **新增專案**  >  **Visual c #** 擴充性  >  **Extensibility**  >  **VSIX 專案**] 來建立新的 VSIX 專案：

![建立 vsix 專案](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>語言伺服器與執行時間安裝

根據預設，為了在 Visual Studio 中支援 LSP 型語言伺服器而建立的擴充功能，不包含語言伺服器本身或執行它們所需的執行時間。 延伸模組開發人員負責散發語言伺服器和所需的執行時間。 有幾種方式可以執行這項操作：

* 語言伺服器可以內嵌在 VSIX 中做為內容檔案。
* 建立 MSI 以安裝語言伺服器和/或需要的執行時間。
* 提供 Marketplace 通知使用者如何取得執行時間和語言伺服器的指示。

### <a name="textmate-grammar-files"></a>TextMate 文法檔

LSP 不包含如何提供語言文字顏色標示的規格。 為了在 Visual Studio 中提供語言的自訂顏色標示，延伸模組開發人員可以使用 TextMate 文法檔案。 若要加入自訂 TextMate 文法或主題檔案，請遵循下列步驟：

1. 在您的延伸模組中建立名為 "文法" 的資料夾 (或者可以是您選擇的任何名稱) 。

2. *在 [文法*] 資料夾內，包含您想要提供自訂顏色標示的任何 *\* . tmlanguage*、 *\* . plist*、 *\* . tmtheme* 或 *\* . json* 檔案。

   > [!TIP]
   > *Tmtheme* 檔案會定義範圍如何對應至 Visual Studio 分類 (命名的色彩索引鍵) 。 如需指導方針，您可以參考 *% ProgramFiles (x86) % \ Microsoft Visual Studio \\ \<version> \\ \<SKU> \Common7\IDE\CommonExtensions\Microsoft\TextMate\Starterkit\Themesg* 目錄中的 *tmtheme* 檔案。

3. 建立 *.pkgdef* 檔案，並新增類似以下的行：

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. 以滑鼠右鍵按一下檔案，然後選取 [ **屬性**]。 將 [ **組建** ] 動作變更為 [ **內容** ]，並將 [ **包含于 VSIX** ] 屬性變更為 [ **true**]。

完成上述步驟之後， *會將文法資料夾新增* 至套件的安裝目錄，作為名為 ' MyLang ' 的存放庫來源 ( ' MyLang ' 只是要去除混淆的名稱，而且可以是) 的任何唯一字串。 所有的文法 (*tmlanguage* 檔案) 和 (主題檔案中，) 在此目錄中的 *tmtheme* 檔案會被挑選為潛力，並取代 TextMate 提供的內建文法。 如果文法檔的宣告延伸符合要開啟之檔案的副檔名，TextMate 將會逐步執行。

## <a name="create-a-simple-language-client"></a>建立簡單的語言用戶端

### <a name="main-interface---ilanguageclient"></a>主要介面- [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true)

建立您的 VSIX 專案之後，將下列 NuGet 套件新增 (s) 至您的專案：

* [VisualStudio. LanguageServer. 用戶端](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> 當您在完成先前的步驟之後相依于 NuGet 套件時，也會將 Newtonsoft.Js和 StreamJsonRpc 套件新增至您的專案。 **除非您確定這些新版本將會安裝在您的延伸模組目標 Visual Studio 版本上，否則請勿更新這些套件**。 元件不會包含在您的 VSIX 中;相反地，系統會從 Visual Studio 安裝目錄中挑選它們。 如果您參考的元件版本與使用者電腦上安裝的版本不同，您的延伸模組將無法運作。

然後，您可以建立新的類別來執行 [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true) 介面，這是連接到 LSP 語言伺服器的語言用戶端所需的主要介面。

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

需要實作為的主要方法是 [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017&preserve-view=true) 和 [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017&preserve-view=true)。 當 Visual Studio 已載入您的延伸模組，而且您的語言伺服器準備好要啟動時，就會呼叫[OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017&preserve-view=true) 。 在這個方法中，您可以立即叫用 [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) 委派，以表示應該啟動語言伺服器，或者您可以進行額外的邏輯，稍後再叫用 [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) 。 **若要啟用您的語言伺服器，您必須在某個時間點呼叫 StartAsync。**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017&preserve-view=true) 是最後藉由呼叫 [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) 委派叫用的方法。 它包含啟動語言伺服器，以及建立其連接的邏輯。 必須傳回連線物件，其中包含寫入伺服器和從伺服器讀取的資料流程。 此處擲回的任何例外狀況，都會透過 Visual Studio 中的資訊列訊息來攔截並顯示給使用者。

### <a name="activation"></a>啟用

一旦執行您的語言用戶端類別之後，您必須定義兩個屬性，以定義如何將它載入 Visual Studio 並啟用：

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio 使用 [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) 來管理其擴充點。 [ [匯出](/dotnet/api/system.componentmodel.composition.exportattribute) ] 屬性會指出要 Visual Studio 此類別應挑選為擴充點，並在適當的時間載入。

若要使用 MEF，您也必須在 VSIX 資訊清單中將 MEF 定義為資產。

開啟您的 VSIX 資訊清單設計工具，然後流覽至 [ **資產** ] 索引標籤：

![新增 MEF 資產](media/lsp-add-asset.png)

按一下 [ **新增** ] 以建立新的資產：

![定義 MEF 資產](media/lsp-define-asset.png)

* **類型**： Microsoft. VisualStudio. [microsoft.visualstudio.mefcomponent]
* **來源**：目前方案中的專案
* **專案**： [您的專案]

### <a name="content-type-definition"></a>內容類型定義

目前，載入 LSP 型語言伺服器延伸模組的唯一方法是使用檔案內容類型。 也就是說，在定義 [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true)) 的語言用戶端類別 (時，您必須定義在開啟時，將會導致擴充功能載入的檔案類型。 如果未開啟任何符合您定義之內容類型的檔案，則不會載入您的延伸模組。

這是透過定義一或多個 `ContentTypeDefinition` 類別來完成：

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

在上述範例中，會針對以 *bar* 副檔名結尾的檔案建立內容類型定義。 內容類型定義的名稱為 "bar"，必須衍生自 [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017&preserve-view=true)。

新增內容類型定義之後，您可以接著定義在 language client 類別中載入語言用戶端延伸模組的時機：

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

新增 LSP 語言伺服器的支援，不需要您在 Visual Studio 中執行自己的專案系統。 客戶可以在 Visual Studio 中開啟單一檔案或資料夾，以開始使用您的語言服務。 事實上，對 LSP 語言伺服器的支援是設計成隻能在開啟的資料夾/檔案案例中運作。 如果已執行自訂專案系統，某些功能 (如設定) 將無法運作。

## <a name="advanced-features"></a>進階功能

### <a name="settings"></a>設定

有提供自訂語言伺服器特定設定的支援，但仍在改進的過程中。 設定是語言伺服器支援的特定設定，而且通常會控制語言伺服器發出資料的方式。 例如，語言伺服器可能會有所報告錯誤數目上限的設定。 延伸模組作者會定義預設值，使用者可以針對特定專案進行變更。

請遵循下列步驟，將設定的支援新增至您的 LSP 語言服務延伸模組：

1. 將 JSON 檔案新增 (例如， *MockLanguageExtensionSettings.js在* 包含設定和其預設值的專案) 上。 例如：

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. 以滑鼠右鍵按一下 JSON 檔案，然後選取 [ **屬性**]。 將 [ **組建** ] 動作變更為 [內容]，並將 [包含在 VSIX 中] 屬性變更為 [ **true**]。

3. 針對 Visual Studio Code 中的 JSON 檔案 (所定義的設定，執行 ConfigurationSections 並傳回首碼的清單，這會對應到) 上 package.js中的設定區段名稱：

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. 將 .pkgdef 檔案加入至專案 (加入新的文字檔，然後將副檔名變更為 .pkgdef) 。 .Pkgdef 檔案應該包含此資訊：

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    範例：

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. 以滑鼠右鍵按一下 .pkgdef 檔案，然後選取 [ **屬性**]。 將 [ **組建** ] 動作變更為 [ **內容** ]，並將 [ **包含于 VSIX** ] 屬性變更為 **true**。

6. 開啟 *extension.vsixmanifest* 檔案，並在 [ **資產** ] 索引標籤中新增資產：

   ![編輯 vspackage 資產](media/lsp-add-vspackage-asset.png)

   * **類型**： Microsoft. VisualStudio. VsPackage
   * **來源**：檔案系統上的檔案
   * **Path**： [ *.Pkgdef* 檔案的路徑]

### <a name="user-editing-of-settings-for-a-workspace"></a>使用者編輯工作區設定

1. 使用者會開啟包含您的伺服器所擁有之檔案的工作區。
2. 使用者會在名為 *VSWorkspaceSettings.js* 的 *vs* 資料夾中新增檔案。
3. 使用者針對伺服器提供的設定，在檔案的 *VSWorkspaceSettings.js中* 加入一行。 例如：

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>啟用診斷追蹤

您可以啟用診斷追蹤來輸出用戶端與伺服器之間的所有訊息，這在對問題進行調試時很實用。 若要啟用診斷追蹤，請執行下列動作：

1. 開啟或建立工作區設定檔 *VSWorkspaceSettings.js* (請參閱「使用者編輯工作區的設定」 ) 。
2. 在設定 json 檔案中新增下列程式程式碼：

```json
{
    "foo.trace.server": "Off"
}
```

追蹤詳細資訊有三個可能的值：

* "Off"：追蹤已完全關閉
* 「訊息」：開啟追蹤，但只會追蹤方法名稱和回應識別碼。
* "Verbose"：開啟追蹤;追蹤整個 rpc 訊息。

開啟追蹤時，內容會寫入 *%temp%\VisualStudio\LSP* 目錄中的檔案。 記錄檔會遵循命名格式 *[LanguageClientName]-[Datetime 戳記] .log*。 目前，只能針對開啟資料夾案例啟用追蹤。 開啟單一檔案以啟動語言伺服器，並沒有診斷追蹤支援。

### <a name="custom-messages"></a>自訂訊息

有一些 Api 可協助您在不屬於標準語言伺服器通訊協定的語言伺服器中傳遞和接收訊息。 若要處理自訂訊息，請在您的語言用戶端類別中執行 [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) 介面。 [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) 程式庫是用來在您的語言用戶端和語言伺服器之間傳輸自訂訊息。 由於您的 LSP 語言用戶端擴充功能就像任何其他 Visual Studio 擴充功能一樣，因此您可以決定將 LSP) 不支援的其他功能 (，以透過自訂訊息在擴充功能中使用其他 (Api Visual Studio Visual Studio) 。

#### <a name="receive-custom-messages"></a>接收自訂訊息

若要從語言伺服器接收自訂訊息，請在[ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true)上執行[CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017&preserve-view=true)屬性，並傳回知道如何處理自訂訊息的物件。 範例如下：

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

若要將自訂訊息傳送至語言伺服器，請在[ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true)上執行[AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017&preserve-view=true)方法。 當您的語言伺服器已啟動且已準備好接收訊息時，就會叫用這個方法。 [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs)物件會以參數的形式傳遞，然後您可以繼續使用[VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) api 將訊息傳送至語言伺服器。 範例如下：

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

有時，延伸模組開發人員可能會想要攔截傳送至和接收自語言伺服器的 LSP 訊息。 例如，延伸模組開發人員可能會想要改變針對特定 LSP 訊息傳送的訊息參數，或修改從 language server 針對 LSP 功能所傳回的結果 (例如完成) 。 當需要這項功能時，延伸模組開發人員可以使用 MiddleLayer API 來攔截 LSP 訊息。

每個 LSP 訊息都有自己的中介層介面可進行攔截。 若要攔截特定訊息，請建立一個類別來執行該訊息的中介層介面。 然後，在您的語言用戶端類別中執行 [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) 介面，並傳回 [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017&preserve-view=true) 屬性中物件的實例。 範例如下：

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

中介層功能仍在開發中，尚未全面完成。

## <a name="sample-lsp-language-server-extension"></a>範例 LSP 語言伺服器延伸模組

若要使用 Visual Studio 中的 LSP 用戶端 API 來查看範例延伸模組的原始程式碼，請參閱 VSSDK-擴充性-範例 [LSP 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol)。

## <a name="faq"></a>常見問題集

**我想要建立一個自訂的專案系統來補充我的 LSP 語言伺服器，以便在 Visual Studio 中提供更豐富的功能支援，該怎麼做呢？**

Visual Studio 中以 LSP 為基礎的語言伺服器支援依賴 [開啟資料夾功能](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) ，並設計為不需要自訂專案系統。 您可以遵循 [此處](https://github.com/Microsoft/VSProjectSystem)的指示來建立您自己的自訂專案系統，但某些功能（例如設定）可能無法運作。 LSP 語言伺服器的預設初始化邏輯是傳入目前開啟之資料夾的根資料夾位置，因此，如果您使用自訂的專案系統，您可能需要在初始化期間提供自訂邏輯，以確保您的語言伺服器可以正常啟動。

**如何? 新增偵錯工具支援？**

我們將在未來的版本中提供 [常見的偵錯工具通訊協定](https://code.visualstudio.com/docs/extensionAPI/api-debugging) 支援。

**如果已安裝 VS 支援的語言服務 (例如，JavaScript) ，我仍然可以安裝可提供額外 (功能的 LSP 語言伺服器延伸模組，例如 linting) ？**

是，但並非所有功能都能正常運作。 LSP 語言伺服器延伸的最終目標是要啟用 Visual Studio 原本不支援的語言服務。 您可以使用 LSP 語言伺服器來建立提供其他支援的延伸模組，但某些功能 (例如 IntelliSense) 將不會有順暢的體驗。 一般情況下，建議使用 LSP 語言伺服器擴充功能來提供新的語言體驗，而不是擴充現有的語言體驗。

**我要在哪裡發佈已完成的 LSP language server VSIX？**

請參閱 [此處](walkthrough-publishing-a-visual-studio-extension.md)的 Marketplace 指示。

## <a name="see-also"></a>另請參閱

- [新增其他語言的 Visual Studio 編輯器支援](../ide/adding-visual-studio-editor-support-for-other-languages.md)
