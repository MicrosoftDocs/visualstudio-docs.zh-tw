---
title: Visual Studio 中的了解 Django 教學課程步驟 1，Django 基本知識
titleSuffix: ''
description: 逐步解說 Visual Studio 專案內容中的 Django 基本知識，示範 Visual Studio 為 Django 開發所提供的支援。
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c6bf427f7597b59fc5bb6fb32766134daa5b22bf
ms.sourcegitcommit: f1dff6c4532c43b0444aa12ea57e90bb7dba6fba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2021
ms.locfileid: "104806065"
---
# <a name="tutorial-get-started-with-the-django-web-framework-in-visual-studio"></a>教學課程：開始使用 Visual Studio 中的 Django Web 架構

[Django (英文)](https://www.djangoproject.com/) 是高階的 Python 架構，專為快速、安全且可擴充的網頁程式開發所設計。 本教學課程會探索 Visual Studio 所提供專案範本內容中的 Django 架構，以簡化以 Django 為基礎之 Web 應用程式的建立。

在本教學課程中，您會了解如何：

::: moniker range="vs-2017"
- 使用 [空白 Django Web 專案] 範本在 Git 存放庫中建立基本的 Django 專案 (步驟 1)
- 建立具有單一頁面的 Django 應用程式，然後使用範本轉譯該頁面 (步驟 2)
- 提供靜態檔案，新增頁面，然後使用範本繼承 (步驟 3)
- 使用 Django Web 專案範本建立具有多個頁面與回應式設計的應用程式 (步驟 4)
- 驗證使用者 (步驟 5)
- 使用 [投票 Django Web 專案] 範本，建立使用模型、移轉資料庫及自訂系統管理介面的應用程式 (步驟 6)
::: moniker-end

::: moniker range=">=vs-2019"
- 使用 [空白 Django Web 專案] 範本在 Git 存放庫中建立基本的 Django 專案 (步驟 1)
- 建立具有單一頁面的 Django 應用程式，然後使用範本轉譯該頁面 (步驟 2)
- 提供靜態檔案，新增頁面，然後使用範本繼承 (步驟 3)
- 使用 Django Web 專案範本建立具有多個頁面與回應式設計的應用程式 (步驟 4)
- 驗證使用者 (步驟 5)
::: moniker-end

## <a name="prerequisites"></a>Prerequisites

- Windows 上具有下列選項的 Visual Studio 2017 或更新版本：
  - **Python 開發** 工作負載 (安裝程式的 [工作負載] 索引標籤)。 如需相關指示，請參閱[在 Visual Studio 中安裝 Python 支援](installing-python-support-in-visual-studio.md)。
  - [程式碼工具] 下 [個別元件] 索引標籤上的 [Git for Windows] 和 [Visual Studio 的 GitHub 擴充]。

Django 專案範本也包含於所有舊版的適用於 Visual Studio 的 Python 工具，不過其詳細資料可能會和本教學課程所討論的內容不同 (和舊版的 Django 架構之間會有特別多的不同之處)。

Visual Studio for Mac 目前不支援 Python 開發。 在 Mac 和 Linux 上，請使用 [Visual Studio Code 中的 Python 延伸模組](https://code.visualstudio.com/docs/python/python-tutorial)。

### <a name="visual-studio-projects-and-django-projects"></a>「Visual Studio 專案」和「Django 專案」

在 Django 用語中，「Django 專案」包含數個網站層級的設定檔，以及您部署至 Web 主機的一或多個「應用程式」，以建立完整 Web 應用程式。 Django 專案可包含多個應用程式，而且相同的應用程式可以存在於多個 Django 專案中。

Visual Studio 專案本身則可包含 Django 專案以及多個應用程式。 為了簡潔起見，本教學課程所單獨提到的「專案」，指的皆是 Visual Studio 專案。 當內容所指的是 Web 應用程式的「Django 專案」部分時，會特別使用「Django 專案」。

您會在本教學課程中將建立單一 Visual Studio 解決方案，其中包含三個不同的 Django 專案，每個專案都會包含單一 Django 應用程式。 透過將專案保留在同一個解決方案中，可讓您輕鬆地來回切換，比較不同的檔案。

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>步驟 1-1：建立 Visual Studio 專案和解決方案

從命令列使用 Django 時，您通常會執行 `django-admin startproject <project_name>` 命令來啟動專案。 在 Visual Studio 中，使用 [空白 Django Web 專案] 範本可在 Visual Studio 專案和解決方案內提供相同的結構。

1. 在 Visual Studio 中，**選取**  >  [檔案 **新增**  >  **專案**]、搜尋 "Django"，然後選取 [**空白 Django Web 專案**] 範本。  (範本也可在左側清單中的 **Python**  >  **Web** 下找到。 ) 

    ![Visual Studio 中針對 [空白 Django Web 專案] 的 [新專案] 對話方塊](media/django/step01-new-blank-project.png)

1. 在對話方塊底部的欄位中，輸入下列資訊 (如上圖所示)，然後選取 [確定]：

    - **名稱**：將 Visual Studio 專案名稱設定為 **BasicProject**。 此名稱也會用於 Django 專案。
    - **位置**：指定要在其中建立 Visual Studio 解決方案和專案的位置。
    - **解決方案**：讓此控制項保持設定為預設的 [建立新解決方案] 選項。
    - **解決方案名稱**：設定為 **LearningDjango**，這適用於本教學課程中作為多個專案容器的解決方案。
    - **為解決方案建立目錄**：設定維持不變 (預設值)。
    - **建立新的 Git 存放庫**：選取此選項 (預設為清除)，以便 Visual Studio 在建立解決方案時一併建立本機 Git 存放庫。 若您沒有看到此選項，請執行 Visual Studio 安裝工具，並在 [程式碼工具] 下的 [個別元件] 索引標籤上新增 **Git for Windows** 和 **Visual Studio 的 GitHub 延伸模組**。

1. 隨後 Visual Studio 會以對話方塊提示您，指出 **此專案需要外部套件** (如下所示)。 之所以會出現此對話方塊，是因為範本包含參考最新 Django 1.x 套件的 *requirements.txt* 檔案。 (選取 [顯示必要套件] 來查看確切相依性)。

    ![提示指出專案需要外部套件](media/django/step01-requirements-prompt-install-myself.png)

1. 選取 [我將自行安裝] 選項。 您很快便會建立虛擬環境，以確定它已從原始檔控制中排除。 (環境隨時可以從 *requirements.txt* 建立。)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>步驟 1-2：檢查 Git 控制項並發佈至遠端存放庫

因為您已在 [新專案] 對話方塊中選取 [建立新的 Git 存放庫]，所以在建立流程完成時，系統便會立即對本機原始檔控制認可此專案。 在此步驟中，您將能熟悉 Visual Studio 的 Git 控制項，以及用來處理原始檔控制的 [Team Explorer] 視窗。

1. 檢查 Visual Studio 主視窗右下角的 Git 控制項。 這些控制項由左至右會顯示未推送的認可、未認可的變更、存放庫名稱，以及目前的分支：

    ![Visual Studio 視窗中的 Git 控制項](media/django/step01-git-controls.png)

    > [!Note]
    > 如果您並未在 [新專案] 對話方塊中選取 [建立新的 Git 存放庫]，Git 控制項只會顯示建立本機存放庫的 [新增至原始檔控制] 命令。
    >
    > ![在尚未建立存放庫的情況下顯示於 Visual Studio 中的 [新增至原始檔控制]](media/django/step01-git-add-to-source-control.png)

1. 選取變更按鈕，Visual Studio 會將其 [Team Explorer] 視窗開啟至 [變更] 頁面。 因為新建立的專案已經自動認可至原始檔控制，所以您不會看到任何暫止的變更。

    ![顯示 [變更] 頁面的 [Team Explorer] 視窗](media/django/step01-team-explorer-changes.png)

1. 在 Visual Studio 狀態列上，選取未推送認可按鈕 (具有 **2** 的向上箭頭)，以在 Team Explorer 中開啟 [同步處理] 頁面。 因為您只有本機存放庫，該頁面會提供簡單的選項，以將存放庫發佈至不同的遠端存放庫。

    ![[Team Explorer] 視窗顯示可用於原始檔控制的 Git 存放庫選項](media/django/step01-team-explorer.png)

    您可以選擇任何要用於自己專案的服務。 本教學課程示範如何使用 GitHub，用於教學課程的完整範例程式碼維護於 [Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django) 存放庫中。

1. 選取任何 [發佈] 控制項時，[Team Explorer] 會提示您輸入更多資訊。 例如，發佈此教學課程的範例時，必須先建立存放庫本身，而在 這種情況下，[推送至遠端存放庫] 選項會和存放庫的 URL 搭配使用。

    ![用於推入至現有遠端存放庫的 [Team Explorer] 視窗](media/django/step01-push-to-github.png)

    如果您尚無現有存放庫，[發佈至 GitHub] 與 [推送至 Azure DevOps] 選項可讓您直接在 Visual Studio 內建立存放庫。

1. 隨著您逐步完成本教學課程，請建立定期使用 Visual Studio 中的控制項來認可並推送變更的習慣。 本教學課程會合適的時機點提醒您。

> [!Tip]
> 若要在 Team Explorer 內快速瀏覽，請選取標題 (在上面影像中標為 [變更] 或 [推送]) 以查看可用頁面的快顯功能表。

### <a name="question-what-are-some-advantages-of-using-source-control-from-the-beginning-of-a-project"></a>問題：從專案一開始就使用原始檔控制會有哪些優點？

回答：首先，從一開始就使用原始檔控制 (特別是在您也使用遠端存放庫時)，可為專案提供頻繁的離站備份。 不同於只在本機檔案系統上維護專案，原始檔控制也能提供完整的變更記錄，並能輕易將單一檔案或整個專案還原至先前的狀態。 該變更記錄可協助判斷迴歸 (測試失敗) 的原因。 此外，原始檔控制在有多人一起處理專案的情況下是不可或缺的，因為它可管理覆寫並提供衝突解決方式。 最後，原始檔控制基本上是一種自動化的形式，可為您妥善設定自動化建置、測試和發行管理。 它確實是針對專案採用 DevOps 的第一步；由於其門檻非常低，因此實在沒有什麼原因不在一開始便使用原始檔控制。

如需原始檔控制作為自動化的進一步討論，請參閱 MSDN Magazine 針對行動應用程式 (但也同樣適用於 Web 應用程式) 所撰寫的文章：[本質來源：存放庫在 DevOps 中的角色](/archive/msdn-magazine/2016/september/mobile-devops-the-source-of-truth-the-role-of-repositories-in-devops) \(英文\)。

### <a name="question-can-i-prevent-visual-studio-from-auto-committing-a-new-project"></a>問題：我能夠避免 Visual Studio 自動認可新專案嗎？

回答：是。 若要停用自動認可，請移至 [Team Explorer] 中的 [設定] 頁面，選取 [Git] > [全域設定]，清除標示為 [預設在合併後認可變更] 的選項，然後選取 [更新]。

## <a name="step-1-3-create-the-virtual-environment-and-exclude-it-from-source-control"></a>步驟 1-3：建立虛擬環境並將它從原始檔控制中排除

在您為專案設定原始檔控制之後，便可以建立包含專案所需之 Django 套件的虛擬環境。 接著，您可以使用 [Team Explorer] 將環境的資料夾從原始檔控制中排除。

1. 在 [方案總管] 中，以滑鼠右鍵按一下 [Python 環境] 節點，然後選取 [新增虛擬環境]。

    ![[方案總管] 中的 [新增虛擬環境] 命令](media/django/step01-add-virtual-environment-command.png)

1. [新增虛擬環境] 對話方塊隨即出現，上面的訊息指出 **我們找到 requirements.txt 檔案。** 此訊息表示 Visual Studio 會使用該檔案來設定虛擬環境。

    ![含有 requirements.txt 訊息的 [新增虛擬環境] 對話方塊](media/django/step01-add-virtual-environment-found-requirements.png)

1. 選取 [建立] 來接受預設值。 (您可以視需要變更虛擬環境的名稱，這只會變更其子資料夾的名稱，但 `env` 為標準慣例)。

1. 在出現提示時同意賦與系統管理員權限，靜待數分鐘以讓 Visual Studio 下載和安裝套件，這對於 Django 來說，表示會在任意數量的子資料夾中擴充數以千計的檔案！ 您可以在 Visual Studio 的 [輸出] 視窗中查看進度。 您可在等候期間思考下方的＜問題＞小節。

1. 在 Visual Studio Git 控制項 (位於狀態列) 上，選取變更指標 (顯示 **99&#42;**)，這會在 Team Explorer 中開啟 [變更] 頁面。

    建立虛擬環境帶來了數千個變更，但是並不需要將其中任何一個變更包含在原始檔控制中，因為您 (或複製專案的任何其他人) 隨時可從 *requirements.txt* 重新建立環境。

    若要排除虛擬環境，請以滑鼠右鍵按一下 **env** 資料夾，然後選取 [略過這些本機項目]。

    ![在原始檔控制變更中略過虛擬環境](media/django/step01-ignore-local-items.png)

1. 排除虛擬環境之後，剩下的變更都是針對專案檔和 *.gitignore* 的變更。 *.gitignore* 檔案包含針對虛擬環境資料夾的新增項目。 您可以按兩下該檔案以查看差異。

1. 輸入認可訊息並選取 [全部認可] 按鈕，然後視需要將認可推送至遠端存放庫。

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>問題：為什麼我要建立虛擬環境？

答案：虛擬環境是隔離應用程式確切相依性的絕佳方法。 這類隔離方式可避免在全域 Python 環境中發生衝突，並協助測試和共同作業。 隨著您持續開發應用程式，不免會帶入許多有用的 Python 套件。 透過將套件留在專案特定的虛擬環境中，您可以輕鬆更新專案中描述該環境的 *requirements.txt* 檔案 (其包含在原始檔控制中)。 將專案複製到任何其他電腦 (包括建置伺服器、部署伺服器及其他開發電腦) 時，只要使用 *requirements.txt* 就能輕鬆重新建立環境 (這就是為何環境不需要位於原始檔控制中的原因)。 如需詳細資訊，請參閱[使用虛擬環境](selecting-a-python-environment-for-a-project.md#use-virtual-environments)。

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>問題：我要如何移除已認可至原始檔控制的虛擬環境？

回答：首先，請編輯 *.gitignore* 檔案以將該資料夾排除：在結尾尋找註解為 `# Python Tools for Visual Studio (PTVS)` 的區段，然後為虛擬環境資料夾新增一行，例如 `/BasicProject/env`。 (因為 Visual Studio 不會在 [方案總管] 中顯示該檔案，請使用 [檔案] > [開啟] > [檔案] 功能表命令來直接開啟該檔案。 您也可以從 Team Explorer 開啟該檔案：在 [設定] 頁面上，選取 [存放庫設定]，移至 [忽略屬性檔案] 區段，然後選取 **.gitignore** 旁邊的 [編輯] 連結。)

再來，請開啟命令視窗，巡覽至包含虛擬環境資料夾 (例如 *env*) 的資料夾 (例如 *BasicProject*)，然後執行 `git rm -r env`。 接著，從命令列 (`git commit -m 'Remove venv'`) 認可那些變更，或是從 [Team Explorer] 的 [變更] 頁面認可它們。

## <a name="step-1-4-examine-the-boilerplate-code"></a>步驟 1-4：檢查未定案程式碼

專案建立完成之後，請檢查未定案的 Django 專案程式碼 (這同樣和 CLI 命令 `django-admin startproject <project_name>` 所產生的程式碼相同)。

1. 位於專案根目錄中的是 *manage.py*，這是 Visual Studio 自動設定為專案啟動檔案的 Django 命令列系統管理公用程式。 您需在命令列上使用 `python manage.py <command> [options]` 來執行該公用程式。 針對一般 Django 工作，Visual Studio 會提供方便的功能表命令。 以滑鼠右鍵按一下 [方案總管] 中的專案，然後選取 [Python] 以查看清單。 您會在本教學課程過程中遇到一部分的這些命令。

    ![Python 專案內容功能表上的 Django 命令](media/django/step01-django-commands-menu.png)

2. 在您的專案中，會有一個名稱和專案相同的資料夾。 其中包含基本的 Django 專案檔：

   - *__init.py*：告訴 Python 此資料夾為 Python 套件的空白檔案。
   - *wsgi.py*：供 WSGI 相容的網頁伺服器服務您專案的進入點。 您通常會將此檔案保持原狀，因為它會提供生產 Web 伺服器的勾點。
   - *settings.py*：包含 Django 專案的設定，您可以在開發 Web 應用程式的過程中修改。
   - *urls.py*：包含 Django 專案的目錄，您也可以在開發過程中修改。

     ![[方案總管] 中的 Django 專案檔](media/django/step01-django-project-in-solution-explorer.png)

3. 如前文所述，Visual Studio 範本也會將指定 Django 套件相依性的 *requirements.txt* 檔案新增至專案。 正是因為這個檔案，系統才會在您首次建立專案時邀請您建立虛擬環境。

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>問題：Visual Studio 是否可以在我安裝其他套件之後，從虛擬環境產生 requirements.txt 檔案？

回答：是。 展開 [Python 環境] 節點，以滑鼠右鍵按一下虛擬環境，然後選取 [產生 requirements.txt] 命令。 在您修改環境時，最好定期使用此命令，並將對 *requirements.txt* 的變更，連同依存於該環境的任何其他程式碼變更認可至原始檔控制。 如果您在組建伺服器上設定持續整合，每當您修改環境時，都應該產生該檔案並認可變更。

## <a name="step-1-5-run-the-empty-django-project"></a>步驟 1-5：執行空白 Django 專案

1. 在 Visual Studio 中，選取 [ **Debug**  >  **開始調試**] (**F5**) 或使用工具列上的 [ **Web 服務器**] 按鈕 (您所看到的瀏覽器可能會有不同的) ：

    ![Visual Studio 中的 [執行網頁伺服器] 工具列按鈕](media/django/run-web-server-toolbar-button.png)

1. 執行伺服器表示執行 `manage.py runserver <port>` 命令，此命令會啟動 Django 的內建開發伺服器。 如果 Visual Studio 表示 **無法啟動偵錯工具**，且包含指出沒有啟動檔案的訊息，請以滑鼠右鍵按一下 [方案總管] 中的 [manage.py]，然後選取 [設定為啟動檔案]。

1. 當您啟動伺服器時，會看到主控台視窗隨即開啟，同時顯示伺服器記錄檔。 Visual Studio 會自動開啟瀏覽器並前往 `http://localhost:<port>`。 因為 Django 專案還沒有應用程式，所以 Django 只會顯示預設網頁，以確認您現有的內容運作正常：

    ![Django 專案預設檢視](media/django/step01-first-run-success.png)

1. 當您完成時，請關閉主控台視窗，或使用 Visual Studio 中的 [ **Debug**  >  **停止調試** 程式] 命令，以停止伺服器。

### <a name="question-is-django-a-web-server-as-well-as-a-framework"></a>問題：Django 是網頁伺服器，同時也是架構？

回答：可以說是，也可以說不是。 Django 沒有用於開發用途的內建網頁伺服器。 此網頁伺服器是用於您在本機執行 Web 應用程式 (例如在 Visual Studio 中進行偵錯) 的情況。 不過，當您部署至 Web 主機時，Django 會改為使用主機的 Web 伺服器。 Django 專案中的 *wsgi.py* 模組會負責連結到實際執行伺服器。

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>問題：使用 [偵錯] 功能表命令和使用專案 Python 子功能表上的伺服器命令，兩者有何差異？

回答：除了 [偵錯] 功能表命令與工具列按鈕之外，您也可以使用專案內容功能表上的 [Python] > [執行伺服器]或 [Python] > [執行偵錯伺服器] 命令來啟動伺服器。 這兩個命令都會開啟主控台視窗，您可在該處看到執行中伺服器的本機 URL (localhost:port)。 不過，您必須使用該 URL 手動開啟瀏覽器，執行偵錯伺服器並不會自動啟動 Visual Studio 偵錯工具。 您可以稍後使用 **Debug**  >  **attach to process** 命令，將偵錯工具附加至執行中的進程。

## <a name="next-steps"></a>下一步

此時，基本的 Django 專案並不會包含任何應用程式。 您會在下一個步驟中建立應用程式。 因為比起 Django 專案，您會更常處理 Django 應用程式，所以目前並不需要更深入了解未定案檔案。

> [!div class="nextstepaction"]
> [使用檢視與頁面範本建立 Django 應用程式](learn-django-in-visual-studio-step-02-create-an-app.md)

## <a name="go-deeper"></a>深入了解

- Django 專案程式碼：[撰寫第一個 Django 應用程式，第 1 部分](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) \(英文\) (docs.djangoproject.com)
- 系統管理公用程式：[django-admin 與 manage.py](https://docs.djangoproject.com/en/2.0/ref/django-admin/) \(英文\) (docs.djangoproject.com)
- GitHub 上的教學課程原始程式碼：[Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)