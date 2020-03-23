---
title: Visual Studio 中的 Python 教學課程步驟 6，使用 Git
titleSuffix: ''
description: 在 Visual Studio 中 Python 核心逐步解說的步驟 6，涵蓋 Visual Studio 的 Git 相關功能。
ms.date: 01/28/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: cd8ebd706d9228d23eb5d5ce3b1429063bae55e5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "72289713"
---
# <a name="step-6-work-with-git"></a>步驟 6：使用 Git

**上一個步驟：[安裝套件以及管理 Python 環境](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

Visual Studio 在 GitHub 和 Azure Repos 之類的服務上，提供與本機 Git 存放庫和遠端儲存庫的直接整合。 這項整合包含複製存放庫、認可變更，以及管理分支。

本文提供為現有專案建立本機 Git 存放庫的基本概觀，以及讓您熟悉一些 Visual Studio 的 Git 相關功能。

1. 在 Visual Studio 中開啟專案之後 (例如[上一個步驟](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)中的專案)，以滑鼠右鍵按一下方案，然後選取 [將方案新增至原始檔控制]****。 Visual Studio 會建立包含您的專案程式碼的本機 Git 存放庫。

1. 當 Visual Studio 偵測到於 Git 存放庫管理的專案時，Git 相關的控制項會出現在 Visual Studio 視窗右下角。 這些控制項顯示擱置中認可、變更、存放庫名稱和分支。 將滑鼠指標停留在控制項上方，以查看其他資訊。

    ![將滑鼠指標停留在 Visual Studio 視窗的 Git 控制項上方時，會顯示其他資訊](media/working-with-git-01.png)

1. 當您建立新的存放庫或選取任何 Git 控制項時，Visual Studio 會開啟 [Team Explorer]**** 視窗。 （您可以隨時使用 **"查看** > **Team 總管"** 功能表命令打開視窗。該視窗有三個主窗格，在使用**Team 總管**標頭上的下拉式功能表之間切換。 當您選擇 **"推送"** 控制項（向上箭號圖示）時，也會顯示提供發佈操作的**Sync**窗格：

    ![Visual Studio 中建立本機存放庫之後的 Team Explorer](media/working-with-git-02.png)

1. 選取 [變更]**** (或具有鉛筆圖示的 Git 控制項) 檢閱未認可的變更，並在需要時進行認可。

    ![Visual Studio 中顯示未認可變更的 Team Explorer](media/working-with-git-03.png)

    按兩下 [變更]**** 清單中的檔案，以開啟該檔案的差異檢視：

    ![檔案的變更差異檢視](media/working-with-git-05.png)

1. 選取 [分支]**** (或具有分支名稱的 Git 控制項) 以檢查分支，並執行合併和重訂基底作業：

    ![Visual Studio 中顯示分支的 Team Explorer](media/working-with-git-04.png)

1. 使用存儲庫名稱選擇 Git 控制項（在上一個映射中**加入 CosineWave），Team** **Explorer**顯示了一個**Connect**介面，您可以快速切換到另一個存儲庫。

1. 使用本機存放庫時，已認可的變更會直接進入存放庫。 如果已連接到遠端存放庫，請選擇 **"Team 總管**"中的下拉標頭，選擇 **"同步**"以切換到 **"同步"** 部分，然後使用其中提供的 **"拉取**"和 **"提取**"命令。

## <a name="go-deeper"></a>深入了解

有關從遠端 Git 存儲庫創建專案的簡短演練，請參閱[快速入門：在 Visual Studio 中克隆 Python 代碼的存儲庫](quickstart-03-python-in-visual-studio-project-from-repository.md)。

如需包括處理合併衝突、檢閱具有提取要求的程式碼、重定基底，以及揀選分支之間的變更等更完整的教學課程，請參閱 [Git 與 Azure Repos 使用者入門](/azure/devops/repos/git/gitquickstart)。

## <a name="tutorial-review"></a>教學課程檢閱

恭喜您在 Visual Studio 的 Python 上完成本教學課程。 在本教學課程中，您已了解如何：

- 建立專案，以及檢視專案內容。
- 使用程式碼編輯器，並執行專案。
- 使用**互動式**視窗開發新代碼並輕鬆地將該代碼複製到編輯器中。
- 在 Visual Studio 偵錯工具中執行已完成的程式。
- 安裝套件以及管理 Python 環境。
- 使用 Git 存放庫中的程式碼。

在這裡，探索概念和作法指南，包含下列文章：

- [建立適用於 Python 的 C++ 延伸模組](working-with-c-cpp-python-in-visual-studio.md)
- [發佈到 Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [分析](profiling-python-code-in-visual-studio.md)
- [單元測試](unit-testing-python-in-visual-studio.md)
