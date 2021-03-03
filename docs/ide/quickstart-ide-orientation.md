---
title: 快速入門： Visual Studio IDE 導覽
description: 瞭解 Visual Studio 整合式開發環境 (IDE) 的部分視窗、功能表和其他 UI 功能。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 03/02/2021
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 237b3384d6bec010a760c4bc193b9a95f33febeb
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683986"
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>快速入門：Visual Studio IDE 初探

在這個 5-10 分鐘的 Visual Studio 整合式開發環境 (IDE) 簡介中，我們將簡介部分視窗、功能表和其他 UI 功能。

::: moniker range="vs-2017"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。

::: moniker-end

::: moniker range=">=vs-2019"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads)頁面免費進行安裝。

::: moniker-end

::: moniker range="vs-2017"

## <a name="start-page"></a>起始頁

開啟 Visual Studio 之後，首先看到的畫面很可能是 **起始頁**。 **起始頁** 是設計為「中樞」，可協助您更快速地找到所需的命令和專案檔案。 [最近使用的] 區段會顯示您最近使用的專案和資料夾。 在 [新增專案] 底下，您可以按一下連結來開啟 [新增專案] 對話方塊；或者，在 [開啟] 底下，您可以開啟現有的程式碼專案或資料夾。 右側是最新的開發人員新聞摘要。

![Visual Studio 中的起始頁](media/start-page.png)

如果您關閉 [ **開始] 頁面** ，並想要再次查看它，您可以 **從 [檔案** ] 功能表重新開啟它。

![Visual Studio 的 [檔案] 功能表](media/quickstart-IDE-file-menu-large.png)

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="start-window"></a>啟動視窗

開啟 Visual Studio 之後，首先看到的畫面是 [開始] 視窗。 啟動視窗旨在協助您更快速「開始撰寫程式碼」。 其選項可讓您複製或簽出程式碼、開啟現有專案或解決方案、建立新專案，或僅開啟包含某些程式碼檔案的資料夾。

