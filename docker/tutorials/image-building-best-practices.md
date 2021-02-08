---
title: Docker 教學課程-第8部分：影像分層
description: 如何檢查及管理 Docker 映射中的映射層。
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 8913c558c2860599fbfaaba03fa466d11931a528
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837953"
---
# <a name="image-layering"></a>影像分層

您知道您可以查看組成影像的專案嗎？ `docker image history`您可以使用命令來查看用來在影像內建立每個圖層的命令。

1. 使用 `docker image history` 命令來查看 `getting-started` 您稍早在本教學課程中建立的影像中的圖層。

    ```bash
    docker image history getting-started
    ```

    您應該會取得如下所示的輸出 (日期/識別碼可能不同) 。

    ```plaintext
    IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
    a78a40cbf866        18 seconds ago      /bin/sh -c #(nop)  CMD ["node" "/app/src/ind…   0B                  
    f1d1808565d6        19 seconds ago      /bin/sh -c yarn install --production            85.4MB              
    a2c054d14948        36 seconds ago      /bin/sh -c #(nop) COPY dir:5dc710ad87c789593…   198kB               
    9577ae713121        37 seconds ago      /bin/sh -c #(nop) WORKDIR /app                  0B                  
    b95baba1cfdb        13 days ago         /bin/sh -c #(nop)  CMD ["node"]                 0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  ENTRYPOINT ["docker-entry…   0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) COPY file:238737301d473041…   116B                
    <missing>           13 days ago         /bin/sh -c apk add --no-cache --virtual .bui…   5.35MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV YARN_VERSION=1.21.1      0B                  
    <missing>           13 days ago         /bin/sh -c addgroup -g 1000 node     && addu…   74.3MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV NODE_VERSION=12.14.1     0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  CMD ["/bin/sh"]              0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) ADD file:e69d441d729412d24…   5.59MB   
    ```

    每一行都代表影像中的圖層。 此處的顯示顯示底部有最新圖層的基底。 使用此項，您也可以快速查看每個圖層的大小，協助診斷大型影像。

1. 您會發現有幾行被截斷。 如果您加入 `--no-trunc` 旗標，將會取得完整輸出 (是，您可以使用截斷的旗標來取得 untruncated 輸出) 。

    ```bash
    docker image history --no-trunc getting-started
    ```

## <a name="layer-caching"></a>圖層快取

現在您已瞭解各圖層的運作方式，有一項重要的課程可協助您縮短容器映射的組建時間。

> 一旦圖層變更之後，所有下游層也都必須重新建立

讓我們來看看您使用的 Dockerfile 還有一次 .。。

```dockerfile
FROM node:12-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "/app/src/index.js"]
```

回到影像歷程記錄輸出，您會看到 Dockerfile 中的每個命令都會變成映射中的新圖層。 您可能還記得當您對映射進行變更時，必須重新安裝 yarn 相依性。 是否有辦法修正此問題？ 每次建立時，在相同的相依性周圍都沒有什麼意義，對吧？

若要修正此問題，您可以重建 Dockerfile，以協助支援這些相依性的快取。 若是以節點為基礎的應用程式，則會在檔案中定義這些相依性 `package.json` 。 那麼，如果您先複製該檔案，請先安裝相依性，然後 *再* 複製其他專案呢？ 然後，您只會在變更時重新建立 yarn 相依性 `package.json` 。 有意義嗎？

1. 將 Dockerfile 更新為 `package.json` 先複製，並安裝相依性，然後複製中的其他專案。

    ```dockerfile hl_lines="3 4 5"
    FROM node:12-alpine
    WORKDIR /app
    COPY package.json yarn.lock ./
    RUN yarn install --production
    COPY . .
    CMD ["node", "/app/src/index.js"]
    ```

