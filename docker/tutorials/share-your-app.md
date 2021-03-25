---
title: Docker 教學課程-第3部分：共用您的應用程式
description: 說明如何使用 Docker Hub 登錄共用 Docker 映射。
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: ad9f7d329bf00e3fadd665cefea22a2301fdf695
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061780"
---
# <a name="share-your-app"></a>共用您的應用程式

現在我們已建立映射，讓我們分享！ 若要共用 Docker 映射，您必須使用 Docker registry。 預設的登錄是 Docker Hub，也就是我們使用的所有映射的來源。

## <a name="create-a-repo"></a>建立存放庫

若要推送映射，您必須先在 Docker Hub 上建立存放庫。

1. 移至 [Docker Hub](https://hub.docker.com/signup/msftedge?utm_source=msftedge) 並登入（如果需要）。

1. 按一下 [ **建立存放庫** ] 按鈕。

1. 針對存放庫名稱，請使用 `getting-started` 。 請確定可見度為 `Public` 。

1. 按一下 [ **建立** ] 按鈕！

如果您查看頁面的右側，您會看到名為 **Docker 命令** 的區段。 這會提供一個範例命令，您需要執行此命令才能推送至此存放庫。

![具有推送範例的 Docker 命令](media/push-command.png)

## <a name="push-the-image"></a>推送映像

1. 在命令列中，嘗試執行您在 Docker Hub 上看到的 push 命令。 請注意，您的命令將會使用您的命名空間，而不是 "docker"。

    ```plaintext
    $ docker push docker/getting-started
    The push refers to repository [docker.io/docker/getting-started]
    An image does not exist locally with the tag: docker/getting-started
    ```

    為何失敗？ Push 命令正在尋找名為 docker/開始使用的映射，但找不到它。 如果您執行 `docker image ls` ，您將不會看到其中一種。

    若要修正此問題，您必須「標記」我們所建立的現有映射，以提供另一個名稱。

1. 使用命令登入 Docker Hub `docker login -u <username>` 。

1. 使用 `docker tag` 命令為 `getting-started` 映射提供新的名稱。 請務必 `<username>` 與您的 DOCKER ID 交換。

    ```bash
    docker tag getting-started <username>/getting-started
    ```

1. 現在，請再次嘗試您的 push 命令。 如果您要從 Docker Hub 複製值，您可以卸載 `tagname` 部分，因為您未將標籤新增至映射名稱。 如果您未指定標籤，Docker 會使用名為的標記 `latest` 。

    ```bash
    docker push <username>/getting-started
    ```

    除了命令列之外，您也可以在 Docker view 的 [ **Images** ] 區段中，以滑鼠右鍵按一下映射標籤，然後選擇 [ **推送 ...**]，然後選擇 [連線登錄 **...]** ，再 **Docker Hub**。

## <a name="run-the-image-on-a-new-instance"></a>在新的實例上執行映射

既然您已建立映射並將其推送至登錄，請嘗試在從未見過此容器映射的全新實例上執行應用程式！ 若要這樣做，您將使用 Docker 的 Play。

1. 開啟您的瀏覽器以 [播放 Docker](http://play-with-docker.com)。

1. 使用您的 Docker Hub 帳戶登入。

1. 登入後，按一下左側工具列中的 [+ 新增實例] 連結。  (如果您沒有看到它，請讓您的瀏覽器變得更多 ) 。在幾秒鐘後，就會在瀏覽器中開啟終端機視窗。

    ![使用 Docker 新增實例來播放](media/pwd-add-new-instance.png)

1. 在終端機中，啟動剛剛推送的應用程式。

    ```bash
    docker run -dp 3000:3000 <username>/getting-started
    ```

    您應該會看到影像獲得拉下，最後才會啟動！

1. 當您出現3000徽章時，請按一下它，您應該會看到該應用程式有您的修改！ 萬歲！ 如果3000徽章未顯示，您可以按一下 [ **開啟埠** ] 按鈕，然後輸入3000。

## <a name="recap"></a>概括回顧

在本節中，您已瞭解如何藉由將映射推送至登錄來共用映射。 然後，您會進入全新的實例，而且能夠執行剛剛推送的映射。 這在 CI 管線中很常見，因為管線會建立映射並將其推送至登錄，然後生產環境才能使用最新版本的映射。

既然您已經知道，在上一節的結尾，當您重新開機應用程式時，就會遺失所有的 todo 清單專案。 這顯然不是絕佳的使用者體驗，因此您將會瞭解如何在重新開機時保存資料！

## <a name="next-steps"></a>下一步

繼續進行本教學課程！

> [!div class="nextstepaction"]
> [保存資料庫](persist-your-data.md)
