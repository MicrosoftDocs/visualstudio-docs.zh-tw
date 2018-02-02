---
title: "加入語言伺服器通訊協定的延伸 |Microsoft 文件"
ms.custom: 
ms.date: 11/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 98bbebfb5f82d10179897e94b6a49cbb3d8c6220
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="adding-a-language-server-protocol-extension"></a>加入語言伺服器通訊協定的延伸

語言伺服器通訊協定 (LSP) 是常見的通訊協定，JSON RPC v2.0，用來提供語言服務功能，以各種不同的程式碼編輯器的形式。 使用通訊協定，開發人員可以撰寫單一語言提供語言服務功能，如 IntelliSense、 錯誤診斷、 尋找所有參考、 以各種不同的程式碼編輯器支援 LSP 等伺服器。 傳統上，加入 Visual Studio 中的語言服務，透過使用 TextMate 文法檔案來提供基本功能，例如語法反白顯示，或撰寫自訂語言服務使用完整的 Visual Studio 擴充性 Api 集至提供更多的資料。 現在，LSP 提供第三個選項的支援。

![Visual Studio 中的語言伺服器通訊協定服務](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>語言伺服器通訊協定

如需有關通訊協定本身的詳細資訊，請參閱文件[這裡](https://github.com/Microsoft/language-server-protocol)。 Visual Studio 語言伺服器通訊協定實作處於預覽狀態，並支援應該被視為實驗性。 預覽版本為延伸模組的格式 ([語言伺服器通訊協定用戶端預覽](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview))，**但這項擴充功能只能安裝在預覽通道 Visual Studio 的**。 較新版的 Visual Studio 會包含內建支援語言伺服器通訊協定，此時預覽旗標皆會予以捨棄。 **您不應該使用預覽，生產環境中使用。**

如需有關如何建立範例語言伺服器或如何將現有的語言伺服器整合到 Visual Studio 程式碼，請參閱文件[這裡](https://code.visualstudio.com/docs/extensions/example-language-server)。

![語言伺服器通訊協定的實作](media/lsp-implementation.png)

本文說明如何建立使用 LSP 為基礎的語言伺服器的 Visual Studio 延伸模組。 它會假設您已開發 LSP 為基礎的語言伺服器，而且只想要將它整合到 Visual Studio。

如需支援 Visual Studio 中，語言伺服器可以透過下列機制 (Visual Studio) 用戶端與通訊：

* 標準輸出資料流
* 具名的管道
* 通訊端

LSP 和支援的 Visual Studio 中的用意是不屬於 Visual Studio 產品的上架的語言服務。 它不是擴充語言中現有的服務 （例如 C#) Visual Studio。 若要擴充現有的語言，請參閱語言服務的擴充性指南 (例如， ["Roslyn".NET 編譯器平台](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md))。

## <a name="language-server-protocol-features-supported"></a>支援的語言伺服器通訊協定功能

LSP 支援下列功能在 Visual Studio 中為止：

訊息 | 在 Visual Studio 中有支援
--- | ---
初始化 | 是
初始化 | 
關機 | 是
結束 | 是
$/cancelRequest | 是
window/showMessage | 是
window/showMessageRequest | 是
window/logMessage | 是
遙測/事件 |
client/registerCapability |
client/unregisterCapability |
workspace/didChangeConfiguration | 是
workspace/didChangeWatchedFiles | 是
workspace/symbol | 是
workspace/executeCommand | 是
workspace/applyEdit | 是
textDocument/publishDiagnostics | 是
textDocument/didOpen | 是
textDocument/didChange | 是
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave |
textDocument/didClose | 是
textDocument/completion | 是
completion/resolve | 是
textDocument/hover |
textDocument/signatureHelp |
textDocument/references | 是
textDocument/documentHighlight |
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

## <a name="getting-started"></a>快速入門

### <a name="create-a-vsix-project"></a>建立 VSIX 專案

若要建立語言服務的擴充功能，使用 LSP 為基礎的語言伺服器，首先請確定您有**Visual Studio 擴充功能開發**安裝 VS 執行個體的工作負載。

下一步瀏覽至建立新的空白 VSIXProject**檔案** > **新專案** > **Visual C#**  >  **擴充性** > **VSIX 專案**:

![建立 vsix 專案](media/lsp-vsix-project.png)

針對預覽版本，VS 支援 LSP 會 VSIX 格式 ([Microsoft.VisualStudio.LanguageServer.Client.Preview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview))。 擴充功能開發人員想要建立使用 LSP 語言伺服器擴充功能必須依賴此 VSIX。 因此，想要安裝語言伺服器擴充功能的客戶**必須先安裝語言伺服器通訊協定的用戶端預覽 VSIX。**

若要定義 VSIX 相依性，您的 VSIX 的 VSIX 資訊清單設計工具 （按兩下開啟 source.extension.vsixmanifest 檔案中，您的專案中），並瀏覽至**相依性**:

![將參考加入至語言伺服器通訊協定的用戶端](media/lsp-reference-lsp-dependency.png)

建立新的相依性，如下所示：

![定義語言伺服器通訊協定用戶端相依性](media/lsp-define-lsp-dependency.png)

* **來源**： 手動定義
* **名稱**： 語言伺服器通訊協定用戶端預覽
* **Identifier**: Microsoft.VisualStudio.LanguageServer.Client.Preview
* **版本範圍**: [1.0,2.0)
* **相依性解析方式**： 使用者安裝
* **下載 URL**: [https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)

> [!NOTE]
> **下載 URL**必須填入以便安裝您的擴充功能的使用者知道如何安裝必要的相依性。

### <a name="language-server-and-runtime-installation"></a>伺服器和執行階段安裝的語言

根據預設，建立以 LSP 為基礎的語言伺服器支援 Visual Studio 中的擴充功能不會包含語言伺服器本身或執行它們所需的執行階段。 擴充功能開發人員必須負責發佈語言伺服器及所需的執行階段。 有數種方式，若要這樣做：

* 語言伺服器可以內嵌在 VSIX 中，為內容檔案。
* 建立 MSI 安裝語言伺服器和/或所需執行階段。
* 提供有關指示 Marketplace 通知使用者如何取得執行階段和語言的伺服器。

### <a name="textmate-grammar-files"></a>TextMate 文法檔案

LSP 不包含有關如何提供文字的顏色標示語言規格。 若要提供自訂的顏色標示語言 Visual Studio 中，擴充功能開發人員可以使用的 TextMate 文法檔案。 若要加入自訂的 TextMate 文法或佈景主題檔案，請遵循下列步驟：

1. 建立一個稱為 「 文法 」 在您的擴充功能資料夾 （或它可以是任何您所選擇的名稱）。

2. 在 「 文法 」 資料夾，資料夾會包含您想要提供自訂的顏色標示 *.tmlanguage 或 *.tmtheme 檔案。

3. 以滑鼠右鍵按一下檔案，然後選取**屬性**。 變更的建置動作**內容**和**包含在 VSIX 中的**屬性設定為 true。

4. 建立.pkgdef 檔案，並加入至這個相似的一行：

  ```xml
  [$RootKey$\TextMate\Repositories]
  "MyLang"="$PackageFolder$\Grammars"
  ```

5. 以滑鼠右鍵按一下檔案，然後選取**屬性**。 變更的建置動作**內容**和**包含在 VSIX 中的**屬性設定為 true。

「 文法 」 資料夾新增至套件的安裝後完成上述步驟，做為儲存機制來源目錄名為 'MyLang' （'MyLang' 會是名稱以便釐清，而且可以是任何唯一的字串）。 所有的文法 （.tmlanguage 檔案） 和這個目錄中的佈景主題檔案 （.tmtheme 檔案） 做為 potentials 挑選並以其取代內建提供 TextMate 的文法。 如果文法檔案宣告的延伸模組符合正在開啟檔案的副檔名，TextMate 將步驟。

## <a name="creating-a-simple-language-client"></a>建立簡單的語言用戶端

### <a name="main-interface---ilanguageclientdotnetapimicrosoftvisualstudiolanguageserverclientilanguageclientviewvisualstudiosdk-2017"></a>主要介面為[ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

建立 VSIX 專案之後，將下列 NuGet 封裝加入至專案：

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> 當您完成上述步驟之後，您可以採取 NuGet 封裝上的相依性時，Newtonsoft.Json 和 StreamJsonRpc 套件即會新增至您的專案，以及。 **除非您確定這些新的版本將會安裝 Visual Studio 版本不更新這些套件的擴充功能目標**。 組件將不會包含在您的 VSIX-相反地，它們將會挑選從 Visual Studio 安裝目錄。 如果您要參考的組件比使用者在電腦上，您的擴充功能安裝新的版本*將無法運作*。

然後，您可以建立新的類別可實作[ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)介面、 連接至 LSP 為基礎的語言伺服器語言用戶端所需的主要介面。

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
            await StartAsync?.InvokeAsync(this, EventArgs.Empty);
        }
    }
}
```

必須實作的主要方法為[OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017)和[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017)。 [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) Visual Studio 已載入您的擴充功能，語言伺服器準備好可以啟動時呼叫。 在這種方法，您可以叫用[StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017)立即要表示應該啟動語言伺服器，或者您可以執行額外的邏輯，並叫用委派[StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017)更新版本。 **若要啟用您語言的伺服器，您必須呼叫 StartAsync 在某個時間點。**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017)是最後叫用呼叫的方法[StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017)委派，其中包含邏輯，來啟動語言伺服器並建立其連線。 必須傳回連接物件，包含伺服器寫入及讀取來自伺服器的資料流。 攔截到這裡擲回任何例外狀況，並透過 Visual Studio 中的資訊列訊息的使用者顯示。

### <a name="activation"></a>啟用

一旦您語言的用戶端類別實作時，您必須定義為它定義如何它會載入到 Visual Studio，並啟動兩個屬性：

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio 會使用[MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) 來管理其擴充點。 [匯出](https://msdn.microsoft.com/library/system.componentmodel.composition.exportattribute(v=vs.110).aspx)屬性會指出 Visual studio，這個類別應該收取擴充點，然後在適當的時間載入。

若要使用 MEF，您也必須定義 MEF 為 VSIX 資訊清單中的資產。

開啟您的 VSIX 資訊清單設計工具，並瀏覽至**資產** 索引標籤：

![加入 MEF 資產](media/lsp-add-asset.png)

按一下 [新增] 建立新的資產：

![定義 MEF 資產](media/lsp-define-asset.png)

* **型別**: Microsoft.VisualStudio.MefComponent
* **來源**： 目前的方案中的專案
* **專案**: [專案]

### <a name="content-type-definition"></a>內容類型定義

目前載入 LSP 為基礎的語言的伺服器延伸模組的唯一方式是依檔案內容類型。 也就是定義您語言的用戶端類別時 (它會實作[ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017))，您必須定義類型的檔案，開啟時，會導致您載入的延伸模組。 如果不符合您定義的內容類型的檔案會開啟，您的擴充功能將不載入。

這會透過定義一個或多個 ContentTypeDefinition 類別：

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

在上述範例中，將內容類型定義建立檔案的結尾`.bar`檔案副檔名。 內容類型定義會指定名稱 「 列 」 和**必須**衍生自[CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017)。

之後加入內容類型定義，您可以定義當載入語言用戶端類別中的程式語言用戶端延伸模組：

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

新增支援 LSP 語言伺服器不需要您在 Visual Studio 中實作您自己的專案系統。 客戶可以使用您語言服務的 Visual Studio 中開啟單一檔案或資料夾。 事實上，支援主要是為了 LSP 語言伺服器只有在開啟的資料夾/檔案的情況下運作。 如果實作自訂專案系統時，某些功能 （例如設定） 將不會運作。

## <a name="advanced-features"></a>進階的功能

### <a name="settings"></a>設定

支援自訂語言伺服器特有設定適用於 LSP 支援在 Visual Studio 中的預覽版本，但它仍然正在被提升。 設定專屬於哪些語言伺服器支援，並通常控制語言伺服器發出資料的方式。 例如，語言伺服器可能報告的錯誤數目上限設定。 延伸模組作者會定義預設值，可以變更特定專案的使用者。

請遵循這些步驟來加入 LSP 語言服務延伸模組的支援設定：

1. 將 JSON 檔案 (例如，"MockLanguageExtensionSettings.json 」) 加入專案，其中包含設定和其預設值。 例如: 

  ```json
  {
    "foo.maxNumberOfProblems": -1
  }
  ```
2. JSON 檔案上按一下滑鼠右鍵，然後選取**屬性**。 變更**建置**「 內容 」 的動作，「 在 VSIX 中的包含 ' 屬性設定為 true。

3. 實作 ConfigurationSections 並傳回清單的前置詞的 JSON 檔案中定義的設定 （在 Visual Studio 程式碼，這會對應到 package.json 中的組態區段名稱）：

  ```csharp
  public IEnumerable<string> ConfigurationSections
  {
      get
      {
          yield return "foo";
      }
  }
  ```
4. 加入.pkgdef 檔案加入專案 （加入新的文字檔會將副檔名變更為.pkgdef）。 Pkgdef 檔案應該包含此項資訊：

  ```xml
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
  ```

5. .Pkgdef 檔上按一下滑鼠右鍵，然後選取**屬性**。 變更**建置**動作來 「 內容 」 及 「 包含在 VSIX"屬性設定為 true。

6. 開啟 [`source.extension.vsixmanifest`檔案，然後加入中的資產**資產**] 索引標籤：

  ![編輯 vspackage 資產](media/lsp-add-vspackage-asset.png)

  * **Type**: Microsoft.VisualStudio.VsPackage
  * **來源**： 在檔案系統上的檔案
  * **路徑**: [pkgdef 檔案的路徑]

### <a name="user-editing-of-settings-for-a-workspace"></a>使用者編輯的工作區的設定

1. 使用者開啟工作區中包含您的伺服器擁有的檔案。
2. 使用者將檔案加入名為"VSWorkspaceSettings.json"的".vs"資料夾中。
3. 使用者會將行加入 VSWorkspaceSettings.json 檔案伺服器提供的設定。 例如: 

  ```json
  {
    "foo.maxNumberOfProblems": 10
  }
  ```
### <a name="enabling-diagnostics-tracing"></a>啟用診斷追蹤
輸出之間的用戶端和伺服器，進行問題偵錯時很有用的所有訊息，可以啟用診斷追蹤。  若要啟用診斷追蹤，執行下列作業：

1. 開啟或建立工作區設定檔案"VSWorkspaceSettings.json"（請參閱 「 使用者編輯的工作區的設定 」）。
2. 設定 json 檔案中加入下行：

```json
{
    "foo.server.trace": "Off"
}
```

有三個可能的值為追蹤的詳細資訊：
* 「 關閉 」: 追蹤完全關閉
* "Messages": 追蹤開啟的追蹤，但是唯一的方法名稱和回應的識別碼。
* "Verbose": 開啟，追蹤整個 rpc 訊息會進行追蹤。

"%Temp%\visualstudio\lsp"目錄中的檔案會寫入追蹤時開啟內容。  記錄檔會遵循的命名格式`[LanguageClientName]-[Datetime Stamp].log`。  目前，可以只啟用追蹤，開啟資料夾的案例。  開啟單一檔案，才能啟動語言伺服器不具有診斷追蹤支援。

### <a name="custom-messages"></a>自訂訊息

沒有應用程式開發介面就地為了傳送訊息和來自語言伺服器不屬於標準語言伺服器通訊協定接收訊息。 若要處理的自訂訊息，實作[ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)語言用戶端類別中的介面。 [VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md)程式庫用來傳輸您的語言用戶端和伺服器語言之間的自訂訊息。 因為 LSP 語言用戶端延伸模組，就如同任何其他 Visual Studio 擴充功能，您可以決定加入其他功能 （也就不會受到 LSP） （使用其他 Visual Studio Api） 的 Visual Studio 在您的擴充功能，透過自訂訊息。

#### <a name="receiving-custom-messages"></a>接收的自訂訊息

若要自訂的訊息接收語言伺服器中，實作[CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017)屬性[ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)及傳回物件知道如何處理您的自訂訊息. 下列範例：

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

若要將自訂訊息傳送至語言伺服器中，實作[AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017)方法[ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)。 當語言伺服器已啟動且備妥要接收訊息時，會叫用這個方法。 A [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs)物件會傳遞做為參數，您可以在將訊息傳送至語言伺服器使用保留[VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md)應用程式開發介面。 下列範例：

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
```

