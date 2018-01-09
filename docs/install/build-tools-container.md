---
title: "將建置工具安裝至容器 | Microsoft Docs"
ms.custom: 
ms.date: 10/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: heaths
ms.author: heaths
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 95f9c69ebca7dbdc7e576279b4e1ad3f17d2be25
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="install-build-tools-into-a-container"></a>將建置工具安裝至容器

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

如果使用 Windows 10，您可以下載並安裝 [Docker Community Edition for Windows](https://www.docker.com/docker-windows)。 您可以使用 PowerShell 透過 Desired State Configuration (DSC) [安裝 Docker Enterprise Edition for Windows Server 2016](https://docs.docker.com/engine/installation/windows/docker-ee)，或透過[套件提供者](https://docs.microsoft.com/virtualization/windowscontainers/deploy-containers/deploy-containers-on-server)進行簡單的單一安裝。

## <a name="step-3-switch-to-windows-containers"></a>步驟 3： 切換至 Windows 容器

您只能在 Windows 上安裝 Build Tools 2017，這需要您[切換至 Windows 容器](https://docs.docker.com/docker-for-windows/#getting-started-with-windows-containers)。 Windows 10 上的 Windows 容器僅支援 [Hyper-V 隔離](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container)，而 Windows Server 2016 上的 Windows 容器則同時支援 Hyper-V 和處理序隔離。

## <a name="step-4-expand-maximum-container-disk-size"></a>步驟 4： 擴充容器磁碟大小上限

Visual Studio Build Tools (及更大範圍的 Visual Studio) 需要許多磁碟空間以安裝所有工具。 即使範例 Dockerfile 會停用套件快取，還是必須增加容器映像的磁碟大小，以容納所需的空間。 目前在 Windows 上，您只能透過變更 Docker 組態來增加磁碟大小。

**在 Windows 10 上**：

1. 在系統匣中，[以滑鼠右鍵按一下 Docker for Windows 圖示](https://docs.docker.com/docker-for-windows/#docker-settings)，然後按一下 [設定...]。
2. [按一下 [精靈]](https://docs.docker.com/docker-for-windows/#docker-daemon) 區段。
3. [將 [基本]](https://docs.docker.com/docker-for-windows/#edit-the-daemon-configuration-file) 按鈕切換至 [進階]。
4. 新增下列 JSON 陣列屬性，以將磁碟空間增加到 120GB (讓 Build Tools 有足夠的成長空間)。

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

您必須將下列範例 Dockerfile 儲存至磁碟上的新檔案。 如果檔案直接以 "Dockerfile" 命名，預設會辨識此名稱。

> [!NOTE]
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
   # Use the latest Windows Server Core image.
   FROM microsoft/windowsservercore

   # Download useful tools to C:\Bin.
   ADD https://dist.nuget.org/win-x86-commandline/v4.1.0/nuget.exe C:\\Bin\\nuget.exe

   # Download the Build Tools bootstrapper outside of the PATH.
   ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\\TEMP\\vs_buildtools.exe

   # Add C:\Bin to PATH and install Build Tools excluding workloads and components with known issues.
   RUN setx /m PATH "%PATH%;C:\Bin" \
    && C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache --installPath C:\BuildTools --all \
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 \
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 \
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 \
       --remove Microsoft.VisualStudio.Component.Windows81SDK \
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Start developer command prompt with any other commands specified.
   ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

   # Default to PowerShell if no other command specified.
   CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

4. 從該目錄內執行下列命令。

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   此命令使用 2 GB 的記憶體在目前的目錄中建置 Dockerfile。 安裝某些工作負載時，預設值 1 GB 並不夠；不過，根據您的建置需求，您可能只使用 1 GB 就能夠進行建置。

   最終映像會標記為 "buildtools2017:latest"，因此您可以輕鬆地在容器中當作 "buildtools2017" 來執行 (因為 "latest" 是未指定任何標記時的預設值)。 如果您想要在更[進階的案例](advanced-build-tools-container.md)中使用特定版本的 Visual Studio Build Tools 2017，請改以特定 Visual Studio 組建編號及 "latest" 來標記容器，以確保容器能夠一致地使用特定版本。

## <a name="step-6-using-the-built-image"></a>步驟 6： 使用建置的映像

現在您已建立映像，您可以在容器中執行，以同時執行互動式和自動化組建。 此範例使用開發人員命令提示字元，因此已設定您的 PATH 和其他環境變數。

1. 開啟命令提示字元。
2. 執行容器，以啟動 PowerShell 環境並設定所有開發人員環境變數：

   ```shell
   docker run -it buildtools2017
   ```

若要將此映像用於您的 CI/CD 工作流程，您可以將它發行至自己的 [Azure 容器登錄](https://azure.microsoft.com/services/container-registry)或其他內部 [Docker 登錄](https://docs.docker.com/registry/deploying)，讓伺服器只需要加以提取。

## <a name="get-support"></a>取得支援
有時可能會發生一些問題。 如果您的 Visual Studio 安裝失敗，請參閱[針對 Visual Studio 2017 安裝和升級問題進行疑難排解](troubleshooting-installation-issues.md)頁面。 如果所有疑難排解步驟都沒有幫助，您可以透過即時聊天與我們連絡，以取得安裝協助 (僅限英文)。 如需詳細資訊，請參閱 [Visual Studio 支援頁面](https://www.visualstudio.com/vs/support/#talktous) \(英文\)。

以下是一些支援選項：
* 您可以透過 Visual Studio 安裝程式和 Visual Studio IDE 中的[回報問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)工具來向我們報告產品問題。
* 您可以在 [UserVoice](https://visualstudio.uservoice.com/forums/121579) 上與我們分享產品建議。
* 您可以在 [Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/)追蹤產品問題，也可以在那裡詢問問題和尋找解答。
* 您也可以透過我們[在 Gitter 社群中的 Visual Studio 交談](https://gitter.im/Microsoft/VisualStudio)，與我們以及其他 Visual Studio 開發人員進行互動  (這個選項需要 [GitHub](https://github.com/) 帳戶)。

## <a name="see-also"></a>另請參閱

* [容器的進階範例](advanced-build-tools-container.md)
* [容器的已知問題](build-tools-container-issues.md)
* [Visual Studio Build Tools 2017 工作負載和元件識別碼](workload-component-id-vs-build-tools.md)
