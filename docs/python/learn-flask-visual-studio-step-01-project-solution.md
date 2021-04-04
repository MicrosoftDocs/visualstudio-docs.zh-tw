---
title: Visual Studio 中的了解 Flask 教學課程步驟 1，Flask 基本概念
titleSuffix: ''
description: Visual Studio 專案內容中 Flask 基本概念的逐步解說，包括先決條件、Git 和虛擬環境。
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 89a84198256657ae7f94d0a923780163bee73e48
ms.sourcegitcommit: 5c0e20fc6005bc1f8ca38f4122378c4ac21ba89a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2021
ms.locfileid: "106110606"
---
# <a name="tutorial-get-started-with-the-flask-web-framework-in-visual-studio"></a>教學課程：開始使用 Visual Studio 中的 Flask Web 架構

[Flask](https://palletsprojects.com/p/flask/) 是一個輕量型的 Python Web 應用程式架構，可提供 URL 路由和頁面轉譯的基本要素。

Flask 被稱為「微」架構，因為它並不直接提供表單驗證、資料庫抽象、驗證等功能。 這類功能會改由稱為 Flask「延伸模組」的特殊 Python 套件提供。 這些延伸模組與 Flask 緊密整合，因此看起來就像 Flask 本身的一部分一樣。 例如，Flask 本身並不提供頁面範本引擎。 如本教學課程中所示範，範本化功能是由 Jinja 和 Jade 等延伸模組所提供。

::: moniker range="vs-2017"
在本教學課程中，您會了解如何：
- 使用「空白 Flask Web 專案」範本在 Git 存放庫中建立基本的 Flask 專案 (步驟 1)
- 建立具有單一頁面的 Flask 應用程式，然後使用範本來轉譯該頁面 (步驟 2)
- 提供靜態檔案，新增頁面，然後使用範本繼承 (步驟 3)
- 使用「Flask Web 專案」範本來建立具有多個頁面與回應式設計的應用程式 (步驟 4)
- 使用「投票 Flask Web 專案」範本來建立使用各種儲存體選項 (Azure 儲存體、MongoDB 或記憶體) 的投票應用程式。

在這些步驟的整個過程中，您會建立包含三個個別專案的單一 Visual Studio 解決方案。 您會使用 Visual Studio 隨附的不同 Flask 專案範本來建立專案。 透過將專案保留在同一個解決方案中，可讓您輕鬆地來回切換，比較不同的檔案。
::: moniker-end

::: moniker range=">=vs-2019"

在本教學課程中，您會了解如何：
- 使用「空白 Flask Web 專案」範本在 Git 存放庫中建立基本的 Flask 專案 (步驟 1)
- 建立具有單一頁面的 Flask 應用程式，然後使用範本來轉譯該頁面 (步驟 2)
- 提供靜態檔案，新增頁面，然後使用範本繼承 (步驟 3)
- 使用「Flask Web 專案」範本來建立具有多個頁面與回應式設計的應用程式 (步驟 4)

在這些步驟中，您會建立單一 Visual Studio 方案，其中包含兩個不同的專案。 您會使用 Visual Studio 隨附的不同 Flask 專案範本來建立專案。 透過將專案保留在同一個解決方案中，可讓您輕鬆地來回切換，比較不同的檔案。
::: moniker-end

> [!Note]
> 本教學課程與 [Flask 快速入門](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)的差異在於，您可以深入了解 Flask，以及如何使用各種不同 Flask 專案範本，以便為自己的專案提供更廣泛的起點。 例如，專案範本會在建立專案時自動安裝 Flask 套件，而不像快速入門中所示，需要您手動安裝套件。

## <a name="prerequisites"></a>必要條件

- Windows 上具有下列選項的 Visual Studio 2017 或更新版本：
  - **Python 開發** 工作負載 (安裝程式的 [工作負載] 索引標籤)。 如需相關指示，請參閱[在 Visual Studio 中安裝 Python 支援](installing-python-support-in-visual-studio.md)。
  - [程式碼工具] 下 [個別元件] 索引標籤上的 [Git for Windows] 和 [Visual Studio 的 GitHub 擴充]。

所有舊版「適用於 Visual Studio 的 Python 工具」都隨附 Flask 專案範本，不過其詳細資料可能與本教學課程中所討論的不同。

Visual Studio for Mac 目前不支援 Python 開發。 在 Mac 和 Linux 上，請使用 [Visual Studio Code 中的 Python 延伸模組](https://code.visualstudio.com/docs/python/python-tutorial)。

## <a name="step-1-1-create-a-visual-studio-project-and-solution"></a>步驟 1-1：建立 Visual Studio 專案和解決方案

1. 在 Visual Studio 中，**選取**  >  [檔案 **新增**  >  **專案**]、搜尋 "Flask"，然後選取 [**空白 Flask Web 專案**] 範本。  (範本也可在左側清單中的 **Python**  >  **Web** 下找到。 ) 

    ![Visual Studio 中 [空白 Flask Web 專案] 的 [新增專案] 對話方塊](media/flask/step01-new-blank-project.png)

1. 在對話方塊底部的欄位中，輸入下列資訊 (如上圖所示)，然後選取 [確定]：

    - **名稱**：將 Visual Studio 專案名稱設定為 **BasicProject**。 此名稱也會用於 Flask 專案。
    - **位置**：指定要在其中建立 Visual Studio 解決方案和專案的位置。
    - **解決方案名稱**：設定為 **LearningFlask**，適用于在本教學課程中作為多個專案容器的解決方案。
    - **為解決方案建立目錄**：設定維持不變 (預設值)。
    - **建立新的 Git 存放庫**：選取此選項 (預設為清除)，以便 Visual Studio 在建立解決方案時一併建立本機 Git 存放庫。 若您沒有看到此選項，請執行 Visual Studio 安裝工具，並在 [程式碼工具] 下的 [個別元件] 索引標籤上新增 **Git for Windows** 和 **Visual Studio 的 GitHub 延伸模組**。

1. 隨後 Visual Studio 會以對話方塊提示您，指出 **此專案需要外部套件** (如下所示)。 之所以會出現此對話方塊，是因為範本包含參考最新 Flask 1.x 套件的 *requirements.txt* 檔案。 (選取 [顯示必要套件] 來查看確切相依性)。

    ![提示指出專案需要外部套件](media/tutorials-common/step01-requirements-prompt-install-myself.png)

1. 選取 [我將自行安裝] 選項。 您很快便會建立虛擬環境，以確定它已從原始檔控制中排除。 (環境隨時可以從 *requirements.txt* 建立。)

## <a name="step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository"></a>步驟 1-2：檢查 Git 控制項並發佈至遠端存放庫

因為您已在 [新專案] 對話方塊中選取 [建立新的 Git 存放庫]，所以在建立流程完成時，系統便會立即對本機原始檔控制認可此專案。 在此步驟中，您將能熟悉 Visual Studio 的 Git 控制項，以及用來處理原始檔控制的 [Team Explorer] 視窗。

1. 檢查 Visual Studio 主視窗右下角的 Git 控制項。 這些控制項由左至右會顯示未推送的認可、未認可的變更、存放庫名稱，以及目前的分支：

    ![Visual Studio 視窗中的 Git 控制項](media/flask/step01-git-controls.png)

    > [!Note]
    > 如果您並未在 [新專案] 對話方塊中選取 [建立新的 Git 存放庫]，Git 控制項只會顯示建立本機存放庫的 [新增至原始檔控制] 命令。
    >
    > ![在尚未建立存放庫的情況下顯示於 Visual Studio 中的 [新增至原始檔控制]](media/tutorials-common/step01-git-add-to-source-control.png)

1. 選取變更按鈕，Visual Studio 會將其 [Team Explorer] 視窗開啟至 [變更] 頁面。 因為新建立的專案已經自動認可至原始檔控制，所以您不會看到任何暫止的變更。

    ![顯示 [變更] 頁面的 [Team Explorer] 視窗](media/flask/step01-team-explorer-changes.png)

1. 在 Visual Studio 狀態列上，選取未推送認可按鈕 (具有 **2** 的向上箭頭)，以在 Team Explorer 中開啟 [同步處理] 頁面。 因為您只有本機存放庫，該頁面會提供簡單的選項，以將存放庫發佈至不同的遠端存放庫。

    ![[Team Explorer] 視窗顯示可用於原始檔控制的 Git 存放庫選項](media/flask/step01-team-explorer.png)

    您可以選擇任何要用於自己專案的服務。 本教學課程示範如何使用 GitHub，其中教學課程的完整範例程式碼保存在 [Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask) 存放庫中。

1. 選取任何 [發佈] 控制項時，[Team Explorer] 會提示您輸入更多資訊。 例如，發佈此教學課程的範例時，必須先建立存放庫本身，而在 這種情況下，[推送至遠端存放庫] 選項會和存放庫的 URL 搭配使用。

    ![用於推入至現有遠端存放庫的 [Team Explorer] 視窗](media/flask/step01-push-to-github.png)

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

既然您已為專案設定原始檔控制，現在便可為專案所需的 Flask 套件建立必要的虛擬環境。 接著，您可以使用 [Team Explorer] 將環境的資料夾從原始檔控制中排除。

1. 在 [方案總管] 中，以滑鼠右鍵按一下 [Python 環境] 節點，然後選取 [新增虛擬環境]。

    ![[方案總管] 中的 [新增虛擬環境] 命令](media/flask/step01-add-virtual-environment-command.png)

1. [新增虛擬環境] 對話方塊隨即出現，上面的訊息指出 **我們找到 requirements.txt 檔案。** 此訊息表示 Visual Studio 會使用該檔案來設定虛擬環境。

    ![含有 requirements.txt 訊息的 [新增虛擬環境] 對話方塊](media/tutorials-common/step01-add-virtual-environment-found-requirements.png)

1. 選取 [建立] 來接受預設值。 (您可以視需要變更虛擬環境的名稱，這只會變更其子資料夾的名稱，但 `env` 為標準慣例)。

1. 在出現提示時同意賦與系統管理員權限，然後在 Visual Studio 下載並安裝套件時耐心等待幾分鐘，這對於 Flask 及其相依性來說，意謂著會在超過 100 個子資料夾中擴增數千個檔案。 您可以在 Visual Studio 的 [輸出] 視窗中查看進度。 您可在等候期間思考下方的＜問題＞小節。 您也可以在 [Flask 安裝](https://flask.palletsprojects.com/en/1.0.x/installation/#installation) \(英文\) 頁面 (flask.pcocoo.org) 上查看 Flask 相依性的描述。

1. 在 Visual Studio Git 控制項 (位於狀態列) 上，選取變更指標 (顯示 **99&#42;**)，這會在 Team Explorer 中開啟 [變更] 頁面。

    建立虛擬環境帶來了數千個變更，但是並不需要將其中任何一個變更包含在原始檔控制中，因為您 (或複製專案的任何其他人) 隨時可從 *requirements.txt* 重新建立環境。

    若要排除虛擬環境，請以滑鼠右鍵按一下 **env** 資料夾，然後選取 [略過這些本機項目]。

    ![在原始檔控制變更中略過虛擬環境](media/flask/step01-ignore-local-items.png)

1. 排除虛擬環境之後，剩下的變更都是針對專案檔和 *.gitignore* 的變更。 *.gitignore* 檔案包含針對虛擬環境資料夾的新增項目。 您可以按兩下該檔案以查看差異。

1. 輸入認可訊息並選取 [全部認可] 按鈕，然後視需要將認可推送至遠端存放庫。

### <a name="question-why-do-i-want-to-create-a-virtual-environment"></a>問題：為什麼我要建立虛擬環境？

答案：虛擬環境是隔離應用程式確切相依性的絕佳方法。 這類隔離方式可避免在全域 Python 環境中發生衝突，並協助測試和共同作業。 隨著您持續開發應用程式，不免會帶入許多有用的 Python 套件。 透過將套件留在專案特定的虛擬環境中，您可以輕鬆更新專案中描述該環境的 *requirements.txt* 檔案 (其包含在原始檔控制中)。 將專案複製到任何其他電腦 (包括建置伺服器、部署伺服器及其他開發電腦) 時，只要使用 *requirements.txt* 就能輕鬆重新建立環境 (這就是為何環境不需要位於原始檔控制中的原因)。 如需詳細資訊，請參閱[使用虛擬環境](selecting-a-python-environment-for-a-project.md#use-virtual-environments)。

### <a name="question-how-do-i-remove-a-virtual-environment-thats-already-committed-to-source-control"></a>問題：我要如何移除已認可至原始檔控制的虛擬環境？

回答：首先，請編輯 *.gitignore* 檔案以將該資料夾排除：在結尾尋找註解為 `# Python Tools for Visual Studio (PTVS)` 的區段，然後為虛擬環境資料夾新增一行，例如 `/BasicProject/env`。 (因為 Visual Studio 不會在 [方案總管] 中顯示該檔案，請使用 [檔案] > [開啟] > [檔案] 功能表命令來直接開啟該檔案。 您也可以從 Team Explorer 開啟該檔案：在 [設定] 頁面上，選取 [存放庫設定]，移至 [忽略屬性檔案] 區段，然後選取 **.gitignore** 旁邊的 [編輯] 連結。)

再來，請開啟命令視窗，巡覽至包含虛擬環境資料夾 (例如 *env*) 的資料夾 (例如 *BasicProject*)，然後執行 `git rm -r env`。 接著，從命令列 (`git commit -m 'Remove venv'`) 認可那些變更，或是從 [Team Explorer] 的 [變更] 頁面認可它們。

## <a name="step-1-4-examine-the-boilerplate-code"></a>步驟 1-4：檢查未定案程式碼

1. 建立完專案之後，您就會在 [方案總管] 中看到解決方案和專案，其中專案只包含 *app.py* 和 *requirements.txt* 這兩個檔案：

    ![[方案總管] 中的 Flask 專案檔](media/flask/step01-blank-flask-project-in-solution-explorer.png)

1. 如先前所述，*requirements.txt* 檔案會指定 Flask 套件相依性。 正是因為這個檔案，系統才會在您首次建立專案時邀請您建立虛擬環境。

1. 單一的 *app.py* 檔案包含三個部分。 第一個部分是 Flask 的 `import` 陳述式，此陳述式會建立 `Flask` 類別的執行個體，該執行個體會指派給 `app` 變數，然後指派 `wsgi_app` 變數 (這在部署至 Web 主機時相當有用，但目前未使用)：

    ```python
    from flask import Flask
    app = Flask(__name__)

    # Make the WSGI interface available at the top level so wfastcgi can get it.
    wsgi_app = app.wsgi_app
    ```

1. 第二個部分 (位於檔案結尾) 是些許選擇性程式碼，會以取自環境變數的特定主機和連接埠值 (預設為 localhost:5555) 啟動 Flask 開發伺服器：

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. 第三個部份是些許簡短程式碼，會將函式指派給 URL 路由，這意謂著函式會提供由該 URL 識別的資源。 您將使用 Flask 的 `@app.route` 裝飾項目來定義路由，此裝飾項目的引數是網站根目錄的相對 URL。 正如您在程式碼中所看到的，這裡的函式只會傳回文字字串，這已足以供瀏覽器呈現頁面。 在接下來的步驟中，您會以 HTML 呈現更豐富的頁面。

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

### <a name="question-what-is-the-purpose-of-the-__name__-argument-to-the-flask-class"></a>問題： Flask 類別的 __name__ 引數用途為何？

回答：此引數是應用程式模組或套件的名稱，可告訴 Flask 該去哪裡尋找範本、靜態檔案，以及其他屬於應用程式的資源。 對於包含在單一模組中的應用程式來說，`__name__` 一律是正確的值。 此引數對於需要偵錯資訊的延伸模組來說，也相當重要。 如需詳細資訊和額外的引數，請參閱 [Flask 類別文件](https://flask.palletsprojects.com/en/1.0.x/api/#flask.Flask) \(英文\) (flask.pocoo.org)。

### <a name="question-can-a-function-have-more-than-one-route-decorator"></a>問題：一個函式是否可以有多個路由裝飾項目？

回答：是，如果同一個函式為多個路由提供服務，您可以視需要使用任意數目的裝飾項目。 例如，若要將 `hello` 函式同時用於 "/" 和 "/hello"，請使用下列程式碼：

```python
@app.route('/')
@app.route('/hello')
def hello():
    """Renders a sample page."""
    return "Hello World!"
```

<a name="qa-url-variables"></a>

### <a name="question-how-does-flask-work-with-variable-url-routes-and-query-parameters"></a>問題：Flask 如何與變數 URL 路由和查詢參數搭配運作？

答：在路由中，您可以使用標記任何變數 `<variable_name>` ，而 Flask 會使用 URL 路徑中的具名引數將變數傳遞給函式。 例如，以形式的路由會產生對 `/hello/<name>` 函數呼叫的字串引數 `name` 。 您可以透過屬性取得查詢參數 `request.args` ，特別是透過 `request.args.get` 方法。 如需詳細資訊，請參閱 Flask 文件中的[要求物件](https://flask.palletsprojects.com/en/1.1.x/quickstart/#the-request-object) \(英文\)。

```python
# URL: /hello/<name>?message=Have%20a%20nice%20day
@app.route('/hello/<name>')
def hello(name):
    msg = request.args.get('message','')
    return "Hello " + name + "! "+ msg + "."
```

若要變更類型，請在變數前面加上 `int`、`float`、`path` (可接受使用斜線來描述資料夾名稱) 及 `uuid`。 如需詳細資料，請參閱 Flask 文件中的[變數規則](https://flask.palletsprojects.com/en/1.0.x/quickstart/#variable-rules) \(英文\)。

### <a name="question-can-visual-studio-generate-a-requirementstxt-file-from-a-virtual-environment-after-i-install-other-packages"></a>問題：Visual Studio 是否可以在我安裝其他套件之後，從虛擬環境產生 requirements.txt 檔案？

回答：是。 展開 [Python 環境] 節點，以滑鼠右鍵按一下虛擬環境，然後選取 [產生 requirements.txt] 命令。 在您修改環境時，最好定期使用此命令，並將對 *requirements.txt* 的變更，連同依存於該環境的任何其他程式碼變更認可至原始檔控制。 如果您在組建伺服器上設定持續整合，每當您修改環境時，都應該產生該檔案並認可變更。

## <a name="step-1-5-run-the-project"></a>步驟 1-5：執行專案

1. 在 Visual Studio 中，選取 [ **Debug**  >  **開始調試**] (**F5**) 或使用工具列上的 [ **Web 服務器**] 按鈕 (您所看到的瀏覽器可能會有不同的) ：

    ![Visual Studio 中的 [執行網頁伺服器] 工具列按鈕](media/tutorials-common/run-web-server-toolbar-button.png)

1. 上述任一命令都會將一個隨機連接埠號碼指派給 PORT 環境變數，然後執行 `python app.py`。 此程式碼會在 Flask 的開發伺服器內使用該連接埠來啟動應用程式。 如果 Visual Studio 表示 **無法啟動偵錯工具**，且包含指出沒有啟動檔案的訊息，請以滑鼠右鍵按一下 [方案總管] 中的 **app.py**，然後選取 [設定為啟動檔案]。

1. 當伺服器啟動時，您會看到一個顯示伺服器記錄的主控台視窗開啟。 接著，Visual Studio 會自動將瀏覽器開啟至 `http://localhost:<port>`，您應該可在該處看到 `hello` 函式所轉譯的訊息：

    ![Flask 專案預設檢視](media/flask/step01-first-run-success.png)

1. 當您完成時，請關閉主控台視窗，或使用 Visual Studio 中的 [ **Debug**  >  **停止調試** 程式] 命令，以停止伺服器。

### <a name="question-whats-the-difference-between-using-the-debug-menu-commands-and-the-server-commands-on-the-projects-python-submenu"></a>問題：使用 [偵錯] 功能表命令和使用專案 Python 子功能表上的伺服器命令，兩者有何差異？

回答：除了 [偵錯] 功能表命令與工具列按鈕之外，您也可以使用專案內容功能表上的 [Python] > [執行伺服器]或 [Python] > [執行偵錯伺服器] 命令來啟動伺服器。 這兩個命令都會開啟主控台視窗，您可在該處看到執行中伺服器的本機 URL (localhost:port)。 不過，您必須使用該 URL 手動開啟瀏覽器，執行偵錯伺服器並不會自動啟動 Visual Studio 偵錯工具。 您可以稍後使用 **Debug**  >  **attach to process** 命令，將偵錯工具附加至執行中的進程。

## <a name="next-steps"></a>下一步

目前，基本 Flask 專案會將起始程式碼和頁面程式碼放在同一個檔案中。 最好是將這兩個考量重點分開，並且也使用範本將 HTML 和資料分開。

> [!div class="nextstepaction"]
> [使用檢視與頁面範本來建立 Flask 應用程式](learn-flask-visual-studio-step-02-create-app.md)

## <a name="go-deeper"></a>深入了解

- [Flask 快速入門](https://flask.palletsprojects.com/en/1.0.x/quickstart/) \(英文\) (flask.pocoo.org)
- GitHub 上的教學課程原始程式碼：[Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask) \(英文\)