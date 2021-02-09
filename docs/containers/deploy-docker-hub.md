---
title: 將 ASP.NET Core Docker 容器部署至 Docker Hub |Microsoft Docs
description: 瞭解如何使用 Visual Studio 容器工具將 ASP.NET Core web 應用程式部署至 Docker Hub
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 07/23/2019
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: e51088d135d0d2cdcc5d1bcca71f72fed8b73fd2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867655"
---
# <a name="deploy-to-docker-hub"></a>發佈至 Docker Hub

Docker Hub 為您的映射存放庫提供便利的主機服務。 您可以輕鬆地從 Visual Studio 手動部署至 Docker Hub。

## <a name="create-a-docker-account-and-docker-hub-repository"></a>建立 Docker 帳戶並 Docker Hub 儲存機制

[註冊](https://hub.docker.com/signup) Docker 帳戶（如果您還沒有的話）。

如果您沒有 Docker Hub 存放庫，請在 [Docker Hub](https://hub.docker.com/)建立一個。

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>將單一專案的映射發佈至 Docker Hub

1. 以滑鼠右鍵按一下專案節點，然後選擇 [ **發行 ...**]。顯示部署選項的畫面隨即出現。

   ![部署選項的螢幕擷取畫面](media/container-tools/vs-2019/docker-container-registry.png)

1. 選擇 [ **Docker Container Registry**]，然後選擇 [ **Docker Hub**]。

   ![[發佈] 對話方塊的螢幕擷取畫面-選擇 Docker Hub](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. 輸入您的 Docker 認證。

   ![Docker Hub 對話方塊的螢幕擷取畫面](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. 如果您要連線到自己的儲存機制， (不是組織) 的一部分，請將 [ **發佈至個人存放庫** ] 核取方塊保留為已核取。 如果存放庫是由組織所擁有，請清除該核取方塊，然後輸入組織名稱。 為您的 Docker 帳戶輸入您的 Docker 使用者名稱和密碼，該帳戶具有存取您所連接之存放庫的許可權，然後選取 [ **儲存**]。

   Visual Studio 嘗試將您的映射部署到 Docker Hub。  如果成功，[ **發佈** ] 畫面會顯示存放庫影像的 URL、映射標籤、存放庫和組建設定 (例如， **發行**) 。

   ![發佈畫面的螢幕擷取畫面](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. 您可以按一下此頁面上的 [ **發佈** ] 按鈕，隨時更新映射。  或者，您可以使用 URL 下方的連結來修改或移除設定檔。

## <a name="next-steps"></a>下一步

遵循[部署至 Azure Container Registry](hosting-web-apps-in-docker.md)的步驟，發佈至[Azure Container Registry](/azure/container-registry/) 。

使用 [Azure Pipelines](/azure/devops/pipelines/?view=azure-devops&preserve-view=true)來設定持續整合和傳遞 (CI/CD) 。

## <a name="see-also"></a>另請參閱

[部署至 Azure App Service](deploy-app-service.md) 
[Visual Studio 容器工具](./index.yml)。