---
title: 使用 ASP.NET Core 和 React.js Visual Studio 容器工具
titleSuffix: ''
ms.custom: SEO-VS-2020
author: ghogen
description: 瞭解如何使用 Visual Studio 容器工具和 Docker 來建立容器化回應 SPA 應用程式
ms.author: ghogen
ms.date: 02/21/2021
ms.technology: vs-azure
ms.topic: quickstart
ms.openlocfilehash: 177a44f8af73226d4352c4a48c23c65eadc3e608
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2021
ms.locfileid: "112602029"
---
# <a name="quickstart-use-docker-with-a-react-single-page-app-in-visual-studio"></a>快速入門：在 Visual Studio 中搭配使用 Docker 與回應單一頁面應用程式

使用 Visual Studio，您可以輕鬆地建置、偵錯和執行容器化的 ASP.NET Core 應用程式 (包括具有用戶端 JavaScript 的應用程式，例如 React.js 單一頁面應用程式)，並發佈到 Azure Container Registry (ACR)、Docker Hub、Azure App Service 或您自己的容器登錄。 在本文中，我們將發佈到 ACR。

## <a name="prerequisites"></a>必要條件

::: moniker range="vs-2017"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* 已安裝 [網頁程式開發]、[Azure Tools] 工作負載及/或 [.NET Core 跨平台開發] 工作負載的 [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)
* 發佈至 Azure Container Registry (Azure 訂用帳戶)。 [註冊以免費試用](https://azure.microsoft.com/offers/ms-azr-0044p/)。
* [Node.js](https://nodejs.org/en/download/)
* 針對 Windows 容器（Windows 10 1809 版或更新版本），以使用本文中所參考的 Docker 映射。
::: moniker-end
::: moniker range=">=vs-2019"
* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* 已安裝 **網頁程式開發**、**Azure Tools** 工作負載及(或) **.NET Core 跨平台開發** 工作負載的 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
* 使用 .NET Core 3.1 開發的[.Net core 3.1 開發工具](https://dotnet.microsoft.com/download/dotnet-core/3.1)。
* 發佈至 Azure Container Registry (Azure 訂用帳戶)。 [註冊以免費試用](https://azure.microsoft.com/offers/ms-azr-0044p/)。
* [Node.js](https://nodejs.org/en/download/)
* 針對 Windows 容器（Windows 10 1809 版或更新版本），以使用本文中所參考的 Docker 映射。
::: moniker-end

## <a name="installation-and-setup"></a>安裝與設定

若要安裝 Docker，請先參閱 [Docker Desktop For Windows 的資訊：安裝之前的須知](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)事項。 接下來，安裝 [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)。

## <a name="create-a-project-and-add-docker-support"></a>建立專案並新增 Docker 支援

::: moniker range="vs-2017"
1. 使用 **ASP.NET Core Web 應用程式** 範本建立新專案。
1. 選取 [React.js]。 您無法選取 [Enable Docker Support] \(啟用 Docker 支援\)，不過別擔心，您可以在建立專案後，新增該支援。

   ![新 React.js 專案的螢幕擷取畫面](media/container-tools-react/vs-2017/new-react-project.png)

1. 以滑鼠右鍵按一下專案節點，然後選擇 [ **新增** > **Docker 支援** ]，將 Dockerfile 新增至您的專案。

   ![新增 Docker 支援](media/container-tools-react/vs-2017/add-docker-support.png)

1. 選取容器類型，然後按一下 **[確定]**。
::: moniker-end

::: moniker range=">=vs-2019"

1. 使用 React.js範本的 **ASP.NET Core** 建立新專案。

   ![建立新 React.js 專案的螢幕擷取畫面](media/container-tools-react/vs-2019/create-reactjs-project.png)

1. 在 [ **其他資訊** ] 畫面上，您無法選取 [ **啟用 Docker 支援**]，但別擔心，您可以稍後再新增該支援。

   ![建立新的 React.js 專案-其他資訊畫面的螢幕擷取畫面](media/container-tools-react/vs-2019/new-react-project-additional-information.png)

1. 以滑鼠右鍵按一下專案節點，然後選擇 [ **新增** > **Docker 支援** ]，將 Dockerfile 新增至您的專案。

   ![新增 Docker 支援](media/container-tools-react/vs-2017/add-docker-support.png)

1. 選取容器類型。
::: moniker-end

下一個步驟會根據您使用的是 Linux 容器或 Windows 容器而有所不同。

## <a name="modify-the-dockerfile-linux-containers"></a>修改 Dockerfile (Linux 容器) 

*Dockerfile* 是用於建立最終 Docker 映像的配方，會在專案中建立。 請參閱 [Dockerfile 參考](https://docs.docker.com/engine/reference/builder/) ，以瞭解其內的命令。

在專案中開啟 *Dockerfile*，並新增下列程式碼行，在容器中安裝 Node.js 10.x。 請務必在第一節中新增這些行，以便將節點套件管理員 *npm.exe* 安裝新增至基礎映射，以及 `build` 一節中。

```Dockerfile
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
```

*Dockerfile* 現在看起來應像這樣：

```Dockerfile
#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs

FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
RUN curl -sL https://deb.nodesource.com/setup_10.x |  bash -
RUN apt-get install -y nodejs
WORKDIR /src
COPY ["WebApplication-ReactSPA/WebApplication-ReactSPA.csproj", "WebApplication-ReactSPA/"]
RUN dotnet restore "WebApplication-ReactSPA/WebApplication-ReactSPA.csproj"
COPY . .
WORKDIR "/src/WebApplication-ReactSPA"
RUN dotnet build "WebApplication-ReactSPA.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApplication-ReactSPA.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApplication-ReactSPA.dll"]
```

上述 *Dockerfile* 是以 [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) 映射為基礎，並包含透過建立您的專案並將其新增至容器來修改基底映射的指示。

核取新專案對話方塊的 [設定 HTTPS] 核取方塊時，*Dockerfile* 會提供兩個連接埠。 其中一個連接埠用於 HTTP 流量，另一個連接埠則用於 HTTPS。 如果未選取該核取方塊，則會為 HTTP 流量提供單一連接埠 (80)。

## <a name="modify-the-dockerfile-windows-containers"></a>修改 Dockerfile (Windows 容器) 

按兩下專案節點以開啟專案檔，然後將下列屬性新增為專案的子系，以更新專案檔 ( * .csproj) `<PropertyGroup>` ：

   ```xml
    <DockerfileFastModeStage>base</DockerfileFastModeStage>
   ```

藉由新增下列幾行來更新 Dockerfile。 這會將節點和 npm 複製到容器。

   1. 新增 ``# escape=` `` 至 Dockerfile 的第一行
   1. 在之前新增下列幾行 `FROM … base`

      ```Dockerfile
      FROM mcr.microsoft.com/powershell AS downloadnodejs
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs
      ```

   2. 在前面和之後加入下行 `FROM … build`

      ```Dockerfile
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      ```

   3. 完成的 Dockerfile 現在看起來應該像這樣：

      ```Dockerfile
      # escape=`
      #Depending on the operating system of the host machines(s) that will build or run the containers, the image specified in the FROM statement may need to be changed.
      #For more information, please see https://aka.ms/containercompat
      FROM mcr.microsoft.com/powershell AS downloadnodejs
      RUN mkdir -p C:\nodejsfolder
      WORKDIR C:\nodejsfolder
      SHELL ["pwsh", "-Command", "$ErrorActionPreference = 'Stop';$ProgressPreference='silentlyContinue';"]
      RUN Invoke-WebRequest -OutFile nodejs.zip -UseBasicParsing "https://nodejs.org/dist/v10.16.3/node-v10.16.3-win-x64.zip"; `
      Expand-Archive nodejs.zip -DestinationPath C:\; `
      Rename-Item "C:\node-v10.16.3-win-x64" c:\nodejs

      FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
      WORKDIR /app
      EXPOSE 80
      EXPOSE 443
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\

      FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
      COPY --from=downloadnodejs C:\nodejs\ C:\Windows\system32\
      WORKDIR /src
      COPY ["WebApplicationReact1/WebApplicationReact1.csproj", "WebApplicationReact1/"]
      RUN dotnet restore "WebApplicationReact1/WebApplicationReact1.csproj"
      COPY . .
      WORKDIR "/src/WebApplicationReact1"
      RUN dotnet build "WebApplicationReact1.csproj" -c Release -o /app/build

      FROM build AS publish
      RUN dotnet publish "WebApplicationReact1.csproj" -c Release -o /app/publish

      FROM base AS final
      WORKDIR /app
      COPY --from=publish /app/publish .
      ENTRYPOINT ["dotnet", "WebApplicationReact1.dll"]
      ```

   4. 藉由移除來更新 >.dockerignore `**/bin` 檔案。

## <a name="debug"></a>偵錯

從工具列的偵錯下拉式清單中選取 [Docker]，然後開始對應用程式進行偵錯。 您可能會看到提示信任憑證的訊息，請選擇信任憑證以繼續進行。  當您第一次建立時，docker 會下載基礎映射，因此可能需要更長的時間。

[輸出] 視窗中的 [容器工具] 選項會顯示要採取哪些動作。 您應該會看到與 *npm.exe* 相關聯的安裝步驟。

瀏覽器會顯示應用程式的首頁。

::: moniker range="vs-2017"
   ![正在執行的應用程式螢幕擷取畫面](media/container-tools-react/vs-2017/running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![正在執行的應用程式螢幕擷取畫面](media/container-tools-react/vs-2019/running-app.png)
::: moniker-end

嘗試瀏覽至 [計數器] 頁面，然後按一下 [遞增] 按鈕，測試計數器的用戶端程式碼。

從 [工具] > [NuGet 套件管理員]、[套件管理員主控台] 功能表開啟 [套件管理員主控台] (PMC)。

產生的應用程式 Docker 映像，會標記為 *dev*。 映射是以 *dotnet/core/aspnet* 基底映射的 *3.1* 標記為基礎。 在 [套件管理員主控台] (PMC) 視窗中，執行 `docker images` 命令。 這會顯示電腦上的映像：

```console
REPOSITORY                             TAG                 IMAGE ID            CREATED             SIZE
webapplicationreact1                   dev                 09be6ec2405d        2 hours ago         352MB
mcr.microsoft.com/dotnet/core/aspnet   3.1                 e3559b2d50bb        10 days ago         207MB
```

> [!NOTE]
> **dev** 映像未包含應用程式二進位檔案和其他內容，因為 [偵錯] 組態會使用磁碟區掛接來提供反覆編輯和偵錯體驗。 若要建立包含所有內容的生產映像，請使用 [發行] 組態。

在 PMC 中執行 `docker ps` 命令。 請注意是使用容器來執行應用程式：

```console
CONTAINER ID        IMAGE                      COMMAND               CREATED             STATUS              PORTS                                           NAMES
56d1b1008c89        webapplicationreact1:dev   "tail -f /dev/null"   2 hours ago         Up 2 hours          0.0.0.0:32771->80/tcp, 0.0.0.0:32770->443/tcp   WebApplication-React1
```

## <a name="publish-docker-images"></a>發行 Docker 映像

一旦應用程式的開發和偵錯循環完成，您就可以建立應用程式的生產映像。

:::moniker range="vs-2017"

1. 將組態下拉式清單變更為 [發行] 並建置應用程式。
1. 在 **方案總管** 中以滑鼠右鍵按一下專案，並選擇 [發佈]。
1. 在 [發佈目標] 對話方塊中，選取 [ **Container Registry**]。
1. 選擇 [建立新的 Azure Container Registry]，然後按一下 [發佈]。
1. 在 [建立新的 Azure Container Registry] 中填入您想要的值。

    | 設定      | 建議的值  | 描述                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS 首碼** | 全域唯一的名稱 | 用以唯一識別容器登錄的名稱。 |
    | **訂用帳戶** | 選擇您的訂用帳戶 | 要使用的 Azure 訂用帳戶。 |
    | **[資源群組](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  要在其中建立容器登錄的資源群組名稱。 選擇 [新增] 以建立新的資源群組。|
    | **[SKU](/azure/container-registry/container-registry-skus)** | 標準 | 容器登錄的服務層  |
    | **登錄位置** | 接近您的位置 | 在[區域](https://azure.microsoft.com/regions/)中選擇您附近的 [位置]，或選擇將會使用容器登錄的其他服務所接近的位置。 |

    ![Visual Studio 的 [建立 Azure Container Registry] 對話方塊](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

1. 選取 [建立]。

   ![顯示成功發佈的螢幕擷取畫面](media/container-tools/publish-succeeded.png)
:::moniker-end

:::moniker range=">=vs-2019"

1. 將組態下拉式清單變更為 [發行] 並建置應用程式。
1. 在 **方案總管** 中以滑鼠右鍵按一下專案，並選擇 [發佈]。
1. 在 [發佈目標] 對話方塊中，選取 [ **Docker Container Registry**]。

   ![選擇 Docker Container Registry](media/container-tools-react/vs-2019/publish-dialog1.png)

1. 接著，選擇 [ **Azure Container Registry**]。

   ![選擇 Azure Container Registry](media/container-tools-react/vs-2019/publish-dialog-acr.png)

1. 選擇 [ **建立新的 Azure Container Registry**]。
1. 在 [ **建立新的 Azure Container Registry** ] 畫面中，填入所需的值。

    | 設定      | 建議的值  | 描述                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS 首碼** | 全域唯一的名稱 | 用以唯一識別容器登錄的名稱。 |
    | **訂用帳戶** | 選擇您的訂用帳戶 | 要使用的 Azure 訂用帳戶。 |
    | **[資源群組](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  要在其中建立容器登錄的資源群組名稱。 選擇 [新增] 以建立新的資源群組。|
    | **[SKU](/azure/container-registry/container-registry-skus)** | 標準 | 容器登錄的服務層  |
    | **登錄位置** | 接近您的位置 | 在[區域](https://azure.microsoft.com/regions/)中選擇您附近的 [位置]，或選擇將會使用容器登錄的其他服務所接近的位置。 |

    ![Visual Studio 的 [建立 Azure Container Registry] 對話方塊](media/container-tools-react/vs-2019/azure-container-registry-details.png)

1. 選取 [ **建立**]，然後選取 **[完成]**。

   ![選取或建立新的 ACR](media/container-tools-react/vs-2019/publish-dialog2.png)

   當發行程式結束時，您可以檢查發行設定，並在需要時進行編輯，或使用 [ **發行** ] 按鈕再次發佈映射。

   ![顯示成功發佈的螢幕擷取畫面](media/container-tools-react/vs-2019/publish-finished.png)

   若要使用 [ **發佈** ] 對話方塊再次開始，請使用此頁面上的 [ **刪除** ] 連結來刪除發行設定檔，然後再次選擇 [ **發行** ]。
:::moniker-end

## <a name="next-steps"></a>後續步驟

您現在可以從登錄中，將容器提取至能夠執行 Docker 映像的任何主機，例如 [Azure 容器執行個體](/azure/container-instances/container-instances-tutorial-deploy-app)。

## <a name="additional-resources"></a>其他資源

* [使用 Visual Studio 進行容器開發](./index.yml)
* [對使用 Docker 進行的 Visual Studio 開發進行疑難排解](troubleshooting-docker-errors.md)
* [GitHub 存放庫上的 Visual Studio 容器工具](https://github.com/Microsoft/DockerTools)

