---
title: Docker 教學課程-第1部分：建立和執行 todo 清單範例應用程式
description: 在 Node.js 中執行之 todo 清單範例應用程式的總覽。
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 1b92792cf9db0090c52f583754e56c306e6d7234
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/31/2021
ms.locfileid: "106082574"
---
# <a name="build-and-run-the-todo-sample-app"></a>建立並執行待辦事項範例應用程式

在本教學課程的其餘部分，您將使用在 Node.js 中執行的簡單待辦事項清單管理員。 如果您不熟悉 Node.js，別擔心！ 不需要真正的 JavaScript 體驗！

目前，您的開發小組相當小，而且您只需要建立應用程式來證明您的 MVP (最小可行產品) 。 您想要示範它的運作方式，以及它能夠執行的工作，而不需要考慮如何針對大型小組、多位開發人員等等。

![Todo 清單管理員螢幕擷取畫面](media/todo-list-sample.png)

## <a name="get-the-app"></a>取得應用程式

在您可以執行應用程式之前，您必須先將應用程式原始程式碼放到您的電腦上。 針對真實的專案，您通常會複製存放庫。 但是在本教學課程中，我們建立了一個包含應用程式的 ZIP 檔案。

1. 請確定您已在本機電腦上安裝適用於 Windows 的 Docker 或 Docker 社區版。 請參閱 [適用於 Windows 的 Docker 安裝檔](https://docs.docker.com/docker-for-windows/install/)。 安裝程式會將包含範例的 ZIP 檔案提供給 localhost 位址。

1. [下載 ZIP](https://github.com/docker/getting-started/tree/master/app)。 開啟 ZIP 檔案，並確定您已將內容解壓縮。

1. 解壓縮之後，請使用您慣用的程式碼編輯器來開啟專案。 如果您需要編輯器，可以使用 [Visual Studio Code](https://code.visualstudio.com/)。 您應該會看到 `package.json` 和兩個子目錄 (`src` 和 `spec`) 。

    ![已載入應用程式時所開啟 Visual Studio Code 的螢幕擷取畫面](media/ide-screenshot.png)

## <a name="building-the-apps-container-image"></a>建立應用程式的容器映射

若要建立應用程式，您必須使用 `Dockerfile` 。 Dockerfile 只是用來建立容器映射之指令的文字型腳本。 如果您先前已建立 Dockerfile，您可能會在下列 Dockerfile 中看到一些瑕疵。 但別擔心！ 我們就來討論一下。

1. 在 `Dockerfile` 具有下列內容的檔案所在的同一個資料夾中，建立名為的檔案 `package.json` 。

    ```dockerfile
    FROM node:12-alpine
    WORKDIR /app
    COPY . .
    RUN yarn install --production
    CMD ["node", "/app/src/index.js"]
    ```

    請確認檔案 `Dockerfile` 沒有像這樣的副檔名 `.txt` 。 某些編輯器可能會自動附加此副檔名，而這會導致下一個步驟發生錯誤。

1. 如果您尚未這麼做，請開啟終端機並移至 `app` 具有的目錄 `Dockerfile` 。 現在使用命令建立容器映射 `docker build` 。

    ```bash
    docker build -t getting-started .
    ```

    或者，您也可以在 Dockerfile 上按一下滑鼠右鍵，並選擇 [ **建立映射** ]，然後在提示字元中指定標記。

    此命令使用 Dockerfile 來建立新的容器映射。 您可能已經注意到許多「圖層」已下載。 這是因為您已指示您想要從映射啟動的產生器 `node:12-alpine` 。 但因為您的電腦上沒有該映射，所以需要下載該映射。

    下載影像之後，您會在應用程式中複製該影像，並用 `yarn` 來安裝應用程式的相依性。 指示詞會 `CMD` 指定從這個映射啟動容器時要執行的預設命令。

    最後，旗標會 `-t` 標記您的影像。 把這想成是人們看得懂的最終影像名稱。 由於您已將映射命名為 `getting-started` ，因此當您執行容器時，可以參考該映射。

    `.`命令結束時， `docker build` 會告知 Docker 應該 `Dockerfile` 在目前的目錄中尋找。

## <a name="starting-an-app-container"></a>啟動應用程式容器

現在您已有映射，請執行應用程式！ 若要這樣做，請使用 `docker run` 命令 (記住，從先前的？ ) 。

1. 使用命令來啟動您的容器 `docker run` ，並指定您剛才建立的映射名稱：

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

    要記住 `-d` and `-p` 旗標嗎？ 您是在背景) 中以「卸離」模式執行新的容器 (，並在主機的埠3000與容器的埠3000之間建立對應。 如果沒有埠對應，您將無法存取應用程式。

1. 幾秒鐘後，開啟您的網頁瀏覽器 [http://localhost:3000](http://localhost:3000) 。
    您應該會看到應用程式！

    ![空白 Todo 清單](media/todo-list-empty.png)

1. 請繼續加入一個或兩個專案，看看它是否如預期般運作。 您可以將專案標示為完成和移除專案。 您的前端已成功將專案儲存在後端！ 很簡單快速，對吧？

此時，您應該會有一個執行中的待辦事項清單管理員，其中有幾個專案，全都由您建立！ 現在，讓我們進行一些變更，並瞭解如何管理您的容器。

如果您快速查看 VS Code 擴充功能，您應該會看到您現在執行的兩個容器 (本教學課程和您剛推出的應用程式容器) ！

![執行教學課程和應用程式容器的 Docker 擴充功能](media/vs-two-containers.png)

## <a name="recap"></a>概括回顧

在這個簡短的章節中，您已瞭解建立容器映射以及建立 Dockerfile 來完成這項作業的基本概念。 建立映射之後，您會啟動容器，並看到執行中的應用程式！

接下來，您將修改應用程式，並瞭解如何使用新的映射來更新執行中的應用程式。 在過程中，您將會瞭解一些其他有用的命令。

## <a name="next-steps"></a>下一步

繼續進行本教學課程！

> [!div class="nextstepaction"]
> [更新您的應用程式](update-your-app.md)
