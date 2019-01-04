---
title: 新增語言伺服器通訊協定延伸模組 |Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ad112d34c8f23a7738137f148f00a38a27335424
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53966556"
---
# <a name="add-a-language-server-protocol-extension"></a>新增語言伺服器通訊協定延伸模組

語言伺服器通訊協定 (LSP) 是常見的通訊協定，JSON RPC v2.0，用來提供語言服務功能，以各種不同的程式碼編輯器的形式。 使用通訊協定，開發人員可以撰寫單一語言伺服器提供語言服務功能，例如 IntelliSense、 錯誤診斷中，尋找所有參考、 等，以支援 LSP 的各種程式碼編輯器。 傳統上，加入 Visual Studio 中的語言服務，透過下列方式使用 TextMate 文法檔案，提供基本的功能，例如語法反白顯示，或透過撰寫自訂的語言服務中使用完整的 Visual Studio 擴充性 Api 以提供更豐富的資料。 現在，LSP 可提供第三個選項的支援。

![Visual Studio 中的語言伺服器通訊協定服務](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>語言伺服器通訊協定

![語言伺服器通訊協定實作](media/lsp-implementation.png)

本文說明如何建立 Visual Studio 擴充功能使用 LSP 為基礎的語言伺服器。 假設您已開發的 LSP 為基礎的語言伺服器，並且只想要整合到 Visual Studio。

如需在 Visual Studio 中的支援，語言伺服器可以與用戶端通訊 (Visual Studio) 透過任何資料流為基礎的傳輸機制，例如：

* 標準輸入/輸出資料流
* 具名的管道
* 通訊端 (僅限 TCP)

LSP 和 Visual Studio 中的支援它的目的是不屬於 Visual Studio 產品的上架的語言服務。 它不是擴充現有的語言服務 （例如 C# 中) 在 Visual Studio 中。 若要擴充現有的語言，請參閱語言服務的擴充性指南 (例如["Roslyn".NET 編譯器平台](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md))。

如需有關通訊協定本身的詳細資訊，請參閱文件[此處](https://github.com/Microsoft/language-server-protocol)。

如需有關如何建立範例語言伺服器或如何將現有的語言伺服器整合到 Visual Studio Code，請參閱文件[此處](https://code.visualstudio.com/docs/extensions/example-language-server)。

## <a name="language-server-protocol-features-supported"></a>支援的語言伺服器通訊協定功能

LSP 支援下列功能在 Visual Studio 中到目前為止：

訊息 | 在 Visual Studio 中提供支援
--- | ---
初始化 | 是
初始化 | 是
關機 | 是
結束 | 是
可以呼叫 cancelRequest $/ | 是
視窗/showMessage | 是
window/showMessageRequest | 是
視窗/logMessage | 是
遙測資料/事件 |
用戶端/registerCapability |
用戶端/unregisterCapability |
workspace/didChangeConfiguration | 是
workspace/didChangeWatchedFiles | 是
工作區/符號 | 是
workspace/executeCommand | 是
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
textDocument/hover | 是
textDocument/signatureHelp | 是
textDocument/references | 是
textDocument/documentHighlight | 是
textDocument/documentSymbol | 是
textDocument/格式 | 是
textDocument/rangeFormatting | 是
textDocument/onTypeFormatting |
textDocument/definition | 是
textDocument/codeAction | 是
textDocument/codeLens |
codeLens/resolve |
textDocument/documentLink |
documentLink/resolve |
textDocument/rename | 是

## <a name="getting-started"></a>使用者入門

> [!NOTE]
> 開始使用 Visual Studio 15.8 Preview 3 為常用的語言伺服器通訊協定的支援是內建 Visual Studio。  如果您已經建置使用預覽的 LSP 延伸模組[語言伺服器用戶端 VSIX](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)版本中，它們將會停止運作後到已升級至 15.8 Preview 3 或更新版本。  您必須執行下列作業來取得您的 LSP 擴充功能，能夠再次運作：
>
> 1. 解除安裝 Microsoft Visual Studio 語言伺服器通訊協定預覽 VSIX。  從 15.8 Preview 4 開始，每次您執行升級，在 Visual Studio 中，我們會自動偵測並移除預覽 VSIX 為您在升級過程中。
>
> 2. 更新為最新的非預覽版本的 Nuget 參考[LSP 封裝](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)。
>
> 3. 在您的 VSIX 資訊清單中移除對 Microsoft Visual Studio 語言伺服器通訊協定預覽 VSIX 的相依性。
>
> 4. 請確定您的 VSIX 會做為安裝目標的下限指定 Visual Studio 15.8 Preview 3。
>
> 5. 重建並重新部署。

### <a name="create-a-vsix-project"></a>建立 VSIX 專案

若要建立語言服務延伸模組使用 LSP 為基礎的語言伺服器，首先請確定您擁有**Visual Studio 延伸模組開發**安裝您的 VS 執行個體的工作負載。

接下來，瀏覽至建立新的空白 VSIXProject**檔案** > **新專案** > **Visual C#**  >  **擴充性** > **VSIX 專案**:

![建立 vsix 專案](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>伺服器和執行階段安裝的語言

根據預設，語言伺服器本身或它們執行所需的執行階段，不會包含在 Visual Studio 中支援 LSP 為基礎的語言伺服器建立的擴充功能。 延伸模組開發人員會負責將語言伺服器與所需的執行階段。 有數種方式可以執行這項操作：

* 語言伺服器可以內嵌在 VSIX 中，內容檔案的形式。
* 建立安裝語言伺服器 MSI 和/或所需執行階段。
* 提供 Marketplace 通知使用者如何取得執行階段和語言伺服器指示。

### <a name="textmate-grammar-files"></a>TextMate 文法檔案

LSP 不包含有關如何提供文字顏色標示語言規格。 若要提供自訂的顏色標示，在 Visual Studio 中的語言，延伸模組開發人員可以使用 TextMate 文法檔案。 若要新增自訂的 TextMate 文法或佈景主題檔案，請遵循下列步驟：

1. 建立稱為 「 文法 」 您的延伸模組內的資料夾 （或它可以是任何您選擇的名稱）。

2. 內部*文法*資料夾，包含任何 *\*.tmlanguage*，  *\*.plist*，  *\*.tmtheme*，或 *\*.json*檔案您想要提供自訂的顏色標示。

3. 以滑鼠右鍵按一下檔案，然後選取**屬性**。 變更**建置**動作來**內容**並**Include in VSIX**屬性設為 true。

4. 建立 *.pkgdef*檔案，並新增一行如下所示：

   ```xml
   [$RootKey$\TextMate\Repositories]
   "MyLang"="$PackageFolder$\Grammars"
   ```

5. 以滑鼠右鍵按一下檔案，然後選取**屬性**。 變更**建置**動作來**內容**並**Include in VSIX**屬性設為 true。

完成先前步驟中之後,*文法*資料夾已新增至套件的安裝目錄，做為存放庫來源名為 'MyLang' （'MyLang' 會是用於去除混淆的名稱，而且可以是任何唯一的字串）。 所有的文法 (*.tmlanguage*檔案) 和佈景主題檔案 (*.tmtheme*檔案) 在此目錄會挑選為潛力並以其取代 TextMate 所提供的內建文法。 如果文法檔案的宣告的延伸模組符合正在開啟檔案的副檔名，TextMate 將中的步驟。

## <a name="create-a-simple-language-client"></a>建立簡單的語言，用戶端

### <a name="main-interface---ilanguageclientdotnetapimicrosoftvisualstudiolanguageserverclientilanguageclientviewvisualstudiosdk-2017"></a>主要的介面- [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

建立 VSIX 專案之後，將下列 NuGet 封裝加入專案：

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> 當您完成上述步驟之後，您可以採取的 NuGet 套件的相依性時，Newtonsoft.Json 和 StreamJsonRpc 封裝會新增至您的專案，以及。 **不要更新這些套件，除非您確定這些新的版本，將會安裝在新版 Visual Studio 的擴充功能目標**。 組件將不會包含在您的 VSIX，相反地，它們將會選取從 Visual Studio 安裝目錄。 如果您要參考的組件版本比使用者在電腦上，您的延伸模組安裝的項目新*將無法運作*。

然後，您就可以建立新的類別可實作[ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)介面、 連接到 LSP 為基礎的語言伺服器的語言用戶端所需的主要介面。

以下是範例：

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

需要實作的主要方法如下[OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017)並[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017)。 [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) Visual Studio 已載入您的擴充功能和您語言的伺服器已準備好啟動時呼叫。 在此方法中，您可以叫用[StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017)立即對語言伺服器應該啟動，或者您可以執行額外的邏輯，並叫用的委派[StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017)更新版本。 **若要啟用您語言的伺服器，您必須呼叫 StartAsync 在某個時間點。**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017)是最後叫用呼叫之方法[StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017)委派，其中包含邏輯，來啟動語言伺服器，並建立連線。 必須傳回連接物件，包含寫入至伺服器，並從伺服器讀取的資料流。 這裡擲回任何例外狀況會攔截，並顯示給使用者，透過 Visual Studio 中的資訊列訊息。

### <a name="activation"></a>啟用

一旦您語言的用戶端類別會實作，您必須定義為其定義如何它將會載入到 Visual Studio，並啟動兩個屬性：

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio 會使用[MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) 來管理其擴充性點。 [匯出](/dotnet/api/system.componentmodel.composition.exportattribute)屬性會指出 Visual studio，這個類別應該挑選擴充點，並在適當的時間載入。

若要使用 MEF，您也必須定義 MEF 為 VSIX 資訊清單中的資產。

開啟您的 VSIX 資訊清單設計工具，並瀏覽至**資產** 索引標籤：

![加入 MEF 資產](media/lsp-add-asset.png)

按一下 [新增] 建立新的資產：

![定義 MEF 資產](media/lsp-define-asset.png)

* **型別**:Microsoft.VisualStudio.MefComponent
* **來源**:目前的方案中的專案
* **專案**: [專案]

### <a name="content-type-definition"></a>內容類型定義

目前載入您的 LSP 為基礎的語言伺服器延伸模組的唯一方式是依檔案內容類型。 也就是定義您的語言用戶端類別時 (它會實作[ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017))，您必須定義類型的檔案，當開啟時，會導致您載入的延伸模組。 如果沒有符合您定義的內容類型的檔案會開啟，您的延伸模組將不載入。

這是透過定義一或多個 ContentTypeDefinition 類別：

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

在上述範例中，內容類型定義建立的檔案結尾 *.bar*副檔名。 內容類型定義指定名稱"bar"並**必須**衍生自[CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017)。

新增內容類型定義之後, 您可以接著定義何時要載入您的語言用戶端類別的語言用戶端延伸模組：

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

新增支援 LSP 語言伺服器不需要您在 Visual Studio 中實作您自己的專案系統。 客戶可以在 Visual Studio 來開始使用您的語言服務中開啟單一檔案或資料夾。 事實上，支援 LSP 語言伺服器設計用於只有在開啟的資料夾/檔案的情況下。 如果實作自訂專案系統時，某些功能 （例如設定） 將不會運作。

## <a name="advanced-features"></a>進階功能

### <a name="settings"></a>設定

支援自訂語言伺服器特定的設定可供使用，但還改進。 設定專屬於什麼語言伺服器支援和通常控制語言伺服器發出資料的方式。 例如，語言伺服器可能有報告的錯誤數目上限的設定。 延伸模組作者會定義預設值，可以變更特定專案的使用者。

請遵循下列步驟來設定的支援新增至您的 LSP 語言服務延伸模組：

1. 將 JSON 檔案 (例如*MockLanguageExtensionSettings.json*) 在您的專案，其中包含設定和其預設值。 例如: 

   ```json
   {
    "foo.maxNumberOfProblems": -1
   }
   ```
2. JSON 檔案上按一下滑鼠右鍵，然後選取**屬性**。 變更**建置**動作 「 內容 」 和 「 Include in VSIX' 屬性設為 true。

3. 實作 ConfigurationSections 並傳回 JSON 檔案中定義的設定的前置詞清單 （在 Visual Studio Code 中，這會對應至 package.json 中的組態區段名稱）：

   ```csharp
   public IEnumerable<string> ConfigurationSections
   {
      get
      {
          yield return "foo";
      }
   }
   ```

4. 加入.pkgdef 檔案至專案 （加入新的文字檔，並將副檔名變更為.pkgdef）。 Pkgdef 檔案應該包含這項資訊：

   ```xml
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
   ```

    範例：
    ```xml
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. .Pkgdef 檔上按一下滑鼠右鍵，然後選取**屬性**。 變更**建置**動作來**內容**並**Include in VSIX**屬性設為 true。

6. 開啟*source.extension.vsixmanifest*檔案，並新增中的資產**資產** 索引標籤：

   ![編輯 vspackage 資產](media/lsp-add-vspackage-asset.png)

   * **型別**:Microsoft.VisualStudio.VsPackage
   * **來源**:檔案系統上的檔案
   * **路徑**: [路徑您 *.pkgdef*檔案]

### <a name="user-editing-of-settings-for-a-workspace"></a>使用者編輯的工作區設定

1. 使用者開啟含有您的伺服器擁有的檔案的工作區。
2. 使用者新增的檔案 *.vs*稱為資料夾*VSWorkspaceSettings.json*。
3. 使用者新增至一行*VSWorkspaceSettings.json*檔案伺服器提供的設定。 例如: 

   ```json
   {
    "foo.maxNumberOfProblems": 10
   }
   ```
   ### <a name="enabling-diagnostics-tracing"></a>啟用診斷追蹤
   可以啟用診斷追蹤，以用戶端與伺服器，這有助於進行問題偵錯之間的所有訊息都輸出。  若要啟用診斷追蹤，執行下列作業：

4. 開啟或建立工作區的設定檔*VSWorkspaceSettings.json* （請參閱 「 編輯設定的工作區的使用者 」）。
5. 設定 json 檔案中加入下面這一行：

```json
{
    "foo.trace.server": "Off"
}
```

有三個可能的值，用於追蹤的詳細資訊：
* 「 關閉 」: 追蹤完全關閉
* 「 訊息 」: 追蹤開啟的追蹤，但唯一的方法名稱和回應的識別碼。
* "Verbose": 追蹤保持開啟;整個 rpc 訊息會進行追蹤。

中的檔案追蹤時開啟的內容寫入 *%temp%\VisualStudio\LSP*目錄。  記錄檔會遵循的命名格式 *[LanguageClientName]-[日期時間戳記].log*。  目前，開啟資料夾的情況下可以只會啟用追蹤。  開啟單一檔案，才能啟動語言伺服器沒有診斷追蹤支援。

### <a name="custom-messages"></a>自訂訊息

有就地來加速傳遞訊息和來自語言伺服器不屬於標準的語言伺服器通訊協定的接收訊息的 Api。 若要處理的自訂訊息，實作[ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)您語言的用戶端類別中的介面。 [VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md)程式庫用來傳輸您的語言用戶端與語言伺服器之間的自訂訊息。 因為您的 LSP 語言用戶端延伸模組，就如同任何其他 Visual Studio 擴充功能，您可以決定加入其他功能 （也就不會受到 LSP） （使用其他 Visual Studio Api） 的 Visual Studio 在您的延伸模組，透過自訂的訊息。

#### <a name="receiving-custom-messages"></a>自訂訊息接收

若要自訂從伺服器接收訊息的語言，實作[CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017)屬性上的[ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) ，並傳回物件知道如何處理您的自訂訊息. 下列範例：

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

#### <a name="sending-custom-messages"></a>傳送自訂訊息

若要將自訂的訊息傳送到語言伺服器中，實作[AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017)方法[ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)。 當您的語言伺服器已啟動且準備好接收訊息時，會叫用這個方法。 A [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs)物件會傳遞做為參數，您可以在將訊息傳送至伺服器使用的語言保持[VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) Api。 下列範例：

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

### <a name="middle-layer"></a>中間層

有時延伸模組開發人員可能想要攔截 LSP 訊息來傳送和接收自語言伺服器。 比方說，延伸模組開發人員可能想要變更特定的 LSP 訊息，傳送之訊息參數，或修改從語言伺服器 LSP 功能 （例如完成） 所傳回的結果。 當需要時，延伸模組開發人員可以使用 MiddleLayer API，以攔截 LSP 訊息。

每個 LSP 訊息有自己用於攔截的中介層介面。 若要攔截特定的訊息，建立實作該訊息的中介層介面的類別。 然後，實作[ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)程式語言的用戶端類別中介面，並傳回您物件中的執行個體[MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017)屬性。 下列範例：

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

仍在開發和並非完整的中間層功能。

## <a name="sample-lsp-language-server-extension"></a>範例 LSP 語言伺服器延伸模組

若要查看使用 LSP 用戶端 API，在 Visual Studio 中的範例延伸模組的原始程式碼，請參閱 VSSDK 擴充性範例[LSP 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol)。

## <a name="faq"></a>常見問題集

**我想要建立自訂專案系統，以補充我 LSP 語言伺服器，以提供更豐富的功能支援，在 Visual Studio 中，如何著手進行這麼做？**

Visual Studio 中的 LSP 為基礎的語言伺服器支援依賴[開啟資料夾 功能](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/)和專為需要自訂專案系統。 您可以建置自己的自訂專案系統指示[此處](https://github.com/Microsoft/VSProjectSystem)，但某些功能，例如設定，可能無法運作。 LSP 語言伺服器的預設初始化邏輯是傳入目前正開啟的資料夾的根資料夾位置，因此如果您使用的自訂專案系統時，您可能需要提供自訂邏輯以確保您的語言伺服器可以初始化期間正常啟動。

**如何新增偵錯工具支援？**

我們將提供的支援[常見偵錯通訊協定](https://code.visualstudio.com/docs/extensionAPI/api-debugging)未來的版本。

**如果已經有 VS 支援的語言安裝的服務 (例如 JavaScript)，我仍然可以安裝 LSP 語言伺服器延伸模組，提供額外功能 （例如 linting)？**

可以，但並非所有的功能將會正常運作。 LSP 語言伺服器延伸模組的終極目標是讓原本不支援 Visual Studio 的語言服務。 您可以建立擴充功能提供其他支援使用 LSP 語言伺服器，但某些功能 （例如 IntelliSense) 不會擁有順暢的體驗。 一般情況下，建議您使用 LSP 語言伺服器擴充功能用來提供新的語言體驗，不會擴充現有的。

**其中將發行我已完成的 LSP 語言伺服器 VSIX？**

請參閱 Marketplace 指示[此處](walkthrough-publishing-a-visual-studio-extension.md)。
