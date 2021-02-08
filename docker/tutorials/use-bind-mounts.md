---
title: Docker 教學課程-第5部分：使用系結裝載
description: 說明如何使用系結裝載來控制主機上的掛接點。
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 57cb56d0d9a93d0f11e4047f6e25b64841c47e93
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841675"
---
# <a name="use-bind-mounts"></a>使用系結裝載

在上一章中，您已瞭解並使用 **命名磁片** 區，將資料保存在您的資料庫中。 如果您只是想要儲存資料，則命名磁片區非常好用，因為您不需要擔心資料的儲存 *位置* 。

使用系結 **裝載**，您可以控制主機上的確切掛接點。 您可以使用此項來保存資料，但通常用來將其他資料提供給容器。 使用應用程式時，您可以使用系結裝載將原始程式碼裝載至容器，讓它查看程式碼變更、回應，並讓您立即看到變更。

針對以節點為基礎的應用程式， [nodemon](https://npmjs.com/package/nodemon) 是很棒的工具，可監看檔案變更，然後重新開機應用程式。 大部分其他語言和架構都有同等的工具。

## <a name="quick-volume-type-comparisons"></a>快速磁片區類型比較

系結裝載和命名磁片區是 Docker 引擎隨附的兩個主要磁片區類型。 不過，其他的磁片區驅動程式可支援其他使用案例 ([SFTP](https://github.com/vieux/docker-volume-sshfs)、 [Ceph](https://ceph.com/geen-categorie/getting-started-with-the-docker-rbd-volume-plugin/)、 [NetApp](https://netappdvp.readthedocs.io/en/stable/)、 [S3](https://github.com/elementar/docker-s3-volume)及更多) 。

| 屬性 | 具名磁碟區 | 繫結裝載 |
| -------- | ------------- | ----------- |
| 主機位置 | Docker 選擇 | 您可以控制 |
| 使用) 掛接範例 (`-v` | my volume：/usr/local/data | /path/to/data:/usr/local/data |
| 以容器內容填入新的磁片區 | 是 | 否 |
| 支援磁片區驅動程式 | 是 | 否 |

## <a name="start-a-dev-mode-container"></a>啟動開發模式容器

若要執行容器來支援開發工作流程，請執行下列動作：

- 將您的原始程式碼掛接到容器中
- 安裝所有相依性，包括「dev」相依性
- 開始 nodemon 以監看檔案系統變更

1. 確定您沒有任何先前執行 `getting-started` 的容器。

1. 執行下列命令， (` \ ` `` ` `` 以 Windows PowerShell) 取代字元。 您將瞭解之後的進展：

    ```bash
    docker run -dp 3000:3000 \
        -w /app -v ${PWD}:/app \
        node:12-alpine \
        sh -c "yarn install && yarn run dev"
    ```

    - `-dp 3000:3000` -與之前相同。 在卸離 (背景) 模式中執行，並建立埠對應
    - `-w /app` -設定要執行命令的「工作目錄」或目前目錄
    - `-v ${PWD}:/app` -將目前目錄從容器中的主機掛接到 `/app` 目錄中
    - `node:12-alpine` -要使用的映射。 請注意，這是您的應用程式從 Dockerfile 的基礎映射
    - `sh -c "yarn install && yarn run dev"` -命令。 我們正在使用 `sh` (alpine 啟動 shell 沒有 `bash`) 並正在執行， `yarn install` 以安裝 *所有* 相依性，然後執行 `yarn run dev` 。 如果您查看 `package.json` ，我們會看到 `dev` 腳本正在啟動 `nodemon` 。

1. 您可以使用來觀賞記錄 `docker logs -f <container-id>` 。 當您看到這種情況時，您會知道您已經準備好了：

    ```bash
    docker logs -f <container-id>
    $ nodemon src/index.js
    [nodemon] 1.19.2
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching dir(s): *.*
    [nodemon] starting `node src/index.js`
    Using sqlite database at /etc/todos/todo.db
    Listening on port 3000
    ```

    當您完成監看記錄之後，請按 [結束] `Ctrl` + `C` 。

1. 現在，對應用程式進行變更。 在檔案中 `src/static/js/app.js` ，將 [ **加入專案** ] 按鈕變更為 [ **加入**]。 這種變更將會在第109行。

    ```diff
    -                         {submitting ? 'Adding...' : 'Add Item'}
    +                         {submitting ? 'Adding...' : 'Add'}
    ```

1. 只要重新整理頁面 (或) 開啟，您應該會立即看到變更反映在瀏覽器中。 節點伺服器可能需要幾秒鐘的時間才會重新開機，因此如果您收到錯誤，請在幾秒鐘後嘗試重新整理。

    ![[新增] 按鈕的已更新標籤螢幕擷取畫面](media/updated-add-button.png)

1. 您可以隨意進行任何其他想要進行的變更。 當您完成時，請停止容器，並使用建立新的映射 `docker build -t getting-started .` 。

在本機開發環境中，使用系結裝載 *非常* 常見。 優點在於開發電腦不需要安裝所有的組建工具和環境。 使用單一 `docker run` 命令，就會提取開發環境並準備好開始使用。 您將在未來的步驟中瞭解 Docker Compose，因為這有助於簡化您的命令， (您已經取得許多旗標) 。

## <a name="recap"></a>概括回顧

至此，您可以保存資料庫，並快速回應投資者和創辦人的需求和需求。 萬歲！ 但是，猜到什麼呢？ 您已收到絕佳新聞！

**已選取您的專案進行未來的開發！**

為了準備生產環境，您需要將您的資料庫從 SQLite 中的工作遷移到可以更妥善擴充的事物。 為了簡單起見，您將會繼續使用關係資料庫，並將您的應用程式切換為使用 MySQL。 但是，您應該如何執行 MySQL？ 您要如何讓容器互相溝通？ 您將會瞭解下一步！

## <a name="next-steps"></a>下一步

繼續進行本教學課程！

> [!div class="nextstepaction"]
> [多容器應用程式](multi-container-apps.md)