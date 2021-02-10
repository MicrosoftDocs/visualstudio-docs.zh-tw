---
title: Visual Studio 中的了解 Flask 教學課程步驟 2，檢視與範本
titleSuffix: ''
description: 逐步解說 Visual Studio 專案內容中的 Flask 基本知識，特別是建立應用程式及使用檢視與範本的步驟。
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8e9d55d9c1c22edea1ff826b23beb6d0ec6b392c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942408"
---
# <a name="step-2-create-a-flask-app-with-views-and-page-templates"></a>步驟 2：使用檢視與頁面範本來建立 Flask 應用程式

**上一個步驟：[建立 Visual Studio 專案和解決方案](learn-flask-visual-studio-step-01-project-solution.md)**

本教學課程步驟 1 會產生一個 Flask 應用程式。此應用程式為單一檔案，其中包含單一頁面與所有程式碼。 若要考慮進一步開發，最好是將程式碼重構，並為頁面範本建立結構。 特別是，您會想要將應用程式檢視程式碼與其他方面 (例如起始程式碼) 分開。

在這個步驟中，您現在將了解如何：

> [!div class="checklist"]
> - 重構應用程式的程式碼以將檢視與起始程式碼分割 (步驟 2-1)
> - 使用頁面範本來轉譯檢視 (步驟 2-2)

## <a name="step-2-1-refactor-the-project-to-support-further-development"></a>步驟 2-1：重構專案以支援進一步的開發

在「空白 Flask Web 專案」範本所建立的程式碼中，會有單一 *app.py* 檔案，其中除了單一檢視，還包含啟動程式碼。 若要考慮使用多個檢視和範本來進一步開發應用程式，最好是將這些考量重點分開。

1. 在您的專案資料夾中，建立一個名為 `HelloFlask` 的應用程式資料夾 (在 [方案總管] 中的專案上按一下滑鼠右鍵，然後選取 [新增] > [新增資料夾])。

2. 在 *HelloFlask* 資料夾中，使用下列內容建立名為 *\_ \_ \_ \_ .py* 的檔案，其會建立 `Flask` 實例，並載入 (下一個步驟中建立的應用程式視圖) ：

    ```python
    from flask import Flask
    app = Flask(__name__)

    import HelloFlask.views
    ```

3. 在 *HelloFlask* 資料夾中，使用下列內容來建立名為 *views.py* 的檔案。 名稱 *views.py* 很重要，因為您在 `import HelloFlask.views` *\_ \_ init \_ \_ . .py* 中使用; 如果名稱不相符，您將會在執行時間看到錯誤。

    ```python
    from flask import Flask
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        return "Hello Flask!"
    ```

    除了將函式重新命名並路由至之外 `home` ，此程式碼還包含 *app.py* 的頁面轉譯程式碼，並匯入 `app` 在 *\_ \_ init \_ \_ . .py* 中宣告的物件。

4. 在 *HelloFlask* 中建立名為 *templates* 的子資料夾，此子資料夾目前會維持空白。

5. 在專案的根資料夾中，將 *app.py* 重新命名為 *runserver.py*，並讓內容符合下列程式碼：

    ```python
    import os
    from HelloFlask import app    # Imports the code from HelloFlask/__init__.py

    if __name__ == '__main__':
        HOST = os.environ.get('SERVER_HOST', 'localhost')

        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555

        app.run(HOST, PORT)
    ```

6. 您的專案結構應該看起來如下圖：

    ![重構程式碼後的專案結構](media/flask/step02-project-structure.png)

7. 選取 [ **Debug**  >  **開始調試** 程式] (**F5**) 或使用工具列上的 [ **Web 服務器**] 按鈕 (您所看到的瀏覽器可能會有不同的) 啟動應用程式並開啟瀏覽器。 同時嘗試 / 和 /home URL 路由。

