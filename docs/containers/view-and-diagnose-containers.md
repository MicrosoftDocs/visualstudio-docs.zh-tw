---
title: 容器記錄、環境變數、& 檔案系統存取
description: 說明如何使用工具視窗來改善在 Visual Studio 中的容器型應用程式的偵測和診斷功能，以瞭解裝載應用程式的容器內有哪些狀況。
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 05/06/2019
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: 3fb9a52f990a2e492c63a6e71a7cc2063110c816
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70312270"
---
# <a name="how-to-view-and-diagnose-containers-in-visual-studio"></a>如何在 Visual Studio 中查看和診斷容器

您可以使用 [**容器**] 視窗來查看裝載應用程式之容器內的狀況。 如果您使用命令提示字元來執行 Docker 命令，以查看並診斷容器的情況，此視窗可讓您更方便地監視容器，而不需要離開 Visual Studio IDE。

> [!NOTE]
> [容器] 視窗目前以預覽擴充功能的形式提供，您可以[下載](https://aka.ms/vscontainerspreview)以 Visual Studio 2019。

## <a name="prerequisites"></a>必要條件

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- 安裝[Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
- 安裝[容器視窗延伸](https://aka.ms/vscontainerspreview)模組

## <a name="view-information-about-your-containers"></a>查看容器的相關資訊

[**容器**] 視窗會在您啟動容器化 .net 專案時自動開啟。 若要在 Visual Studio 中隨時查看您的容器，請使用**Ctrl** + **Q**來啟動 [Visual Studio 搜尋] 方塊`Containers` ，然後輸入並選擇第一個專案。 您也可以從主功能表開啟 [**容器**] 視窗。 使用功能表路徑**視圖** > [**其他 Windows**  > **容器**]。  

![[容器] 視窗中 [環境] 索引標籤的螢幕擷取畫面](media/view-and-diagnose-containers/container-window.png)

在左側，您會看到本機電腦上的容器清單。 與解決方案相關聯的容器會顯示在 [**方案容器**] 底下。 在右邊，您會看到一個窗格，其中包含**環境**、**埠**、**記錄**和檔案的索引卷**標。**

> [!TIP]
> 您可以輕鬆地自訂 [**容器**] 工具視窗停駐在 Visual Studio 中的位置。 請參閱[在 Visual Studio 中自訂視窗版面](/visualstudio/ide/customizing-window-layouts-in-visual-studio)配置。 根據預設，當偵錯工具正在執行時，[**容器**] 視窗會停駐于 [**監看**式] 視窗。

## <a name="view-environment-variables"></a>View 環境變數

[**環境**] 索引標籤會顯示容器中的環境變數。 針對您應用程式的容器，您可以透過許多方式來設定這些變數，例如，在 Dockerfile 中、在 env 檔案中，或在使用 Docker 命令啟動容器時使用-e 選項。

![[容器] 視窗中 [環境] 索引標籤的螢幕擷取畫面](media/view-and-diagnose-containers/container-environment-vars.png)

> [!NOTE]
> 對環境變數所做的任何變更都不會即時反映出來。 此外，此索引標籤中的環境變數是容器上的系統內容變數，而且不會反映應用程式本機的使用者環境變數。

## <a name="view-port-mappings"></a>查看埠對應

在 [**埠**] 索引標籤上，您可以檢查您的容器是否有作用的埠對應。

![[容器] 視窗中 [埠] 索引標籤的螢幕擷取畫面](media/view-and-diagnose-containers/container-ports.png)

已知的埠已連結，因此，如果埠上有可用的內容，您可以按一下連結以開啟瀏覽器。

## <a name="view-logs"></a>檢視記錄

[**記錄**] 索引標籤會顯示`docker logs`命令的結果。 根據預設，索引標籤會顯示容器上的 stdout 和 stderr 資料流程，但是您可以設定輸出。 如需詳細資訊，請參閱[Docker 記錄](https://docs.docker.com/config/containers/logging/)。  根據預設，[**記錄**] 索引標籤會串流處理記錄，但是您可以選擇**索引標籤**上的 [停止] 按鈕來停用。

![[容器] 視窗中 [記錄] 索引標籤的螢幕擷取畫面](media/view-and-diagnose-containers/containers-logs.jpg)

若要清除記錄檔，請使用 [**記錄**] 索引標籤上的 [**清除**] 按鈕。若要取得所有記錄檔，請使用 [重新整理 **] 按鈕。**

> [!NOTE]
> Visual Studio 會自動將 stdout 和 stderr 重新導向至 [**輸出**] 視窗，因此從 Visual Studio （也就是 [**方案容器**] 區段中的容器）啟動的容器將不會在此索引標籤中顯示記錄;請改用 [**輸出**] 視窗。

## <a name="view-the-filesystem"></a>查看檔案系統

**在 [檔案**] 索引標籤上，您可以查看容器的檔案系統，包括包含您專案的應用程式資料夾。

![[容器] 視窗中 [檔案] 索引標籤的螢幕擷取畫面](media/view-and-diagnose-containers/container-filesystem.png)

若要在 Visual Studio 中開啟檔案，請流覽至該檔案，然後按兩下該檔案，或以滑鼠右鍵按一下並選擇 [**開啟**]。 Visual Studio 以唯讀模式開啟檔案。

![檔案開啟以供在 Visual Studio 中進行查看的螢幕擷取畫面](media/view-and-diagnose-containers/container-file-open.png)

使用 [檔案] 索引標籤，您可以在容器**的檔案系統**中，查看應用程式記錄檔，例如 IIS 記錄、設定檔和其他內容檔案。

## <a name="start-stop-and-remove-containers"></a>啟動、停止和移除容器

根據預設，[**容器**] 視窗會顯示 Docker 管理之電腦上的所有容器。 您可以使用工具列按鈕來啟動、停止或移除（刪除）您不再需要的容器。  在建立或移除容器時，會動態更新此清單。

## <a name="next-steps"></a>後續步驟

閱讀[容器工具總覽](overview.md)，以深入瞭解 Visual Studio 中提供的容器工具。

## <a name="see-also"></a>另請參閱

[Visual Studio 中的容器開發](/visualstudio/containers)

[Visual Studio 的延伸模組 Marketplace](https://marketplace.visualstudio.com/)
