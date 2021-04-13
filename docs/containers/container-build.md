---
title: Visual Studio 容器工具組建和調試總覽
author: ghogen
description: 容器工具組建和偵錯工具的總覽
ms.author: ghogen
ms.date: 03/15/2021
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 6b860abeab0745ebae580e3020c94e446f2441c8
ms.sourcegitcommit: c875360278312457f4d2212f0811466b4def108d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2021
ms.locfileid: "107315949"
---
# <a name="how-visual-studio-builds-containerized-apps"></a>Visual Studio 如何建置容器化應用程式

無論您是從 Visual Studio IDE 建立，還是要設定命令列組建，都必須知道 Visual Studio 如何使用 Dockerfile 來建立您的專案。  基於效能考慮，Visual Studio 遵循容器化應用程式的特殊程式。 當您藉由修改 Dockerfile 來自訂群組建流程時，瞭解 Visual Studio 組建專案的方式特別重要。

當 Visual Studio 建立不使用 Docker 容器的專案時，它會在本機電腦上叫用 MSBuild，並在資料夾中產生輸出檔案， (通常是在 `bin` 您的本機方案資料夾下) 。 不過，針對容器化專案，組建程式會考慮 Dockerfile 的指示，以建立容器化應用程式。 Visual Studio 使用的 Dockerfile 會分成多個階段。 此處理程式依賴 Docker 的 *多階段組建* 功能。

## <a name="multistage-build"></a>多階段組建

多階段組建功能可協助您更有效率地建立容器，並讓容器只包含應用程式在執行時間所需的位，讓容器變得更小。 多階段 build 是用於 .NET Core 專案，而不是 .NET Framework 專案。

多階段組建可讓您以產生中繼映射的階段建立容器映射。 例如，假設 Visual Studio 產生的一般 Dockerfile-第一個階段是 `base` ：

