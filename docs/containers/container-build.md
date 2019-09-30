---
title: Visual Studio 容器工具組建總覽
author: ghogen
description: 容器工具組建流程的總覽
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: edc4674e2468124ecb46b25a1411043ed4b66a2a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253110"
---
# <a name="building-containerized-apps-using-visual-studio-or-the-command-line"></a>使用 Visual Studio 或命令列建立容器化應用程式

無論您是從 Visual Studio IDE 建立，或是設定命令列組建，都必須知道 Visual Studio 組建如何使用 Dockerfile 來建立您的專案。  基於效能考慮，Visual Studio 會遵循容器化應用程式的特殊流程。 當您藉由修改 Dockerfile 自訂您的組建流程時，瞭解 Visual Studio 組建專案的方式特別重要。

當 Visual Studio 建立不使用 Docker 容器的專案時，它會在本機電腦上叫用 MSBuild，並在本機方案資料夾下的`bin`資料夾（通常是）中產生輸出檔案。 不過，針對容器化的專案，組建程式會考慮 Dockerfile 的指示來建立容器化應用程式。 Visual Studio 使用的 Dockerfile 會分成多個階段。 此程式依賴 Docker 的*多階段組建*功能。

## <a name="multistage-build"></a>多階段組建

多階段組建功能有助於讓容器的建立作業更有效率，並讓容器只包含應用程式在執行時間所需的位，使其變得更小。 多階段 build 用於 .NET Core 專案，而不是 .NET Framework 專案。

多階段組建可讓您在產生中繼映射的階段中建立容器映射。 例如，假設 Visual Studio 產生的一般 Dockerfile-第一個階段是`base`：

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Dockerfile 中的程式程式碼以 Microsoft Container Registry （mcr.microsoft.com）中的 Nanoserver 映射開頭，並建立可`base`公開端口80和443的中繼映射，並將工作目錄`/app`設定為。

下一個階段是`build`，其顯示如下：

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

您可以看到`build`階段是從登錄中不同的原始映射（`sdk`而`aspnet`非）開始，而不是從基底繼續進行。  `sdk`映射具有所有的組建工具，因此，它比 aspnet 映射大得多，只包含執行時間元件。 當您查看 Dockerfile 的其餘部分時，使用個別影像的原因會變得很清楚：

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

最後一個階段會從`base`重新開始，並`COPY --from=publish`包含將已發行的輸出複製到最終影像的。 此程式可讓最終影像變得很小，因為它不需要包含`sdk`映射中的所有組建工具。

## <a name="faster-builds-for-the-debug-configuration"></a>更快速的 Debug 設定組建

有數項優化可 Visual Studio 執行，協助處理容器化專案的組建程式效能。 當您啟動調試（F5）時，可能的話，會重複使用先前建立的映射。 如果您不想要重複使用先前的容器，您可以使用 Visual Studio 中的 [**重建**] 或 [**清除**] 命令，強制 Visual Studio 使用全新的容器。

此外，若要改善效能，容器化應用程式的組建流程不只是遵循 Dockerfile 中所述的步驟。 在容器中建立的速度會比在本機電腦上建立的速度慢很多。  因此，當您在**Debug**設定中建立時，Visual Studio 實際上會在本機電腦上建立您的專案，然後使用磁片區掛接將輸出檔案夾共用至容器。 已啟用此優化的組建稱為*快速*模式組建。

在**快速**模式中，Visual Studio `docker build`會呼叫，並提供引數，告訴 Docker `base`只建立階段。  Visual Studio 會處理其餘的進程，而不考慮 Dockerfile 的內容。 因此，當您修改 Dockerfile （例如自訂容器環境或安裝其他相依性）時，您應該在第一個階段中進行修改。  將不會執行放在 Dockerfile 的`build`、 `publish`或`final`階段中的任何自訂步驟。

只有當您在**Debug**設定中建立時，才會發生此效能優化。 在**發行**設定中，組建會依照 Dockerfile 中指定的方式出現在容器中。

如果您想要在 Dockerfile 指定時停用效能優化和組建，請在專案檔中將**ContainerDevelopmentMode**屬性設定為 [**一般**]，如下所示：

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

若要還原效能優化，請從專案檔中移除屬性。

## <a name="building-from-the-command-line"></a>從命令列建立

您可以使用`docker build`或`MSBuild` ，從命令列建立。

### <a name="docker-build"></a>docker 組建

若要從命令列建立容器化解決方案，您通常可以針對方案中`docker build <context>`的每個專案使用命令。 您會提供*組建內容*引數。 Dockerfile 的*組建內容*是本機電腦上的資料夾，用來做為產生映射的工作資料夾。 例如，當您將檔案複製到容器時，它就是您複製檔案的資料夾。  在 .NET Core 專案中，使用包含方案檔（.sln）的資料夾。  以相對路徑表示，此引數通常會是 "：" （代表專案資料夾中的 Dockerfile），以及其父資料夾中的方案檔。  針對 .NET Framework 專案，組建內容是專案資料夾，而不是方案資料夾。

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

針對 .NET Framework 專案所建立 Visual Studio 的 dockerfile （以及 Visual Studio 2017 Update 4 之前的 Visual Studio 版本所建立的 .NET Core 專案），都不是多階段 Dockerfile。  這些 Dockerfile 中的步驟不會編譯您的程式碼。  相反地，當 Visual Studio 建立 .NET Framework Dockerfile 時，它會先使用 MSBuild 編譯您的專案。  當此動作成功時，Visual Studio 會建立 Dockerfile，這會直接將 MSBuild 的組建輸出複製到產生的 Docker 映射。  由於編譯器代碼的步驟不包含在 Dockerfile 中，因此您無法從命令列使用`docker build`建立 .NET Framework dockerfile。 您應該使用 MSBuild 來建立這些專案。

若要建立單一 docker 容器專案的映射，您可以使用 MSBuild `/t:ContainerBuild`搭配命令選項。 例如：

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

當您從 Visual Studio IDE 建立方案時，您會看到類似于 [**輸出**] 視窗中所顯示的輸出。 請一律`/p:Configuration=Release`使用，因為在 Visual Studio 使用多階段組建優化的情況下，建立**Debug**設定時的結果可能不會如預期般執行。

如果您使用 Docker Compose 專案，請使用命令來建立映射：

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="next-steps"></a>後續步驟

瞭解如何在專案檔中設定其他 MSBuild 屬性，以進一步自訂您的組建。 請參閱[容器專案的 MSBuild 屬性](container-msbuild-properties.md)。

## <a name="see-also"></a>另請參閱


Windows 上 windows[Linux 容器](/virtualization/windowscontainers/deploy-containers/linux-containers)上的 [MSBuild](../msbuild/msbuild.md)[Dockerfile](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile) 