1. 使用建立新的映射 `docker build` 。

    ```bash
    docker build -t getting-started .
    ```

    您應該會看到如下所示的輸出 .。。

    ```plaintext
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Running in d53a06c9e4c2
    yarn install v1.17.3
    [1/4] Resolving packages...
    [2/4] Fetching packages...
    info fsevents@1.2.9: The platform "linux" is incompatible with this module.
    info "fsevents@1.2.9" is an optional dependency and failed compatibility check. Excluding it from installation.
    [3/4] Linking dependencies...
    [4/4] Building fresh packages...
    Done in 10.89s.
    Removing intermediate container d53a06c9e4c2
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> a239a11f68d8
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 49999f68df8f
    Removing intermediate container 49999f68df8f
    ---> e709c03bc597
    Successfully built e709c03bc597
    Successfully tagged getting-started:latest
    ```

    您會看到所有圖層都已重建。 完全沒問題，因為您很 Dockerfile 地改變了這一點。

1. 現在，請變更檔案 `src/static/index.html` (例如，將變更為「出色 `<title>` 的待辦事項應用程式」 ) 。

1. 立即使用重新建立 Docker 映射 `docker build` 。 這次，您的輸出看起來應該有點不同。

    ```plaintext hl_lines="5 8 11"
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> Using cache
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Using cache
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> cccde25a3d9a
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 2be75662c150
    Removing intermediate container 2be75662c150
    ---> 458e5c6f080c
    Successfully built 458e5c6f080c
    Successfully tagged getting-started:latest
    ```

    首先，您應該注意到組建速度更快！ 而且，您會看到步驟1-4 全部都有 `Using cache` 。 因此，個歡呼！ 您使用的是組建快取。 推送和提取此映射以及更新，也會以更快的速度進行。 萬歲！

## <a name="multi-stage-builds"></a>多階段組建

雖然我們不會在本教學課程中深入探討，但多階段組建是相當強大的工具，可協助您使用多個階段來建立映射。 有幾個優點：

- 從執行時間相依性分隔組建時間相依性
- *只* 傳送您的應用程式需要執行的內容，以減少整體映射大小

### <a name="maventomcat-example"></a>Maven/Tomcat 範例

建立以 JAVA 為基礎的應用程式時，需要 JDK 才能將原始程式碼編譯成 JAVA 位元組程式碼。 不過，在生產環境中不需要 JDK。 此外，您可能會使用 Maven 或 Gradle 等工具來協助建立應用程式。
您的最終映射中也不需要這些功能。 多階段組建說明。

```dockerfile
FROM maven AS build
WORKDIR /app
COPY . .
RUN mvn package

FROM tomcat
COPY --from=build /app/target/file.war /usr/local/tomcat/webapps 
```

此範例會使用一個稱為 `build`) 的階段 (，以使用 Maven 來執行實際的 JAVA 組建。 第二個階段 (從 `FROM tomcat` 階段開始) 複製檔案 `build` 。 最終的映射只是最後建立的階段 (可以使用旗標) 來覆寫 `--target` 。

### <a name="react-example"></a>回應範例

建立回應的應用程式時，您需要節點環境來編譯 JS 程式碼 (通常會 JSX) 、SASS 樣式表單，以及更多靜態 HTML、JS 和 CSS。 如果您未進行伺服器端轉譯，則您甚至不需要在生產組建中使用節點環境。 為什麼不在靜態 nginx 容器中傳送靜態資源？

```dockerfile
FROM node:12 AS build
WORKDIR /app
COPY package* yarn.lock ./
RUN yarn install
COPY public ./public
COPY src ./src
RUN yarn run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
```

在這裡，您會使用 `node:12` 映射來執行組建 (將圖層快取最大化) 然後將輸出複製到 nginx 容器。 很酷吧？

## <a name="recap"></a>概括回顧

藉由深入瞭解影像的結構，您可以更快速地建立映射並提供較少的變更。 多階段組建也有助於減少整體映射大小，並藉由分隔組建時間相依性與執行時間相依性來提高最終的容器安全性。

## <a name="next-steps"></a>下一步

繼續進行本教學課程！

> [!div class="nextstepaction"]
> [部署至雲端](deploy-to-cloud.md)