```
FROM mcr.microsoft.com/dotnet/aspnet:3.1-buster-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Dockerfile 中的行會以 Microsoft Container Registry 中的 Debian 映射開始 (mcr.microsoft.com) 並建立可 `base` 公開端口80和443的中繼映射，並將工作目錄設定為 `/app` 。

下一個階段是 `build` ，其顯示如下：

```
FROM mcr.microsoft.com/dotnet/sdk:3.1-buster-slim AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app/build
```

您可以看到階段從登錄中的 `build` 不同原始映射開始 (`sdk` 而不是 `aspnet`) ，而不是從基底繼續。  `sdk`映射具有所有的組建工具，因此它會比僅包含執行時間元件的 aspnet 映射大很多。 當您查看 Dockerfile 的其餘部分時，使用個別影像的原因會變得很清楚：

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

最後一個階段會從開始 `base` ，並包含將 `COPY --from=publish` 已發佈的輸出複製到最後一個映射的。 此程式可讓最終映射變得較小，因為它不需要包含映射中的所有組建工具 `sdk` 。

## <a name="building-from-the-command-line"></a>從命令列建立

如果您想要在 Visual Studio 之外建立，您可以使用 `docker build` 或 `MSBuild` 從命令列建立。

### <a name="docker-build"></a>docker build

若要從命令列建立容器化的解決方案，您通常可以 `docker build <context>` 針對方案中的每個專案使用命令。 您會提供 *組建內容* 引數。 Dockerfile 的 *組建內容* 是本機電腦上的資料夾，用來做為產生映射的工作資料夾。 例如，當您將檔案複製到容器時，它就是您從中複製檔案的資料夾。  在 .NET Core 專案中，使用包含方案檔 ( .sln) 的資料夾。  以相對路徑表示，在專案資料夾中，此引數通常為 ".."，而在其父資料夾中則為方案檔。  針對 .NET Framework 專案，組建內容是專案資料夾，而不是方案資料夾。

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Visual Studio 針對 .NET Framework 專案所建立的 dockerfile (以及 Visual Studio 2017 Update 4) 之前的 Visual Studio 版本所建立的 .NET Core 專案不會多階段 Dockerfile。  這些 Dockerfile 中的步驟不會編譯您的程式碼。  相反地，當 Visual Studio 建立 .NET Framework Dockerfile 時，它會先使用 MSBuild 編譯您的專案。  當這種情況成功時，Visual Studio 接著會建立 Dockerfile，只要將 MSBuild 的組建輸出複製到產生的 Docker 映射即可。  因為編譯器代碼的步驟不包含在 Dockerfile 中，所以您無法使用 `docker build` 從命令列建立 .NET Framework dockerfile。 您應該使用 MSBuild 來建立這些專案。

若要建立單一 docker 容器專案的映射，您可以搭配使用 MSBuild 與 `/t:ContainerBuild` 命令選項。 例如：

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

當您從 Visual Studio IDE 建立方案時，您會在 [ **輸出** ] 視窗中看到類似您所看到的輸出。 一律使用 `/p:Configuration=Release` ，因為在 Visual Studio 使用多階段組建優化的情況下，建立 **Debug** 設定時的結果可能不會如預期般執行。 請參閱 [調試](#debugging)。

如果您使用 Docker Compose 專案，請使用此命令來建立映射：

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="project-warmup"></a>專案預熱

*專案* 準備是指標對專案選取 docker 設定檔時所發生的一系列步驟 (也就是當載入專案或新增 Docker 支援時) ，以改善後續執行 (**f5** 或 **Ctrl** + **F5**) 的效能。 這可在 [**工具**  >  **選項**]  >  **容器工具** 下設定。 以下是在背景中執行的工作：

- 檢查 Docker Desktop 是否已安裝且正在執行。
- 確定 Docker Desktop 已設定為與專案相同的作業系統。
- 在 Dockerfile 的第一個階段中，將映射提取 (`base` 最 dockerfile) 中的階段。  
- 建立 Dockerfile 並啟動容器。

預先準備只會在 **快速** 模式中執行，因此執行中的容器將會裝載應用程式資料夾。 這表示對應用程式所做的任何變更都不會使容器失效。 因此可大幅改善偵錯工具的效能，並減少長時間執行的工作（例如，提取大型映射）的等候時間。

## <a name="volume-mapping"></a>磁片區對應

若要讓偵錯工具在容器中運作，Visual Studio 會使用磁片區對應，從主機電腦對應偵錯工具和 NuGet 資料夾。 [這裡](https://docs.docker.com/storage/volumes/)的 Docker 檔會說明磁片區對應。 以下是在您的容器中掛接的磁片區：

|磁碟區|描述|
|-|-|
| **遠端偵錯程式** | 包含在容器中執行偵錯工具所需的位（視專案類型而定）。 這會在 [調試](#debugging) 程式區段中更詳細地說明。|
| **應用程式資料夾** | 包含 Dockerfile 所在的專案資料夾。|
| **源資料夾** | 包含傳遞至 Docker 命令的組建內容。|
| **NuGet 套件資料夾** | 包含從專案中的 *obj \{ 專案} .props* 檔案讀取的 NuGet 封裝和回溯資料夾。 |

針對 ASP.NET core web 應用程式，SSL 憑證和使用者密碼可能會有兩個額外的資料夾，在下一節中會更詳細地說明。

## <a name="ssl-enabled-aspnet-core-apps"></a>啟用 SSL 的 ASP.NET Core 應用程式

Visual Studio 中的容器工具支援使用開發憑證來對啟用 SSL 的 ASP.NET core 應用程式進行偵錯工具，就像您預期它在沒有容器的情況下運作一樣。 若要這樣做，Visual Studio 會新增幾個步驟來匯出憑證，並將它提供給容器。 以下是在容器中進行偵錯工具時，Visual Studio 為您處理的流程：

1. 確定本機開發憑證存在於主機電腦上，並透過工具受到信任 `dev-certs` 。
2. 使用儲存在此特定應用程式的使用者秘密存放區中的安全密碼，將憑證匯出至%APPDATA%\ASP.NET\Https。
3. 磁片區-裝載下列目錄：

   - *%APPDATA%\Microsoft\UserSecrets*
   - *%APPDATA%\ASP.NET\Https*

ASP.NET Core 尋找符合 *Https* 資料夾下元件名稱的憑證，這就是為什麼它會對應至該路徑中的容器。 您也可以使用環境變數來定義憑證路徑和密碼 (也就是 `ASPNETCORE_Kestrel__Certificates__Default__Path` `ASPNETCORE_Kestrel__Certificates__Default__Password`) 或在使用者秘密 json 檔案中，例如：

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

如果您的設定同時支援容器化和非容器化組建，您應該使用環境變數，因為路徑是容器環境的特定路徑。

如需在容器中使用 SSL 搭配 ASP.NET Core apps 的詳細資訊，請參閱 [使用 Docker OVER HTTPS 裝載 ASP.NET Core 映射](/aspnet/core/security/docker-https)) 。

## <a name="debugging"></a>偵錯

在「 **調試** 程式」設定中建立時，有幾項優化 Visual Studio 可協助您處理容器化專案的組建程式效能。 容器化應用程式的組建程式不像單純遵循 Dockerfile 中所述的步驟一樣簡單。 在容器中建立的速度會比在本機電腦上建立慢很多。  因此，當您在 **調試** 程式中建立時，Visual Studio 實際上會在本機電腦上建立您的專案，然後使用磁片區掛接，將輸出檔案夾共用至容器。 啟用此優化的組建稱為「 *快速* 模式組建」。

在 **快速** 模式中，Visual Studio `docker build` 使用引數來呼叫，此引數會指示 Docker 只建立 `base` 階段。  Visual Studio 處理其餘的進程，而不考慮 Dockerfile 的內容。 因此，當您修改 Dockerfile （例如自訂容器環境或安裝其他相依性）時，您應該將修改放在第一個階段。  `build` `publish` 將不會執行放在 Dockerfile、或階段中的任何自訂步驟 `final` 。

只有當您在 **Debug** 設定中建立時，才會發生此效能優化。 在 **發行** 設定中，組建會出現在 Dockerfile 中指定的容器中。

如果您想要在 Dockerfile 指定時停用效能優化和組建，請在專案檔中將 **ContainerDevelopmentMode** 屬性設定為「 **一般** 」，如下所示：

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

若要還原效能優化，請從專案檔中移除該屬性。

 當您開始進行 (**F5**) 的偵錯工具時，會盡可能重複使用先前啟動的容器。 如果您不想要重複使用先前的容器，您可以在 Visual Studio 中使用 [ **重建** ] 或 [ **清除** ] 命令，強制 Visual Studio 使用全新的容器。

執行偵錯工具的程式取決於專案和容器作業系統的類型：

|狀況|偵錯工具進程|
|-|-|
| **(Linux 容器的 .NET Core 應用程式)**| Visual Studio 下載 `vsdbg` 並將它對應至容器，則會使用您的程式和引數來呼叫， (也就是 `dotnet webapp.dll`) ，然後偵錯工具會附加至進程。 |
| **(Windows 容器的 .NET Core 應用程式)**| Visual Studio 使用 `onecoremsvsmon` 並將它對應至容器、以進入點的形式執行，然後 Visual Studio 連接到該容器並附加至您的程式。 這與您通常會在另一部電腦或虛擬機器上設定遠端偵錯程式的方式類似。|
| **.NET Framework 應用程式** | Visual Studio 使用 `msvsmon` 並將它對應至容器、將其作為 Visual Studio 可連接的進入點一部分來執行，並附加至您的程式。|

如需的詳細資訊 `vsdbg.exe` ，請參閱 [Offroad 在 Linux 和 OSX 上的 .net Core 和 Visual Studio 的](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)。

## <a name="container-entry-point"></a>容器進入點

Visual Studio 會根據專案類型和容器作業系統使用自訂容器進入點，以下是不同的組合：

|容器類型|進入點|
|-|-|
| **Linux 容器** | 進入點是 `tail -f /dev/null` 無限期等候，讓容器保持執行狀態。 透過偵錯工具啟動應用程式時，偵錯工具會負責執行應用程式 (也就是 `dotnet webapp.dll`) 。 如果在未進行偵錯工具的情況下啟動，則工具會執行 `docker exec -i {containerId} dotnet webapp.dll` 以執行應用程式。|
| **Windows 容器**| 進入點類似于 `C:\remote_debugger\x64\msvsmon.exe /noauth /anyuser /silent /nostatus` 執行偵錯工具，因此它會接聽連接。 同樣地，偵錯工具會執行應用程式，並在 `docker exec` 不進行偵錯工具啟動時使用命令。 針對 .NET Framework web 應用程式，進入點會與新增至命令的位置稍有不同 `ServiceMonitor` 。|

容器進入點只能在 docker 撰寫專案中進行修改，而不能在單一容器專案中修改。

## <a name="next-steps"></a>下一步

瞭解如何在您的專案檔中設定其他 MSBuild 屬性，以進一步自訂您的組建。 請參閱 [容器專案的 MSBuild 屬性](container-msbuild-properties.md)。

## <a name="see-also"></a>另請參閱

[MSBuild](../msbuild/msbuild.md) 
Windows 上的[Dockerfile](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile) 
[Windows 上的 Linux 容器](/virtualization/windowscontainers/deploy-containers/linux-containers)
