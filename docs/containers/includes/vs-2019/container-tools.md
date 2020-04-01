---
title: 帶ASP.NET的 Docker 視覺化工作室工具
author: ghogen
description: 瞭解如何使用 Visual Studio 2019 工具和 Windows Docker
ms.author: ghogen
ms.date: 02/01/2019
ms.prod: visual-studio-dev16
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: bd9ac1bda9cb5f5d9cc5d84248200434426307c8
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2020
ms.locfileid: "80501384"
---
借助 Visual Studio,可以輕鬆地構建、調試和運行容器化的 .NET、ASP.NET 和ASP.NET核心應用,並將它們發布到 Azure 容器註冊表 (ACR)、Docker Hub、Azure 應用服務或您自己的容器註冊表。 在本文中,我們將向 ACR 發佈ASP.NET核心應用。

## <a name="prerequisites"></a>Prerequisites

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* 已安裝**網頁程式開發**、**Azure Tools** 工作負載及(或) **.NET Core 跨平台開發** 工作負載的 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
* [.NET 核心開發工具](https://dotnet.microsoft.com/download/dotnet-core/),用於 .NET 核心開發
* 發佈至 Azure Container Registry (Azure 訂用帳戶)。 [註冊免費試用](https://azure.microsoft.com/offers/ms-azr-0044p/)。

## <a name="installation-and-setup"></a>安裝與設定

對 Docker 安裝,首先檢視[Windows 的 Docker 桌面資訊:安裝 之前需要瞭解哪些內容](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install)。 接下來，安裝 [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)。

## <a name="add-a-project-to-a-docker-container"></a>將專案新增至 Docker 容器

1. 使用**ASP.NET核心 Web 應用程式**樣本建立新專案,或者如果要使用 .NET 框架而不是 .NET Core,請選擇 ASP.NET Web 應用程式 **(.NET Framework)**。
1. 選擇**Web 應用程式**,並確保選擇了 啟用**Docker 支援**複選方塊。

   ![啟用 Docker 支援核取方塊](../../media/container-tools/vs-2019/create-new-web-application.PNG)

   屏幕截圖顯示 .NET 核心;如果您使用的是 .NET 框架,它看起來有點不同。

1. 選取您想要的容器類型 (Windows 或 Linux)，然後按一下 [建立]****。

## <a name="dockerfile-overview"></a>Dockerfile 概觀

*Dockerfile* 是用於建立最終 Docker 映像的配方，會在專案中建立。 請參閱 [Dockerfile reference](https://docs.docker.com/engine/reference/builder/) (Dockerfile 參考) 以了解其中的命令：

```
FROM microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM microsoft/dotnet:2.2-sdk-stretch AS build
WORKDIR /src
COPY ["HelloDockerTools/HelloDockerTools.csproj", "HelloDockerTools/"]
RUN dotnet restore "HelloDockerTools/HelloDockerTools.csproj"
COPY . .
WORKDIR "/src/HelloDockerTools"
RUN dotnet build "HelloDockerTools.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "HelloDockerTools.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "HelloDockerTools.dll"]
```

上述的 *Dockerfile* 以 [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) 映像為基礎，其中包含藉由建置專案並將其新增至容器來修改基底映像的指示。 如果使用 .NET 框架,則基本映射將有所不同。

核取新專案對話方塊的 [設定 HTTPS]**** 核取方塊時，*Dockerfile* 會提供兩個連接埠。 其中一個連接埠用於 HTTP 流量，另一個連接埠則用於 HTTPS。 如果未選取該核取方塊，則會為 HTTP 流量提供單一連接埠 (80)。

## <a name="debug"></a>偵錯

從工具列的偵錯下拉式清單中選取 [Docker]****，然後開始對應用程式進行偵錯。 您可能會看到提示信任憑證的訊息，請選擇信任憑證以繼續進行。

[輸出]**** 視窗中的 [容器工具]**** 選項會顯示要採取哪些動作。 第一次,可能需要一段時間才能下載基本映射,但在後續運行時速度要快得多。

>[!NOTE]
> 如果需要更改埠進行調試,可以在*啟動設置.json*檔中執行此操作。 請參考[容器啟動設定](../../container-launch-settings.md)。

## <a name="containers-window"></a>容器視窗

如果您有 Visual Studio 2019 版本 16.4 或更高版本,則可以使用 **「容器」** 視窗查看電腦上的正在執行的容器以及可用的圖像。

使用 IDE 中的搜尋框開啟**容器**視窗(按**Ctrl**+`container`**Q**將其使用)、鍵入 ,並從清單中選擇 **「容器」** 視窗。

您可以通過移動容器視窗並遵循視窗放置指南,將**容器**視窗安裝在方便的位置(如編輯器下方)。

在視窗中,查找容器並單步執行每個選項卡以查看環境變數、埠映射、日誌和檔案系統。

![容器視窗的螢幕擷取](../../media/overview/vs-2019/container-tools-window.png)

有關詳細資訊,請參閱在[Visual Studio 中查看和診斷容器和影像](../../view-and-diagnose-containers.md)。

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
    | **訂用帳戶** | 選擇您的訂用帳戶 | 要使用的 Azure 訂用帳戶。 |
    | **[資源群組](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  要在其中建立容器登錄的資源群組名稱。 選擇 [新增]**** 以建立新的資源群組。|
    | **[Sku](/azure/container-registry/container-registry-skus)** | 標準 | 容器登錄的服務層  |
    | **登錄位置** | 接近您的位置 | 在[區域](https://azure.microsoft.com/regions/)中選擇您附近的 [位置]，或選擇將會使用容器登錄的其他服務所接近的位置。 |

    ![Visual Studio 的 [建立 Azure Container Registry] 對話方塊][0]

1. 按下 **"創建"**

   ![顯示成功發佈的螢幕擷取畫面](../../media/container-tools/publish-succeeded.png)

## <a name="next-steps"></a>後續步驟

您現在可以從登錄中，將容器提取至能夠執行 Docker 映像的任何主機，例如 [Azure 容器執行個體](/azure/container-instances/container-instances-tutorial-deploy-app)。

[0]:../../media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog-2019.png
