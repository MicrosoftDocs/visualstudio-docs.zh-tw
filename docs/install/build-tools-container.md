---
title: 將 Visual Studio Build Tools 安裝至容器
titleSuffix: ''
description: 了解如何將 Visual Studio Build Tools 安裝至 Windows 容器，以便支援持續整合與持續傳遞 (CI/CD) 工作流程。
ms.date: 04/18/2018
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: heaths
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a7134fbe40fb68a2ed1e957b9a2d910adfad591
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929149"
---
# <a name="install-build-tools-into-a-container"></a>將 Build Tools 安裝至容器

您可以將 Visual Studio Build Tools 安裝至 Windows 容器，以便支援持續整合與持續傳遞 (CI/CD) 工作流程。 本文將引導您了解需要進行的 Docker 組態變更，以及可在容器中安裝的[工作負載和元件](workload-component-id-vs-build-tools.md)。

[容器](https://www.docker.com/what-container)是用來封裝一致之建置系統的好方法，不僅可用於 CI/CD 伺服器環境，也可用於開發環境。 例如，您可以將原始程式碼裝載於容器中以供自訂環境建置，同時繼續使用 Visual Studio 或其他工具來撰寫程式碼。 如果您的 CI/CD 工作流程使用相同的容器映像，就能確信您的程式碼會以一致的方式建置。 您也可以使用容器來取得執行階段一致性，此做法常見於使用具有一套協調流程系統之多個容器的微服務，但不在本文討論範圍內。

如果 Visual Studio Build Tools 沒有您建置原始程式碼所需的工具，這些相同步驟可用於其他 Visual Studio 產品。 但請注意，Windows 容器不支援互動式使用者介面，因此所有命令都必須自動化。

## <a name="overview"></a>總覽

您可以使用 [Docker](https://www.docker.com/what-docker) 建立映像，然後從中建立容器以建置您的原始程式碼。 範例 Dockerfile 會安裝最新版 Visual Studio Build Tools 2017，以及其他常用於建置原始程式碼的實用程式。 您可以進一步修改自己的 Dockerfile，以包含其他工具和指令碼來執行測試、發行建置輸出等等。

如果您已安裝 Docker for Windows，則可以跳至步驟 3。

## <a name="step-1-enable-hyper-v"></a>步驟 1： 啟用 Hyper-V

預設不會啟用 Hyper-V。 由於目前只有 Windows 10 支援 Hyper-V 隔離，因此必須啟用才能啟動 Docker for Windows。

* [在 Windows 10 上啟用 Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)
* [在 Windows Server 2016 上啟用 Hyper-V](https://docs.microsoft.com/windows-server/virtualization/hyper-v/get-started/install-the-hyper-v-role-on-windows-server)

> [!NOTE]
> 您的電腦必須啟用虛擬化。 通常預設會啟用；不過，如果 Hyper-V 安裝失敗，請參閱您的系統文件以了解如何啟用虛擬化。

## <a name="step-2-install-docker-for-windows"></a>步驟 2： 安裝 Docker for Windows

如果使用的是 Windows 10，則可以[下載並安裝 Docker Community Edition](https://docs.docker.com/docker-for-windows/install)。 如果使用的是 Windows Server 2016，請遵循[指示來安裝 Docker Enterprise Edition](https://docs.docker.com/install/windows/docker-ee)。

## <a name="step-3-switch-to-windows-containers"></a>步驟 3： 切換至 Windows 容器

您只能在 Windows 上安裝 Build Tools 2017，這需要您[切換至 Windows 容器](https://docs.docker.com/docker-for-windows/#getting-started-with-windows-containers)。 Windows 10 上的 Windows 容器僅支援 [Hyper-V 隔離](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container)，而 Windows Server 2016 上的 Windows 容器則同時支援 Hyper-V 和處理序隔離。

## <a name="step-4-expand-maximum-container-disk-size"></a>步驟 4： 擴充容器磁碟大小上限

Visual Studio Build Tools (及更大範圍的 Visual Studio) 需要許多磁碟空間以安裝所有工具。 即使範例 Dockerfile 會停用套件快取，還是必須增加容器映像的磁碟大小，以容納所需的空間。 目前在 Windows 上，您只能透過變更 Docker 組態來增加磁碟大小。

**在 Windows 10 上**：

1. 在系統匣中，[以滑鼠右鍵按一下適用於 Windows 的 Docker 圖示](https://docs.docker.com/docker-for-windows/#docker-settings) \(英文\)，然後按一下 [設定]。
2. [按一下 [精靈]](https://docs.docker.com/docker-for-windows/#docker-daemon) 區段。
3. [將 [基本]](https://docs.docker.com/docker-for-windows/#edit-the-daemon-configuration-file) 按鈕切換至 [進階]。
4. 新增下列 JSON 陣列屬性，以將磁碟空間增加到 120 GB (讓 Build Tools 有足夠的成長空間)。

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   這個屬性會新增至您已有的任何項目。 例如，將這些變更套用至預設精靈組態檔之後，您現在應該會看到：

   ```json
   {
     "registry-mirrors": [],
     "insecure-registries": [],
     "debug": true,
     "experimental": true,
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

5. 按一下 [套用]。

**在 Windows Server 2016 上**：

1. 停止 "docker" 服務：

   ```shell
   sc.exe stop docker
   ```

2. 從提升權限的命令提示字元，編輯 "%ProgramData%\Docker\config\daemon.json" (或任何您指定給 `dockerd --config-file` 的目錄)。
3. 新增下列 JSON 陣列屬性，以將磁碟空間增加到 120 GB (讓 Build Tools 有足夠的成長空間)。

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   這個屬性會新增至您已有的任何項目。
4. 儲存並關閉檔案。
5. 啟動 "docker" 服務：

   ```shell
   sc.exe start docker
   ```

## <a name="step-5-create-and-build-the-dockerfile"></a>步驟 5： 建立並建置 Dockerfile

將下列範例 Dockerfile 儲存至磁碟上的新檔案。 如果檔案直接以 "Dockerfile" 命名，預設會辨識此名稱。

> [!WARNING]
> 此範例 Dockerfile 只會排除無法安裝至容器的舊版 Windows SDK。 較舊版本會造成建置命令失敗。

1. 開啟命令提示字元。
2. 建立新的目錄 (建議)：

   ```shell
   mkdir C:\BuildTools
   ```

3. 將目錄變更為此新目錄：

   ```shell
   cd C:\BuildTools
   ```

3. 將下列內容儲存至 C:\BuildTools\Dockerfile。

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.1.
   FROM microsoft/dotnet-framework:4.7.1

   # Restore the default Windows shell for correct batch processing below.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --all `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Start developer command prompt with any other commands specified.
   ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

   # Default to PowerShell if no other command specified.
   CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!WARNING]
   > 如果您讓映像直接以 microsoft/windowsservercore 為基礎，.NET Framework 可能無法正確安裝，且不會指出任何安裝錯誤。 安裝完成之後，可能無法執行受控碼。 相反地，讓您的映像以 [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) 或更新版本為基礎。 另請注意，標記為 4.7.1 版的映像可能會使用 PowerShell 作為預設 `SHELL`，導致 `RUN` 和 `ENTRYPOINT` 指令失敗。
   >
   > Visual Studio 2017 15.8 或更早版本 (任何產品) 無法在 mcr<span></span>.microsoft\.com\/windows\/servercore:1809 (或更新版本) 上正確安裝。 不會顯示錯誤。
   >
   > 請參閱[容器的已知問題](build-tools-container-issues.md)以取得詳細資訊。

4. 從該目錄內執行下列命令。

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   此命令使用 2 GB 的記憶體在目前的目錄中建置 Dockerfile。 安裝某些工作負載時，預設值 1 GB 並不夠；不過，根據您的建置需求，您可能只使用 1 GB 記憶體就能夠進行建置。

   最終映像會標記為 "buildtools2017:latest"，因此您可以輕鬆地在容器中當作 "buildtools2017" 來執行 (因為 "latest" 是未指定任何標記時的預設值)。 如果您想要在更[進階的案例](advanced-build-tools-container.md)中使用特定版本的 Visual Studio Build Tools 2017，請改以特定 Visual Studio 組建編號及 "latest" 來標記容器，以確保容器能夠一致地使用特定版本。

## <a name="step-6-using-the-built-image"></a>步驟 6： 使用建置的映像

現在您已建立映像，您可以在容器中執行，以同時執行互動式和自動化組建。 此範例使用開發人員命令提示字元，因此已設定您的 PATH 和其他環境變數。

1. 開啟命令提示字元。
2. 執行容器，以啟動 PowerShell 環境並設定所有開發人員環境變數：

   ```shell
   docker run -it buildtools2017
   ```

若要將此映像用於您的 CI/CD 工作流程，您可以將它發行至自己的 [Azure 容器登錄](https://azure.microsoft.com/services/container-registry)或其他內部 [Docker 登錄](https://docs.docker.com/registry/deploying)，讓伺服器只需要加以提取。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [容器的進階範例](advanced-build-tools-container.md)
* [容器的已知問題](build-tools-container-issues.md)
* [Visual Studio Build Tools 2017 工作負載和元件識別碼](workload-component-id-vs-build-tools.md)