8. 您也可以在程式碼的各個不同部分設定中斷點，然後重新啟動應用程式以依照該啟動順序。 例如，在 *runserver.py* 和 *HelloFlask\_* init_ *.py* 的前幾行上設定中斷點，並在 *views.py* 的 `return "Hello Flask!"` 行上設定中斷點。 然後，重新開機應用程式 (**Debug**  >  **重新開機**、 **Ctrl** + **Shift** + **F5** 或如下所示的工具列按鈕) 和逐步解說 (**F10**) 程式碼，或使用 **F5** 從每個中斷點執行。

    ![Visual Studio 中偵錯工具列上的重新啟動按鈕](media/debugging-restart-toolbar-button.png)

9. 完成時，請停止應用程式。

### <a name="commit-to-source-control"></a>認可至原始檔控制

因為您已變更並成功測試程式碼，所以現在是檢閱並認可對原始碼控制所做變更的絕佳時機。 本教學課程稍後的步驟會在適當時刻提醒您再次認可至原始檔控制，並請您返回參閱本節。

1. 選取位於 Visual Studio 底部的變更按鈕 (下面圈起處)，這會瀏覽至 [Team Explorer]。

    ![Visual Studio 狀態列上的原始檔控制變更按鈕](media/flask/step02-source-control-changes-button.png)

1. 在 [Team Explorer] 中，輸入 "Refactor code" (重構程式碼) 之類的訊息，然後選取 [全部認可]。 當認可完成時，您會看到在 **本機建立的訊息認可 \<hash> 。同步以與伺服器共用您的變更。** 如果您想要將變更推送至遠端存放庫，請選取 [同步]，然後選取 [傳出的認可] 底下的 [推送]。 您也可以在累積多個本機認可之後，再推送至遠端。

    ![在 [Team Explorer] 中將認可推送至遠端](media/flask/step02-source-control-push-to-remote.png)

### <a name="question-how-frequently-should-one-commit-to-source-control"></a>問題：認可至原始檔控制的頻率應該有多高？

回答：將變更認可至原始檔控制會在變更記錄檔中建立記錄，以及可供您視需要還原存放庫的點。 您也可以檢查每個認可來了解其特定的變更。 由於在 Git 中進行認可並不會耗費太多資源，因此最好是經常進行認可，而不要累積大量變更再一次進行認可。 顯然地，您並不需要認可對個別檔案所做的每個微小變更。 通常，您會在新增功能、變更結構 (就像在此步驟中所做的) 或已完成一些程式碼重構時，才進行認可。 此外，也請與您小組中的其他人進行確認，以找出最適合每個人的認可細微性。

進行認可的頻率與將認可推送至遠端存放酷的頻率，是兩個不同的考量重點。 您可以先在本機存放庫中累積多個認可，然後再將它們推送到遠端存放庫。 同樣地，認可頻率取決於您小組管理存放庫的方式。

## <a name="step-2-2-use-a-template-to-render-a-page"></a>步驟 2-2：使用範本來轉譯頁面

目前您在 *views.py* 中已有的 `home` 函式，只會針對網頁產生純文字 HTTP 回應。 不過，大多數真實世界的網頁都是以通常含有即時資料的豐富 HTML 網頁來回應。 確實，使用函式來定義檢視的主要原因就是為了動態產生內容。

因為檢視的傳回值只是一個字串，所以您可以使用動態內容，視需要在字串內建置任何 HTML。 不過，由於最好是將標記與資料分開，因此較理想的做法是將標記放在範本中，而將資料保留在程式碼中。

1. 對於初學者來說，請編輯 *views.py* 來包含下列程式碼，這些程式碼會針對頁面使用內嵌 HTML 搭配某些動態內容：

    ```python
    from datetime import datetime
    from flask import render_template
    from HelloFlask import app

    @app.route('/')
    @app.route('/home')
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        html_content = "<html><head><title>Hello Flask</title></head><body>"
        html_content += "<strong>Hello Flask!</strong> on " + formatted_now
        html_content += "</body></html>"

        return html_content
    ```

1. 執行應用程式並將頁面重新整理幾次，以查看日期/時間是否更新。 完成時，請停止應用程式。

