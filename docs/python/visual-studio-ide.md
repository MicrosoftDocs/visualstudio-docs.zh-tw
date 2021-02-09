---
title: 適用於 Python 開發人員的 Visual Studio 概觀
titleSuffix: ''
ms.date: 03/13/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
dev_langs:
- Python
ms.workload:
- python
- data-science
ms.openlocfilehash: d90ee69b8ee7f264a48d6ae01f77ea65e5d1c1b9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908788"
---
# <a name="welcome-to-the-visual-studio-ide--python"></a>歡迎使用 Visual Studio IDE | Python

Visual Studio 整合式開發環境是支援 Python (和其他語言) 且創作功能豐富的啟動控制板，可供您編輯、偵錯及測試程式碼，然後發行應用程式。 整合式開發環境 (IDE) 是功能豐富的程式，可用於軟體開發的許多方面。 除了大部分 IDE 提供的標準編輯器和偵錯工具之外，Visual Studio 還有程式碼完成工具、互動式 REPL 環境及其他功能，讓軟體開發程序變得更為容易。

[![使用 Python 專案 Visual Studio](media/tour-ide-overview.png)](media/tour-ide-overview.png#lightbox)

此圖顯示 Visual Studio 有一個開啟的 Python 專案，以及數個您可能會用到的重要工具視窗：

- [**方案總管**](../ide/solutions-and-projects-in-visual-studio.md) (右上方) 可讓您查看、流覽和管理程式碼檔案。 **方案總管** 可以將檔案分組到 [方案和專案](../get-started/tutorial-projects-solutions.md)中，以協助組織程式碼。
  - 方案總管 旁的是 [Python 環境](managing-python-environments-in-visual-studio.md)，您可以在此環境中管理安裝在電腦上的其他 Python 解譯器。

  ::: moniker range=">=vs-2019"
  - 您也可以開啟並執行資料夾中的 Python 程式碼，不需建立 Visual Studio 專案和方案檔案。 如需詳細資訊，請參閱 [快速入門：在資料夾中開啟及執行 Python 程式碼](quickstart-05-python-visual-studio-open-folder.md)。
  ::: moniker-end

- 「編輯器視窗」(中間) 會顯示檔案內容，您大部分的時間可能都是花在這裡。 您可在這裡[編輯 Python 控制碼](editing-python-code-in-visual-studio.md)、瀏覽程式碼架構，以及在偵錯工作階段期間設定中斷點。 使用 Python 時，您也可按 Ctrl+Enter 在 [[互動式 REPL] 視窗](python-interactive-repl-in-visual-studio.md)中執行該程式碼。

- [[輸出] 視窗](../ide/reference/output-window.md) (中下) 是 Visual Studio 傳送通知的位置，例如偵錯和錯誤訊息、警告、發佈狀態訊息等。 每個訊息來源都有自己的索引標籤。
  - [[Python 互動式 REPL] 視窗](python-interactive-repl-in-visual-studio.md) 與輸出視窗位於同一個區域。

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts&preserve-view=true) (右下) 可讓您追蹤工作項目，並使用版本控制技術 (例如 [Git](https://git-scm.com/) 和 [Team Foundation 版本控制 (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts&preserve-view=true)) 與其他人共用程式碼。

## <a name="editions"></a>版本

Visual Studio 適用於 Windows 及 Mac；但 Python 僅支援適用於 Windows 的 Visual Studio。

Windows 上有三個版本的 Visual Studio：「社區」、「專業」和「企業」。 若要了解每個版本支援哪些功能，請參閱[比較 Visual Studio IDE](https://visualstudio.microsoft.com/vs/compare/)。

## <a name="popular-productivity-features"></a>熱門的生產力功能

Visual Studio 的某些熱門功能可在您開發軟體時協助您提高生產力，這些功能包括：

- [智慧](editing-python-code-in-visual-studio.md#intellisense)

   IntelliSense 為一組功能的字詞，會直接在編輯器中顯示有關您程式碼的資訊，而在某些情況下會為您撰寫一些程式碼。 就像內嵌在編輯器中的基本文件，讓您不必在其他位置查閱類型資訊。 IntelliSense 的功能會依語言而有所不同，[編輯 Python 程式碼](editing-python-code-in-visual-studio.md#intellisense)一文中有 Python 的詳細說明。 下圖顯示 IntelliSense 如何顯示類型的成員清單：

   ![Visual Studio IntelliSense 的成員完成](media/code-editing-completions-simple.png)

- [重構](refactoring-python-code.md)

   您可以右鍵按一下一段程式碼並選取 [快速控制項目及重構]，Visual Studio 會提供您智慧型重新命名變數、將一或多行程式碼擷取至新方法，還有變更方法參數順序等作業。

   ![在 Visual Studio 中重構](media/tour-ide-refactor-extract-method.png)

- [進行 Lint 檢查](refactoring-python-code.md)

   Linting 會檢查 Python 程式碼中的錯誤與常見問題，藉由良好的 Python 編碼模式讓您信心大增。

   ![操作功能表上 Python 專案的 PyLint 命令](media/code-pylint-command.png)

- 搜尋方塊

   Visual Studio 使用這麼多的功能表、選項和屬性，有時似乎讓人有壓迫感。 搜尋方塊是一個可讓您在 Visual Studio 中快速找到所需項目的絕佳方式。 當您開始鍵入要尋找的項目名稱時，Visual Studio 會列出結果，將您引導至您確實想要去的地方。 如果您需要在 Visual Studio 中新增功能，例如新增對其他程式設計語言的支援，搜尋方塊提供的結果可開啟 Visual Studio 安裝程式，安裝工作負載或個別元件。

   ![Visual Studio 中的搜尋方塊](media/tour-ide-quick-launch.png)

- 波浪線和[快速動作](../ide/quick-actions.md)

   波浪線是波浪底線，可在您鍵入程式碼時，針對錯誤或潛在問題提出警示。 這些視覺提示可讓您立即修正問題，不必等到建置期間或執行程式時發現錯誤。 如果您將滑鼠停留在波浪線，您會看到有關此錯誤的其他資訊。 左邊界也可能會出現燈泡與修正錯誤的動作，稱為「快速動作」。

   ![Visual Studio 的波浪線](media/tour-ide-squiggles.png)

- [移至及查看定義](../ide/go-to-and-peek-definition.md)

   [移至定義] 功能可以直接帶您到定義函式或類型的位置。 [查看定義] 命令會在視窗中顯示定義，且無須開啟另外的檔案。 [尋找所有參考] 命令也可提供您探索同時已定義和使用之任何指定識別碼的實用方法。

   ![程式碼巡覽命令](media/tour-ide-navigation-commands.png)

## <a name="powerful-features-for-python"></a>適用於 Python 的強大功能

::: moniker range=">=vs-2019"
- [在不使用專案的情況下執行程式碼](quickstart-05-python-visual-studio-open-folder.md)

    從 Visual Studio 2019 開始，您可以開啟包含 Python 程式碼的資料夾，享受像 IntelliSense 這樣的功能，而且不需要為程式碼建立 Visual Studio 專案就能偵錯。
::: moniker-end

- [使用 Visual Studio 共同作業](/visualstudio/liveshare/)

    Visual Studio Live Share 可讓您即時與其他人以共同作業方式編輯和偵錯，不論您使用的程式設計語言或建置的應用程式類型為何。

- [Python 互動式 REPL](python-interactive-repl-in-visual-studio.md)

    Visual Studio 為您的每個 Python 環境提供互動式「讀取、求值、輸出」迴圈 (REPL) 視窗，它是以透過命令列上的 *python.exe* 取得的 REPL 為基礎加以改進。 在 [互動] 視窗中，您可輸入任意 Python 程式碼，然後查看即時結果。

    ![Python 互動式視窗](media/interactive-window.png)

- [偵錯](debugging-python-in-visual-studio.md)

    Visual Studio 為 Python 提供完整的偵錯工具體驗，包括附加至執行中進程、在 **監看** 式和即時 **運算視窗中** 評估運算式、檢查區域變數、中斷點、逐步執行/跳過/跳過語句、 **設定下一個語句** 等。 您也可針對在 Linux 電腦上執行的遠端 Python 程式碼進行偵錯。

    ![在 Visual Studio 中針對 Python 進行偵錯](media/remote-debugging-breakpoint-hit.png)

- [與 C++ 互動](working-with-c-cpp-python-in-visual-studio.md)

    許多為 Python 而建立的程式庫都是以 C++ 撰寫，以達最佳效能。 Visual Studio 提供用以開發 C++ 延伸模組的豐富功能，包含[混合模式偵錯](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)。

    ![同時針對 Python 和 C++ 進行混合模式偵錯](media/mixed-mode-debugging.png)

- [程式碼剖析](profiling-python-code-in-visual-studio.md)

    當您使用 CPython 型解譯器時，可以在 Visual Studio 中評估 Python 程式碼的效能。

    ![分析效能報告](media/profiling-results.png)

- [單元測試](unit-testing-python-in-visual-studio.md)

    Visual Studio 提供用以探索、執行和偵錯單元測試的整合支援，這些都包含在 IDE 中。

    ![顯示失敗測試狀態的單元測試](media/unit-test-A-fail.png)

## <a name="next-steps"></a>下一步

透過遵循以下其中一個快速入門或教學課程，在 Visual Studio 中進一步探索 Python：

> [!div class="nextstepaction"]
> [快速入門：使用 Flask 建立 web 應用程式](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)

> [!div class="nextstepaction"]
> [在 Visual Studio 中使用 Python](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

> [!div class="nextstepaction"]
> [開始使用 Visual Studio 中的 Django Web 架構](learn-django-in-visual-studio-step-01-project-and-solution.md)

> [!div class="nextstepaction"]
> [開始使用 Visual Studio 中的 Flask Web 架構](learn-flask-visual-studio-step-01-project-solution.md)

## <a name="see-also"></a>另請參閱

- 探索[更多 Visual Studio 功能](../ide/advanced-feature-overview.md)
- 瀏覽 [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
- 閱讀 [Visual Studio 部落格](https://devblogs.microsoft.com/visualstudio/)
