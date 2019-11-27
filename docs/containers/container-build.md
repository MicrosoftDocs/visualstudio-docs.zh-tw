---
title: Visual Studio 容器工具組建和 debug 總覽
author: ghogen
description: 容器工具組建和偵錯工具的總覽
ms.author: ghogen
ms.date: 11/20/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 6b96f23bc7bcd7e6d970025b23f89f572d07daf1
ms.sourcegitcommit: e825d1223579b44ee2deb62baf4de0153f99242a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2019
ms.locfileid: "74473997"
---
# <a name="build-and-debug-containerized-apps-using-visual-studio-or-the-command-line"></a>使用 Visual Studio 或命令列建立和偵測容器化應用程式

無論您是從 Visual Studio IDE 建立，或是設定命令列組建，都必須知道 Visual Studio 組建如何使用 Dockerfile 來建立您的專案。  基於效能考慮，Visual Studio 會遵循容器化應用程式的特殊流程。 當您藉由修改 Dockerfile 自訂您的組建流程時，瞭解 Visual Studio 組建專案的方式特別重要。

當 Visual Studio 建立不使用 Docker 容器的專案時，它會在本機電腦上叫用 MSBuild，並在本機方案資料夾下的資料夾（通常是 `bin`）中產生輸出檔案。 不過，針對容器化的專案，組建程式會考慮 Dockerfile 的指示來建立容器化應用程式。 Visual Studio 使用的 Dockerfile 會分成多個階段。 此程式依賴 Docker 的*多階段組建*功能。

## <a name="multistage-build"></a>多階段組建

多階段組建功能有助於讓容器的建立作業更有效率，並讓容器只包含應用程式在執行時間所需的位，使其變得更小。 多階段 build 用於 .NET Core 專案，而不是 .NET Framework 專案。

多階段組建可讓您在產生中繼映射的階段中建立容器映射。 例如，假設 Visual Studio 產生的一般 Dockerfile，`base`第一個階段：

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Dockerfile 中的程式碼會從 Microsoft Container Registry （mcr.microsoft.com）中的 Nano Server 映射開始，並建立可公開端口80和443的中繼映射 `base`，並將工作目錄設定為 `/app`。

下一個階段是 `build`，如下所示：

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

您可以看到 `build` 階段是從登錄的不同原始映射（`sdk` 而不是 `aspnet`）開始，而不是從基底繼續進行。  `sdk` 的映射具有所有組建工具，因此它會比 aspnet 映射大得多，因為它只包含執行時間元件。 當您查看 Dockerfile 的其餘部分時，使用個別影像的原因會變得很清楚：

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

最後一個階段會從 `base`重新開始，並包含 `COPY --from=publish` 將已發行的輸出複製到最終的映射。 此程式可讓最終影像變得很小，因為它不需要包含 `sdk` 映射中的所有組建工具。

## <a name="faster-builds-for-the-debug-configuration"></a>更快速的 Debug 設定組建

有數項優化可 Visual Studio 執行，協助處理容器化專案的組建程式效能。 容器化應用程式的組建流程並不簡單，只要遵循 Dockerfile 中所述的步驟即可。 在容器中建立的速度會比在本機電腦上建立的速度慢很多。  因此，當您在**Debug**設定中建立時，Visual Studio 實際上會在本機電腦上建立您的專案，然後使用磁片區掛接將輸出檔案夾共用至容器。 已啟用此優化的組建稱為*快速*模式組建。

在**快速**模式中，Visual Studio 會以指示 Docker 只建立 `base` 階段的引數來呼叫 `docker build`。  Visual Studio 會處理其餘的進程，而不考慮 Dockerfile 的內容。 因此，當您修改 Dockerfile （例如自訂容器環境或安裝其他相依性）時，您應該在第一個階段中進行修改。  在 Dockerfile 的 `build`、`publish`或 `final` 階段中的任何自訂步驟都不會執行。

只有當您在**Debug**設定中建立時，才會發生此效能優化。 在**發行**設定中，組建會依照 Dockerfile 中指定的方式出現在容器中。

如果您想要在 Dockerfile 指定時停用效能優化和組建，請在專案檔中將**ContainerDevelopmentMode**屬性設定為 [**一般**]，如下所示：

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

若要還原效能優化，請從專案檔中移除屬性。

## <a name="building-from-the-command-line"></a>從命令列建立

