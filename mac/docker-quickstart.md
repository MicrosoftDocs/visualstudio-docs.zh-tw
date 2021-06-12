---
title: 開始使用 Docker
description: 了解如何在 Visual Studio for Mac 中將 Docker 新增至您的專案
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.topic: how-to
ms.openlocfilehash: 4ddb15c8bc5bf90663c5431d2379af61b43e73a6
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2021
ms.locfileid: "112043090"
---
# <a name="get-started-with-docker-in-visual-studio-for-mac"></a>開始使用 Visual Studio for Mac 中的 Docker

使用 Visual Studio for Mac，您可以輕鬆地建置、進行偵錯，以及執行容器化的 ASP.NET Core 應用程式並將它們發行至 Azure。

## <a name="prerequisites"></a>先決條件

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Visual Studio for Mac 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="installation-and-setup"></a>安裝和設定

若要安裝 Docker，請檢閱[安裝適用於 Mac 的 Docker Desktop](https://docs.docker.com/docker-for-mac/install/)，並遵循其中的資訊。

## <a name="creating-an-aspnet-core-web-application-and-adding-docker-support"></a>建立 ASP.NET Core Web 應用程式並新增 Docker 支援

1. 藉由移至 [檔案] > [新增解決方案] 來建立新解決方案。
1. 在 [ **.Net Core > 應用** 程式] 下，選擇 [ **Web 應用程式** ] 範本： ![ 建立新的 ASP.NET 應用程式](media/docker-quickstart-1.png)
1. 選取目標 Framework。 在此範例中，我們將使用 .NET Core 2.2： ![ 設定目標 framework](media/docker-quickstart-2.png)
1. 輸入專案詳細資料，例如，名稱 (此範例中為 _DockerDemo_)。 所建立的專案包含建置和執行 ASP.NET Core 網站所需的所有基本項目。
1. 在 [方案] 視窗中，以滑鼠右鍵按一下 >dockerdemo 專案，然後選取 [ **新增] > 新增 Docker 支援**： ![ 新增 docker 支援]](media/docker-quickstart-3.png)

Visual Studio for Mac 會將稱為 **docker-compose** 的專案自動新增到解決方案，並將 **Dockerfile** 新增到您的現有專案。

![產生的 Docker 支援檔案](media/docker-quickstart-4.png)

## <a name="dockerfile-overview"></a>Dockerfile 概觀

Dockerfile 是用於建立最終 Docker 映像的配方。 請參閱 [Dockerfile 參考](https://docs.docker.com/engine/reference/builder/) ，以瞭解其內的命令。

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY DockerDemo/DockerDemo.csproj DockerDemo/
RUN dotnet restore "DockerDemo/DockerDemo.csproj"
COPY . .
WORKDIR "/src/DockerDemo"
RUN dotnet build "DockerDemo.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "DockerDemo.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "DockerDemo.dll"]
```

上述的 *Dockerfile* 以 [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) 映像為基礎，其中包含藉由建置專案並將其新增至容器來修改基底映像的指示。

> [!NOTE]
> 由 Visual Studio for Mac 中建立的預設 Dockerfile 為 HTTP 流量公開連接埠 80。 若要啟用 HTTPS 流量，請將 `Expose 443` 新增至 Dockerfile。

## <a name="debugging"></a>偵錯

選取 `docker-compose` 專案作為 [啟始專案] 並開始偵錯 ([執行] > [開始偵錯])。 這會在容器中建置、部署並啟動 ASP.NET 專案。

> [!TIP]
> 在安裝 Docker Desktop 後第一次執行時，您可能會在進行偵錯時收到下列錯誤：`Cannot start service dockerdemo: Mounts denied`
>
> 請將 `/usr/local/share/dotnet/sdk/NuGetFallbackFolder` 新增到 Docker Desktop 中的 [File Sharing] \(檔案共用\) 索引標籤：
>
> ![將 [NuGetFallbackFolder] 資料夾新增至 [File Sharing] \(檔案共用\)](media/docker-quickstart-5.png)

當組建完成時，應用程式會在 Safari 中啟動：

![在 Safari 中執行的預設 Docker 專案](media/docker-quickstart-6.png)

請注意，容器會接聽連接埠 (例如，`http://localhost:32768`)，而此連接埠可能會不同。

若要查看執行中容器的清單，請在 [終端機] 中使用 `docker ps` 命令。

請注意以下螢幕擷取畫面中的連接埠轉送 (在 **PORTS** 底下)。 此圖顯示容器正在接聽之前在 Safari 中所見的連接埠，並將要求轉送到內部 Webserver 的連接埠 80 (如 Dockerfile 中所定義) 上。 從應用程式的觀點來看，它在接聽連接埠 80：

![Docker 容器清單](media/docker-quickstart-7.png)
