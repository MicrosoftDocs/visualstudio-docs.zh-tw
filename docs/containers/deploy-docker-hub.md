---
title: 將 ASP.NET Core Docker 容器部署至 Docker Hub |Microsoft Docs
description: 瞭解如何使用 Visual Studio 容器工具將 ASP.NET Core web 應用程式部署至 Docker Hub
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 07/23/2019
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: cd17726d5ba09dcb901fd529e6bdfd97dee52f31
ms.sourcegitcommit: 2c26d6e6f2a5c56ae5102cdded7b02f2d0fd686c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2020
ms.locfileid: "88168623"
---
# <a name="deploy-to-docker-hub"></a>發佈至 Docker Hub

Docker Hub 為您的映射存放庫提供便利的主機服務。 您可以輕鬆地從 Visual Studio 手動部署至 Docker Hub。

## <a name="create-a-docker-account-and-docker-hub-repository"></a>建立 Docker 帳戶和 Docker Hub 存放庫

[註冊](https://hub.docker.com/signup)Docker 帳戶（如果還沒有的話）。

如果您沒有 Docker Hub 存放庫，請在[Docker hub](https://hub.docker.com/)建立一個。

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>將單一專案的映射發佈至 Docker Hub

1. 以滑鼠右鍵按一下專案節點，然後選擇 [**發佈 ...**]。顯示部署選項的畫面隨即出現。

   ![部署選項的螢幕擷取畫面](media/container-tools/vs-2019/docker-container-registry.png)

1. 選擇 [ **Docker Container Registry**]，然後選擇 [ **docker Hub**]。

   ![[發佈] 對話方塊的螢幕擷取畫面-選擇 [Docker Hub]](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. 輸入您的 Docker 認證。

   ![[Docker Hub] 對話方塊的螢幕擷取畫面](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. 如果您要連線到您自己的存放庫， (不是組織) 的一部分，請將 [**發行至個人存放庫**] 核取方塊保持核取狀態。 如果存放庫是由組織所擁有，請清除此核取方塊，然後輸入組織名稱。 針對您的 Docker 帳戶，輸入有權存取您所連接之儲存機制的 Docker 使用者名稱和密碼，然後選取 [**儲存**]。  

   Visual Studio 嘗試將您的映射部署至 Docker Hub。  如果成功，[**發佈**] 畫面會顯示存放庫影像的 URL、影像標籤、存放庫和組建設定 (例如 [**發行**) ]。

   ![[發佈] 畫面的螢幕擷取畫面](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. 您可以隨時按一下此頁面上的 [**發佈**] 按鈕來更新映射。  或者，您可以使用 URL 底下的連結來修改或移除設定檔。

## <a name="next-steps"></a>後續步驟

遵循[部署至 Azure Container Registry](hosting-web-apps-in-docker.md)中的步驟，發佈至[Azure Container Registry](/azure/container-registry/) 。

使用[Azure Pipelines](/azure/devops/pipelines/?view=azure-devops)來設定持續整合和傳遞 (CI/CD) 。

## <a name="see-also"></a>請參閱

[部署至 Azure App Service](deploy-app-service.md) 
[Visual Studio 容器工具](/visualstudio/containers/)。