您可以使用 `docker build` 或 `MSBuild`，從命令列建立。

### <a name="docker-build"></a>docker 組建

若要從命令列建立容器化解決方案，您通常可以針對方案中的每個專案使用命令 `docker build <context>`。 您會提供*組建內容*引數。 Dockerfile 的*組建內容*是本機電腦上的資料夾，用來做為產生映射的工作資料夾。 例如，當您將檔案複製到容器時，它就是您複製檔案的資料夾。  在 .NET Core 專案中，使用包含方案檔（.sln）的資料夾。  以相對路徑表示，此引數通常會是 "：" （代表專案資料夾中的 Dockerfile），以及其父資料夾中的方案檔。  針對 .NET Framework 專案，組建內容是專案資料夾，而不是方案資料夾。

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

針對 .NET Framework 專案所建立 Visual Studio 的 dockerfile （以及 Visual Studio 2017 Update 4 之前的 Visual Studio 版本所建立的 .NET Core 專案），都不是多階段 Dockerfile。  這些 Dockerfile 中的步驟不會編譯您的程式碼。  相反地，當 Visual Studio 建立 .NET Framework Dockerfile 時，它會先使用 MSBuild 編譯您的專案。  當此動作成功時，Visual Studio 會建立 Dockerfile，這會直接將 MSBuild 的組建輸出複製到產生的 Docker 映射。  由於編譯器代碼的步驟不包含在 Dockerfile 中，因此您無法從命令列使用 `docker build` 建立 .NET Framework 的 Dockerfile。 您應該使用 MSBuild 來建立這些專案。

若要建立單一 docker 容器專案的映射，您可以使用 MSBuild 搭配 `/t:ContainerBuild` 命令選項。 例如：

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

當您從 Visual Studio IDE 建立方案時，您會看到類似于 [**輸出**] 視窗中所顯示的輸出。 請一律使用 `/p:Configuration=Release`，因為在 Visual Studio 使用多階段組建優化的情況下，建立**Debug**設定時的結果可能不會如預期般執行。

如果您使用 Docker Compose 專案，請使用命令來建立映射：

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="project-warmup"></a>專案準備

這些是為專案選取 Docker 設定檔時所發生的一連串步驟（也就是在載入專案或新增 Docker 支援時），以便改善後續執行的效能（**f5**或**Ctrl**+**f5**）。 這可在 **工具**  > **選項** 下設定 > **容器工具**。 以下是在背景執行的工作：

- 檢查 Docker Desktop 是否已安裝且正在執行。
- 確定 Docker Desktop 已設定為與專案相同的作業系統。
- 在 Dockerfile 的第一個階段中提取映射（大部分 Dockerfile 中的 `base` 階段）。  
- 建立 Dockerfile 並啟動容器。

只有**快速**模式才會進行準備，因此執行中的容器將會掛接應用程式資料夾磁片區，而且對應用程式所做的任何變更都不應使容器失效。 因此可大幅改善偵錯工具效能，並縮短長時間執行工作（例如提取大型映射）的等候時間。

## <a name="volume-mapping"></a>磁片區對應

若要在容器中工作的偵錯工具，Visual Studio 使用磁片區對應，從主機電腦對應偵錯工具和 NuGet 資料夾。 以下是裝載于容器中的磁片區：

