---
title: Docker 教學課程-第4部分：保存您的資料
description: 瞭解如何藉由裝載磁片區，將資料保存在資料庫中，並將目錄共用到容器中。
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: c9408e099caaef097be3fc4eea26cee2b1889e8e
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222899"
---
# <a name="persist-your-data"></a> 保存您的資料

如果您未注意到，每次您啟動容器時，就會清除 todo 清單。 這是為什麼？ 讓我們深入瞭解容器的運作方式。

## <a name="the-containers-filesystem"></a>容器的檔案系統

當容器執行時，它會使用映射中的各種層級作為檔案系統。 每個容器也會取得自己的「臨時空間」，以建立、更新或移除檔案。 任何變更都不會顯示在另一個容器中， *即使* 它們使用相同的映射也一樣。

### <a name="see-this-in-practice"></a>在實務上查看

若要查看其實際運作情形，您將會啟動兩個容器，並在每個容器中建立一個檔案。 您將會看到，在一個容器中建立的檔案無法在另一個容器中使用。

1. 啟動一個 `ubuntu` 容器，該容器會建立名為 `/data.txt` 的檔案，並以介於1到10000之間的亂數來建立檔案。

    ```bash
    docker run -d ubuntu bash -c "shuf -i 1-10000 -n 1 -o /data.txt && tail -f /dev/null"
    ```

    如果您對命令感到好奇，則會啟動 bash shell，並叫用兩個命令 (它有) 的原因 `&&` 。 第一個部分會挑選單一亂數字，並將其寫入 `/data.txt` 。 第二個命令只是監看檔案，讓容器保持執行狀態。

1. 驗證您可以使用取得容器來查看輸出 `exec` 。 若要這樣做，請開啟 VS Code 擴充功能，然後按一下 [**附加 Shell** ] 選項。 這會用 `exec` 來在 VS Code 終端機內的容器中開啟 shell。

    ![VS Code 將 CLI 開啟至 ubuntu 容器](media/attach_shell.png)

    您會看到在 Ubuntu 容器中執行 shell 的終端機。 執行下列命令以查看檔案的內容 `/data.txt` 。 再次關閉此終端機。

    ```bash
    cat /data.txt
    ```

    如果您偏好命令列，您可以使用 `docker exec` 命令來執行相同的動作。 您需要取得容器的識別碼 (用 `docker ps` 來取得它) 並使用下列命令取得內容。

    ```bash
    docker exec <container-id> cat /data.txt
    ```

    您應該會看到一個亂數字！

1. 現在，啟動另一個 `ubuntu` 容器 (相同的映射) ，您會看到您沒有相同的檔案。

    ```bash
    docker run -it ubuntu ls /
    ```

    然後看看！ 沒有檔案 `data.txt` ！ 這是因為它只會寫入至第一個容器的臨時空間。

1. 繼續並使用命令移除第一個容器 `docker rm -f` 。

## <a name="container-volumes"></a>容器磁片區

在先前的實驗中，您會看到每個容器每次啟動時都會從映射定義開始。 雖然容器可以建立、更新和刪除檔案，但在移除容器時，這些變更會遺失，而且所有變更都已隔離至該容器。 您可以使用磁片區來變更所有的磁片區。

