---
title: 具有ASP.NET核心和 React.js 的視覺化工作室容器工具
author: ghogen
description: 了解如何使用 Visual Studio 容器工具和適用於 Windows 的 Docker
ms.author: ghogen
ms.date: 10/16/2019
ms.technology: vs-azure
ms.topic: quickstart
ms.openlocfilehash: af859c1c06820aa477869f6968e9c652bd525de6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "75916740"
---
# <a name="quickstart-use-docker-with-a-react-single-page-app-in-visual-studio"></a>快速入門：在視覺化工作室中使用帶有"反應單頁應用程式"的 Docker

使用 Visual Studio，您可以輕鬆地建置、偵錯和執行容器化的 ASP.NET Core 應用程式 (包括具有用戶端 JavaScript 的應用程式，例如 React.js 單一頁面應用程式)，並發佈到 Azure Container Registry (ACR)、Docker Hub、Azure App Service 或您自己的容器登錄。 在本文中，我們將發佈到 ACR。

## <a name="prerequisites"></a>必要條件

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* 已安裝 [網頁程式開發]****、[Azure Tools]**** 工作負載及/或 [.NET Core 跨平台開發]**** 工作負載的 [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)
* 發佈至 Azure Container Registry (Azure 訂用帳戶)。 [註冊免費試用](https://azure.microsoft.com/offers/ms-azr-0044p/)。
* [Node.js](https://nodejs.org/en/download/)
* 對於 Windows 容器，Windows 10 版本 1903 或更高版本，請使用本文中引用的 Docker 映射。
::: moniker-end
::: moniker range=">=vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* 已安裝**網頁程式開發**、**Azure Tools** 工作負載及(或) **.NET Core 跨平台開發** 工作負載的 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
* 適用於 .NET Core 2.2 開發的 [.NET Core 2.2 開發工具](https://dotnet.microsoft.com/download/dotnet-core/2.2)
* 發佈至 Azure Container Registry (Azure 訂用帳戶)。 [註冊免費試用](https://azure.microsoft.com/offers/ms-azr-0044p/)。
* [Node.js](https://nodejs.org/en/download/)
* 對於 Windows 容器，Windows 10 版本 1903 或更高版本，請使用本文中引用的 Docker 映射。
::: moniker-end

## <a name="installation-and-setup"></a>安裝與設定

對於 Docker 安裝，首先查看[Windows 的 Docker 桌面資訊：安裝 之前需要瞭解哪些內容](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)。 接下來，安裝 [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)。

## <a name="create-a-project-and-add-docker-support"></a>建立專案並新增 Docker 支援

::: moniker range="vs-2017"
1. 使用 **ASP.NET Core Web 應用程式**範本建立新專案。
1. 選取 [React.js]****。 您無法選取 [Enable Docker Support] \(啟用 Docker 支援\)****，不過別擔心，您可以在建立專案後，新增該支援。

   ![新 React.js 專案的螢幕擷取畫面](media/container-tools-react/vs2017/new-react-project.png)

1. 以滑鼠右鍵按一下專案節點，然後選擇 [新增]** [Docker 支援]** > ****，將 Dockerfile 新增至您的專案。

   ![新增 Docker 支援](media/container-tools-react/vs2017/add-docker-support.png)

1. 選擇容器類型，然後按一下 **"確定**"。
::: moniker-end
::: moniker range=">=vs-2019"
1. 使用 **ASP.NET Core Web 應用程式**範本建立新專案。
1. 選取 **React.js**，然後按一下 [建立]****。 您無法選取 [Enable Docker Support] \(啟用 Docker 支援\)****，不過別擔心，稍後可以新增該支援。

   ![新 React.js 專案的螢幕擷取畫面](media/container-tools-react/vs2019/new-react-project.png)

1. 以滑鼠右鍵按一下專案節點，然後選擇 [新增]** [Docker 支援]** > ****，將 Dockerfile 新增至您的專案。

   ![新增 Docker 支援](media/container-tools-react/vs2017/add-docker-support.png)

1. 選擇容器類型。
::: moniker-end

下一步會有所不同，具體取決於您使用的是 Linux 容器還是 Windows 容器。

## <a name="modify-the-dockerfile-linux-containers"></a>修改 Docker 檔（Linux 容器）

*Dockerfile* 是用於建立最終 Docker 映像的配方，會在專案中建立。 有關瞭解其中的命令，請參閱[Dockerfile 引用](https://docs.docker.com/engine/reference/builder/)。

在專案中開啟 *Dockerfile*，並新增下列程式碼行，在容器中安裝 Node.js 10.x。 請務必將這些程式碼行新增在第一個區段中，將節點套件管理員 *npm.exe* 的安裝新增至用在後續步驟中的基底映像。

```
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
```

*Dockerfile* 現在看起來應像這樣：

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80 
EXPOSE 443
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs

FROM microsoft/dotnet:2.2-sdk-stretch AS build
WORKDIR /src
COPY ["WebApplication37/WebApplication37.csproj", "WebApplication37/"]
RUN dotnet restore "WebApplication37/WebApplication37.csproj"
COPY . .
WORKDIR "/src/WebApplication37"
RUN dotnet build "WebApplication37.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "WebApplication37.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication37.dll"]
```

上述的 *Dockerfile* 以 [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) 映像為基礎，其中包含藉由建置專案並將其新增至容器來修改基底映像的指示。

核取新專案對話方塊的 [設定 HTTPS]**** 核取方塊時，*Dockerfile* 會提供兩個連接埠。 其中一個連接埠用於 HTTP 流量，另一個連接埠則用於 HTTPS。 如果未選取該核取方塊，則會為 HTTP 流量提供單一連接埠 (80)。

## <a name="modify-the-dockerfile-windows-containers"></a>修改 Docker 檔（Windows 容器）

通過按兩下專案節點打開專案檔案，並通過將以下屬性添加為`<PropertyGroup>`元素的子項來更新專案檔案 （*.csproj）：

   ```xml
    <DockerfileFastModeStage>base</DockerfileFastModeStage>
   ```

通過添加以下行更新 Docker 檔。 這將將節點和 npm 複製到容器。

   1. 添加到``# escape=` ``Docker 檔的第一行
   1. 添加以下行之前`FROM … base`

      ```
      FROM mcr.microsoft.com/powershell:nanoserver-1903 AS downloadnodejs
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs
      ```

   1. 前後添加以下行`FROM … build`

      ```
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      ```

   1. 完整的 Dockerfile 現在應如下所示：

      ```
      # escape=`
      #Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
      #For more information, please see https://aka.ms/containercompat
      FROM mcr.microsoft.com/powershell:nanoserver-1903 AS downloadnodejs
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      RUN Expand-Archive nodejs.zip -DestinationPath C:\; `
      RUN Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs

      FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1903 AS base
      WORKDIR /app
      EXPOSE 80
      EXPOSE 443
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\

      FROM mcr.microsoft.com/dotnet/core/sdk:2.2-nanoserver-1903 AS build
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      WORKDIR /src
      COPY ["WebApplication7/WebApplication37.csproj", "WebApplication37/"]
      RUN dotnet restore "WebApplication7/WebApplication7.csproj"
      COPY . .
      WORKDIR "/src/WebApplication37"
      RUN dotnet build "WebApplication37.csproj" -c Release -o /app/build

      FROM build AS publish
      RUN dotnet publish "WebApplication37.csproj" -c Release -o /app/publish

      FROM base AS final
      WORKDIR /app
      COPY --from=publish /app/publish .
      ENTRYPOINT ["dotnet", "WebApplication37.dll"]
      ```

1. 通過刪除 .dockerignore 檔更新`**/bin`。

## <a name="debug"></a>偵錯

從工具列的偵錯下拉式清單中選取 [Docker]****，然後開始對應用程式進行偵錯。 您可能會看到提示信任憑證的訊息，請選擇信任憑證以繼續進行。  首次生成時，Docker 會下載基本映射，因此可能需要稍長一點。

[輸出]**** 視窗中的 [容器工具]**** 選項會顯示要採取哪些動作。 您應該會看到與 *npm.exe* 相關聯的安裝步驟。

瀏覽器會顯示應用程式的首頁。

::: moniker range="vs-2017"
   ![正在執行的應用程式螢幕擷取畫面](media/container-tools-react/vs2017/running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![正在執行的應用程式螢幕擷取畫面](media/container-tools-react/vs2019/running-app.png)
::: moniker-end

嘗試瀏覽至 [計數器]** 頁面，然後按一下 [遞增]**** 按鈕，測試計數器的用戶端程式碼。

從 [工具]**** > [NuGet 套件管理員]、[套件管理員主控台]**** 功能表開啟 [套件管理員主控台]**** (PMC)。

產生的應用程式 Docker 映像，會標記為 *dev*。 此映像以 *microsoft/dotnet* 基底映像的 *2.2-aspnetcore-runtime* 標籤為基礎。 在 [套件管理員主控台]**** (PMC) 視窗中，執行 `docker images` 命令。 這會顯示電腦上的映像：

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
webapplication37  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.2-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> **dev** 映像未包含應用程式二進位檔案和其他內容，因為 [偵錯]**** 組態會使用磁碟區掛接來提供反覆編輯和偵錯體驗。 若要建立包含所有內容的生產映像，請使用 [發行]**** 組態。

在 PMC 中執行 `docker ps` 命令。 請注意是使用容器來執行應用程式：

```console
CONTAINER ID        IMAGE                  COMMAND               CREATED             STATUS              PORTS                                           NAMES
cf5d2ef5f19a        webapplication37:dev   "tail -f /dev/null"   2 minutes ago       Up 2 minutes        0.0.0.0:52036->80/tcp, 0.0.0.0:44342->443/tcp   priceless_cartwright
```

## <a name="publish-docker-images"></a>發行 Docker 映像

一旦應用程式的開發和偵錯循環完成，您就可以建立應用程式的生產映像。

1. 將組態下拉式清單變更為 [發行]**** 並建置應用程式。
1. 在**方案總管**中以滑鼠右鍵按一下專案，並選擇 [發佈]****。
1. 在 [發佈目標] 對話方塊中，選取 [容器登錄]**** 索引標籤。
1. 選擇 [建立新的 Azure Container Registry]****，然後按一下 [發佈]****。
1. 在 [建立新的 Azure Container Registry]**** 中填入您想要的值。

    | 設定      | 建議的值  | 描述                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS 首碼** | 全域唯一的名稱 | 用以唯一識別容器登錄的名稱。 |
    | **訂閱** | 選擇您的訂用帳戶 | 要使用的 Azure 訂用帳戶。 |
    | **[資源組](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  要在其中建立容器登錄的資源群組名稱。 選擇 [新增]**** 以建立新的資源群組。|
    | **[Sku](/azure/container-registry/container-registry-skus)** | 標準 | 容器登錄的服務層  |
    | **登錄位置** | 接近您的位置 | 在[區域](https://azure.microsoft.com/regions/)中選擇您附近的 [位置]，或選擇將會使用容器登錄的其他服務所接近的位置。 |

    ![Visual Studio 的 [建立 Azure Container Registry] 對話方塊][0]

1. 按一下 **[建立]**。

   ![顯示成功發佈的螢幕擷取畫面](media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>後續步驟

您現在可以從登錄中，將容器提取至能夠執行 Docker 映像的任何主機，例如 [Azure 容器執行個體](/azure/container-instances/container-instances-tutorial-deploy-app)。

## <a name="additional-resources"></a>其他資源

* [使用 Visual Studio 進行容器開發](/visualstudio/containers)
* [對使用 Docker 進行的 Visual Studio 開發進行疑難排解](troubleshooting-docker-errors.md)
* [GitHub 存放庫上的 Visual Studio 容器工具](https://github.com/Microsoft/DockerTools)

::: moniker range="vs-2017"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png
::: moniker-end
::: moniker range=">=vs-2019"
[0]:media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
::: moniker-end