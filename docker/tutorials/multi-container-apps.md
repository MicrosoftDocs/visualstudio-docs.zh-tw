---
title: Docker 教學課程-第6部分：多容器應用程式
description: 如何設定容器之間的網路功能，以及新增 MySQL 資料庫的容器。
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: d23d1f5d94729741630ee76263fd5b32041e9cfd
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222912"
---
# <a name="multi-container-apps"></a>多容器應用程式

到目前為止，您已在使用單一容器應用程式。 但是，您現在會將 MySQL 新增至應用程式堆疊。 下列問題通常會發生-「MySQL 會在哪裡執行？ 將它安裝在相同的容器中，或分別執行它？」 一般情況下， **每個容器都應該做一件事，並妥善處理。** 有幾個原因：

- 您很可能需要以不同于資料庫的方式調整 Api 和前端
- 個別容器可讓您以隔離方式進行版本和更新版本
- 雖然您可以在本機使用資料庫的容器，但是您可能會想要在生產環境中使用資料庫的受控服務。 您不想要使用您的應用程式來傳送資料庫引擎。
- 執行多個進程將需要進程管理員 (容器只會啟動一個進程) ，這會增加容器啟動/關機的複雜度。

還有其他原因。 因此，您會更新您的應用程式，使其運作方式如下：

![Todo 應用程式已連線至 MySQL 容器](media/multi-app-architecture.png)

## <a name="container-networking"></a>容器網路服務

請記住，容器依預設會在隔離的情況下執行，且不會知道同一部電腦上其他進程或容器的任何相關資訊。 那麼，您要如何讓一個容器與另一個容器交談？ 答案是 **網路** 功能。 現在，您不必是網路工程師 (個歡呼！ ) 。 只要記住此規則 .。。

> [!NOTE]
> 如果有兩個容器位於相同的網路上，則可以互相溝通。 如果不是，則無法。

## <a name="start-mysql"></a>啟動 MySQL

有兩種方式可在網路上放置容器：在啟動時指派，或連接現有的容器。 目前，您將會先建立網路，並在啟動時附加 MySQL 容器。

1. 建立網路。

    ```bash
    docker network create todo-app
    ```