1. 若要將頁面轉譯轉換成使用範本，請使用下列內容在 *templates* 資料夾中建立名為 *index.html* 的檔案，其中 `{{ content }}` 是您在程式碼中為其提供值的預留位置或取代權杖 (也稱為「範本變數」)：

    ```html
    <html>
        <head><title>Hello Flask</title></head>

        <body>
            {{ content }}
        </body>
    </html>
    ```

1. 修改 `home` 函式以使用 `render_template` 來載入範本及為 "content" 提供值，這會使用符合預留位置名稱的具名引數來完成。 Flask 會自動在 *templates* 資料夾中尋找範本，因此範本路徑會是該資料夾的相對路徑：

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            content = "<strong>Hello, Flask!</strong> on " + formatted_now)
    ```

1. 執行應用程式以查看結果，您會觀察到 `content` 值中的內嵌 HTML 並未轉譯成 HTML，因為範本化引擎 (Jinja) 會自動逸出 HTML 內容。 自動逸出可防止意外遭受插入式攻擊：開發人員經常會透過範本預留位置從一個頁面收集輸入，並使用該輸入作為另一個頁面的值。 逸出也可作為一種提醒，就是最好將 HTML 放在程式碼外。

    因此，請檢閱 *templates\index.html*，以在標記內針對每個資料片段包含不同的預留位置：

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
        </head>
        <body>
            <strong>{{ message }}</strong>{{ content }}
        </body>
    </html>
    ```

    接著，更新 `home` 函式來為所有預留位置提供值：

    ```python
    def home():
        now = datetime.now()
        formatted_now = now.strftime("%A, %d %B, %Y at %X")

        return render_template(
            "index.html",
            title = "Hello Flask",
            message = "Hello, Flask!",
            content = " on " + formatted_now)
    ```

1. 重新執行應用程式以查看正確轉譯的輸出。

    ![使用範本執行應用程式](media/flask/step02-result.png)

1. 將變更認可至原始檔控制，並視需要更新遠端存放庫，如[步驟 2-1](#commit-to-source-control)所述。

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>問題：頁面範本是否一定要位於個別檔案中？

回答：雖然範本通常會維護於個別的 HTML 檔案中，您也可以使用內嵌範本。 不過，還是建議您使用個別的檔案，以在標記和程式碼之間維持清楚的分隔。

### <a name="question-must-templates-use-the-html-file-extension"></a>問題：範本一定要使用 .html 副檔名嗎？

回答：頁面範本檔案的 *.html* 副檔名完全是選擇性的，因為您一律是在 `render_template` 函式的第一個引數中識別檔案的確切相對路徑。 不過，Visual Studio (與其他編輯器) 通常會針對 *.html* 檔案為您提供程式碼完成和語法色彩等功能，其重要性超過頁面範本不一定是 HTML 的事實。

實際上，當您在處理 Flask 專案時，Visual Studio 會自動偵測出您正在編輯的 HTML 檔案實際上是 Flask 範本，然後提供一些自動完成功能。 例如，當您開始鍵入 Flask 頁面範本註解 (`{#`) 時，Visual Studio 會自動提供結尾的 `#}` 字元。 [註解選取範圍] 與 [取消註解選取範圍] 命令 (位在 [編輯] > [進階] 功能表和工具列上) 也會使用範本註解，而不是 HTML 註解。

### <a name="question-can-templates-be-organized-into-further-subfolders"></a>問題：是否可以將範本組織成進一步的子資料夾？

回答：是，您可以使用子資料夾，然後在對 `render_template` 的呼叫中參考 *templates* 底下的相對路徑。 這樣做是一個可有效地為範本建立命名空間的絕佳方式。

## <a name="next-steps"></a>下一步

> [!div class="nextstepaction"]
> [提供靜態檔案、新增頁面，然後使用範本繼承](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)

## <a name="go-deeper"></a>深入了解

- [Flask 快速入門 - 轉譯範本](https://flask.palletsprojects.com/en/1.0.x/quickstart/#rendering-templates) \(英文\) (flask.pocoo.org)
- GitHub 上的教學課程原始程式碼：[Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask) \(英文\)
