---
title: 將ASP.NET Docker 容器部署到 ACR 註冊表
description: 瞭解如何使用 Visual Studio 容器工具將ASP.NET或 ASP.NET核心 Web 應用部署到容器註冊表
author: ghogen
manager: jillfra
ms.assetid: e5e81c5e-dd18-4d5a-a24d-a932036e78b9
ms.devlang: dotnet
ms.topic: conceptual
ms.technology: vs-azure
ms.date: 03/14/2019
ms.author: ghogen
ms.openlocfilehash: cfed918633f62700f464ee5f9911fbbfc6463c36
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75916919"
---
# <a name="deploy-an-aspnet-container-to-a-container-registry-using-visual-studio"></a>使用 Visual Studio 將 ASP.NET 容器部署到容器登錄

## <a name="overview"></a>概觀

Docker 是輕量級容器引擎，與虛擬機器在某些方面類似，您可以用它來裝載應用程式和服務。
本教學課程會引導您使用 Visual Studio，將容器化應用程式發佈至 [Azure Container Registry](https://azure.microsoft.com/services/container-registry)。

如果您沒有 Azure 訂用帳戶，請在開始前建立[免費帳戶](https://azure.microsoft.com/free/dotnet/?utm_source=acr-publish-doc&utm_medium=docs&utm_campaign=docs)。

## <a name="prerequisites"></a>必要條件

若要完成本教學課程：

::: moniker range="vs-2017"
* 安裝最新版本的[Visual Studio 2017，](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)具有"ASP.NET和 Web 開發"工作負載
::: moniker-end
::: moniker range=">=vs-2019"
* 使用"ASP.NET和 Web 開發"工作負載安裝最新版本的[Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
::: moniker-end
* [安裝用於 Windows 的 Docker](https://docs.docker.com/docker-for-windows/install/)

## <a name="create-an-aspnet-core-web-app"></a>建立 ASP.NET Core Web 應用程式
下列步驟會逐步引導您建立將在本教學課程中使用的基本 ASP.NET Core 應用程式。 如果您已有專案，則可以跳過此部分。

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">=vs-2019"
[!INCLUDE [create-aspnet5-app](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

## <a name="publish-your-container-to-azure-container-registry"></a>將容器發佈至 Azure Container Registry
1. 在**方案總管**中以滑鼠右鍵按一下專案，並選擇 [發佈]****。
2. 在 [發佈目標] 對話方塊中，選取 [容器登錄]**** 索引標籤。
3. 選擇 [新 Azure Container Registry]**** 然後按一下 [發佈]****。
4. 在 [建立新的 Azure Container Registry]**** 中填入您想要的值。

    | 設定      | 建議的值  | 描述                                |
    | ------------ |  ------- | -------------------------------------------------- |
    | **DNS 首碼** | 全域唯一的名稱 | 用以唯一識別容器登錄的名稱。 |
    | **訂閱** | 選擇您的訂用帳戶 | 要使用的 Azure 訂用帳戶。 |
    | **[資源組](/azure/azure-resource-manager/resource-group-overview)** | myResourceGroup |  要在其中建立容器登錄的資源群組名稱。 選擇 [新增]**** 以建立新的資源群組。|
    | **[Sku](/azure/container-registry/container-registry-skus)** | 標準 | 容器登錄的服務層  |
    | **登錄位置** | 接近您的位置 | 在[區域](https://azure.microsoft.com/regions/)中選擇您附近的 [位置]，或選擇將會使用容器登錄的其他服務所接近的位置。 |

    ![Visual Studio 的 [建立 Azure Container Registry] 對話方塊](media/hosting-web-apps-in-docker/vs-acr-provisioning-dialog.png)

5. 按一下 **"創建"**

您現在可以從登錄中，將容器提取至能夠執行 Docker 映像的任何主機，例如 [Azure 容器執行個體](/azure/container-instances/container-instances-tutorial-deploy-app)。

## <a name="see-also"></a>另請參閱

[快速入門：使用 Azure CLI 在 Azure 中部署容器實例](/azure/container-instances/container-instances-quickstart)