### <a name="middle-layer"></a>中介層

有時候擴充功能開發人員可能想要攔截 LSP 訊息傳送和接收來自語言伺服器。 比方說，擴充功能開發人員可能想要變更的特定 LSP 訊息，傳送的訊息參數，或修改語言伺服器 LSP 的功能 （例如完成） 所傳回的結果。 當需要時，擴充功能開發人員可以使用 MiddleLayer API，以攔截 LSP 訊息。

每個 LSP 訊息都有它自己的中介層介面，用於攔截。 若要攔截特定的訊息，建立實作該訊息的中介層介面的類別。 然後，實作[ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017)介面語言用戶端類別中，並傳回中的物件執行個體[MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017)屬性。 下列範例：

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
```

仍在開發而並非完整的中間層功能。

## <a name="sample-lsp-language-server-extension"></a>範例 LSP 語言伺服器延伸模組

若要查看使用 LSP 用戶端應用程式開發介面，在 Visual Studio 中的範例延伸模組的原始程式碼，請參閱 VSSDK 擴充性範例[LSP 範例](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol)。

## <a name="faq"></a>常見問題集

**我想要建立自訂專案系統，以補充我 LSP 語言伺服器，以提供更豐富的功能支援，在 Visual Studio 中，我該怎麼，？**

Visual Studio 中的 LSP 為基礎的語言伺服器支援依賴[開啟資料夾功能](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/)和專為需要自訂專案系統。 您可以建立自己的自訂專案系統指示[這裡](https://github.com/Microsoft/VSProjectSystem)，但某些功能，例如設定，可能無法運作。 LSP 語言伺服器的預設初始化邏輯是傳入開啟目前，資料夾的根資料夾位置，因此，如果您使用自訂專案系統，您可能需要提供自訂邏輯以確保您的語言伺服器可以初始化期間正常啟動。

**如何新增偵錯工具支援？**

我們將提供的支援[常見偵錯通訊協定](https://code.visualstudio.com/docs/extensionAPI/api-debugging)未來的版本。

**如果已經有與支援的語言安裝的服務 (例如 JavaScript)，我仍然可以安裝 LSP 語言伺服器延伸模組，提供額外的功能 （例如 linting)？**

是，但並非所有功能將會正常運作。 LSP 語言伺服器延伸模組的最終目標是啟用原本不受 Visual Studio 支援的語言服務。 您可以建立延伸模組可提供其他支援使用 LSP 語言伺服器，但某些功能 （例如 IntelliSense) 不會流暢的體驗。 一般情況下，建議 LSP 語言伺服器擴充功能，用於提供，不會擴充現有的新語言體驗。

**其中將發行我已完成的 LSP 語言伺服器 VSIX？**

請參閱 Marketplace 指示[這裡](walkthrough-publishing-a-visual-studio-extension.md)。