|||
|-|-|
| **遠端偵錯程式** | 包含在容器中執行偵錯工具所需的位（視專案類型而定）。 詳細說明請見 |[[調試](#debugging)] 區段中的詳細資料。
| **應用程式資料夾** | 包含 Dockerfile 所在的專案資料夾。|
| **源資料夾** | 包含傳遞至 Docker 命令的組建內容。|
| **NuGet 封裝資料夾** | 包含從專案中的*obj\{專案} .props*檔案中讀取的 NuGet 封裝和回溯資料夾。 |

針對 ASP.NET 核心 web 應用程式，可能會有兩個額外的 SSL 憑證資料夾和使用者密碼，在下一節中會有更詳細的說明。

## <a name="ssl-enabled-aspnet-core-apps"></a>已啟用 SSL 的 ASP.NET Core 應用程式

Visual Studio 中的容器工具支援使用 dev 憑證來對具備 SSL 功能的 ASP.NET 核心應用程式進行程式開發，方法與您預期它在沒有容器的情況下運作。 若要進行這項工作，Visual Studio 新增幾個步驟來匯出憑證，並將它提供給容器使用。 流程如下：

1. 請確定本機開發憑證存在，並透過 `dev-certs` 工具在主機電腦上受到信任。
2. 使用儲存在此特定應用程式之使用者秘密存放區中的安全密碼，將憑證匯出至%APPDATA%\ASP.NET\Https。
3. 磁片區掛接下列目錄：

   - *%APPDATA%\Microsoft\UserSecrets*
   - *%APPDATA%\ASP.NET\Https*

ASP.NET Core 會尋找符合*Https*資料夾下元件名稱的憑證，這就是為什麼它會對應到該路徑中的容器。 您也可以使用環境變數（也就是 `ASPNETCORE_Kestrel__Certificates__Default__Path` 和 `ASPNETCORE_Kestrel__Certificates__Default__Password`）或在使用者秘密 json 檔案中定義憑證路徑和密碼，例如：

```json
{
  "Kestrel": {
    "Certificates": {
      "Default": {
        "Path": "c:\\app\\mycert.pfx",
        "Password": "strongpassword"
      }
    }
  }
}
```

如需在容器中使用 SSL 搭配 ASP.NET Core 應用程式的詳細資訊，請參閱[使用 Docker OVER HTTPS 裝載 ASP.NET Core 映射](https://docs.microsoft.com/aspnet/core/security/docker-https)。

## <a name="debugging"></a>偵錯

 當您啟動調試（**F5**）時，可能的話，會重複使用先前啟動的容器。 如果您不想要重複使用先前的容器，您可以使用 Visual Studio 中的 [**重建**] 或 [**清除**] 命令，強制 Visual Studio 使用全新的容器。

執行偵錯工具的進程視專案和容器作業系統的類型而定：

|||
|-|-|
| **.NET Core 應用程式（Linux 容器）**| Visual Studio 下載 `vsdbg` 並將其對應至容器，然後使用您的程式和引數（也就是 `dotnet webapp.dll`）來呼叫它，然後偵錯工具會附加至進程。 |
| **.NET Core 應用程式（Windows 容器）**| Visual Studio 會使用 `onecoremsvsmon` 並將其對應至容器、將其做為進入點執行，然後 Visual Studio 連接到您的程式，並將其附加至您的程式。 這類似于您通常會在另一部電腦或虛擬機器上設定遠端偵錯。|
| **.NET Framework 應用程式** | Visual Studio 會使用 `msvsmon` 並將其對應至容器、將其做為進入點的一部分執行，以供 Visual Studio 連接到它，並附加至您的程式。|

如需 `vsdbg.exe`的詳細資訊，請參閱[從 Visual Studio 在 Linux 和 OSX 上 Offroad .Net Core 的調試](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)程式。

## <a name="container-entry-point"></a>容器進入點

Visual Studio 使用自訂容器進入點，視專案類型和容器作業系統而定，以下是不同的組合：

|||
|-|-|
| **Linux 容器** | 進入點是 `tail -f /dev/null`，這是無限期等候，讓容器保持執行狀態。 當應用程式透過偵錯工具啟動時，它就是負責執行應用程式的偵錯工具（也就是 `dotnet webapp.dll`）。 如果在未進行偵錯工具的情況下啟動，則工具會執行 `docker exec -i {containerId} dotnet webapp.dll` 來執行應用程式。|
| **Windows 容器**| 進入點類似于執行偵錯工具的 `C:\remote_debugger\x64\msvsmon.exe /noauth /anyuser /silent /nostatus`，因此正在接聽連接。 同樣地，偵錯工具會執行應用程式，並在未進行偵測的情況下啟動 `docker exec` 命令。 針對 .NET Framework web 應用程式，進入點會稍有不同，其中 `ServiceMonitor` 會新增至命令。|
  
> [!NOTE]
> 容器進入點只能在 docker 撰寫專案中修改，而不能在單一容器專案中修改。

## <a name="next-steps"></a>後續步驟

瞭解如何在專案檔中設定其他 MSBuild 屬性，以進一步自訂您的組建。 請參閱[容器專案的 MSBuild 屬性](container-msbuild-properties.md)。

## <a name="see-also"></a>請參閱

Windows
[Linux 上的 windows 容器上](/virtualization/windowscontainers/deploy-containers/linux-containers)的[MSBuild](../msbuild/msbuild.md)
[Dockerfile](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
