---
title: 將ASP.NET核心 Docker 容器部署到 Docker 集線器 |微軟文檔
description: 瞭解如何使用視覺化工作室容器工具將ASP.NET核心 Web 應用部署到 Docker Hub
author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: article
ms.date: 07/23/2019
ms.author: ghogen
ms.openlocfilehash: b033825bbe8facbeae3dcdee6a5b563461921522
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "73188756"
---
# <a name="deploy-to-docker-hub"></a>發佈至 Docker Hub

Docker Hub 為您的映射存儲庫提供了方便的託管服務。 您可以輕鬆地從視覺化工作室手動部署到 Docker 集線器。

## <a name="create-a-docker-account-and-docker-hub-repository"></a>創建 Docker 帳戶和 Docker 中心存儲庫

如果您還沒有 Docker 帳戶，請[註冊](https://hub.docker.com/signup)。

如果沒有 Docker Hub 存儲庫，請在[Docker 中心](https://hub.docker.com/)創建一個存儲庫。

## <a name="publish-the-image-for-a-single-project-to-docker-hub"></a>將單個專案的圖像發佈到 Docker 中心

1. 按右鍵專案節點並選擇 **"發佈..."** 將顯示顯示部署選項的螢幕。

   ![](media/deploy-docker-hub/container-tools-docker-hub-deploy.png)

1. 在 **"選擇發佈目標**"下，選擇**容器註冊表**，然後選擇**Docker 集線器**。 將顯示**Docker 中心**對話方塊。

   ![](media/deploy-docker-hub/container-tools-docker-hub-credentials.png)

1. 如果要連接到自己的存儲庫（不是組織的一部分），請選中 **"發佈到個人存儲庫**"核取方塊。 如果存儲庫為組織所有，請清除該核取方塊，然後輸入組織名稱。 輸入您擁有訪問要連接到的存儲庫的許可權的 Docker 帳戶的 Docker 使用者名和密碼，然後選擇"**保存**"。  

   視覺化工作室嘗試將映射部署到 Docker 中心。  如果成功，"**發佈"** 螢幕將顯示存儲庫映射的 URL、圖像標記、存儲庫和組建組態*（例如，**發佈**）。

   ![](media/deploy-docker-hub/container-tools-docker-hub-finished.png)

1. 您可以隨時按一下此頁面上的 **"發佈"** 按鈕來更新圖像。  或者，您可以使用 URL 下方的連結修改或刪除設定檔。

## <a name="next-steps"></a>後續步驟

按照[部署到 Azure 容器註冊表](hosting-web-apps-in-docker.md)中的步驟發佈到[Azure 容器](/azure/container-registry/)註冊表。

設置與[Azure 管道](/azure/devops/pipelines/?view=azure-devops)的持續集成和傳遞 （CI/CD）。

## <a name="see-also"></a>另請參閱

[部署到 Azure 應用程式服務](deploy-app-service.md)
[視覺化工作室容器工具](/visualstudio/containers/)。