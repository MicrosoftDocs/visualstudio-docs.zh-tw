---
title: 視覺化工作室容器工具生成和調試概述
author: ghogen
description: 容器工具生成和調試過程概述
ms.author: ghogen
ms.date: 11/20/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: d91dd01879ac3bb62b981109463f6762046382ef
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027266"
---
# <a name="how-visual-studio-builds-containerized-apps"></a>Visual Studio 如何建置容器化應用程式

無論您是從 Visual Studio IDE 構建，還是設置命令列生成，您都需要瞭解 Visual Studio 如何使用 Dockerfile 構建專案。  出於性能原因，Visual Studio 會遵循容器化應用的特殊過程。 通過修改 Dockerfile 自訂生成過程時，瞭解 Visual Studio 如何構建專案尤為重要。

當 Visual Studio 生成不使用 Docker 容器的專案時，它會在本地電腦上調用 MSBuild，並在本地解決方案資料夾下的資料夾中生成輸出檔案`bin`（通常為 ）。 但是，對於容器化專案，生成過程會考慮 Dockerfile 關於構建容器化應用的說明。 Visual Studio 使用的 Docker 檔分為多個階段。 此過程依賴于 Docker 的*多階段構建*功能。

## <a name="multistage-build"></a>多階段構建

多階段生成功能有助於提高構建容器的過程，並通過允許容器僅包含應用在運行時所需的位來縮小容器。 多階段生成用於 .NET 核心專案，而不是 .NET 框架專案。

多階段生成允許在生成中間圖像的階段創建容器映射。 例如，考慮 Visual Studio 生成的典型 Dockerfile - 第一`base`階段是 ：

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Dockerfile 中的行從 Microsoft 容器註冊表 （mcr.microsoft.com） 中的 Debian 映射開始，`base`並創建一個中間映射，公開端口 80 和 443，並將工作目錄設置為`/app`。

下一階段是`build`，如下所示：

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

您可以看到，`build`該階段從與註冊表 （`sdk`而不是`aspnet`） 的不同原始映射開始，而不是從基級繼續。  該`sdk`映射具有所有生成工具，因此它比僅包含運行時元件的 aspnet 映射大得多。 當您查看 Dockerfile 的其餘部分時，使用單獨映射的原因變得清晰：

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

最後階段從`base`重新開始，包括`COPY --from=publish`將已發佈的輸出複製到最終圖像。 此過程使最終映射可能更小，因為它不需要包括`sdk`映射中的所有生成工具。

## <a name="building-from-the-command-line"></a>從命令列生成

如果要在 Visual Studio 外部生成，則可以使用`docker build`或`MSBuild`從命令列生成。

### <a name="docker-build"></a>docker build

要從命令列生成容器化解決方案，通常`docker build <context>`可以使用 解決方案中的每個專案的命令。 提供*生成上下文*參數。 Dockerfile 的*生成上下文*是本地電腦上的資料夾，用作生成映射的工作資料夾。 例如，它是從複製到容器時複製檔的資料夾。  在 .NET Core 專案中，使用包含解決方案檔 （.sln） 的資料夾。  此參數通常表示為".."，用於專案資料夾中的 Dockerfile 及其父資料夾中的解決方案檔。  對於 .NET 框架專案，生成上下文是專案資料夾，而不是解決方案資料夾。

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Visual Studio 為 .NET 框架專案（和 .NET Core 專案創建的 Dockerfile，在 Visual Studio 2017 更新 4 之前使用 Visual Studio 版本創建）不是多階段 Dockerfile。  這些 Dockerfiles 中的步驟不會編譯您的代碼。  相反，當 Visual Studio 構建 .NET 框架 Dockerfile 時，它首先使用 MSBuild 編譯您的專案。  成功後，Visual Studio 會生成 Dockerfile，只需將 MSBuild 中的生成輸出複製到生成的 Docker 映射中即可。  由於編譯代碼的步驟不包括在 Dockerfile 中，因此無法使用命令列生成 .NET 框架 Docker 檔`docker build`。 您應該使用 MSBuild 來構建這些專案。

