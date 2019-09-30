---
title: 針對 Windows 上的 Docker 用戶端錯誤進行疑難排解 | Microsoft Docs
description: 針對使用 Visual Studio 在 Windows 上建立 web 應用程式並將其部署至 Docker 時所遇到的問題進行疑難排解，方法是使用 Visual Studio。
ms.technology: vs-azure
author: ghogen
manager: jillfra
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: conceptual
ms.workload: multiple
ms.date: 10/13/2017
ms.author: ghogen
ms.openlocfilehash: ca43098740a1e8e940f27eae8d2c4d405c23230b
ms.sourcegitcommit: 16d8ffc624adb716753412a22d586eae68a29ba2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2019
ms.locfileid: "70312195"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>對使用 Docker 進行的 Visual Studio 開發進行疑難排解

當您使用 Visual Studio 容器工具時，您可能會在建立或偵測應用程式時遇到問題。 以下是一些常見的疑難排解步驟。

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>未啟用磁片區共用。 在適用於 Windows 的 Docker CE 設定中啟用磁片區共用（僅限 Linux 容器）

若要解決此問題︰

1. 以滑鼠右鍵按一下通知區域中的 [**適用於 Windows 的 Docker** ]，然後選取 [**設定**]。
1. 選取 [**共用磁片磁碟機**]，並共用系統磁片磁碟機以及專案所在的磁片磁碟機。

> [!NOTE]
> 如果檔案顯示為 [共用]，您可能仍然需要按一下 [重設認證 ...]連結，以便重新啟用磁片區共用。 若要在重設認證之後繼續，您可能必須重新開機 Visual Studio。

![共用磁片磁碟機](media/troubleshooting-docker-errors/shareddrives.png)

> [!TIP]
> 當未設定**共用磁片磁碟機**時，Visual Studio 高於 Visual Studio 2017 15.6 版的版本提示。

### <a name="container-type"></a>容器類型

將 Docker 支援新增至專案時，您可以選擇 Windows 或 Linux 容器。 Docker 主機必須執行相同的容器類型。 若要變更執行中 Docker 執行個體中的容器類型，請以滑鼠右鍵按一下系統匣的 Docker 圖示，然後選擇 [Switch to Windows containers...] (切換至 Windows 容器...) 或 [Switch to Linux containers] (切換至 Linux 容器...)。

## <a name="unable-to-start-debugging"></a>無法啟動調試

其中一個原因可能與在您的使用者設定檔資料夾中具有過時的偵錯工具元件有關。 執行下列命令來移除這些資料夾，以便在下一個 debug 會話下載最新的偵錯工具元件。

- del%userprofile%\vsdbg
- del%userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>在偵測應用程式時，網路的特定錯誤

請嘗試從[清理容器主機網路](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking)功能執行可下載的腳本，這會重新整理您主機電腦上的網路相關元件。

## <a name="mounts-denied"></a>已拒絕裝載

使用 Docker 進行 macOS 時，您可能會遇到參考資料夾/usr/local/share/dotnet/sdk/NuGetFallbackFolder. 的錯誤 將此資料夾新增至 Docker 中的 [檔案共用] 索引標籤

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

您也可以在系統`net localgroup`管理員命令提示字元中使用命令，將使用者新增至特定群組。

```cmd
net localgroup docker-users DOMAIN\username /add
```

在 PowerShell 中，使用[LocalGroupMember](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember)函數。

## <a name="microsoftdockertools-github-repo"></a>Microsoft/DockerTools GitHub 存放庫

如有任何您遇到的其他問題，請參閱[Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues)問題。