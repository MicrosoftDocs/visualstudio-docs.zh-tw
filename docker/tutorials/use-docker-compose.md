---
title: Docker 教學課程-第7部分：使用 Docker Compose
description: 說明如何安裝和使用 Docker Compose。
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 3bcf3a69dcf8053851e3d8519a25f61fe23ae7e3
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/31/2021
ms.locfileid: "106082561"
---
# <a name="use-docker-compose"></a>使用 Docker Compose

[Docker Compose](https://docs.docker.com/compose/) 是為了協助定義和共用多容器應用程式而開發的工具。 透過撰寫，您可以建立 YAML 檔案來定義服務，並使用單一命令，將所有專案向上或全部拉出。

使用撰寫的 *主要* 優點是您可以在檔案中定義應用程式堆疊，將它保留在專案存放庫的根目錄 (它現在是) 的版本控制，而且可以輕鬆地讓其他人參與您的專案。 有些人只需要複製您的存放庫，就可以開始撰寫應用程式。 事實上，您可能會在 GitHub/GitLab 上看到相當多的專案，現在就完成這項工作。

那麼，您該如何著手？

## <a name="install-docker-compose"></a>安裝 Docker Compose

如果您已安裝適用于 Windows 或 Mac 的 Docker Desktop，您已經有 Docker Compose！ Docker 實例也已 Docker Compose 安裝。 如果您是在 Linux 機器上，則必須使用 [此處的指示](https://docs.docker.com/compose/install/)來安裝 Docker Compose。

安裝之後，您應該能夠執行下列各項，並查看版本資訊。

```bash
docker-compose version
```

## <a name="create-the-compose-file"></a>建立撰寫檔案

1. 在應用程式專案的根目錄中，建立名為的檔案 `docker-compose.yml` 。

1. 在撰寫檔案中，我們會先定義架構版本。 在大部分的情況下，最好是使用最新支援的版本。 您可以查看目前架構版本和相容性矩陣的 [撰寫檔案參考](https://docs.docker.com/compose/compose-file/) 。

    ```yaml
    version: "3.7"
    ```

1. 接下來，定義您想要在應用程式中執行的服務 (或容器) 清單。

    ```yaml hl_lines="3"
    version: "3.7"

    services:
    ```

現在，您會開始一次將服務遷移到撰寫檔案中。

## <a name="define-the-app-service"></a>定義 App Service

請記住，這是您用來定義應用程式容器的命令 (取代 ` \ ` `` ` `` Windows PowerShell) 中的字元。

```bash
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

1. 首先，定義容器的服務專案和映射。 您可以為服務挑選任何名稱。 名稱會自動成為網路別名，在定義 MySQL 服務時將會很有用。

    ```yaml hl_lines="4 5"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
    ```

1. 一般而言，您會看到接近定義的命令 `image` ，雖然不需要排序。 因此，請移至檔案中。

    ```yaml hl_lines="6"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
    ```

1. 藉 `-p 3000:3000` 由定義服務的來遷移命令的 `ports` 部分。 您將在這裡使用 [簡短語法](https://docs.docker.com/compose/compose-file/#short-syntax-1) ，但也有更詳細的 [long 語法](https://docs.docker.com/compose/compose-file/#long-syntax-1) 可用。

    ```yaml hl_lines="7 8"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
    ```

1. 接下來， `-w /app` `-v ${PWD}:/app` 使用和定義 () 和磁片區對應 () 遷移工作目錄 `working_dir` `volumes` 。 磁片區也有 [簡短](https://docs.docker.com/compose/compose-file/#short-syntax-3) 且 [完整](https://docs.docker.com/compose/compose-file/#long-syntax-3) 的語法。

   Docker Compose 磁片區定義的其中一個優點是您可以使用目前目錄中的相對路徑。

    ```yaml hl_lines="9 10 11"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
    ```

1. 最後，使用金鑰遷移環境變數定義 `environment` 。

    ```yaml hl_lines="12 13 14 15 16"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
        environment:
          MYSQL_HOST: mysql
          MYSQL_USER: root
          MYSQL_PASSWORD: secret
          MYSQL_DB: todos
    ```

### <a name="define-the-mysql-service"></a>定義 MySQL 服務

現在是時候定義 MySQL 服務。 您用於該容器的命令如下 (` \ ` `` ` `` 以 Windows PowerShell) 取代字元：

```bash
docker run -d \
  --network todo-app --network-alias mysql \
  -v todo-mysql-data:/var/lib/mysql \
  -e MYSQL_ROOT_PASSWORD=secret \
  -e MYSQL_DATABASE=todos \
  mysql:5.7
```

1. 首先，請定義新的服務，並將它命名為 `mysql` 自動取得網路別名。 也可以指定要使用的映射。

    ```yaml hl_lines="6 7"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
    ```

1. 接下來，定義磁片區對應。 當您執行容器時 `docker run` ，會自動建立命名磁片區。 不過，使用撰寫時並不會發生這種情況。 您需要在最上層區段中定義磁片 `volumes:` 區，然後在服務設定中指定掛接點。只要只提供磁片區名稱，就會使用預設選項。 不過還有 [許多選項可供使用](https://github.com/compose-spec/compose-spec/blob/master/spec.md#volumes-top-level-element) 。

    ```yaml hl_lines="8 9 10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
    
    volumes:
      todo-mysql-data:
    ```

1. 最後，您只需要指定環境變數。

    ```yaml hl_lines="10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
        environment: 
          MYSQL_ROOT_PASSWORD: secret
          MYSQL_DATABASE: todos
    
    volumes:
      todo-mysql-data:
    ```

到目前為止，完成的結果應該如下所示 `docker-compose.yml` ：

```yaml
version: "3.7"

services:
  app:
    image: node:12-alpine
    command: sh -c "yarn install && yarn run dev"
    ports:
      - 3000:3000
    working_dir: /app
    volumes:
      - ./:/app
    environment:
      MYSQL_HOST: mysql
      MYSQL_USER: root
      MYSQL_PASSWORD: secret
      MYSQL_DB: todos

  mysql:
    image: mysql:5.7
    volumes:
      - todo-mysql-data:/var/lib/mysql
    environment: 
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: todos

volumes:
  todo-mysql-data:
```

## <a name="run-the-application-stack"></a>執行應用程式堆疊

既然您已經有檔案 `docker-compose.yml` ，就可以開始使用了！

1. 首先，請確定沒有任何其他複本的應用程式和資料庫正在執行 (`docker ps` 和 `docker rm -f <ids>`) 。

1. 使用命令來啟動應用程式堆疊 `docker-compose up` 。 新增 `-d` 旗標以在背景中執行所有專案。 或者，您也可以用滑鼠右鍵按一下您的撰寫檔案，然後選取 [VS Code 提要欄位的 [ **撰寫** ] 選項。 

    ```bash
    docker-compose up -d
    ```

    當您執行此動作時，您應該會看到如下所示的輸出：

    ```plaintext
    Creating network "app_default" with the default driver
    Creating volume "app_todo-mysql-data" with default driver
    Creating app_app_1   ... done
    Creating app_mysql_1 ... done
    ```

    您將會注意到磁片區已建立和網路！ 根據預設，Docker Compose 會自動為應用程式堆疊建立網路 (這是您未在撰寫檔案) 中定義一個的原因。

1. 使用命令來查看記錄 `docker-compose logs -f` 。 您會看到每個服務中交錯成單一資料流程的記錄。 當您想要監看時間相關問題時，這非常有用。 旗標「 `-f` 跟隨」記錄檔，因此會在產生時提供即時輸出。

    如果您還沒有這麼做，您會看到如下所示的輸出：

    ```plaintext
    mysql_1  | 2019-10-03T03:07:16.083639Z 0 [Note] mysqld: ready for connections.
    mysql_1  | Version: '5.7.27'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL)
    app_1    | Connected to mysql db at host mysql
    app_1    | Listening on port 3000
    ```

    服務名稱會顯示在行首， (通常會有彩色的) ，以協助區分訊息。 如果您想要查看特定服務的記錄，您可以將服務名稱新增至 logs 命令的結尾 (例如 `docker-compose logs -f app`) 。

    > [!TIP]
    > **在啟動應用程式之前等候資料庫** 當應用程式啟動時，它實際上是在嘗試連線至 it.Docker 沒有任何內建支援，可等候另一個容器完全啟動、執行，並在啟動另一個容器之前準備好。 針對以節點為基礎的專案，您可以使用 [等待埠](https://github.com/dwmkerr/wait-port) 相依性。 其他語言/架構有類似的專案。

1. 此時，您應該能夠開啟您的應用程式，並查看它是否正在執行。 嘿！ 您會遇到一個命令！

## <a name="see-the-app-stack-in-the-docker-extension"></a>請參閱 Docker 延伸模組中的應用程式堆疊

如果您查看 Docker 延伸模組，您可以使用 [齒輪] 和 [group by] 來變更群組選項。 在此情況下，您會想要查看依「撰寫專案名稱」分組的容器：

![具有撰寫的 VS 延伸模組](media/vs-app-project-collapsed.png)

如果您在網路上扭曲，您將會看到您在撰寫檔案中定義的兩個容器。

![已展開撰寫的 VS 延伸模組](media/vs-app-project-expanded.png)

## <a name="tear-it-all-down"></a>全部拉出

當您準備好將其卸載時，只要執行 `docker-compose down` ，或在 VS Code Docker 擴充功能的 [容器] 清單中的應用程式上按一下滑鼠右鍵，然後選取 [ **向下撰寫**]。 容器將會停止，且會移除網路。

> [!WARNING]
> **移除磁片** 區依預設，在執行時，不會移除撰寫檔案中的命名磁片區 `docker-compose down` 。 如果您想要移除磁片區，就必須新增 `--volumes` 旗標。

當您關閉後，您可以切換到另一個專案、執行， `docker-compose up` 並準備好參與該專案！ 其實比這樣簡單得多。

## <a name="recap"></a>概括回顧

在本節中，您已瞭解 Docker Compose，以及它如何有助於大幅簡化多服務應用程式的定義和共用。 您已藉由將使用的命令轉譯為適當的撰寫格式來建立撰寫檔案。

至此，您將開始總結教學課程。 不過，有幾個關於映射建立的最佳作法，因為您使用的 Dockerfile 有很大的問題。 現在就來看看！

## <a name="next-steps"></a>下一步

繼續進行本教學課程！

> [!div class="nextstepaction"]
> [映射建立最佳做法](image-building-best-practices.md)