[![Visual Studio 2019 中的開始視窗](media/vs-2019/start-window-labeled.png)](media/vs-2019/start-window-labeled.png#lightbox)

如果這是您第一次使用 Visual Studio，則最近使用的專案清單會是空白。

如果您使用非 MSBuild 架構程式碼基底，則您將使用 [開啟本機資料夾] 選項在 Visual Studio 開啟您的程式碼。 如需詳細資訊，請參閱[在 Visual Studio 中不使用專案或方案來開發程式碼](develop-code-in-visual-studio-without-projects-or-solutions.md)。 否則，您可以建立新的專案或從來源提供者複製專案，例如 GitHub 或 Azure DevOps。

[不使用程式碼繼續] 選項僅會開啟 Visual Studio 開發環境，而不包含任何特定專案，也不會載入程式碼。 您可以選擇此選項來加入 [Live Share](/visualstudio/liveshare/) 工作階段或附加至處理序以進行偵錯。 您也可以按 **Esc** 來關閉啟動視窗並開啟 IDE。

::: moniker-end

## <a name="create-a-project"></a>建立專案

若要繼續探索 Visual Studio 的功能，讓我們建立新的專案。

::: moniker range="vs-2017"

1. 在 [起始頁] 上，於 [新增專案] 下的搜尋方塊中，鍵入 **console** 從專案類型清單中篩選出名稱中包含 "console" 的專案類型。

   ![在 Visual Studio 起始頁上搜尋專案範本](media/start-page-search-templates.png)

   Visual Studio 提供各種專案範本，協助您開始快速撰寫程式碼。 選擇 C# [主控台應用程式 (.NET Core)] 專案範本。 (或者，如果您是 Visual Basic、C++、Javascript 或其他程式設計語言開發人員，則也可以使用其中一種程式設計語言來建立專案。 我們稍後要介紹的 UI 在所有程式設計語言中都很類似)。

1. 在出現的 [新增專案] 對話方塊中，接受預設專案名稱，並選擇 [確定]。

::: moniker-end

::: moniker range=">=vs-2019"

1. 在 [開始] 視窗中，選擇 [ **建立新專案**]。

    :::image type="content" source="../get-started/media/vs-2019/start-window-create-new-project.png" alt-text="Visual Studio 2019 中 [建立新專案] 視窗的螢幕擷取畫面。":::

   [建立新專案] 視窗隨即開啟，並顯示數個專案「範本」。 範本包含指定專案類型所需的基本檔案和設定。

   在這裡，您可以搜尋、篩選和選取專案範本。 它也會顯示一份最近使用的專案範本清單。

1. 在上方的搜尋方塊中，輸入 **console**，從專案類型清單中篩選出名稱包含 "console" 的專案類型。 從 [**所有語言**] 下拉式清單中挑選 **c #** (或您) 選擇的另一種語言，進一步精簡搜尋結果。

    :::image type="content" source="media/vs-2019/create-new-project.png" alt-text="Visual Studio 2019 中 [建立新專案] 視窗的螢幕擷取畫面，您可以在其中選取所需的範本。":::

1. 如果您選取 c #、Visual Basic 或 F # 作為您的語言，請選取 [ **主控台應用程式** ] 範本，然後選擇 [ **下一步]**。 (如果您選取不同的語言，只需挑選任意範本。 我們稍後要介紹的 UI 在所有程式設計語言中都很類似)。

1. 在 [ **設定您的新專案** ] 視窗中，接受預設的 [專案名稱] 和 [位置]，然後選擇 **[下一步**]。

    :::image type="content" source="media/vs-2019/configure-new-project-console.png" alt-text="Visual Studio 2019 中 [設定新專案] 視窗的螢幕擷取畫面，您可以在其中輸入專案的名稱。":::

1. 在 [**其他資訊**] 視窗中，確認 [**目標 Framework** ] 下拉式功能表中出現 **.net Core 3.1** ，然後按一下 [**建立**]。

    :::image type="content" source="../get-started/media/vs-2019/create-project-additional-info.png" alt-text="Visual Studio 2019 中 [其他資訊] 視窗的螢幕擷取畫面，您可以在其中選取所需的 .NET Core Framework 版本。":::

::: moniker-end

   系統隨即建立專案，並在 [編輯器] 視窗中開啟名為 *Program.cs* 的檔案。 **編輯器** 會顯示檔案的內容，您可以在 Visual Studio 中進行大部分的編碼工作。

   ![Visual Studio 中的編輯器](media/editor.png)

## <a name="solution-explorer"></a>方案總管

[方案總管] 一般位在 Visual Studio 右側，並示範以圖形呈現專案、方案或程式碼資料夾中的檔案和資料夾階層。 您可以流覽階層，並流覽至 **方案 Explorer** 中的檔案。

![Visual Studio 中的 [方案總管]](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>功能表

Visual Studio 頂端的功能表列可將命令依類別分組。 例如，[專案] 功能表會包含您正在處理的專案相關命令。 在 [工具] 功能表上，您可以選取 [選項] 來自訂 Visual Studio 行為，或選取 [取得工具與功能] 來將功能新增到您的安裝。

::: moniker range="vs-2017"

![Visual Studio 2017 中的功能表列](media/quickstart-IDE-menu-bar.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Visual Studio 2019 中的功能表列](media/vs-2019/menu-bar.png)

::: moniker-end

## <a name="error-list"></a>錯誤清單

選擇 [檢視] 功能表，然後選擇 [錯誤清單]，以開啟 [錯誤清單] 視窗。

[ **錯誤清單** ] 會顯示有關程式碼目前狀態的錯誤、警告和訊息。 如果您的檔案中或專案中的任何位置有任何錯誤 (例如遺漏大括弧或分號)，則會在此處列出。

![Visual Studio 中的錯誤清單](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>輸出視窗

[輸出] 視窗會顯示建置專案的輸出訊息以及來自原始檔控制提供者的輸出訊息。

請建置專案以查看一些建置輸出。 從 [ **組建** ] 功能表中，選擇 [ **建立方案**]。 [ **輸出** ] 視窗會自動取得焦點並顯示成功的組建訊息。

![Visual Studio 中的輸出視窗](media/build-output-minimal.png)

## <a name="search-box"></a>搜尋方塊

透過搜尋方塊，即可快速且輕鬆地巡覽 Visual Studio 中大部分的工作。 您可以輸入想要執行工作的相關文字，它就會顯示與該文字相關的選項清單。 例如，假設您想要增加建置輸出的詳細資料，以顯示建置實際工作內容的其他詳細資料。 您可能使用的方法如下：

::: moniker range="vs-2017"

1. 在 IDE 右上角尋找 [快速啟動] 搜尋方塊。  (您也可以按 **Ctrl** + **Q** 加以存取。 ) 

2. 在搜尋方塊中，輸入 **詳細資訊**。 從顯示的結果中，選擇 [選項] 類別下的 [專案和方案] --> [建置並執行]。

   ![Visual Studio 2017 中的 [快速啟動] 搜尋方塊](media/quickstart-IDE-quick-launch.png)

   [選項] 對話方塊會開啟 [建置並執行] 選項頁面。

::: moniker-end

::: moniker range=">=vs-2019"

1. 按 **Ctrl** + **Q** ，以啟動 IDE 上半部的 [搜尋] 方塊。

2. 在搜尋方塊中，輸入 **詳細資訊**。 從顯示的結果中，選擇 [變更 MSBuild 詳細資訊]。

   ![Visual Studio 2019 中的搜尋方塊](media/vs-2019/quick-launch-verbosity.png)

   [選項] 對話方塊會開啟 [建置並執行] 選項頁面。

::: moniker-end

3. 在 [MSBuild 專案建置輸出詳細等級] 底下，選擇 [一般]，然後按一下 [確定]。

4. 以滑鼠右鍵按一下 [方案總管] 中的 [ConsoleApp1] 專案，然後選擇操作功能表中的 [重建]，以再次建置專案。

   這次 **輸出** 視窗會顯示來自組建程式的更多詳細資訊記錄，包括複製的檔案。

   ![Visual Studio 中的詳細資訊組建輸出](media/build-output-verbose.png)

## <a name="send-feedback-menu"></a>[傳送意見反應] 功能表

如果您在使用 Visual Studio 時遇到任何問題，或如果您有改善產品的建議，請使用靠近 Visual Studio 視窗頂端的 [傳送意見反應] 功能表。

::: moniker range="vs-2017"

![Visual Studio 2017 中的 [傳送意見反應] 功能表](media/quickstart-IDE-send-feedback.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Visual Studio 2019 中的 [傳送意見反應] 功能表](media/vs-2019/send-feedback-menu.png)

::: moniker-end

## <a name="next-steps"></a>下一步

我們已經介紹 Visual Studio 的幾個功能，藉以熟悉使用者介面。 若要進一步探索：

> [!div class="nextstepaction"]
> [了解程式碼編輯器](../get-started/tutorial-editor.md)

> [!div class="nextstepaction"]
> [了解專案與解決方案](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>另請參閱

- [Visual Studio IDE 預覽](../get-started/visual-studio-ide.md)
- [Visual Studio 的其他功能](../ide/advanced-feature-overview.md)
- [變更佈景主題與字型色彩](../ide/quickstart-personalize-the-ide.md)
