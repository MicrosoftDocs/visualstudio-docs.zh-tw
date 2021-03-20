---
title: '自訂 codespace (預覽) '
description: 深入瞭解如何自訂 codespace。
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: 0e23ca3255761f4d93f89251d00c12c14aecf7b9
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672347"
---
# <a name="how-to-customize-a-codespace-preview"></a>如何自訂 codespace (預覽) 

> [!Important] 
> 自2021年4月12日起，將不再支援從 Visual Studio 2019 連接到 GitHub Codespaces，且此私人預覽已結束。 我們著重于針對一組廣泛的 Visual Studio 工作負載優化的雲端式內部迴圈和 VDI 解決方案的不斷演進體驗。 我們建議您參與我們的 [開發人員社區論壇](https://developercommunity.visualstudio.com/home) ，以取得 Visual Studio 的詳細資訊，以取得未來預覽和藍圖資訊的相關資訊。 

GitHub Codespaces 在雲端提供完整的開發環境。 針對使用 Visual Studio 2019 的 Windows 型開發，GitHub Codespaces 預設實例提供很好的起點，但您也可以自訂特定專案的環境。

## <a name="installed-software"></a>安裝的軟體

Windows codespaces 隨附許多已安裝的架構和工具，可讓您立即開始使用。 下表列出所有 Windows codespace 環境中的可用應用程式和功能。

| 應用程式                                         | 路徑別名 | 版本            |
|---------------------------------------------|------------|--------------------|
| .NET                                        | N/A        | 4.8                |
| .NET Core 執行階段                           | dotnet     | 2.1、3。1           |
| .NET Core SDK                               | dotnet     | 2.1、3.1.3、3.1。4  |
| Azure CLI                                   | Az         | 2.5                |
| Chocolatey \(英文\)                                  | 崔克      | 0.10.15            |
| CMake                                       | cmake      | 3.17               |
| Git                                         | git        | 2.26               |
| Microsoft build                             | msbuild    | 16.7               |
| Microsoft SQL Server Express 版本2019   | N/A        | 15.0               |
| Ninja                                       | 忍者      | 1.8.2              |
| Node.js                                     | node       | 12.16              |
| NPM                                         | npm        | 6.14               |
| Python                                      | Python     | 3.7                |
| VC 封裝管理員                          | vcpkg      | 2020.02            |
| Windows SDK                                 | N/A        | 10.0.18362         |

上面的清單並不完整，也排除了許多 Visual Studio 安裝的工具 (例如 IISExpress) 。 元件的次要或修補程式版本也可能與上面所述的版本不同。

有關預先安裝的架構和工具的特定詳細資料，請見下文的 [ [已安裝的軟體詳細](#installed-software-specifics) 資料] 區段。

## <a name="modifications-to-a-codespace"></a>Codespace 的修改
 
一旦建立 codespace 之後，就會保存該特定 codespace 的任何變更，而 codespace 實例則可在 GitHub Codespaces 上取得。 您可以複製額外的存放庫、安裝工具和應用程式產生器，以及新增其他開發資產，即使在 codespace 暫止時，也會保留這些修改。 但是，如果您刪除 codespace，就不會有任何修改。

> [!NOTE]
> 如果您刪除 codespace，則在 codespace 中 (暫止或已認可) 的本機儲存機制變更將會遺失。 刪除 codespace 之前，請務必將存放庫變更推送到遠端位置。

使用 Visual Studio 連接到 codespace 時，您可以使用 Visual Studio 終端機來執行命令列工具。 您可以使用 PowerShell 或 Windows 命令提示字元，這兩者都是以本機系統管理員帳戶提升許可權。 若要深入瞭解 Visual Studio 終端機，請參閱 [Visual Studio 終端機公告 blog](https://devblogs.microsoft.com/visualstudio/say-hello-to-the-new-visual-studio-terminal/)。

## <a name="customize-a-codespace"></a>自訂 codespace

GitHub Codespaces 的真正價值，在於您可以在雲端中建立獨特且可重複的開發環境，並為您自己的工作以及小組進行量身打造。 藉由建立預設的 GitHub Codespaces 實例，您可以自訂建立新 codespace 時所安裝和設定的內容。

接下來的幾節將說明使用 *.devcontainer.json* 和 *.devinit.js* 檔案的兩個 codespace 設定方法。 這些檔案可讓您設定 codespace 的安裝架構和工具，並在將其新增至您的存放庫時，根據您的存放庫建立 codespace 的任何人都有相同的遠端開發環境。

## <a name="customize-with-devcontainerjson"></a>使用 devcontainer.js自訂

建立 codespace 時，GitHub Codespaces 會尋找存放庫根目錄中的檔案 [*devcontainers.js*](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) ，並使用中的設定來自訂 codespace 或連接到它的用戶端實例 (瀏覽器基底編輯器、Visual Studio 或 Visual Studio Code) 。 大部分的 *devcontainer.js* 設定都適用于以 Linux 為基礎的 codespaces 或其他兩個用戶端，但有些則適用于 Windows codespaces 和 Visual Studio。

檔案 *上的devcontainer.js* 可以放在存放庫中的兩個位置之一：

1. *{存放庫-根目錄}/.devcontainer.js開啟*
2. *{存放庫-根目錄}/.devcontainer/devcontainer.js于*

GitHub Codespaces 支援屬性上的下列 *devcontainer.js* 。 如果您想要與其他用戶端連線到您的 codespace，以及 Visual Studio 以外的其他用戶端，則設定 Visual Studio Code 特定屬性會很有用。 

* `extensions` -應安裝 [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/vscode) 延伸模組的陣列。
* `settings`  -一組要套用的 [Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings) 設定。
* `forwardPorts`-當 codespace 正在執行時，應在本機自動轉寄的埠或埠陣列。
* `postCreateCommand` -在建立 codespace 之後要執行的命令字串或命令引數清單。

> [!NOTE]
> 檔案 **上的devcontainer.js** 也用來支援 Visual Studio Code [遠端開發](https://code.visualstudio.com/docs/remote/remote-overview)，並且具有本檔未涵蓋的其他屬性。 您可以安全地將這些額外的屬性新增至檔案，但 Codespaces 會忽略這些屬性。 如需詳細資訊，請參閱 code.visualstudio.com [ 上的參考devcontainer.js](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) 。

## <a name="customize-with-devinit"></a>使用 devinit 自訂

[devinit](../../devinit/getting-started-with-devinit.md) 是 Windows codespaces 中包含的命令列工具，可讓您將架構和工具安裝到您的環境中。 您可以從命令提示字元以手動方式執行 (`devinit run -t require-dotnetcoresdk`) 但其真正的威力在於建立檔案的自訂 [ *.devinit.js*](../../devinit/devinit-json.md) ，以便在每次建立時一致地設定 codespace。

`devinit` 包含一組用來安裝特定專案的工具，例如 SQL Server 和 Azure CLI，以及執行一般套件管理員（例如 chocolatey、npm 和 vcpkg）。 您可以 `devinit` 在 [ [可用的工具](../../devinit/devinit-tool-list.md) ] 檔中找到完整的工具清單。

### <a name="devinitjson"></a>devinit.js開啟

雖然您可以直接執行 `devinit` 命令列，但建議您在設定檔 [*上建立devinit.js*](../../devinit/devinit-json.md) ，以描述 `devinit` 要執行的工具組。 

例如，若要安裝 [.NET Core SDK](/dotnet/core/sdk)， *.devinit.js* 會顯示如下：

```json
{
    "run": [
        {
            "comments": "We need the .NET Core SDK."
            "tool": "require-dotnetcoresdk"
        }
    ]
}
```

當您在專案的根目錄中撰寫 *.devinit.js* 檔案時，它會在您執行時使用 `devinit init` 。 依預設，會 `devinit.exe` 在下列位置尋找檔案：

1. *{目前的目錄} \\.devinit.js開啟*
2. *{目前的目錄} \\.devinit\devinit.js開啟*

### <a name="running-devinit-when-creating-a-codespace"></a>建立 codespace 時執行 devinit

您可以 `devinit` 使用 `postCreateCommand` *devcontainers.json* 檔案中的屬性，指示 GitHub Codespaces 在 codespace 建立之後執行。 如上所述，GitHub Codespaces 會尋找您所複製存放庫中的檔案 *devcontainer.js* ，以便自訂 codespace 或用戶端實例，並將執行屬性中所述的任何命令 `postCreateCommand` 。

藉由指定 `devinit init` ， `devinit` 將會使用您 *的devinit.js* 設定來執行。

```json
{
  "postCreateCommand": "devinit init"
}
```

### <a name="an-example"></a>範例

以下是安裝 .NET Core Entity Framework 命令列工具的簡單範例 `dotnet-ef` 。

**devcontainer.json**

存放庫根目錄中檔案 *.devcontainer.js* 的內容。 

```json
{
  "postCreateCommand": "devinit init"
}
```

**devinit.js開啟**

檔案 *.devinit.js* 的內容。 此檔案必須位於與 *.devcontainer.js* 的相同資料夾中。

```json
{
    "run": [
        {
            "comments": "Install the Entity Framework tools",
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
        }
     ]
}
```

您可以 `devinit` 在 `devinit` [範例清單](../../devinit/sample-readme.md)中找到更多範例。

## <a name="port-forwarding"></a>連接埠轉送

GitHub Codespaces 可讓您透過埠轉送來存取遠端環境中執行的應用程式和服務。 基於安全性考慮，預設不會轉送任何埠。 不過，您可以指定要在 codespace 中開啟的特定埠。

### <a name="configure-port-forwarding"></a>設定連接埠轉送

如果有一或多個埠應該依預設針對指定的存放庫轉送，可以使用屬性在的 *devcontainer.js* 中設定 `forwardPorts` 。

* `forwardPorts` -當環境正在執行時，應在本機自動轉寄的埠或埠陣列。

## <a name="installed-software-specifics"></a>已安裝的軟體細節

### <a name="microsoft-sql-server"></a>Microsoft SQL Server

Microsoft SQL Server 2019 Express 版本可供使用，並以本機服務的形式執行， (localdb) 在 Windows Codespace 環境中運作。 目前的使用者（即您的應用程式和 Visual Studio 終端機執行身分）具有 SQL server 的 SQL 系統管理員許可權。 若要管理伺服器，您必須在 Visual Studio 終端機或其他命令列工具（例如）中使用 PowerShell `dotnet-ef` 。 目前無法使用 SQL Server Management Studio 和其他遠端系統管理工具。

#### <a name="example-connection-string"></a>範例連接字串

以下是連接到本機 MS SQL server 的連接字串範例。

```csharp
"Server=(LocalDB);Integrated Security=true;"
```

### <a name="azure-cli"></a>Azure CLI

Azure CLI 安裝在所有 Windows Codespace 環境中，而且可在 path as 上使用 `az` 。

#### <a name="using-azure-resources"></a>使用 Azure 資源

如果您使用 Azure Active Directory 身分識別對 Azure 資源驗證應用程式，您必須先從 Visual Studio 終端機登入 Azure。 若要登入，請使用 Azure CLI `login` 命令搭配裝置登入流程 (，如下列範例所示) 。 登入之後，您的應用程式和終端機會話應能使用該身分識別。

```powershell
> az login --use-device-code
```

您可以從 `az login` Azure CLI [檔](/cli/azure/reference-index#az_login)中的命令進一步瞭解。

## <a name="see-also"></a>另請參閱

- [什麼是 GitHub Codespaces？](codespaces-overview.md)
- [如何搭配 codespace 使用 Visual Studio](use-visual-studio-with-codespaces.md)