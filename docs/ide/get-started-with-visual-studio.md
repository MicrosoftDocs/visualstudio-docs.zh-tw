---
redirect_url: /visualstudio/ide/visual-studio-ide
ms.openlocfilehash: 5f1fa39d6e6cde1664a8aaa34aed7cba726b1d56
ms.sourcegitcommit: 64c7682ec3a2cbea684e716803398d4278b591d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2017
---
# <a name="get-started-with-visual-studio"></a>Visual Studio 使用者入門
Visual Studio 是用於開發應用程式的功能強大工具。 如果您尚未這麼做，請繼續進行，並下載和安裝 [Visual Studio](https://www.visualstudio.com/vs/)。 如需下載 Visual Studio 並以想要方式進行設定的詳細資訊，請觀看 [Getting Started with Visual Studio - Setting up your IDE](https://www.youtube.com/watch?v=xLCedknQkN0&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=1) (Visual Studio 使用者入門 - 設定 IDE) 影片。

## <a name="visual-studio-tour"></a>Visual Studio 導覽
Visual Studio 有一組工具視窗、功能表和工具列，統稱為整合式開發環境或 IDE。 Visual Studio IDE 可協助您完成開發工作。 以下是您可能最常使用的 IDE 項目的快速概觀。

### <a name="code-editor"></a>程式碼編輯器
Visual Studio 中的其中一個最大量使用的工具視窗，這是您撰寫、檢視和巡覽程式碼的位置。

![程式碼編輯器](../ide/media/VSIDE_CodeWindow.png)

輸入程式碼時，程式碼編輯器提供陳述式完成、語法顏色標示、地圖模式等這類功能，協助您更快速且輕鬆地撰寫和尋找程式碼。 如需詳細資訊，請觀看 [Getting Started with Visual Studio - Editing and navigating your code](https://www.youtube.com/watch?v=4glwwioCVjA&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=5) (Visual Studio 使用者入門 - 編輯和巡覽程式碼) 影片。

有些方案類型可能包含稱為「表單」的視窗，例如 Windows Presentation Foundation (WPF) 表單、Windows 表單、Extensible Application Markup Language (XAML) 表單等等。 在這些情況下，您也會在此空間中看到視覺化設計工具，此工具可讓您將控制項 (例如按鈕和清單方塊) 拖放到使用者執行您應用程式時所進行互動的表單上。

### <a name="solution-explorer"></a>底下提供說明，包括方案總管
稱為「方案總管」的工具視窗會列出所有程式碼檔案。 方案總管透過將程式碼的檔案分組到方案和專案，以協助組織程式碼。 以粗體顯示的專案稱為「啟始專案」。 它是您啟動方案時執行的第一個程式碼。 您可以變更啟始專案。 如需詳細資訊，請觀看 [Getting Started with Visual Studio - Building blocks of the IDE](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK) (Visual Studio 使用者入門 - IDE 的建置組塊) 影片。

![方案總管摺疊的節點](../ide/media/VSIDE_SolutionExplorer2_callouts.png)

 除了方案和專案之外，方案總管還會在展開專案節點時列出每個專案中的所有檔案。 每個專案都會包含一個或多個檔案，例如原始程式碼檔和資源檔 (例如映像或程式庫)。

![底下提供說明，包括方案總管](../ide/media/VSIDE_SolutionExplorer3.png)

若要查看方案、專案和檔案的屬性，請選擇捷徑 (右鍵) 功能表上的 [屬性] 命令，或依序選擇功能表上的 [檢視] 和 [屬性視窗]。

![屬性視窗](../ide/media/VSIDE_SolutionExplorer4.png)

不過，您不需要建立方案或專案，即可開始撰寫程式碼。 您只需要直接在 Visual Studio 中開啟程式碼檔 (例如從 Git 存放庫複製的檔案)，並立即開始進行編輯。 檔案將會顯示在方案總管中，並取得語法顏色標示、基本陳述式完成等作業，就像傳統解決方案一樣。 如需詳細資訊，請參閱[在 Visual Studio 中不使用專案或方案來開發程式碼](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)。

### <a name="toolbar-and-menus"></a>工具列和功能表
若要執行專案、建立新方案、儲存檔案等作業，請使用 Visual Studio 工具列和功能表命令。 例如，準備好執行程式碼以進行偵錯之後，即可選擇工具列上的 [啟動] 按鈕，或依序選擇功能表上的 [偵錯] 和 [開始偵錯]。 若要建立新方案，請選擇 [新增專案] 按鈕，或依序選擇功能表上的 [檔案]、[新增] 和 [專案] 等。

![Visual Studio 工具列](../ide/media/VSIDE_SolutionExplorer5_callouts.png)

請注意，工具列圖示和功能表命令會根據內容 (即目前選取的項目) 而變更。 您可以透過鍵盤命令及透過滑鼠來存取幾乎所有命令。

### <a name="team-explorer"></a>Team Explorer
**Team Explorer** 可讓您連線至原始檔控制工具 (例如 [Git](https://git-scm.com/) 和 [Team Foundation Version Control (TFVC)](https://www.visualstudio.com/en-us/docs/tfvc/overview)) 以在本機儲存程式碼，或將它與裝載服務的其他人共用。 您也可以使用它來追蹤工作等。

如需詳細資訊，請觀看 [Getting Started with Visual Studio - Building blocks of the IDE](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK) (Visual Studio 使用者入門 - IDE 的建置組塊) 和 [Getting Started with Visual Studio - Opening a project from Source Control](https://www.youtube.com/watch?v=pc9vX_4RGV4&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=3) (Visual Studio 使用者入門 - 從原始檔控制開啟專案) 影片。

![Team Explorer](../ide/media/TeamExplorer.png)

### <a name="output-window"></a>輸出視窗
[輸出] 視窗就是 Visual Studio 傳送其通知的位置，例如偵錯和錯誤訊息、編譯器警告、發行狀態訊息等。 每個訊息類型都有自己的索引標籤。

![輸出視窗](../ide/media/VSIDE_OutputWindow.png)

若要深入了解如何使用 [輸出] 視窗進行偵錯，請參閱 [The Output window while debugging with Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2015/02/09/the-output-window-while-debugging-with-visual-studio/) (使用 Visual Studio 偵錯時的輸出視窗)。

## <a name="first-steps"></a>第一步
- **了解全貌** - 若要概要了解 Visual Studio 中的主要功能，請參閱導覽！ 請參閱 [Visual Studio IDE 功能導覽](../ide/visual-studio-ide.md)。
- **安裝** - 若要了解如何下載並安裝 Visual Studio，請參閱[安裝 Visual Studio 2017](../install/install-visual-studio.md)。
- **基本概念** - 若要深入了解 Visual Studio 的運作方式，請參閱 [Visual Studio 使用者開發入門](../ide/get-started-developing-with-visual-studio.md)。
- **設定** - 了解如何自訂 Visual Studio 以符合您想要的工作方式。 請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。
- **教學課程** - 若要深入了解如何在 Visual Studio 中開發程式碼，請瀏覽教學課程 (例如[Visual C# 和 Visual Basic 使用者入門](../ide/getting-started-with-visual-csharp-and-visual-basic.md)或 [Visual Studio 中的 C++ 使用者入門](../ide/getting-started-with-cpp-in-visual-studio.md)。
- **影片** - 若要深入了解 Visual Studio 的其他功能和方面，請查看 YouTube 上 [Microsoft Visual Studio 頻道](https://www.youtube.com/user/VisualStudio/videos)的影片，以及 [Channel 9](https://channel9.msdn.com/Tags/visual+studio) 或 [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!jobf=Developer) 上的 Visual Studio 影片。

## <a name="access-cloud-based-resources"></a>存取雲端式資源
如果您想要在應用程式或遊戲中使用雲端式資源，則作法是包括 [Azure 服務](https://azure.microsoft.com/en-us/services/)。 您可以使用新的「Visual Studio 安裝程式」來安裝「Azure 開發」工作負載，以取得 Azure SDK for .NET。 安裝的套件與 2.9.5 的 SDK 版本位於相同的功能層級。 對於此版本的 Visual Studio 和所有未來的版本，Azure SDK for .NET 只可從 Visual Studio 安裝程式取得。

安裝 Azure 開發工作負載之後，Visual Studio 中會出現稱為 **Cloud Explorer** 的新工具視窗。 Cloud Explorer 可讓您瀏覽和管理 Visual Studio 內的 Azure 資產和資源。 如果特定作業需要 Azure 入口網站，Cloud Explorer 會提供連結，將您帶到 Azure 入口網站中您所需前往的位置。

![Cloud Explorer](../ide/media/VSIDE_CloudExplorer.png)

若要深入了解如何使用 Cloud Explorer，請參閱[使用雲端總管管理 Azure 資源](https://azure.microsoft.com/en-us/documentation/articles/vs-azure-tools-resources-managing-with-cloud-explorer/)。
安裝 Azure 開發工作負載也會提供 [Visual Studio Tools for Azure](https://www.visualstudio.com/vs/azure-tools/) 及其他相關工具。

## <a name="tips-and-tricks"></a>秘訣和訣竅
如需如何充分利用 Visual Studio 的捷徑以及實用秘訣和訣竅，請參閱下列各項。
- [Getting Started with Visual Studio - Tips & Tricks](https://www.youtube.com/watch?v=vmXqGwn1Glk&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=4) (Visual Studio 使用者入門 - 秘訣和訣竅)
- [使用 Visual Studio 提高產能的秘訣](../ide/productivity-tips-for-visual-studio.md)
- [Visual Studio Tips and Tricks](https://channel9.msdn.com/events/TechEd/2013/DEV-B353) (Visual Studio 秘訣和訣竅)
- [C++ Debugging Tips and Tricks](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/C-Plus-Plus-Debugging-Tips-and-Tricks) (C++ 偵錯秘訣和訣竅)
- [Visual Studio 最實用 (且未充分運用) 的秘訣 (英文) [Scott Hanselman 部落格]](https://www.hanselman.com/blog/VisualStudiosMostUsefulAndUnderusedTips.aspx)
- [Getting Started with Visual Studio - Installing Visual Studio extensions](https://www.youtube.com/watch?v=MWLLQaknRZY&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=7) (Visual Studio 使用者入門 - 安裝 Visual Studio 延伸模組)
