---
title: 在 Linux 上設定遠端 R 服務
description: 如何在 Ubuntu 和適用於 Linux 的 Windows 子系統上設定遠端 R 服務。
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
ms.reviewer: karthiknadig
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 586f3038ff4bb091fb99160d7965ad927eda070a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851812"
---
# <a name="remote-r-service-for-linux"></a>適用於 Linux 的遠端 R 服務

適用於 Linux 的遠端 R 服務目前已封裝成 rtvs-daemon。 精靈已在 Ubuntu 16.04、16.10 LTS 桌面版、伺服器版，以及適用於執行 Ubuntu 之 Linux 的 Windows 子系統上進行測試並獲得支援。 本文主要是在這些不同系統上設定遠端 R 服務的指示。

當您完成遠端電腦的設定後，下列步驟會將 Visual Studio R 工具 (RTVS) 連線到該服務：

1. 選取 [ **R 工具**  >  **Windows**  >  **工作區**] 以開啟 [**工作區**] 視窗。
1. 選取 [ **新增連接**]。
1. 給予連線一個名稱並提供 URL，例如 `https://localhost:5444` (適用於 Linux 的 Windows 子系統) 或 `https://public-ip:5444` (Azure 容器)。 完成時選取 [儲存]。
1. 選取連線圖示或按兩下連線項目。
1. 提供登入認證。 使用者名稱必須加上 `<<unix>>\` 的前置詞，如 `<<unix>>\ruser1` (所有連線到 Linux 遠端電腦的連線都必須如此)。
1. 若您使用的是自我簽署的憑證，您可能會看見警告訊息。 訊息會提供修正警告的指示。

## <a name="set-up-remote-r-service"></a>設定遠端 R 服務

本節將描述下列選項：

- [實體 Ubuntu 電腦](#physical-ubuntu-computer)
- [Ubuntu Server VM 或 Azure 上的資料科學 VM](#ubuntu-server-vm-or-data-science-vm-on-azure)
- [本機或遠端 Docker 容器 (全新組建)](#local-or-remote-docker-container-clean-build)
- [在 Azure 容器執行個體上執行的容器](#container-running-on-azure-container-instances)

在每個案例中，遠端電腦都必須安裝下列 R 解譯器中的其中一個：

- [Microsoft R Open](https://mran.microsoft.com/open/)
- [CRAN R for Windows](https://cran.r-project.org/bin/linux/ubuntu/)

### <a name="physical-ubuntu-computer"></a>實體 Ubuntu 電腦

1. 登入電腦之後，下載 rtvs-daemon tarball：

    ```bash
    wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current
    tar -xvzf rtvs-daemon.tar.gz
    ```

1. 執行安裝指令碼：

    ```bash
    sudo ./rtvs-install
    ```

    若要使用無訊息自動化功能，請使用 `sudo ./rtvs-install -s`。

1. 啟用並啟動服務：

    ```bash
    sudo systemctl enable rtvsd
    sudo systemctl start rtvsd
    ```

1. 設定 SSL 憑證 (生產環境下將需要此憑證)。 根據預設，rtvs-daemon 會使用由 `ssl-cert` 套件產生的 `ssl-cert-snakeoil.pem` 及 `ssl-cert-snakeoil.pem`。 在安裝期間，它們會合併成 `ssl-cert-snakeoil.pfx`。 針對生產環境目的，請使用由您系統管理員提供的 SSL 憑證。 您可以藉由在 */etc/rtvs/rtvsd.config.json* 中提供 *.pfx* 檔案及選擇性匯入密碼來設定 SSL 憑證。

1. (選擇性) 檢查服務是否已在執行：

    ```bash
    ps -A -f | grep rtvsd
    ```

    若您沒有看到處理序以 `rtvssvc` 的使用者名稱執行。 請使用下列命令啟動它：

    ```bash
    sudo systemctl start rtvsd
    ```

1. 若要進一步設定 rtvs-daemon，請參閱 `man rtvsd`。

### <a name="ubuntu-server-vm-or-data-science-vm-on-azure"></a>Ubuntu Server VM 或 Azure 上的資料科學 VM

#### <a name="create-a-vm"></a>建立 VM

1. 登入 [Azure 入口網站](https://portal.azure.com)。
1. 巡覽至 [虛擬機器]，然後選取 [新增]。
1. 在可用的 VM 映像清單中，搜尋它並選取下列項目中的其中一個：
    - Ubuntu Server：`Ubuntu Server 16.04 LTS`
    - 資料科學 VM：`Linux Data Science` (請參閱[資料科學虛擬機器](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/)以取得詳細資料)
1. 將部署模型設為 `Resource manager`，然後選取 [建立]。
1. 為 VM 選擇一個名稱，提供使用者名稱及密碼 (由於系統不支援 SSH 公開金鑰登入，因此需要密碼)。
1. 對 VM 設定進行任何其他想要的變更。
1. 選擇 VM 大小、驗證設定，然後選取 [建立]。 建立 VM 之後，請繼續下一節。

#### <a name="configure-the-vm"></a>設定 VM

1. 在 VM 的 [網路] 區段中，新增 5444 作為允許的輸入連接埠。 若要使用不同的連接埠，請在 RTVS 精靈設定檔案 (*/etc/rtvs/rtvsd.config.json*) 中變更設定。
1. (選擇性) 設定 DNS 名稱；您也可以使用 IP 位址。
1. 使用 SSH 用戶端 (例如適用於 Windows 的 PuTTY) 連線到 VM。
1. 遵循上述適用於[實體 Ubuntu 電腦](#physical-ubuntu-computer)的指示。

### <a name="windows-subsystem-for-linux-wsl"></a>適用於 Linux 的 Windows 子系統 (WSL)

1. 請遵循適用於 [Windows 10](/windows/wsl/install-win10#install-the-windows-subsystem-for-linux) 或 [Windows Server](/windows/wsl/install-on-server#enable-the-windows-subsystem-for-linux-wsl) 的 WSL 安裝指示。
1. 在 Windows 上啟動 Bash，然後遵循先前[實體 Ubuntu 電腦](#physical-ubuntu-computer)一節中所描述的指示，除了其中一點。 在步驟 3 中，請改為使用命令 `rtvsd` 啟動服務，因為 WSL 目前不支援 systemd/systemctl 介面。

### <a name="local-or-remote-docker-container-clean-build"></a>本機或遠端 Docker 容器 (全新組建)

1. 使用下列內容建立 Docker 檔案。該檔案會安裝遠端 R 服務精靈及最新版本的 R。**注意**：此指令碼會建立名為「ruser1」且密碼為「foobar」的使用者。您可以在最後兩個 `RUN` 陳述式中自行修改。

    ```docker
    FROM ubuntu:16.04

    ARG DEBIAN_FRONTEND=noninteractive

    RUN apt-get update \
     && apt-get install -y software-properties-common python-software-properties \
     && apt-get install -y apt-transport-https \
     && rm -rf /var/lib/apt/lists/*

    RUN sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list' \
     && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 417A0893 \
     && sh -c 'echo "deb https://cran.revolutionanalytics.com/bin/linux/ubuntu xenial/" > /etc/apt/sources.list.d/cran-r.list' \
     && apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9 \
     && rm -rf /var/lib/apt/lists/* \
     && apt-get clean

    RUN apt-get update --fix-missing && apt-get update \
     && apt-get install -y dotnet-dev-1.0.4 libexplain51 libzip4 libc6 git lshw ssl-cert wget \
     && rm -rf /var/lib/apt/lists/*

    # install R
    RUN apt-get update && apt-get install -y r-base-dev
    RUN apt upgrade -y

    # install rtvs-daemon
    RUN wget -O rtvs-daemon.tar.gz https://aka.ms/r-remote-services-linux-binary-current && tar -xvzf rtvs-daemon.tar.gz && ./rtvs-install -s

    RUN useradd --create-home ruser1
    RUN echo "ruser1:foobar" | chpasswd

    EXPOSE 5444
    ```

1. 建置和執行 Docker 檔案：

    ```bash
    docker build -t myrimage .
    docker run -p 5444:5444 myrimage rtvsd
    ```

1. 若要連線至來自 RTVS 的容器，請使用 `https://localhost:5444` 作為路徑、`<<unix>>\ruser1` 作為使用者名稱、`foobar` 作為密碼。 若容器正在遠端電腦上執行，請使用 `https://remote-host-name:5444` 作為路徑。 藉由更新 */etc/rtvs/rtvsd.config.json*，可以變更連接埠。

### <a name="container-running-on-azure-container-instances"></a>在 Azure 容器執行個體上執行的容器

1. 請遵循[本機或遠端 Docker 容器 (全新組建)](#local-or-remote-docker-container-clean-build) 中描述的指示建立映像。
1. 將容器推送到 Docker 中樞或 Azure 容器存放庫。
1. 使用 `az login` 命令啟動 Azure CLI 並登入。
1. 使用 `az container create` 命令建立容器；若您還沒有設定將 `rtvsd` 作為 `systemd` 服務執行的容器，請使用 `--command-line "rtvsd"`。 在下列命令中，預期映像會位於 Docker 中樞。 您也可以藉由將容器存放庫認證引數新增至命令列來使用 Azure 容器存放庫。

    ```bash
    az container create --image myimage:latest --name myaz-container --resource-group myaz-container-res --ip-address public --port 5444 --cpu 2 --memory 4 --command-line "rtvsd"
    ```

1. 使用 `az container list` 命令來檢查狀態。 尋找 `provisioningState`：`Succeeded`。
1. 若佈建成功，您現在即可連線到容器。 在 `ipAddress` 欄位中尋找在 Docker 檔案中與認證一同用來連線到來自 RTVS 容器的公用 IP 位址。
