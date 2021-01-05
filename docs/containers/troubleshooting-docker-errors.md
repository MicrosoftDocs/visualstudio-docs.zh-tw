---
title: 針對 Windows 上的 Docker 用戶端錯誤進行疑難排解 | Microsoft Docs
description: 疑難排解使用 Visual Studio 在 Windows 上建立及部署 Web 應用程式到 Docker 時您會遇到的問題。
ms.technology: vs-azure
author: ghogen
manager: jillfra
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: troubleshooting
ms.workload: multiple
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: 9535a7d88cb375d97867092eddf969095c327329
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729238"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>對使用 Docker 進行的 Visual Studio 開發進行疑難排解

當您使用 Visual Studio 容器工具時，您可能會在建立或偵測應用程式時遇到問題。 以下是一些常見的疑難排解步驟。

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>未啟用磁碟區共用。 在 Docker CE for Windows 設定中啟用磁碟區共用 (僅限 Linux 容器)

如果您搭配使用 Hyper-v 與 Docker，則只需要管理檔案共用。 如果您使用的是 WSL 2，則不需要執行下列步驟，而且將不會顯示檔案共用選項。 若要解決此問題：

1. 以滑鼠右鍵按一下通知區域中的 [適用於 Windows 的 Docker]，然後選取 [設定]。
1. 選取 **資源**  >  **檔共用**，並共用需要存取的資料夾。 您可以共用整個系統磁片磁碟機，但不建議這麼做。

    ![共用的磁碟機](media/troubleshooting-docker-errors/docker-settings-image.png)

> [!TIP]
> 當未設定 **共用磁片磁碟機** 時，Visual Studio Visual Studio 2017 15.6 版以後的版本將會提示。

## <a name="unable-to-start-debugging"></a>無法開始偵錯

其中一個原因可能與您的使用者設定檔資料夾中有過時的偵錯元件有關。 請執行下列命令移除這些資料夾，以便在下一個偵錯工作階段下載最新的偵錯元件。

- del %userprofile%\vsdbg
- del %userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>偵錯您的應用程式時與網路功能相關的錯誤

請嘗試執行可從[清除容器主機網路](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking)下載的指令碼，這會重新整理主機電腦上與網路相關的元件。

## <a name="mounts-denied"></a>拒絕掛接

使用 macOS 適用的 Docker 時，您可能會遇到參考 /usr/local/share/dotnet/sdk/NuGetFallbackFolder 資料夾的錯誤。 將此資料夾新增至 Docker 中的 [檔案共用] 索引標籤。

## <a name="docker-users-group"></a>Docker 使用者群組

使用容器時，您可能會在 Visual Studio 中遇到下列錯誤：

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

您必須是「docker 使用者」群組的成員，才能擁有使用 Docker 容器的許可權。  若要將您自己新增至 Windows 10 中的群組，請遵循下列步驟：

1. 從 [開始] 功能表中，開啟 [ **電腦管理**]。
1. 展開 [ **本機使用者和群組**]，然後選擇 [ **群組**]。
1. 尋找 **docker 使用者** 群組，按一下滑鼠右鍵並選擇 [ **加入群組**]。
1. 新增您的使用者帳戶或帳戶。
1. 登出後再重新登入，這些變更才會生效。

您也可以 `net localgroup` 在系統管理員命令提示字元中使用命令，將使用者新增至特定群組。

```cmd
net localgroup docker-users DOMAIN\username /add
```

在 PowerShell 中，使用 [LocalGroupMember](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember) 函數。

## <a name="low-disk-space"></a>磁碟空間不足

根據預設，Docker 會將影像儲存在 *% ProgramData%/Docker/* 資料夾中，此資料夾通常位於系統磁片磁碟機 * C:\ProgramData\Docker \* 。 若要防止映射佔用系統磁片磁碟機上的寶貴空間，您可以變更映射資料夾位置。 操作方法：

 1. 以滑鼠右鍵按一下工作列上的 Docker 圖示，然後選取 [ **設定**]。
 1. 選取 [ **Docker 引擎**]。 
 1. 在編輯窗格中，新增 `graph` 具有您所需 Docker 映射位置值的屬性設定：

```json
    "graph": "D:\\mypath\\images"
```

![Docker 檔案共用的螢幕擷取畫面](media/troubleshooting-docker-errors/docker-daemon-settings.png)

按一下 [套用 **& 重新開機**]。 這些步驟會修改 *% ProgramData% \docker\config\daemon.js上* 的設定檔。 先前建立的映射不會移動。

## <a name="container-type-mismatch"></a>容器類型不符

將 Docker 支援新增至專案時，您可以選擇 Windows 或 Linux 容器。 如果 Docker Server 主機未設定為與專案目標執行相同的容器類型，您可能會看到類似下面的錯誤：

![Docker 主機和專案不符的螢幕擷取畫面](media/troubleshooting-docker-errors/docker-host-config-change-linux-to-windows.png)

若要解決此問題：

- 以滑鼠右鍵按一下系統匣中的適用於 Windows 的 Docker 圖示，然後選擇 [ **切換到 Windows 容器 ...** ] 或 [ **切換至 Linux 容器**...]。

## <a name="microsoftdockertools-github-repo"></a>Microsoft/DockerTools GitHub 存放庫

對於您遇到的其他任何問題，請參閱 [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues) 問題。

## <a name="see-also"></a>請參閱

- [Visual Studio 疑難排解](/troubleshoot/visualstudio/welcome-visual-studio/)
