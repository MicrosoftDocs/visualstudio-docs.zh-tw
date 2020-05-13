---
title: Docker 容器日誌、環境變數和檔案系統訪問
description: 介紹如何使用工具視窗查看託管應用的容器內發生的情況，從而介紹如何在 Visual Studio 中改進調試和診斷基於容器的應用的能力。
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 01/20/2020
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: b4670c003c06f8d16979589a4dce5abf33d5e27d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027299"
---
# <a name="how-to-view-and-diagnose-containers-and-images-in-visual-studio"></a>如何在視覺化工作室中查看和診斷容器和圖像

您可以使用 **"容器"** 視窗查看承載應用的容器內發生的情況。 如果您習慣于使用命令提示符運行 Docker 命令來查看和診斷容器發生的情況，則此視窗提供了一種更方便的方式來監視容器，而無需離開 Visual Studio IDE。

## <a name="prerequisites"></a>必要條件

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual Studio 2019 版本 16.4 預覽 2](https://visualstudio.microsoft.com/downloads)或更高版本，或者如果您使用的是早期版本的 Visual Studio 2019，請安裝[容器視窗擴展](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-containers-tools-extensions)名 。

## <a name="view-information-about-your-containers"></a>查看有關容器的資訊

啟動容器化的 .NET 專案時，"**容器**"視窗將自動打開。 要隨時在 Visual Studio 中查看容器，請使用**Ctrl**+**Q**啟動"視覺工作室搜索"`Containers`框，然後鍵入並選擇第一個專案。 您還可以從主功能表打開**容器**視窗。 使用功能表路徑**查看** > **其他 Windows** > **容器**。  

![容器視窗中環境選項卡的螢幕截圖](media/view-and-diagnose-containers/container-window.png)

在左側，您可以看到本地電腦上的容器清單。 與解決方案關聯的容器顯示在**解決方案容器**下。 在右側，您將看到一個窗格，其中包含**環境**、**埠**、**日誌**和**檔**選項卡。

> [!TIP]
> 您可以輕鬆地自訂**容器**工具視窗停靠在 Visual Studio 中的位置。 請參閱[在視覺化工作室中自訂視窗佈局](../ide/customizing-window-layouts-in-visual-studio.md)。 預設情況下，當調試器運行時，**容器**視窗與 **"監視"** 視窗停靠。

## <a name="view-environment-variables"></a>查看環境變數

"**環境**"選項卡顯示容器中的環境變數。 對於應用的容器，您可以通過多種方式設置這些變數，例如，在 Dockerfile 中、在 .env 檔中，或者在使用 Docker 命令啟動容器時使用 -e 選項。

![容器視窗中環境選項卡的螢幕截圖](media/view-and-diagnose-containers/containers-environment-vars.png)

> [!NOTE]
> 對環境變數的任何更改不會即時反映。 此外，此選項卡中的環境變數是容器上的系統內容變數，並不反映應用本地的使用者環境變數。

## <a name="view-port-mappings"></a>查看埠映射

在 **"埠"** 選項卡上，可以檢查對容器有效的埠映射。

![容器視窗中埠選項卡的螢幕截圖](media/view-and-diagnose-containers/containers-ports.png)

已知埠是連結的，因此，如果埠上有可用的內容，可以按一下連結打開瀏覽器。

## <a name="view-logs"></a>檢視記錄

"**日誌"** 選項卡顯示命令的結果`docker logs`。 預設情況下，該選項卡在容器上顯示抖出和穩穩的流，但您可以配置輸出。 有關詳細資訊，請參閱[Docker 日誌記錄](https://docs.docker.com/config/containers/logging/)。  預設情況下，"**日誌"** 選項卡會資料流日誌，但您可以通過選擇選項卡上的 **"停止"** 按鈕來禁用日誌。

![容器視窗中日誌選項卡的螢幕截圖](media/view-and-diagnose-containers/containers-logs.png)

要清除日誌，請使用 **"日誌"** 選項卡上的 **"清除**"按鈕。 要獲取所有日誌，請使用 **"刷新"** 按鈕。

> [!NOTE]
> 當您在沒有使用 Windows 容器進行調試的情況下運行時，Visual Studio 會自動將斯特點和穩重重定向到 **"輸出"** 視窗，因此使用 Ctrl F5 從 Visual Studio 啟動的 Windows 容器將不會在此選項卡中顯示日誌;因此，使用**Ctrl**+**F5**從 Visual Studio 啟動的 Windows 容器將不會在此選項卡中顯示日誌。而是使用 **"輸出"** 視窗。

## <a name="view-the-filesystem"></a>查看檔案系統

在"**檔"** 選項卡上，您可以查看容器的檔案系統，包括包含專案的應用資料夾。

![容器視窗中的檔選項卡的螢幕截圖](media/view-and-diagnose-containers/container-filesystem.png)

要在 Visual Studio 中打開檔，請流覽到該檔並按兩下該檔，或按右鍵並選擇 **"打開**"。 視覺化工作室以唯讀模式打開檔。

![打開供在視覺工作室中查看的檔螢幕截圖](media/view-and-diagnose-containers/container-file-open.png)

使用 **"檔**"選項卡，您可以在容器的檔案系統中查看應用程式日誌，如 IIS 日誌、設定檔和其他內容檔。

## <a name="start-stop-and-remove-containers"></a>啟動、停止和刪除容器

預設情況下，"**容器"** 視窗顯示 Docker 管理的電腦上的所有容器。 您可以使用工具列按鈕啟動、停止或刪除（刪除）不再需要的容器。  創建或刪除容器時，將動態更新此清單。

## <a name="open-a-terminal-window-in-a-running-container"></a>在正在運行的容器中打開終端視窗

您可以使用**容器**視窗中的 **"打開終端視窗**"按鈕在容器中打開終端視窗（命令提示符或互動式外殼）。

![容器視窗中打開終端視窗的螢幕截圖](media/view-and-diagnose-containers/containers-open-terminal-window.png)

對於 Windows 容器，將打開 Windows 命令提示符。 對於 Linux 容器，它使用 bash shell 打開一個視窗。

![bash 視窗的螢幕截圖](media/view-and-diagnose-containers/container-bash-window.png)

通常，終端視窗在 Visual Studio 外部作為單獨的視窗打開。 如果希望將命令列環境作為可停靠的工具視窗集成到 Visual Studio IDE 中，則可以安裝[Whack Whack 終端](https://marketplace.visualstudio.com/items?itemName=DanielGriffen.WhackWhackTerminal)。

## <a name="attach-the-debugger-to-a-process"></a>將調試器附加到進程

可以使用容器視窗工具列上的"**附加到進程**"按鈕將調試器附加到容器中運行的進程。 使用此按鈕時，將顯示 **"附加到進程"** 對話方塊，並顯示容器中正在運行的可用進程。  

![附加到進程的螢幕截圖對話方塊](media/view-and-diagnose-containers/containers-attach-to-process.jpg)

您可以附加到容器中的託管進程。 要在另一個容器中查找進程，請使用 **"查找**"按鈕，並在 **"選擇 Docker 容器"** 對話方塊中選擇另一個容器。

## <a name="viewing-images"></a>查看圖像

您還可以使用 **"容器"** 視窗中的 **"圖像"** 選項卡查看本地電腦上的圖像。 從外部存儲庫提取的圖像在樹狀檢視中分組在一起。 選擇一個圖像來檢查圖像的詳細資訊。

要刪除圖像，請按右鍵樹狀檢視中的圖像並選擇 **"刪除**"或"刪除"圖像，然後使用工具列上的 **"刪除**"按鈕。

## <a name="next-steps"></a>後續步驟

通過閱讀容器工具概述，瞭解有關視覺化工作室中可用的[容器工具的詳細資訊](overview.md)。

## <a name="see-also"></a>另請參閱

[視覺化工作室中的容器開發](/visualstudio/containers)

[視覺工作室擴展市場](https://marketplace.visualstudio.com/)
