---
title: 容器的進階範例
description: ''
ms.custom: ''
ms.date: 04/18/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c941928495dc39dc6b6ecbe9600f39dad969fec2
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
ms.locfileid: "31621141"
---
# <a name="advanced-example-for-containers"></a>容器的進階範例

[將建置工具安裝至容器](build-tools-container.md)中的範例 Dockerfile 一律使用根據最新 microsoft/windowsservercore 映像的 [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) 映像，和最新的 Visual Studio Build Tools 2017 安裝程式。 如果您將此映像發行到 [Docker 登錄](https://azure.microsoft.com/services/container-registry)以供其他人提取，此映像在許多情況下可能沒問題。 不過，實際上較常見的做法是指定您使用的基底映像、您下載的二進位檔及您安裝的工具版本。

下列範例 Dockerfile 使用 microsoft/dotnet-framework 映像的特定版本標記。 使用基底映像的特定標記很常見，很容易就記住建立或重建映像一律會有相同的基礎。

> [!NOTE]
> 您無法將 Visual Studio 安裝到 microsoft/windowsservercore:10.0.14393.1593 或以它為基礎的任何映像，此版本已知在容器中啟動安裝程式時會發生問題。 如需詳細資訊，請參閱[已知問題](build-tools-container-issues.md)。

下列範例會下載最新版的 Build Tools 2017。 如果您想要使用較舊版本的 Build Tools，可以稍後再安裝至容器時，您必須先[建立](create-an-offline-installation-of-visual-studio.md)和[維護](update-a-network-installation-of-visual-studio.md)配置。

## <a name="install-script"></a>安裝指令碼

若要在發生安裝錯誤時收集記錄檔，請在工作目錄中建立名為 "Install.cmd" 的批次指令碼，且具有下列內容：

```shell
@if not defined _echo echo off
setlocal enabledelayedexpansion

call %*
if "%ERRORLEVEL%"=="3010" (
    exit /b 0
) else (
    if not "%ERRORLEVEL%"=="0" (
        set ERR=%ERRORLEVEL%
        call C:\TEMP\collect.exe -zip:C:\vslogs.zip

        exit /b !ERR!
    )
)
```

## <a name="dockerfile"></a>Dockerfile

在工作目錄中，建立具有下列內容的 Dockerfile：

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:1a66e2b5f3a5b8b98ac703a8bfd4902ae60d307ed9842978df40dbc04ac86b1b
ARG FROM_IMAGE=microsoft/dotnet-framework:4.7.1-20180410-windowsservercore-1709
FROM ${FROM_IMAGE}

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/15/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Download and install Build Tools excluding workloads and components with known issues.
ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --all `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Start developer command prompt with any other commands specified.
ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

# Default to PowerShell if no other command specified.
CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

執行下列命令，在目前工作目錄中建置映像：

```shell
docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
```

選擇性地使用 `--build-arg` 命令列參數傳遞 `FROM_IMAGE` 或 `CHANNEL_URL` 引數中的任一者或兩者都傳遞，以指定不同的基底映像或內部配置的位置，以維護固定的映像。

## <a name="diagnosing-install-failures"></a>診斷安裝失敗

此範例會下載特定工具，並驗證雜湊相符。 它也會下載最新的 Visual Studio 和 .NET 記錄收集公用程式，因此如果確實發生安裝失敗，您可以將記錄複製到主機電腦以分析失敗。

```shell
> docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
Sending build context to Docker daemon
...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

最後一行完成執行之後，開啟您電腦上的 "%TEMP%\vslogs.zip"，或在[開發人員社群](https://developercommunity.visualstudio.com)網站上提交問題。

## <a name="get-support"></a>取得支援

有時可能會發生一些問題。 如果您的 Visual Studio 安裝失敗，請參閱[針對 Visual Studio 2017 安裝和升級問題進行疑難排解](troubleshooting-installation-issues.md)頁面。 如果所有疑難排解步驟都沒有幫助，您可以透過即時聊天與我們連絡，以取得安裝協助 (僅限英文)。 如需詳細資訊，請參閱 [Visual Studio 支援頁面](https://www.visualstudio.com/vs/support/#talktous) \(英文\)。

以下是一些支援選項：

* 您可以透過 Visual Studio 安裝程式和 Visual Studio IDE 中的[回報問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)工具來向我們報告產品問題。
* 您可以在 [UserVoice](https://visualstudio.uservoice.com/forums/121579) 上與我們分享產品建議。
* 您可以追蹤產品問題並在 [Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/) \(英文\) 中尋找解答。
* 您也可以透過[在 Gitter 社群中的 Visual Studio 交談](https://gitter.im/Microsoft/VisualStudio)，與我們以及其他 Visual Studio 開發人員進行互動。 (這個選項需要 [GitHub](https://github.com/) 帳戶)。

## <a name="see-also"></a>另請參閱

* [將建置工具安裝至容器](build-tools-container.md)
* [容器的已知問題](build-tools-container-issues.md)
* [Visual Studio Build Tools 2017 工作負載和元件識別碼](workload-component-id-vs-build-tools.md)
