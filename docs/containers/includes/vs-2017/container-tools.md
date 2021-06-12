---
title: Visual Studio 容器工具搭配 ASP.NET Core
author: ghogen
description: 了解如何使用 Visual Studio 2017 工具和適用於 Windows 的 Docker
ms.author: ghogen
ms.date: 02/01/2019
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: 92b97cb1091722bdf0caa6e7708e015612c545ad
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2021
ms.locfileid: "112044705"
---
有了 Visual Studio，您就可以輕鬆地建立、偵測和執行容器化 ASP.NET Core 應用程式，並將其發佈至 Azure Container Registry、Docker Hub、Azure App Service 或您自己的容器登錄。 在本文中，我們將發佈至 Container Registry。

## <a name="prerequisites"></a>先決條件

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* 已安裝 [網頁程式開發]、[Azure Tools] 工作負載及/或 [.NET Core 跨平台開發] 工作負載的 [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)
* 發佈至 Azure Container Registry (Azure 訂用帳戶)。 [註冊以免費試用](https://azure.microsoft.com/free/dotnet/)。

## <a name="installation-and-setup"></a>安裝與設定

若要安裝 Docker，請先參閱 [Docker Desktop For Windows 的資訊：安裝之前的須知](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)事項。 接下來，安裝 [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)。

## <a name="add-a-project-to-a-docker-container"></a>將專案新增至 Docker 容器

1. 從 Visual Studio 功能表中，選取 [檔案] > [新增] > [專案]。
1. 在 [新增專案] 對話方塊的 [範本] 區段下，選取 [Visual C#] > [Web]。
1. 選取 **ASP.NET Core Web 應用程式** ，如果您想要使用 .NET Framework 而不是 .net Core，請選取 [ **ASP.NET web 應用程式**]。
1. 指定新應用程式的名稱 (或使用預設值)，然後選取 [確定] 。
1. 選取 [ **Web 應用程式**]。
1. 請勾選 [啟用 Docker 支援] 核取方塊。

   ![啟用 Docker 支援核取方塊](../../media/container-tools/enable-docker-support.PNG)

   螢幕擷取畫面顯示 .NET Core;如果您使用 .NET Framework，看起來會有點不同。

1. 選取您想要 (Windows 或 Linux) 的容器類型，，然後按一下 [確定]。

## <a name="dockerfile-overview"></a>Dockerfile 概觀

*Dockerfile* 是用於建立最終 Docker 映像的配方，會在專案中建立。 請參閱 [Dockerfile reference](https://docs.docker.com/engine/reference/builder/) (Dockerfile 參考) 以了解其中的命令：

```
FROM mcr.microsoft.com/dotnet/aspnet:2.1 AS base
WORKDIR /app
EXPOSE 59518
EXPOSE 44364

FROM mcr.microsoft.com/dotnet/sdk:2.1 AS build
WORKDIR /src
COPY HelloDockerTools/HelloDockerTools.csproj HelloDockerTools/
RUN dotnet restore HelloDockerTools/HelloDockerTools.csproj
COPY . .
WORKDIR /src/HelloDockerTools
RUN dotnet build HelloDockerTools.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish HelloDockerTools.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "HelloDockerTools.dll"]
```

上述的 *Dockerfile* 以 [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) 映像為基礎，其中包含藉由建置專案並將其新增至容器來修改基底映像的指示。 如果您是使用 .NET Framework，基底映射將會不同。

核取新專案對話方塊的 [設定 HTTPS] 核取方塊時，*Dockerfile* 會提供兩個連接埠。 其中一個連接埠用於 HTTP 流量，另一個連接埠則用於 HTTPS。 如果未選取該核取方塊，則會為 HTTP 流量提供單一連接埠 (80)。

## <a name="debug"></a>偵錯

從工具列的偵錯下拉式清單中選取 [Docker]，然後開始對應用程式進行偵錯。 您可能會看到提示信任憑證的訊息，請選擇信任憑證以繼續進行。

[輸出] 視窗會顯示要採取哪些動作。

從 [工具] > [NuGet 套件管理員]、[套件管理員主控台] 功能表開啟 [套件管理員主控台] (PMC)。

產生的應用程式 Docker 映像，會標記為 *dev*。 此映像以 *microsoft/dotnet* 基底映像的 *2.1-aspnetcore-runtime* 標籤為基礎。 在 [套件管理員主控台] (PMC) 視窗中，執行 `docker images` 命令。 這會顯示電腦上的映像：

```console
REPOSITORY        TAG                     IMAGE ID      CREATED         SIZE
hellodockertools  dev                     d72ce0f1dfe7  30 seconds ago  255MB
microsoft/dotnet  2.1-aspnetcore-runtime  fcc3887985bb  6 days ago      255MB
```

> [!NOTE]
> **dev** 映像未包含應用程式二進位檔案和其他內容，因為 [偵錯] 組態會使用磁碟區掛接來提供反覆編輯和偵錯體驗。 若要建立包含所有內容的生產映像，請使用 [發行] 組態。

在 PMC 中執行 `docker ps` 命令。 請注意是使用容器來執行應用程式：

```console
CONTAINER ID        IMAGE                  COMMAND                   CREATED             STATUS              PORTS                   NAMES
baf9a678c88d        hellodockertools:dev   "C:\\remote_debugge..."   21 seconds ago      Up 19 seconds       0.0.0.0:37630->80/tcp   dockercompose4642749010770307127_hellodockertools_1
```

## <a name="publish-docker-images"></a>發行 Docker 映像

一旦應用程式的開發和偵錯循環完成，您就可以建立應用程式的生產映像。

1. 將組態下拉式清單變更為 [發行] 並建置應用程式。
1. 在 **方案總管** 中以滑鼠右鍵按一下專案，並選擇 [發佈]。
1. 在 [發佈目標] 對話方塊中，選取 [容器登錄] 索引標籤。
1. 選擇 [建立新的 Azure Container Registry]，然後按一下 [發佈]。
1. 在 [建立新的 Azure Container Registry] 中填入您想要的值。

    | 設定      | 建議的值  | 描述                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS 首碼** | 全域唯一的名稱 | 用以唯一識別容器登錄的名稱。 |
    | **訂用帳戶** | 選擇您的訂用帳戶 | 要使用的 Azure 訂用帳戶。 |
    | **[資源群組](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  要在其中建立容器登錄的資源群組名稱。 選擇 [新增] 以建立新的資源群組。|
    | **[SKU](/azure/container-registry/container-registry-skus)** | 標準 | 容器登錄的服務層  |
    | **登錄位置** | 接近您的位置 | 在[區域](https://azure.microsoft.com/regions/)中選擇您附近的 [位置]，或選擇將會使用容器登錄的其他服務所接近的位置。 |

    ![Visual Studio 的 [建立 Azure Container Registry] 對話方塊][0]

1. 按一下 [建立] 

## <a name="next-steps"></a>下一步

您現在可以從登錄中，將容器提取至能夠執行 Docker 映像的任何主機，例如 [Azure 容器執行個體](/azure/container-instances/container-instances-tutorial-deploy-app)。

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png