[磁片](https://docs.docker.com/storage/volumes/) 區可讓您將容器的特定檔案系統路徑連接回主機電腦。 如果裝載容器中的目錄，該目錄中的變更也會顯示在主機電腦上。 如果您跨容器重新開機裝載相同的目錄，您會看到相同的檔案。

磁片區有兩種主要類型。 您最終會使用這兩種方式，但您將從 **命名磁片** 區開始。

## <a name="persist-your-todo-data"></a>保存您的 Todo 資料

根據預設，待辦事項應用程式會將其資料儲存在 [SQLite 資料庫](https://www.sqlite.org/index.html) 的中 `/etc/todos/todo.db` 。 如果您不熟悉 SQLite，別擔心！ 這只是一種關係資料庫，其中所有的資料都儲存在單一檔案中。 雖然這不是大型應用程式的最佳選擇，但適用于小型的示範。 我們稍後會討論如何將此功能切換到實際的資料庫引擎。

當資料庫是單一檔案時，如果您可以將該檔案保存在主機上，並將它提供給下一個容器使用，它應該就可以從最後一個容器中挑選最後一個。 藉由建立磁片區並將 (（通常稱為「掛接」） ) 至儲存資料的目錄，您就可以保存資料。 當容器寫入檔案時 `todo.db` ，它會保存到磁片區中的主機。

如前所述，您將使用 **命名磁片** 區。 將命名磁片區視為只是資料的 bucket。 Docker 會維護磁片上的實體位置，而您只需要記住磁片區的名稱。 每次使用磁片區時，Docker 都會確保提供正確的資料。

1. 使用命令建立磁片區 `docker volume create` 。

    ```bash
    docker volume create todo-db
    ```

1. 在 Docker view (中再次停止 todo 應用程式容器，或使用 `docker rm -f <id>`) ，因為它仍在執行，而不使用永久性磁片區。

1. 啟動 todo 應用程式容器，但新增 `-v` 旗標來指定磁片區掛接。 您將使用命名磁片區並將其掛接至 `/etc/todos` ，以抓取路徑上建立的所有檔案。

    ```bash
    docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started
    ```

1. 容器啟動後，開啟應用程式，並將一些專案新增至待辦事項清單。

    ![加入待辦事項清單的專案](media/items-added.png)

1. 移除 todo 應用程式的容器。 使用 Docker view 或 `docker ps` 取得識別碼，然後將 `docker rm -f <id>` 其移除。

1. 使用與上述相同的命令來啟動新的容器。

1. 開啟應用程式。 您應該會看到您的專案仍在清單中！

1. 當您完成簽出列表之後，請繼續並移除容器。

萬歲！ 您現在已瞭解如何保存資料！

> [!TIP]
> 當命名磁片區和系結掛接 (，我們會在一分鐘內討論) 是預設 Docker 引擎安裝所支援的兩種主要磁片區類型，有許多磁片磁碟機外掛程式可支援 NFS、SFTP、NetApp 和更多功能！ 當您在具有 Swarm、Kubernetes 等的叢集環境中的多部主機上開始執行容器時，這將特別重要。

## <a name="dive-into-your-volume"></a>深入瞭解您的磁片區

很多人常問「當我使用命名磁片區時，Docker 會 *實際* 儲存我的資料嗎？」 如果您想知道，可以使用 `docker volume inspect` 命令。

```bash
docker volume inspect todo-db
[
    {
        "CreatedAt": "2019-09-26T02:18:36Z",
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/var/lib/docker/volumes/todo-db/_data",
        "Name": "todo-db",
        "Options": {},
        "Scope": "local"
    }
]
```

`Mountpoint`是儲存資料之磁片上的實際位置。 請注意，在大部分的電腦上，您必須具有根目錄存取權，才能從主機存取此目錄。 但那就是！

> [!NOTE]
> **直接在 Docker 桌面上存取磁片區資料** 在 Docker Desktop 中執行時，Docker 命令實際上是在您電腦上的小型 VM 內執行。 如果您想要查看 *裝入* 點目錄的實際內容，您必須先取得 VM 內的內容。 在 WSL 2 中，這會在 WSL 2 發行版本內，並可透過檔案總管存取。

## <a name="recap"></a>概括回顧

至此，您有一個可正常運作的應用程式，可以繼續重新開機！ 您可以向投資者展示，希望他們能夠趕上您的願景！

不過，您稍早看到針對每項變更重建映射需要相當長的時間。 有更好的方式可以進行變更，對吧？ 使用系結裝載 (我們在稍早) 提示的情況下，有更好的方法！ 現在就來看看這是什麼！

## <a name="next-steps"></a>下一步

繼續進行本教學課程！

> [!div class="nextstepaction"]
> [使用系結裝載](use-bind-mounts.md)
