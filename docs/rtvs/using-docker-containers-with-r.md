---
title: R 和 Docker 容器
description: 如何設定 R Docker 容器，以及使用 Visual Studio 來連線到容器。
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 3aefba3880443269dbdb1c933e2c12b2f8001469
ms.sourcegitcommit: fc05a763b59e212c86350d117a1900a1f2686ec8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2021
ms.locfileid: "111551276"
---
# <a name="use-docker-containers-with-r-tools-for-visual-studio"></a>搭配 Visual Studio R 工具使用 Docker 容器

Visual Studio R 工具 (RTVS) 版本 1.3 以後，與[適用於 Windows 的 Docker](https://www.docker.com/docker-windows) 一同安裝，可支援與 Docker 容器一同使用。

## <a name="create-a-container"></a>建立容器

1. 選取位於 [工作區] 視窗 ([R 工具] > [視窗] > [工作區]) 右邊角落的 [容器] 按鈕。 若您尚未安裝適用於 Windows 的 Docker，視窗會通知您並提供下載連結。 安裝 Docker 可能需要將電腦重新開機。

    ![Visual Studio R 工具 (VS2017) 中的 [工作區] 視窗及容器命令](media/container-workspaces-window.png)

1. 在 [容器] 視窗中，選取 [建立]：

    ![[容器] 視窗中的 [建立] 命令](media/containers-window-create.png)

1. 在對話方塊中完成所需的資訊並選取 [建立]。 您輸入的認證也可以用來建立稍後在 Linux 上用來登入的帳戶。

    ![建立容器時，輸入容器名稱及認證](media/containers-window-create-fill.png)

1. RTVS 可能需要一些時間來建置映像。 Visual Studio 中的 [輸出]  視窗會顯示進度，但在需要冗長時間下載映像的過程中可能會顯得相當緩慢，請耐心等候。 映像建置完成之後，RTVS 便會啟動容器，並在 [容器] 視窗中顯示。 右側的控制項可停止、移除，或重新啟動容器。

    ![顯示已完成容器的 [容器] 視窗](media/containers-window-created.png)

## <a name="connect-to-a-container"></a>連線到容器

1. [工作區] 視窗的 [Local Running Containers] (本機執行容器) 區段會顯示在連接埠 5444 執行 RTVS 精靈的容器。 (請參閱 [Linux 的遠端 R 伺服器](setting-up-remote-r-service-on-linux.md)以取得設定精靈的詳細資料。)

    ![顯示可用容器的 [工作區] 視窗](media/workspaces-window-running-containers.png)

1. 若要連線到容器，請按兩下容器名稱，或選取容器名稱右邊的向前箭頭按鈕。 當連線時，您會看見 [R 互動] 視窗 (請參閱[使用 R 互動視窗](interactive-repl-for-r-in-visual-studio.md))：

    ![[工作區] 視窗及為容器開啟的 REPL 視窗](media/workspaces-window-container-connected.png)

## <a name="use-custom-built-images"></a>使用自訂映像

RTVS 會偵測及允許管理使用自訂映像建立的容器，例如下列 Docker 檔案中描述的 microsoft/rtvs 映像。 這裡使用的基礎映像已預先安裝 rtvs-daemon、R 3.4.2，以及常見的 R 套件。 **注意**：請根據您的需要變更此處顯示的使用者名稱及密碼。

```docker
FROM mcr.microsoft.com/rtvs:1.3-ub1604-r3.4.2
RUN useradd --create-home ruser1
RUN echo "ruser1:foobar" | chpasswd

#Install additional R packages. You may have to install OS dependencies, see package info or error messages during build.
#RUN Rscript --vanilla -e "install.packages(c('AzureML','wordcloud'), repos = 'http://cran.us.r-project.org');"
```

使用下列命令建置映像，並根據需要變更容器名稱 (`--name` 引數)：

```bash
docker build -t my-rtvs-image:latest .
docker run -p 6056:5444 --name my-rtvs-container my-rtvs-image:latest rtvsd
```

`-p 6056:5444` 引數會將連接埠 6056 對應到內部連接埠 5444，即 RTVS 用來偵測 rtvs-daemon 的連接埠。 任何公開容器連接埠 5444 的容器都會在 [工作區] 視窗中列出。 您接下來可使用 [工作區] 視窗來使用 `<<unix>>\ruser1` 作為使用者名稱，「foobar」作為密碼來連線到容器，除非您在 Docker 檔案中指定了不同的認證。
