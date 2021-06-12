---
title: 將 Visual Studio Build Tools 安裝至容器
titleSuffix: ''
description: 了解如何將 Visual Studio Build Tools 安裝至 Windows 容器，以便支援持續整合與持續傳遞 (CI/CD) 工作流程。
ms.date: 03/25/2020
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fc3133692007a53b48d658ed284d6af0bde0af4a
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2021
ms.locfileid: "112043077"
---
# <a name="install-build-tools-into-a-container"></a>將 Build Tools 安裝至容器

您可以將 Visual Studio Build Tools 安裝至 Windows 容器，以便支援持續整合與持續傳遞 (CI/CD) 工作流程。 本文將引導您了解需要進行的 Docker 組態變更，以及可在容器中安裝的[工作負載和元件](workload-component-id-vs-build-tools.md)。

[容器](https://www.docker.com/what-container)是用來封裝一致之建置系統的好方法，不僅可用於 CI/CD 伺服器環境，也可用於開發環境。 例如，您可以將原始程式碼裝載於容器中以供自訂環境建置，同時繼續使用 Visual Studio 或其他工具來撰寫程式碼。 如果您的 CI/CD 工作流程使用相同的容器映像，就能確信您的程式碼會以一致的方式建置。 您也可以使用容器來取得執行階段一致性，此做法常見於使用具有一套協調流程系統之多個容器的微服務，但不在本文討論範圍內。

如果 Visual Studio Build Tools 沒有您建置原始程式碼所需的工具，這些相同步驟可用於其他 Visual Studio 產品。 但請注意，Windows 容器不支援互動式使用者介面，因此所有命令都必須自動化。

## <a name="before-you-begin"></a>開始之前

假設您已熟悉下列 [Docker](https://www.docker.com/what-docker) 功能。 若不熟悉如何在 Windows 上執行 Docker，請了解如何[在 Windows 上安裝並設定 Docker 引擎](/virtualization/windowscontainers/manage-docker/configure-docker-daemon) \(部分機器翻譯\)。

下面的基底映像是範例，因此可能無法適用於您的系統。 閱讀 [Windows 容器版本相容性](/virtualization/windowscontainers/deploy-containers/version-compatibility)以決定您應該為您的環境使用哪個基底映像。

## <a name="create-and-build-the-dockerfile"></a>建立並建置 Dockerfile

將下列範例 Dockerfile 儲存至磁碟上的新檔案。 如果檔案直接以 "Dockerfile" 命名，預設會辨識此名稱。

> [!WARNING]
> 此範例 Dockerfile 只會排除無法安裝至容器的舊版 Windows SDK。 較舊版本會造成建置命令失敗。

1. 開啟命令提示字元。

1. 建立新的目錄 (建議)：

   ```shell
   mkdir C:\BuildTools
   ```

1. 將目錄變更為此新目錄：

   ```shell
   cd C:\BuildTools
   ```

1. 將下列內容儲存至 C:\BuildTools\Dockerfile。
 
   ::: moniker range="vs-2017"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.2.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   RUN `
       # Download the Build Tools bootstrapper.
       curl -SL --output vs_buildtools.exe https://aka.ms/vs/15/release/vs_buildtools.exe `
       `
       # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
       && (start /w vs_buildtools.exe --quiet --wait --norestart --nocache `
           --installPath C:\BuildTools `
           --add Microsoft.VisualStudio.Workload.AzureBuildTools `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
           --remove Microsoft.VisualStudio.Component.Windows81SDK `
           || IF "%ERRORLEVEL%"=="3010" EXIT 0) `
       `
       # Cleanup
       && del /q vs_buildtools.exe

   # Define the entry point for the Docker container.
   # This entry point starts the developer command prompt and launches the PowerShell shell.
   ENTRYPOINT ["C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!TIP]
   > 如需工作負載和元件的清單，請參閱 [Visual Studio Build Tools 元件目錄](workload-component-id-vs-build-tools.md)。
   >

   > [!WARNING]
   > 如果您是直接以 microsoft/windowsservercore 或 mcr.microsoft.com/windows/servercore 作為映像的基礎 (請參閱 [Microsoft 同步發佈容器目錄](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/) \(英文\))，.NET Framework 可能會無法正確安裝，且不會指出任何安裝錯誤。 安裝完成之後，可能無法執行受控碼。 相反地，讓您的映像以 [microsoft/dotnet-framework:4.7.2](https://hub.docker.com/r/microsoft/dotnet-framework) 或更新版本為基礎。 另請注意，標記為 4.7.2 或更新版的映像可能會使用 PowerShell 作為預設 `SHELL`，導致 `RUN` 和 `ENTRYPOINT` 指令失敗。
   >
   > Visual Studio 2017 15.8 或更早版本 (任何產品) 無法在 mcr.microsoft.com/windows/servercore:1809 (或更新版本) 上正確安裝。 不會顯示錯誤。
   >
   > 請參閱 [Windows 容器版本相容性](/virtualization/windowscontainers/deploy-containers/version-compatibility) \(部分機器翻譯\) 以查看各種主機 OS 版本所支援的容器 OS 版本，並參閱[容器的已知問題](build-tools-container-issues.md)以了解已知問題。
   
   ::: moniker-end

   ::: moniker range="vs-2019"

   ```dockerfile
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.8.
   FROM mcr.microsoft.com/dotnet/framework/sdk:4.8-windowsservercore-ltsc2019

   # Restore the default Windows shell for correct batch processing.
   SHELL ["cmd", "/S", "/C"]

   RUN `
       # Download the Build Tools bootstrapper.
       curl -SL --output vs_buildtools.exe https://aka.ms/vs/16/release/vs_buildtools.exe `
       `
       # Install Build Tools with the Microsoft.VisualStudio.Workload.AzureBuildTools workload, excluding workloads and components with known issues.
       && (start /w vs_buildtools.exe --quiet --wait --norestart --nocache modify `
           --installPath "%ProgramFiles(x86)%\Microsoft Visual Studio\2019\BuildTools" `
           --add Microsoft.VisualStudio.Workload.AzureBuildTools `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
           --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
           --remove Microsoft.VisualStudio.Component.Windows81SDK `
           || IF "%ERRORLEVEL%"=="3010" EXIT 0) `
       `
       # Cleanup
       && del /q vs_buildtools.exe

   # Define the entry point for the docker container.
   # This entry point starts the developer command prompt and launches the PowerShell shell.
   ENTRYPOINT ["C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "&&", "powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!TIP]
   > 如需工作負載和元件的清單，請參閱 [Visual Studio Build Tools 元件目錄](workload-component-id-vs-build-tools.md)。
   >

   > [!WARNING]
   > 如果您讓映像直接以 microsoft/windowsservercore 為基礎，.NET Framework 可能無法正確安裝且不會指出任何安裝錯誤。 安裝完成之後，可能無法執行受控碼。 相反地，讓您的映像以 [microsoft/dotnet-framework:4.8](https://hub.docker.com/r/microsoft/dotnet-framework) 或更新版本為基礎。 另請注意，標記為 4.8 或更新版的映像可能會使用 PowerShell 作為預設 `SHELL`，導致 `RUN` 和 `ENTRYPOINT` 指令失敗。
   >
   > 請參閱 [Windows 容器版本相容性](/virtualization/windowscontainers/deploy-containers/version-compatibility) \(部分機器翻譯\) 以查看各種主機 OS 版本所支援的容器 OS 版本，並參閱[容器的已知問題](build-tools-container-issues.md)以了解已知問題。

   ::: moniker-end
   
   > [!NOTE]
   > 錯誤碼 `3010` 可用來表示成功，需要重新開機，請參閱 [MsiExec.exe 錯誤訊息](/windows/win32/msi/error-codes) 以取得詳細資訊。

1. 從該目錄內執行下列命令。

   ::: moniker range="vs-2017"

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   此命令使用 2 GB 的記憶體在目前的目錄中建置 Dockerfile。 安裝某些工作負載時，預設 1 GB 並不夠；不過，根據您的建置需求，您可能只使用 1 GB 記憶體就能夠進行建置。

   最終映像會標記為 "buildtools2017:latest"，因此您可以輕鬆地在容器中當作 "buildtools2017" 來執行 (因為 "latest" 是未指定任何標記時的預設值)。 如果您想要在更[進階的案例](advanced-build-tools-container.md)中使用特定版本的 Visual Studio Build Tools 2017，請改以特定 Visual Studio 組建編號及 "latest" 來標記容器，以確保容器能夠一致地使用特定版本。

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker build -t buildtools2019:latest -m 2GB .
   ```

   此命令使用 2 GB 的記憶體在目前的目錄中建置 Dockerfile。 安裝某些工作負載時，預設 1 GB 並不夠；不過，根據您的建置需求，您可能只使用 1 GB 記憶體就能夠進行建置。

   最終映像會標記為 "buildtools2019:latest"，因此您可以輕鬆地在容器中當作 "buildtools2019" 來執行 (因為 "latest" 是未指定任何標記時的預設)。 如果您想要在更[進階的案例](advanced-build-tools-container.md)中使用特定版本 Visual Studio Build Tools 2019，請改以特定 Visual Studio 組建編號及 "latest" 來標記容器，以確保容器能夠一致地使用特定版本。

   ::: moniker-end

## <a name="using-the-built-image"></a>使用建置的映像

現在您已建立映像，您可以在容器中執行，以同時執行互動式和自動化組建。 此範例使用開發人員命令提示字元，因此已設定您的 PATH 和其他環境變數。

1. 開啟命令提示字元。

1. 執行容器，以啟動 PowerShell 環境並設定所有開發人員環境變數：

   ::: moniker range="vs-2017"

   ```shell
   docker run -it buildtools2017
   ```

   ::: moniker-end

   ::: moniker range="vs-2019"

   ```shell
   docker run -it buildtools2019
   ```

   ::: moniker-end

若要將此映像用於您的 CI/CD 工作流程，您可以將其發佈至自己的 [Azure 容器登錄](https://azure.microsoft.com/services/container-registry)或其他內部 [Docker 登錄](https://docs.docker.com/registry/deploying)，讓伺服器只需要加以提取。

   > [!NOTE]
   > 如果 Docker 容器無法啟動，可能是 Visual Studio 安裝問題。 您可以更新 Dockerfile，以移除呼叫 Visual Studio 批次命令的步驟。 這可讓您啟動 Docker 容器，並讀取安裝錯誤記錄檔。
   >
   > 在 Dockerfile 檔案中， `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` `&&` 從命令移除和參數 `ENTRYPOINT` 。 命令現在應該是 `ENTRYPOINT ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]` 。 接下來，重建 Dockerfile 並執行 `run` 命令以存取容器檔案。 若要找出安裝錯誤記錄檔，請移至 `$env:TEMP` 目錄並找出檔案 `dd_setup_<timestamp>_errors.log` 。
   >
   > 找出並修正安裝問題之後，您可以將 `C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat` 和參數新增 `&&` 回 `ENTRYPOINT` 命令，並重建您的 Dockerfile。
   >
   > 如需詳細資訊，請參閱[容器的已知問題](build-tools-container-issues.md)。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

* [容器的進階範例](advanced-build-tools-container.md)
* [容器的已知問題](build-tools-container-issues.md)
* [Visual Studio Build Tools 工作負載和元件識別碼](workload-component-id-vs-build-tools.md)
