---
title: "容器的進階範例 | Microsoft Docs"
ms.custom: 
ms.date: 10/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: heaths
ms.author: heaths
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6009114d16871f4582aae298b25de9a3b9fe5888
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="advanced-example-for-containers"></a>容器的進階範例

[將建置工具安裝至容器](build-tools-container.md)中的範例 Dockerfile 一律使用最新的 microsoft/windowsservercore 映像和最新的 Visual Studio Build Tools 2017 安裝程式。 如果您將此映像發行到 [Docker 登錄](https://azure.microsoft.com/services/container-registry)以供其他人提取，此映像在許多情況下可能沒問題。 不過實際上，較常見的做法是指定您使用的基底映像、您下載的二進位檔及您安裝的工具版本。

下列範例 Dockerfile 使用 microsoft/windowsservercore 映像的特定版本標記。 使用基底映像的特定標記很常見，很容易就記住建立或重建映像一律會有相同的基礎。

> [!NOTE]
> 您無法將 Visual Studio 安裝到 microsoft/windowsservercore:10.0.14393.1593，此版本已知在容器中啟動安裝程式時會發生問題。 如需詳細資訊，請參閱[已知問題](build-tools-container-issues.md)。

此範例也會使用 Build Tools 2017 啟動載入器，以安裝與啟動載入器同時建置的特定版本。 您仍然可以透過發行通道來更新此產品，但這對您通常會重建的容器而言並不實際。 如果您想要取得特定通道的 URL，您可以從 https://aka.ms/vs/15/release/channel 下載通道、開啟 JSON 檔案，然後查看啟動載入器 URL。 如需詳細資訊，請參閱[建立 Visual Studio 的網路安裝](create-a-network-installation-of-visual-studio.md)。

```dockerfile
# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:d841bd78721c74f9b88e2700f5f3c2d66b54cb855b8acb4ab2c627a76a46301d
FROM microsoft/windowsservercore:10.0.14393.1770

# Use PowerShell commands to download, validate hashes, etc.
SHELL ["powershell.exe", "-ExecutionPolicy", "Bypass", "-Command", "$ErrorActionPreference='Stop'; $ProgressPreference='SilentlyContinue'; $VerbosePreference = 'Continue';"]

# Download Build Tools 15.4.27004.2005 and other useful tools.
ENV VS_BUILDTOOLS_URI=https://aka.ms/vs/15/release/6e8971476/vs_buildtools.exe \
    VS_BUILDTOOLS_SHA256=D482171C7F2872B6B9D29B116257C6102DBE6ABA481FAE4983659E7BF67C0F88 \
    NUGET_URI=https://dist.nuget.org/win-x86-commandline/v4.1.0/nuget.exe \
    NUGET_SHA256=4C1DE9B026E0C4AB087302FF75240885742C0FAA62BD2554F913BBE1F6CB63A0

# Download tools to C:\Bin and install Build Tools excluding workloads and components with known issues.
RUN New-Item -Path C:\Bin, C:\TEMP -Type Directory | Out-Null; \
    [System.Environment]::SetEnvironmentVariable('PATH', "\"${env:PATH};C:\Bin\"", 'Machine'); \
    function Fetch ([string] $Uri, [string] $Path, [string] $Hash) { \
      Invoke-RestMethod -Uri $Uri -OutFile $Path; \
      if ($Hash -and ((Get-FileHash -Path $Path -Algorithm SHA256).Hash -ne $Hash)) { \
        throw "\"Download hash for '$Path' incorrect\""; \
      } \
    }; \
    Fetch -Uri $env:NUGET_URI -Path C:\Bin\nuget.exe -Hash $env:NUGET_SHA256; \
    Fetch -Uri $env:VS_BUILDTOOLS_URI -Path C:\TEMP\vs_buildtools.exe -Hash $env:VS_BUILDTOOLS_SHA256; \
    Fetch -Uri 'https://aka.ms/vscollect.exe' -Path C:\TEMP\collect.exe; \
    $p = Start-Process -Wait -PassThru -FilePath C:\TEMP\vs_buildtools.exe -ArgumentList '--quiet --wait --norestart --nocache --installPath C:\BuildTools --all --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 --remove Microsoft.VisualStudio.Component.Windows81SDK'; \
    if (($ret = $p.ExitCode) -and ($ret -ne 3010)) { C:\TEMP\collect.exe; throw ('Install failed with exit code 0x{0:x}' -f $ret) }

# Restore default shell for Windows containers.
SHELL ["cmd.exe", "/s", "/c"]

# Start developer command prompt with any other commands specified.
ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

# Default to PowerShell if no other command specified.
CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

此範例會下載特定工具，並驗證雜湊相符。 它也會下載最新的 Visual Studio 和 .NET 記錄收集公用程式，因此如果確實發生安裝失敗，您可以將記錄複製到主機電腦以分析失敗。

```shell
> docker build -t buildtools:15.4.27004.2005 -t buildtools:latest -m 2GB .
Sending build context to Docker daemon
...
Step 4/7 : RUN New-Item -Path C:\Bin, C:\TEMP -Type Directory | Out-Null; ...
 ---> Running in 4b62b4ce3a3c
Install failed with exit code 0x643
At line:1 char:1
+ throw ('Install failed with exit code 0x{0:x}' -f 1603)
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (Install failed with exit code 0x643:String) [], RuntimeException
    + FullyQualifiedErrorId : Install failed with exit code 0x643

> docker cp 4b62b4ce3a3c:C:\Users\ContainerAdministrator\AppData\Local\TEMP\vslogs.zip "%TEMP%\vslogs.zip"
```

最後一行完成執行之後，開啟您電腦上的 "%TEMP%\vslogs.zip"，或在[開發人員社群](https://developercommunity.visualstudio.com)網站上提交問題。

## <a name="get-support"></a>取得支援
有時可能會發生一些問題。 如果您的 Visual Studio 安裝失敗，請參閱[針對 Visual Studio 2017 安裝和升級問題進行疑難排解](troubleshooting-installation-issues.md)頁面。 如果所有疑難排解步驟都沒有幫助，您可以透過即時聊天與我們連絡，以取得安裝協助 (僅限英文)。 如需詳細資訊，請參閱 [Visual Studio 支援頁面](https://www.visualstudio.com/vs/support/#talktous) \(英文\)。

以下是一些支援選項：
* 您可以透過 Visual Studio 安裝程式和 Visual Studio IDE 中的[回報問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)工具來向我們報告產品問題。
* 您可以在 [UserVoice](https://visualstudio.uservoice.com/forums/121579) 上與我們分享產品建議。
* 您可以在 [Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/)追蹤產品問題，也可以在那裡詢問問題和尋找解答。
* 您也可以透過我們[在 Gitter 社群中的 Visual Studio 交談](https://gitter.im/Microsoft/VisualStudio)，與我們以及其他 Visual Studio 開發人員進行互動  (這個選項需要 [GitHub](https://github.com/) 帳戶)。

## <a name="see-also"></a>另請參閱
* [將建置工具安裝至容器](build-tools-container.md)
* [容器的已知問題](build-tools-container-issues.md)
* [Visual Studio Build Tools 2017 工作負載和元件識別碼](workload-component-id-vs-build-tools.md)
