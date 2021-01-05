---
title: 查看和診斷 Docker 容器和映射
description: 說明如何使用工具視窗，以查看裝載您應用程式的容器內發生的情況，以改善您在 Visual Studio 中偵測及診斷容器型應用程式的能力。
author: ghogen
ms.author: ghogen
ms.topic: how-to
ms.date: 01/20/2020
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: fd876e86cefcd0ce50aab02de8e7f4cf37d3ab51
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729219"
---
# <a name="how-to-view-and-diagnose-containers-and-images-in-visual-studio"></a>如何在 Visual Studio 中查看及診斷容器和映射

您可以使用 [ **容器** ] 視窗，在裝載應用程式的容器內查看發生的狀況。 如果您使用命令提示字元來執行 Docker 命令以查看和診斷容器的內容，此視窗提供更方便的方式來監視您的容器，而不需要離開 Visual Studio IDE。

## <a name="prerequisites"></a>必要條件

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual Studio 2019 16.4 版 Preview 2](https://visualstudio.microsoft.com/downloads) 或更新版本，或者如果您使用舊版的 Visual Studio 2019，請安裝 [ [容器] 視窗擴充](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-containers-tools-extensions)功能。

## <a name="view-information-about-your-containers"></a>查看容器的相關資訊

當您啟動容器化 .NET 專案時，[ **容器** ] 視窗會自動開啟。 若要隨時在 Visual Studio 中查看您的容器，請使用 **Ctrl** + **Q** 啟動 Visual Studio 搜尋方塊，然後輸入 `Containers` 並選擇第一個專案。 您也可以從主功能表開啟 [ **容器** ] 視窗。 使用功能表路徑 **視圖**  >  **其他 Windows**  >  **容器**。  

![[容器 Visual Studio] 視窗的螢幕擷取畫面，其中已選取左窗格中的容器，並在右窗格中選取 [環境] 索引標籤。](media/view-and-diagnose-containers/container-window.png)

在左側，您會看到本機電腦上的容器清單。 與解決方案相關聯的容器會顯示在 [ **方案容器**] 下。 在右側，您會看到一個包含 **環境**、**埠**、**記錄** 檔和檔案索引標籤的 **窗格。**

> [!TIP]
> 您可以輕鬆自訂 **容器** 工具視窗在 Visual Studio 中的固定位置。 請參閱 [Visual Studio 中的自訂視窗版面](../ide/customizing-window-layouts-in-visual-studio.md)配置。 依預設，當偵錯工具正在執行時，[ **容器** ] 視窗會停駐在 [ **監看** 式] 視窗中。

## <a name="view-environment-variables"></a>View 環境變數

[ **環境** ] 索引標籤會顯示容器中的環境變數。 針對您的應用程式容器，您可以使用許多方式來設定這些變數，例如，在 Dockerfile、env 檔案中，或使用 Docker 命令啟動容器時，使用-e 選項。

![Visual Studio 中 [容器] 視窗的螢幕擷取畫面，其中顯示容器 WebApplication11 的環境變數。](media/view-and-diagnose-containers/containers-environment-vars.png)

> [!NOTE]
> 對環境變數所做的任何變更都不會即時反映出來。 此外，此索引標籤中的環境變數是容器上的系統內容變數，且不會反映應用程式本機的使用者環境變數。

## <a name="view-port-mappings"></a>查看埠對應

在 [ **埠** ] 索引標籤上，您可以檢查對容器有效的埠對應。

![[容器] 視窗中 [埠] 索引標籤的螢幕擷取畫面](media/view-and-diagnose-containers/containers-ports.png)

已知的埠會連結，因此，如果埠上有可用的內容，您可以按一下連結來開啟瀏覽器。

## <a name="view-logs"></a>檢視記錄

[ **記錄** 檔] 索引標籤會顯示命令的結果 `docker logs` 。 根據預設，索引標籤會在容器上顯示 stdout 和 stderr 資料流程，但您可以設定輸出。 如需詳細資訊，請參閱 [Docker 記錄](https://docs.docker.com/config/containers/logging/)。  依預設，[ **記錄** 檔] 索引標籤會串流記錄，但您可以選擇 **索引標籤** 上的 [停止] 按鈕來停用該記錄。

![[容器] 視窗中 [記錄] 索引標籤的螢幕擷取畫面](media/view-and-diagnose-containers/containers-logs.png)

若要清除記錄檔，請使用 [**記錄**] 索引標籤上的 [**清除**] 按鈕。 若要取得所有記錄檔，請使用 [重新整理 **] 按鈕。**

> [!NOTE]
> 當您執行時，Visual Studio 會自動將 stdout 和 stderr 重新導向至 [**輸出**] 視窗，因此使用 **Ctrl** F5 從 Visual Studio 啟動的 Windows 容器 + 將不會顯示此索引標籤中的記錄，而是改用 [**輸出** 視窗]。

## <a name="view-the-filesystem"></a>查看檔案系統

**在 [檔案] 索引** 標籤上，您可以查看容器的檔案系統，包括包含您專案的應用程式資料夾。

![[容器] 視窗中 [檔案] 索引標籤的螢幕擷取畫面](media/view-and-diagnose-containers/container-filesystem.png)

若要在 Visual Studio 中開啟檔案，請流覽至檔案並按兩下，或按一下滑鼠右鍵並選擇 [ **開啟**]。 Visual Studio 會以唯讀模式開啟檔案。

![開啟以供在 Visual Studio 中觀看之檔案的螢幕擷取畫面](media/view-and-diagnose-containers/container-file-open.png)

您可以 **使用 [檔案** ] 索引標籤，來查看應用程式記錄檔，例如 IIS 記錄檔、設定檔案，以及容器檔案系統中的其他內容檔案。

## <a name="start-stop-and-remove-containers"></a>啟動、停止和移除容器

依預設，[ **容器** ] 視窗會顯示 Docker 管理之電腦上的所有容器。 您可以使用工具列按鈕來啟動、停止或移除您不再想要的容器 (刪除) 。  這份清單會在建立或移除容器時動態更新。

## <a name="open-a-terminal-window-in-a-running-container"></a>在正在執行的容器中開啟終端機視窗

您可以使用 [**容器**] 視窗中的 [**開啟終端機視窗]** 按鈕，在容器中開啟終端機視窗 (命令提示字元或互動式 shell) 。

![在 [容器] 視窗中開啟終端機視窗的螢幕擷取畫面](media/view-and-diagnose-containers/containers-open-terminal-window.png)

若為 Windows 容器，則會開啟 Windows 命令提示字元。 針對 Linux 容器，它會使用 bash shell 來開啟視窗。

![Bash 視窗的螢幕擷取畫面](media/view-and-diagnose-containers/container-bash-window.png)

一般情況下，終端機視窗會在 Visual Studio 之外以個別的視窗開啟。 如果您想要將命令列環境整合到 Visual Studio IDE 作為可停駐的工具視窗，您可以安裝 [摧毀摧毀終端](https://marketplace.visualstudio.com/items?itemName=DanielGriffen.WhackWhackTerminal)機。

## <a name="attach-the-debugger-to-a-process"></a>將偵錯工具附加至進程

您可以使用 [容器] 視窗工具列上的 [ **附加至進程** ] 按鈕，將偵錯工具附加至正在容器中執行的進程。 當您使用此按鈕時，[ **附加至進程** ] 對話方塊隨即出現，並顯示正在容器中執行的可用進程。  

![[附加至進程] 對話方塊的螢幕擷取畫面](media/view-and-diagnose-containers/containers-attach-to-process.jpg)

您可以附加至容器中的 managed 進程。 若要尋找另一個容器中的處理常式，請使用 [ **尋找** ] 按鈕，然後選取 [ **選取 Docker 容器** ] 對話方塊上的另一個容器。

## <a name="viewing-images"></a>查看影像

您也可以使用 [**容器**] 視窗中的 [**映射**] 索引標籤，來查看本機電腦上的影像。 從外部存放庫提取的影像會在 treeview 中群組在一起。 選取映射以檢查影像的詳細資料。

若要移除影像，請以滑鼠右鍵按一下 treeview 中的影像，然後選擇 [ **移除**]，或選取影像，然後使用工具列上的 [ **移除** ] 按鈕。

## <a name="next-steps"></a>後續步驟

閱讀 [容器工具總覽](overview.md)，以深入瞭解 Visual Studio 中提供的容器工具。

## <a name="see-also"></a>請參閱

[Visual Studio 中的容器開發](./index.yml)

[Visual Studio 的延伸模組 Marketplace](https://marketplace.visualstudio.com/)