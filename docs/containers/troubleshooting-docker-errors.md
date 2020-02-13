---
title: 針對 Windows 上的 Docker 用戶端錯誤進行疑難排解 | Microsoft Docs
description: 疑難排解使用 Visual Studio 在 Windows 上建立及部署 Web 應用程式到 Docker 時您會遇到的問題。
ms.technology: vs-azure
author: ghogen
manager: jillfra
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: conceptual
ms.workload: multiple
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: d8aa3028a12bcfb49f2663b2bea688baf14fd7f2
ms.sourcegitcommit: b2fc9ac7d73c847508f6ed082bed026476bb3955
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2020
ms.locfileid: "77027274"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>對使用 Docker 進行的 Visual Studio 開發進行疑難排解

當您使用 Visual Studio 容器工具時，您可能會在建立或偵測應用程式時遇到問題。 以下是一些常見的疑難排解步驟。

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>未啟用磁碟區共用。 在 Docker CE for Windows 設定中啟用磁碟區共用 (僅限 Linux 容器)

若要解決此問題：

1. 以滑鼠右鍵按一下通知區域中的 [適用於 Windows 的 Docker]，然後選取 [設定]。
1. 選取 [共用磁碟機] 並共用系統磁碟機以及專案所在的磁碟機。

> [!NOTE]
> 如果檔案似乎已共用，您仍可能需要按一下對話方塊下的 [重設認證...] 連結，以重新啟用磁碟區共用。 若要在重設認證後繼續，您可能必須重新啟動 Visual Studio。

![共用的磁碟機](media/troubleshooting-docker-errors/shareddrives.png)

> [!TIP]
> 當未設定**共用磁片磁碟機**時，Visual Studio 高於 Visual Studio 2017 15.6 版的版本提示。

### <a name="container-type"></a>容器類型

將 Docker 支援新增至專案時，您可以選擇 Windows 或 Linux 容器。 Docker 主機必須執行相同的容器類型。 若要變更執行中 Docker 執行個體中的容器類型，請以滑鼠右鍵按一下系統匣的 Docker 圖示，然後選擇 [Switch to Windows containers...] (切換至 Windows 容器...) 或 [Switch to Linux containers] (切換至 Linux 容器...)。

## <a name="unable-to-start-debugging"></a>無法開始偵錯

其中一個原因可能與您的使用者設定檔資料夾中有過時的偵錯元件有關。 請執行下列命令移除這些資料夾，以便在下一個偵錯工作階段下載最新的偵錯元件。

- del %userprofile%\vsdbg
- del %userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>偵錯您的應用程式時與網路功能相關的錯誤

請嘗試執行可從[清除容器主機網路](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking)下載的指令碼，這會重新整理主機電腦上與網路相關的元件。

## <a name="mounts-denied"></a>拒絕掛接

使用 macOS 適用的 Docker 時，您可能會遇到參考 /usr/local/share/dotnet/sdk/NuGetFallbackFolder 資料夾的錯誤。 將此資料夾新增至 Docker 中的 [檔案共用] 索引標籤

## <a name="docker-users-group"></a>Docker 使用者群組

使用容器時，您可能會在 Visual Studio 中遇到下列錯誤：

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

您必須是「docker 使用者」群組的成員，才能擁有使用 Docker 容器的許可權。  若要將自己新增至 Windows 10 中的群組，請遵循下列步驟：

1. 在 [開始] 功能表中，開啟 [**電腦管理**]。
1. 展開 [**本機使用者和群組**]，然後選擇 [**群組**]。
1. 尋找 [ **docker-使用者**] 群組，按一下滑鼠右鍵並選擇 [**加入群組**]。
1. 新增您的使用者帳戶或帳戶。
1. 登出後再重新登入，這些變更才會生效。

您也可以在系統管理員命令提示字元中使用 `net localgroup` 命令，將使用者新增至特定群組。

```cmd
net localgroup docker-users DOMAIN\username /add
```

在 PowerShell 中，使用[LocalGroupMember](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember)函數。

## <a name="low-disk-space"></a>磁碟空間不足

根據預設，Docker 會將映射儲存在 *% ProgramData%/Docker/* 資料夾中，這通常是在系統磁片磁碟機上，* c:\programdata\docker 目錄\*。 若要防止影像在系統磁片磁碟機上佔用寶貴的空間，您可以變更映射資料夾位置。  從工作列上的 Docker 圖示開啟 [Docker 設定]，選擇 [ **Daemon**]，然後從 [**基本**] 切換至 [ **Advanced**]。 在編輯窗格中，使用您想要的 Docker 映射位置值來新增 `graph` 屬性設定：

```json
    "graph": "D:\\mypath\\images"
```

![Docker 映射位置設定的螢幕擷取畫面](media/troubleshooting-docker-errors/docker-settings-image-location.png)

按一下 **[** 套用] 以重新開機 Docker。 這些步驟會在 *%ProgramData%\docker\config\daemon.json*修改設定檔。 先前建立的映射不會移動。

## <a name="microsoftdockertools-github-repo"></a>Microsoft/DockerTools GitHub 存放庫

對於您遇到的其他任何問題，請參閱 [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues) 問題。