要為單個 Docker 容器專案生成映射，`/t:ContainerBuild`可以使用 MSBuild 與命令選項一起使用。 例如：

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

當您從視覺化工作室 IDE 構建解決方案時，您將看到與 **"輸出"** 視窗中看到的輸出類似的輸出。 始終使用`/p:Configuration=Release`，因為在 Visual Studio 使用多階段生成優化的情況下，生成**調試**配置時的結果可能不符合預期。 請參閱[調試](#debugging)。

如果使用 Docker 合成專案，請使用此命令生成映射：

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="project-warmup"></a>專案預熱

*專案預熱*是指在為專案選擇 Docker 設定檔（即載入專案或添加 Docker 支援時）以提高後續運行 **（F5**或**Ctrl**+**F5）** 的性能時發生的一系列步驟。 這在**工具** > **選項** > **容器工具**下可配置。 以下是在後臺運行的任務：

- 檢查 Docker 桌面是否安裝並運行。
- 確保 Docker 桌面設置為與專案相同的作業系統。
- 在 Dockerfile 的第一階段（大多數 Dockerfile`base`中階段）中拉出圖像。  
- 生成 Dockerfile 並啟動容器。

預熱僅在**快速**模式下進行，因此正在運行的容器將安裝應用資料夾卷。 這意味著對應用的任何更改不會使容器無效。 因此，這顯著提高了調試性能，並減少了長時間運行任務（如拉大映射）的等待時間。

## <a name="volume-mapping"></a>卷映射

為了在容器中進行調試，Visual Studio 使用卷映射從主機映射調試器和 NuGet 資料夾。 卷映射[在此處](https://docs.docker.com/storage/volumes/)的 Docker 文檔仲介紹。 以下是裝入容器中的卷：

|||
|-|-|
| **遠端偵錯器** | 包含在容器中運行調試器所需的位，具體取決於專案類型。 這在更多 |["調試](#debugging)"部分中的詳細資訊。
| **應用資料夾** | 包含 Docker 檔所在的專案資料夾。|
| **源資料夾** | 包含傳遞給 Docker 命令的生成上下文。|
| **NuGet 包資料夾** | 包含從*專案中 obj\{project_.csproj.nuget.g.props*檔中讀取的 NuGet 包和回退資料夾。 |

對於ASP.NET核心 Web 應用，SSL 憑證和使用者機密可能還有兩個額外的資料夾，下一節將對此進行更詳細的說明。

## <a name="ssl-enabled-aspnet-core-apps"></a>啟用 SSL ASP.NET核心應用

Visual Studio 中的容器工具支援使用開發證書調試啟用 SSL ASP.NET核心應用，就像您希望它在沒有容器的情況下工作一樣。 為此，Visual Studio 添加了幾個步驟來匯出證書並將其提供給容器。 以下是 Visual Studio 在容器中調試時為您處理的流：

1. 通過`dev-certs`該工具確保本地開發證書在主機電腦上存在並受信任。
2. 將證書匯出到 %APPDATA%*ASP.NET_Https，該密碼存儲在此特定應用的使用者機密存儲中。
3. 卷裝入以下目錄：

   - *%APPDATA%*微軟_使用者秘密*
   - *%APPDATA%*ASP.NET_HTTPs*

ASP.NET Core 查找與*Https*資料夾下的程式集名稱匹配的證書，這就是為什麼它映射到該路徑中的容器的原因。 憑證路徑和密碼可以使用環境變數（即`ASPNETCORE_Kestrel__Certificates__Default__Path`和`ASPNETCORE_Kestrel__Certificates__Default__Password`） 或使用者機密 json 檔中定義，例如：

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

如果您的配置同時支援容器化和非容器化生成，則應使用環境變數，因為路徑特定于容器環境。

有關在容器中使用 SSL ASP.NET核心應用的詳細資訊，請參閱[通過 HTTPS 使用 Docker 託管ASP.NET核心映射](/aspnet/core/security/docker-https)。

## <a name="debugging"></a>偵錯

在**調試**配置中生成時，Visual Studio 會執行一些優化，這有助於容器化專案的生成過程的性能。 容器化應用的生成過程並不像簡單地按照 Dockerfile 中概述的步驟那樣簡單。 在容器中構建比在本地電腦上構建要慢得多。  因此，當您在**調試**配置中生成時，Visual Studio 實際上在本地電腦上生成專案，然後使用卷安裝將輸出檔案夾共用到容器。 啟用此優化的生成稱為*快速*模式生成。

在**快速**模式下，Visual Studio`docker build`調用具有一個參數，該參數告訴`base`Docker 僅生成舞臺。  Visual Studio 處理該過程的其餘部分，而不考慮 Dockerfile 的內容。 因此，當您修改 Dockerfile 時（例如自訂容器環境或安裝其他依賴項）時，應將修改放在第一階段。  放置在 Dockerfile 的`build`、`publish`或`final`階段中的任何自訂步驟將不會執行。

只有在**在調試**配置中生成時，才會進行此性能優化。 在**發佈**配置中，生成發生在 Dockerfile 中指定的容器中。

如果要禁用性能優化並在 Dockerfile 指定時生成，請按如下方式將**容器開發模式**屬性設置為專案檔案中**的"常規**"：

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

要還原性能優化，請從專案檔案中刪除該屬性。

 當您開始調試時 **（F5**），如果可能，將重用以前啟動的容器。 如果不想重用以前的容器，可以使用 Visual Studio 中的 **"重建**"或 **"清理"** 命令來強制 Visual Studio 使用新的容器。

運行調試器的過程取決於專案和容器作業系統的類型：

|||
|-|-|
| **.NET 核心應用程式（Linux 容器）**| Visual Studio`vsdbg`會下載它並將其映射到容器，然後使用程式和參數（即`dotnet webapp.dll`），然後調試器附加到進程。 |
| **.NET 核心應用（Windows 容器）**| Visual Studio`onecoremsvsmon`使用它並將其映射到容器，將其作為進入點運行，然後 Visual Studio 連接到它並附加到程式。 這類似于通常在另一台電腦或虛擬機器上設置遠端偵錯的方式。|
| **.NET 框架應用** | Visual Studio`msvsmon`使用它並將其映射到容器，將其作為 Visual Studio 可以連接到該進入點的進入點的一部分運行，並附加到程式。|

有關 的資訊`vsdbg.exe`，請參閱[Linux 上的 .NET Core 的越野調試，以及 Visual Studio 中的 OSX](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)。

## <a name="container-entry-point"></a>集裝箱進入點

Visual Studio 根據專案類型和容器作業系統使用自訂容器進入點，下面是不同的組合：

|||
|-|-|
| **Linux 容器** | 進入點是`tail -f /dev/null`，這是保持容器運行的無限等待。 當應用通過調試器啟動時，負責運行應用的調試器（即`dotnet webapp.dll`）。 如果在未調試的情況下啟動，該工具將運行`docker exec -i {containerId} dotnet webapp.dll`以運行應用。|
| **視窗容器**| 進入點是運行`C:\remote_debugger\x64\msvsmon.exe /noauth /anyuser /silent /nostatus`調試器之類的內容，因此它正在偵聽連接。 調試器運行應用，在未調試的情況下啟動`docker exec`命令也是如此。 對於 .NET Framework Web 應用，進入點在`ServiceMonitor`添加到命令的位置略有不同。|

容器進入點只能在 Docker 組合專案中修改，不能在單容器專案中修改。

## <a name="next-steps"></a>後續步驟

瞭解如何通過在專案檔案中設置其他 MSBuild 屬性來進一步自訂生成。 請參閱[容器專案的 MSBuild 屬性](container-msbuild-properties.md)。

## <a name="see-also"></a>另請參閱

[在](../msbuild/msbuild.md)Windows 上的 Windows
[Dockerfile on Windows](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
Linux[容器上構建](/virtualization/windowscontainers/deploy-containers/linux-containers)Docker 檔
