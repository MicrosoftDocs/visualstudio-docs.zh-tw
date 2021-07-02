---
title: Docker 教學課程-第9部分：部署至雲端
description: 將 docker 應用程式部署至雲端服務以進行裝載。
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: da38b7482396b0bf46f5566c0c4a5416c94e83eb
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222821"
---
# <a name="deploy-to-the-cloud"></a>部署至雲端

現在您已在本機執行您的應用程式，您可以開始思考如何在雲端中執行應用程式，讓其他人可以存取並使用它。 若要這樣做，您將使用 Docker 內容。 內容是您目前正在使用容器的位置。 現在，您只會有「預設」內容，因此您必須新增雲端應用程式，並將您的應用程式部署到其中。

## <a name="create-your-cloud-context"></a>建立您的雲端內容

1. 若要開始，您可以查看 Docker 面板的 [內容] 區段來查看您擁有的內容：

   ![僅顯示預設內容](media/defaultcontext.png)

您應該只會看到本機工作的預設內容。

1. 若要部署至雲端，您需要建立新的 ACI 內容，但若要這樣做，您必須先使用 Azure 帳戶擴充功能來向 Azure 進行驗證。

   ![新增 Azure 擴充功能](media/addazureextension.png)

如果您還沒有 Azure 帳戶，您必須設定一個。

1. 現在您可以建立新的 ACI 內容。 若要這麼做，您可以按一下 Docker **view 內容區段上的加號** 按鈕。

   ![建立 ACI 內容](media/createnewcontext.png)

這會詢問您要執行這些容器的資源群組。 您可以使用方向鍵來選取現有的群組，或使用預設選項來使用新的群組。

![選取您的資源群組](media/selectresourcegroup.png)

您現在可以看到列出的 ACI 內容，並可在其上按一下滑鼠右鍵，使其成為目前的焦點/使用內容：

![可以選取新的 ACI 內容](media/listofcontexts.png)

## <a name="run-containers-in-the-cloud"></a>在雲端中執行容器

1. 現在，使用 ACI 內容並執行容器。

   ```bash
   docker context use myacicontext
   docker run  -dp 3000:3000 <username>/getting-started
   ```

1. 執行這項操作後，現在請查看您內容中的容器。

   ![在 ACI 內容中執行的容器](media/contextcontainer.png)

1. 若要檢查這項作業是否正常運作，您可以在執行中的容器上按一下滑鼠右鍵，然後選擇 [ **在瀏覽器中顯示**]。

   ![ACI 中具有公用 IP 的容器](media/containerinaci.png)

而且，您可以看到容器是在公用 IP 中執行，而且運作正常！

1. 現在，您可以查看執行中的容器，以瞭解其運作方式。 您可以從查看容器記錄開始：
 
 ```bash
   docker logs distracted-jackson
   ```

1. 您也可以執行到容器中，就像使用本機容器一樣。
 
 ```bash
   docker exec -it distracted-jackson sh
   ```

1. 最後，若要清除您的工作空間，並確保您不會被收取繼續執行測試容器的費用，只要以滑鼠右鍵按一下執行中的容器，然後選擇 [ **移除**] 即可。

## <a name="recap"></a>概括回顧

很棒的是，您現在已完成工作負載，並在第一次成功部署至雲端。 您也可以從命令列使用，也可以使用執行 `docker run` `docker compose up` 多容器應用程式，在您的 ACI 內容中執行所有這項作業。 若要深入瞭解如何在雲端中執行容器，請閱讀 [有關使用 ACI](https://docs.docker.com/engine/context/aci-integration/)的擴充檔。

## <a name="next-steps"></a>下一步

繼續進行本教學課程！

> [!div class="nextstepaction"]
> [後續工作](whats-next.md)