1. 啟動 MySQL 容器並將它連結至網路。 我們也會定義一些環境變數，資料庫將使用這些變數來初始化資料庫 (請參閱[MySQL Docker Hub 清單](https://hub.docker.com/_/mysql/)中的「環境變數」一節)  (` \ ` `` ` `` 以 Windows PowerShell) 取代字元。

    ```bash
    docker run -d \
        --network todo-app --network-alias mysql \
        -v todo-mysql-data:/var/lib/mysql \
        -e MYSQL_ROOT_PASSWORD=secret \
        -e MYSQL_DATABASE=todos \
        mysql:5.7
    ```

    您也會看到指定的 `--network-alias` 旗標。 我們稍後會回頭討論。

    > [!TIP]
    > 您會注意到這裡會使用磁片區名稱並將它掛接到 `todo-mysql-data` ，也 `/var/lib/mysql` 就是 MySQL 儲存其資料的位置。 不過，您永遠不會執行 `docker volume create` 命令。 Docker 會辨識出您想要使用命名磁片區，並自動為您建立一個磁片區。

1. 若要確認資料庫已啟動並執行，請連線到資料庫並確認它是否連接。

    ```bash
    docker exec -it <mysql-container-id> mysql -p
    ```

    當密碼提示出現時，請輸入 **secret**。 在 MySQL shell 中，列出資料庫並確認您看到 `todos` 資料庫。

    ```cli
    mysql> SHOW DATABASES;
    ```

    您應該會看到如下輸出：

    ```plaintext
    +--------------------+
    | Database           |
    +--------------------+
    | information_schema |
    | mysql              |
    | performance_schema |
    | sys                |
    | todos              |
    +--------------------+
    5 rows in set (0.00 sec)
    ```

    萬歲！ 您擁有 `todos` 資料庫，而且已準備好可供使用！

## <a name="connect-to-mysql"></a>連線到 MySQL

現在您知道 MySQL 已啟動並執行，讓我們來使用！ 但是，問題是 .。。如何？ 如果您在相同網路上執行另一個容器，您要如何找到容器 (請記住，每個容器都有自己的 IP 位址) ？

為了瞭解這一點，您將使用 [nicolaka/netshoot](https://github.com/nicolaka/netshoot) 容器，此容器隨附 *許多* 適用于疑難排解或偵測網路問題的工具。

1. 使用映射啟動新的容器 `nicolaka/netshoot` 。 請務必將它連接到相同的網路。

    ```bash
    docker run -it --network todo-app nicolaka/netshoot
    ```

1. 在容器內使用 `dig` 命令，這是有用的 DNS 工具。 查詢主機名稱的 IP 位址 `mysql` 。

    ```bash
    dig mysql
    ```

    您將得到如下所示的輸出 .。。

    ```text
    ; <<>> DiG 9.14.1 <<>> mysql
    ;; global options: +cmd
    ;; Got answer:
    ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 32162
    ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

    ;; QUESTION SECTION:
    ;mysql.             IN  A

    ;; ANSWER SECTION:
    mysql.          600 IN  A   172.23.0.2

    ;; Query time: 0 msec
    ;; SERVER: 127.0.0.11#53(127.0.0.11)
    ;; WHEN: Tue Oct 01 23:47:24 UTC 2019
    ;; MSG SIZE  rcvd: 44
    ```

    在 [回應] 區段中，您會看到一個 `A` 記錄 `mysql` ，該記錄會解析成 `172.23.0.2` (您的 IP 位址很可能會有不同的) 值。 雖然 `mysql` 通常不是有效的主機名稱，但 Docker 能夠將它解析成具有該網路別名的容器 IP 位址 (記住您稍 `--network-alias` 早使用的旗標？ ) 。

    這表示 .。。您的應用程式只需要連接到名為的主機 `mysql` ，它就會與資料庫溝通！ 它的速度不如這樣簡單！

## <a name="run-your-app-with-mysql"></a>使用 MySQL 執行您的應用程式

Todo 應用程式支援設定一些環境變數來指定 MySQL 連線設定。 這些包括：

- `MYSQL_HOST` -正在執行之 MySQL 伺服器的主機名稱
- `MYSQL_USER` -用於連接的使用者名稱
- `MYSQL_PASSWORD` -用於連接的密碼
- `MYSQL_DB` -連接後要使用的資料庫

> [!WARNING]
> 透過 **環境變數設定連接設定** 雖然使用環境變數來設定連線設定通常可以進行開發，但是在生產環境中執行應用程式時，強烈建議您不要這麼做。 若要瞭解原因，請參閱 [為何不應針對秘密資料使用環境變數](https://diogomonica.com/2017/03/27/why-you-shouldnt-use-env-variables-for-secret-data/)。
> 更安全的機制是使用容器協調流程架構所提供的秘密支援。 在大部分情況下，這些秘密會以檔案的形式掛接在執行中的容器中。 您會看到許多應用程式 (包括 MySQL 映射和 todo 應用程式) 也支援具有尾碼的 env 變數， `_FILE` 以指向包含檔案的檔案。
> 例如，設定 `MYSQL_PASSWORD_FILE` var 會導致應用程式使用所參考檔案的內容做為連接密碼。 Docker 不會進行任何動作來支援這些環境變數。 您的應用程式必須知道，才能尋找變數並取得檔案內容。

在所有說明的情況下，啟動開發就緒的容器！

1. 指定上述的每個環境變數，並將容器連接到您的應用程式網路 (以 ` \ ` `` ` `` Windows PowerShell) 取代中的字元。

    ```bash hl_lines="3 4 5 6 7"
    docker run -dp 3000:3000 \
      -w /app -v ${PWD}:/app \
      --network todo-app \
      -e MYSQL_HOST=mysql \
      -e MYSQL_USER=root \
      -e MYSQL_PASSWORD=secret \
      -e MYSQL_DB=todos \
      node:12-alpine \
      sh -c "yarn install && yarn run dev"
    ```

1. 如果您查看容器 (的記錄 `docker logs <container-id>`) ，您應該會看到訊息，指出其正在使用 MySQL 資料庫。

    ```plaintext hl_lines="7"
    # Previous log messages omitted
    $ nodemon src/index.js
    [nodemon] 1.19.2
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching dir(s): *.*
    [nodemon] starting `node src/index.js`
    Connected to mysql db at host mysql
    Listening on port 3000
    ```

1. 在您的瀏覽器中開啟應用程式，並將一些專案新增至待辦事項清單。

1. 連線至 MySQL 資料庫，並證明正在將專案寫入資料庫中。 請記住，密碼是 **秘密**。

    ```bash
    docker exec -ti <mysql-container-id> mysql -p todos
    ```

    在 MySQL shell 中執行下列命令：

    ```plaintext
    mysql> select * from todo_items;
    +--------------------------------------+--------------------+-----------+
    | id                                   | name               | completed |
    +--------------------------------------+--------------------+-----------+
    | c906ff08-60e6-44e6-8f49-ed56a0853e85 | Do amazing things! |         0 |
    | 2912a79e-8486-4bc3-a4c5-460793a575ab | Be awesome!        |         0 |
    +--------------------------------------+--------------------+-----------+
    ```

    很明顯地，您的資料表看起來會不同，因為它有您的專案。 但是，您應該會看到它們儲存在該處！

如果您快速查看 Docker 延伸模組，您會看到有兩個應用程式容器正在執行。 但是，並沒有真正的指示，它們會在單一應用程式中群組在一起。 您將瞭解如何讓它更好！

![顯示兩個已取消群組之應用程式容器的 Docker 擴充功能](media/vs-multi-container-app.png)

## <a name="recap"></a>概括回顧

至此，您的應用程式現在會將其資料儲存在另一個容器中執行的外部資料庫。 您稍微瞭解容器網路功能，並瞭解如何使用 DNS 來執行服務探索。

但是，當您啟動此應用程式時，很有可能會開始覺得您需要做的事情。 您必須建立網路、啟動容器、指定所有環境變數、公開端口，以及更多功能！ 這是很多要記住的，而且一定會讓事情更難傳遞給其他人。

在下一節中，我們將討論 Docker Compose。 有了 Docker Compose，您就能以更簡單的方式共用應用程式堆疊，讓其他人使用單一 (和簡單的) 命令來加速處理！

## <a name="next-steps"></a>下一步

繼續進行本教學課程！

> [!div class="nextstepaction"]
> [使用 Docker Compose](use-docker-compose.md)
