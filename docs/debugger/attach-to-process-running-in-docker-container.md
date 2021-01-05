---
title: 附加至在 Docker 容器上執行的進程
description: 瞭解如何使用 Visual Studio 來對執行 Docker 容器的應用程式進行偵錯工具
ms.date: 11/11/2020
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux Docker container
- debugging, Docker container
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: f6e2b851057d924353e6e1e9a211fcbb294353c8
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761260"
---
# <a name="attach-to-a-process-running-on-a-docker-container"></a>附加至在 Docker 容器上執行的進程 

您可以使用 Visual Studio 來對 Windows Docker 容器或 Linux .NET Core Docker 容器中執行的應用程式進行 debug 錯。

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a>附加至在 Linux Docker 容器上執行的進程

您可以使用 [ **附加至進程** ] 對話方塊，將 Visual Studio 偵錯工具附加到本機或遠端電腦上 Linux .Net Core Docker 容器中執行的進程。

> [!IMPORTANT]
> 若要使用此功能，您必須安裝 .NET Core 跨平臺開發工作負載，並具有原始程式碼的本機存取權。

**若要附加至 Linux Docker 容器中的執行中進程：**

1. 在 Visual Studio 中，選取 [ **Debug > 附加至進程 (CTRL + ALT + P)** 以開啟 [ **附加至進程** ] 對話方塊。

![[附加至進程] Visual Studio 對話方塊的螢幕擷取畫面，其中顯示 Docker (Linux 容器) 的連線類型。](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. 將連線 **類型** 設定為 **Docker (Linux 容器)**。
3. 選取 [**尋找**]，以透過 [**選取 Docker 容器**] 對話方塊設定 **連接目標**。

    您可以在本機或遠端進行 Docker 容器進程的偵錯工具。

    **若要在本機上進行 Docker 容器進程的偵錯工具：**
    1. 將 **DOCKER CLI 主機** 設定為 [ **本機電腦**]。
    1. 從清單中選取要附加的執行中容器，然後按 **[確定]**。

    ![選取 Docker 容器功能表](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")

    **B。若要從遠端偵測 Docker 容器進程：**

    > [!NOTE]
    > 有兩個選項可讓您從遠端連線到 Docker 容器中的執行中進程。 如果您未在本機電腦上安裝 Docker 工具，第一個選項（使用 SSH）是理想的選擇。  如果您在本機安裝了 Docker tools，而且您有一個設定為接受遠端要求的 Docker daemon，請使用 Docker daemon 嘗試第二個選項。

    1. *透過 *_SSH 連接到遠端電腦：_* _
        1. 選取 _ *新增 ...** 連接至遠端系統。<br/>
        ![連接至遠端系統](../debugger/media/connect-remote-system.png "連接至遠端系統")
        1. 在成功連線到 SSH 或背景程式之後，選取要附加的執行中容器，並按 **[確定]**。

    1. **_若要將目標設定為透過 [Docker daemon](https://docs.docker.com/engine/reference/commandline/dockerd/)執行進程的遠端容器_* _
        1. 指定背景程式位址 (例如透過 [TCP]、[IP]、[) ] 下的 [*Docker 主機 (選擇性)**]，然後按一下 [重新整理] 連結。
        1. 在連接到 daemon 之後，選取要附加的執行中容器，並按 **[確定]**。

4. 從 **可用** 的程式清單中選擇對應的容器進程，然後選取 [ **附加** ] 以開始在 Visual Studio 中進行 c # 容器進程的偵錯工具！

    ![Visual Studio 中 [附加至進程] 對話方塊的螢幕擷取畫面。連線類型設定為 [Docker (Linux 容器) ]，並已選取 [dotnet] 進程。](../debugger/media/docker-attach-complete.png "完成的 Linux Docker 附加功能表")

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a>附加至在 Windows Docker 容器上執行的進程

您可以使用 [ **附加至進程** ] 對話方塊，將 Visual Studio 偵錯工具附加到本機電腦上的 Windows Docker 容器中執行的進程。

> [!IMPORTANT]
> 若要在 .NET Core 進程中使用這項功能，您必須安裝 .NET Core 跨平臺開發工作負載，並具有原始程式碼的本機存取權。

**若要附加至 Windows Docker 容器中的執行中進程：**

1. 在 Visual Studio 中，選取 [ **Debug] > [附加至進程** ] (或 **CTRL + ALT + P**) 開啟 [ **附加至進程** ] 對話方塊。

   ![[附加至進程] Visual Studio 對話方塊的螢幕擷取畫面，其中顯示 Docker (Windows 容器) 的連線類型。](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. 將連線 **類型** 設定為 **Docker (Windows 容器)**。
3. 選取 [**尋找**]，以使用 [**選取 Docker 容器**] 對話方塊設定 **連接目標**。

    > [!IMPORTANT]
    > 目標進程的處理器架構必須與執行所在的 Docker Windows 容器相同。

   透過 SSH 將目標設定為遠端容器目前無法使用，而且只能使用 Docker daemon 來完成。

    **_若要將目標設定為透過 [Docker daemon](https://docs.docker.com/engine/reference/commandline/dockerd/)執行進程的遠端容器_* _
    1. 指定背景程式位址 (例如透過 [TCP]、[IP]、[) ] 下的 [*Docker 主機 (選擇性)**]，然後按一下 [重新整理] 連結。

    1. 在成功連接到背景程式之後，選取要附加的執行中容器，然後選擇 [確定]。

4. 從 **可用的進程** 清單中選擇對應的容器進程，然後選取 [ **附加** ] 開始對 c # 容器進程進行偵錯工具。

    ![Visual Studio 中 [附加至進程] 對話方塊的螢幕擷取畫面。連線類型設定為 [Docker (Windows 容器) ]，並已選取 dotnet.exe 進程。](../debugger/media/docker-attach-complete-windows.png "完成的 Windows Docker 附加功能表")

5. 從可用的進程清單中選擇對應的容器進程，然後選擇 [ **附加** ] 開始對 c # 容器進程進行偵錯工具。