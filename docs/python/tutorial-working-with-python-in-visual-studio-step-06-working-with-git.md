---
title: "在 Visual Studio 中使用 Python，步驟 6：使用 Git | Microsoft Docs"
description: "在 Visual Studio 內使用 Python 之核心教學課程的步驟 6，涵蓋 Visual Studio 與 Git 相關的功能。"
ms.custom: 
ms.date: 01/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: ef143862c56f07edc844874bbf71cd916ac9eabc
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="step-6-working-with-git"></a>步驟 6：使用 Git

**上一個步驟：[安裝套件以及管理 Python 環境](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)**

Visual Studio 提供與本機 Git 存放庫的直接整合，以及與位在 GitHub 和 Visual Studio Team Services 這類服務之存放庫的直接整合。 這項整合包含複製存放庫、認可變更，以及管理分支。

本文章描述如何建立現有專案的本機 Git 存放庫。 如需從遠端 Git 存放庫建立專案的逐步解說，請參閱[快速入門：在 Visual Studio 中複製 Python 程式碼的存放庫](quickstart-03-python-in-visual-studio-project-from-repository.md)。

1. 在 Visual Studio 中開啟專案之後 (例如[上一個步驟](tutorial-working-with-python-in-visual-studio-step-05-installing-packages.md)中的專案)，以滑鼠右鍵按一下方案，然後選取 [將方案新增至原始檔控制]。 Visual Studio 會建立包含您專案程式碼並顯示 Git 相關控制項的本機 Git 存放庫，也會出現在 Visual Studio 視窗底部。 這些控制項顯示擱置中認可、變更、存放庫名稱和分支。 將滑鼠指標停留在控制項上方，以查看其他資訊。

  ![將滑鼠指標停留在 Visual Studio 視窗的 Git 控制項上方時，會顯示其他資訊](media/working-with-git-01.png)

1. 透過選取存放庫標頭，也會顯示 [Team Explorer] 視窗與各種可用的 Git 選項。 如同選取 [推送] 標題時所示，[同步] 窗格會提供用於發行至遠端存放庫的選項。

  ![Visual Studio 中建立本機存放庫之後的 Team Explorer](media/working-with-git-02.png)

1. 選取 [變更] 檢閱未認可的變更，並在需要時進行認可。

  ![Visual Studio 中顯示未認可變更的 Team Explorer](media/working-with-git-03.png)

1. 選取 [分支] 以檢查分支，並執行合併和重訂基底作業：

  ![Visual Studio 中顯示分支的 Team Explorer](media/working-with-git-04.png)

1. 使用本機存放庫時，已認可的變更會直接進入存放庫。 如果您連線至遠端存放庫，請選取標題，再選擇 [同步] 以切換至 [同步處理] 區段，然後使用其中顯示的命令。

## <a name="going-deeper"></a>繼續探討

如需使用 Git 的更廣泛教學課程，請參閱[與 Visual Studio 2017 和 VSTS Git 共用程式碼](/vsts/git/share-your-code-in-git-vs-2017)

## <a name="tutorial-review"></a>教學課程檢閱

恭喜您在 Visual Studio 的 Python 上完成本教學課程。 在本教學課程中，您已了解如何：

- 建立專案，以及檢視專案內容。
- 使用程式碼編輯器，並執行專案。
- 使用互動式視窗來開發新的程式碼，並輕鬆地將該程式碼複製至編輯器。
- 在 Visual Studio 偵錯工具中執行已完成的程式。
- 安裝套件以及管理 Python 環境
- 使用 Git 存放庫中的程式碼

在這裡，瀏覽概念和做法指南，包含下列項目：

- [建立適用於 Python 的 C++ 延伸模組](working-with-c-cpp-python-in-visual-studio.md)
- [發行至 Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [程式碼剖析](profiling-python-code-in-visual-studio.md)
- [單元測試](unit-testing-python-in-visual-studio.md)
