---
title: Docker 容器記錄、環境變數及檔案系統存取
description: 說明如何使用工具視窗來改善在 Visual Studio 中的容器型應用程式的偵測和診斷功能，以瞭解裝載應用程式的容器內有哪些狀況。
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 10/16/2019
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: a398adf047ebfe2e76ed91da72513eb7646c36c3
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535558"
---
# <a name="how-to-view-and-diagnose-containers-and-images-in-visual-studio"></a>如何在 Visual Studio 中查看及診斷容器和映射

您可以使用 [**容器**] 視窗來查看裝載應用程式之容器內的狀況。 如果您使用命令提示字元來執行 Docker 命令，以查看並診斷容器的情況，此視窗可讓您更方便地監視容器，而不需要離開 Visual Studio IDE。

## <a name="prerequisites"></a>Prerequisites

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual Studio 2019 16.4 Preview 2](https://visualstudio.microsoft.com/downloads)或更新版本，或如果您使用舊版的 Visual Studio 2019，請安裝 [[容器] 視窗延伸](https://aka.ms/vscontainerspreview)模組。

## <a name="view-information-about-your-containers"></a>查看容器的相關資訊

[**容器**] 視窗會在您啟動容器化 .net 專案時自動開啟。 若要在 Visual Studio 中隨時查看您的容器，請使用**Ctrl** +**Q**來啟動 [Visual Studio 搜尋] 方塊，然後輸入 `Containers` 並選擇第一個專案。 您也可以從主功能表開啟 [**容器**] 視窗。 使用 [功能表路徑]**視圖** > **其他 Windows**  > **容器**。  

![[容器] 視窗中 [環境] 索引標籤的螢幕擷取畫面](media/view-and-diagnose-containers/container-window.png)

在左側，您會看到本機電腦上的容器清單。 與解決方案相關聯的容器會顯示在 [**方案容器**] 底下。 在右邊，您會看到一個窗格，其中包含**環境**、**埠**、**記錄**和檔案的索引卷**標。**

> [!TIP]
> 您可以輕鬆地自訂 [**容器**] 工具視窗停駐在 Visual Studio 中的位置。 請參閱[在 Visual Studio 中自訂視窗版面](/visualstudio/ide/customizing-window-layouts-in-visual-studio)配置。 根據預設，當偵錯工具正在執行時，[**容器**] 視窗會停駐于 [**監看**式] 視窗。

## <a name="view-environment-variables"></a>View 環境變數

[**環境**] 索引標籤會顯示容器中的環境變數。 針對您應用程式的容器，您可以透過許多方式來設定這些變數，例如，在 Dockerfile 中、在 env 檔案中，或在使用 Docker 命令啟動容器時使用-e 選項。

![[容器] 視窗中 [環境] 索引標籤的螢幕擷取畫面](media/view-and-diagnose-containers/containers-environment-vars.png)

> [!NOTE]
> 對環境變數所做的任何變更都不會即時反映出來。 此外，此索引標籤中的環境變數是容器上的系統內容變數，而且不會反映應用程式本機的使用者環境變數。

## <a name="view-port-mappings"></a>查看埠對應

在 [**埠**] 索引標籤上，您可以檢查您的容器是否有作用的埠對應。

![[容器] 視窗中 [埠] 索引標籤的螢幕擷取畫面](media/view-and-diagnose-containers/containers-ports.png)

已知的埠已連結，因此，如果埠上有可用的內容，您可以按一下連結以開啟瀏覽器。

## <a name="view-logs"></a>檢視記錄

[**記錄**] 索引標籤會顯示 `docker logs` 命令的結果。 根據預設，索引標籤會顯示容器上的 stdout 和 stderr 資料流程，但是您可以設定輸出。 如需詳細資訊，請參閱[Docker 記錄](https://docs.docker.com/config/containers/logging/)。  根據預設，[**記錄**] 索引標籤會串流處理記錄，但是您可以選擇**索引標籤**上的 [停止] 按鈕來停用。

![[容器] 視窗中 [記錄] 索引標籤的螢幕擷取畫面](media/view-and-diagnose-containers/containers-logs.png)

若要清除記錄檔，請使用 [**記錄**] 索引標籤上的 [**清除**] 按鈕。 若要取得所有記錄檔，請使用 [重新整理 **] 按鈕。**

> [!NOTE]
> 當您執行時，Visual Studio 會自動將 stdout 和 stderr 重新導向至 [**輸出**] 視窗，因此 windows 容器會使用**Ctrl** +**F5**從 Visual Studio 啟動，而不會顯示記錄此索引標籤;請改用 [**輸出**] 視窗。

## <a name="view-the-filesystem"></a>查看檔案系統

**在 [檔案**] 索引標籤上，您可以查看容器的檔案系統，包括包含您專案的應用程式資料夾。

![[容器] 視窗中 [檔案] 索引標籤的螢幕擷取畫面](media/view-and-diagnose-containers/container-filesystem.png)

若要在 Visual Studio 中開啟檔案，請流覽至該檔案，然後按兩下該檔案，或以滑鼠右鍵按一下並選擇 [**開啟**]。 Visual Studio 以唯讀模式開啟檔案。

![檔案開啟以供在 Visual Studio 中進行查看的螢幕擷取畫面](media/view-and-diagnose-containers/container-file-open.png)

使用 [檔案] 索引標籤，您可以在容器**的檔案系統**中，查看應用程式記錄檔，例如 IIS 記錄、設定檔和其他內容檔案。

## <a name="start-stop-and-remove-containers"></a>啟動、停止和移除容器

根據預設，[**容器**] 視窗會顯示 Docker 管理之電腦上的所有容器。 您可以使用工具列按鈕來啟動、停止或移除（刪除）您不再需要的容器。  在建立或移除容器時，會動態更新此清單。

## <a name="open-a-terminal-window-in-a-running-container"></a>在執行中的容器中開啟終端機視窗

您可以使用 [**容器**] 視窗中的 [**開啟終端機視窗]** 按鈕，在容器中開啟終端機視窗（命令提示字元或互動式 shell）。

![在 [容器] 視窗中開啟終端機視窗的螢幕擷取畫面](media/view-and-diagnose-containers/containers-open-terminal-window.png)

針對 Windows 容器，會開啟 Windows 命令提示字元。 針對 Linux 容器，它會使用 bash shell 開啟視窗。

![Bash 視窗的螢幕擷取畫面](media/view-and-diagnose-containers/container-bash-window.png)

一般來說，終端機視窗會以另一個視窗的形式在 Visual Studio 外部開啟。 如果您想要將命令列環境整合到 Visual Studio IDE 做為可停駐的工具視窗，您可以安裝[摧毀摧毀終端](https://marketplace.visualstudio.com/items?itemName=DanielGriffen.WhackWhackTerminal)機。

## <a name="attach-the-debugger-to-a-process"></a>將偵錯工具附加至進程

您可以使用 [容器] 視窗工具列上的 [**附加至進程**] 按鈕，將偵錯工具附加至正在容器中執行的進程。 當您使用此按鈕時，[**附加至進程**] 對話方塊隨即出現，並顯示在容器中執行的可用進程。  

![[附加至進程] 對話方塊的螢幕擷取畫面](media/view-and-diagnose-containers/containers-attach-to-process.jpg)

您可以附加至容器中的受控進程。 若要尋找另一個容器中的進程，請使用 [**尋找**] 按鈕，然後選取 [**選取 Docker 容器**] 對話方塊上的另一個容器。

## <a name="viewing-images"></a>查看影像

您也可以使用 [**容器**] 視窗中的 [**映射**] 索引標籤，來查看本機電腦上的影像。 從外部存放庫提取的影像會在 treeview 中群組在一起。 選取影像以檢查映射的詳細資料。

若要移除影像，請以滑鼠右鍵按一下 treeview 中的影像，然後選擇 [**移除**]，或選取影像，然後使用工具列上的 [**移除**] 按鈕。

## <a name="next-steps"></a>後續步驟

閱讀[容器工具總覽](overview.md)，以深入瞭解 Visual Studio 中提供的容器工具。

## <a name="see-also"></a>請參閱

[Visual Studio 中的容器開發](/visualstudio/containers)

[Visual Studio 的延伸模組 Marketplace](https://marketplace.visualstudio.com/)
