---
title: Visual Studio 中的了解 Flask 教學課程步驟 3，靜態檔案和頁面
titleSuffix: ''
description: 逐步解說 Visual Studio 專案內容中的 Flask 基本知識，特別是示範如何提供靜態檔案、將頁面新增至應用程式，以及使用範本繼承
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: d474236aca50a74b96689001a56e7d0701caae30
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942382"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance-with-flask-app"></a>步驟3：提供靜態檔案、新增頁面，以及搭配 Flask 應用程式使用範本繼承

**上一個步驟：[使用檢視與頁面範本來建立 Flask 應用程式](learn-flask-visual-studio-step-02-create-app.md)**

在本教學課程的先前步驟中，您已學會如何建立具有單一獨立式 HTML 頁面的精簡 Flask 應用程式。 不過，現代化 Web 應用程式通常是由許多網頁所組成，並且利用 CSS 和 JavaScript 檔案等共用資源來提供一致的樣式和行為。

在這個步驟中，您將了解如何：

> [!div class="checklist"]
> - 使用 Visual Studio 項目範本，為可重複使用的程式碼 (步驟 3-1) 新增不同類型的檔案
> - 從程式碼提供靜態檔案 (步驟 3-2，選擇性)
> - 將額外頁面加入應用程式 (步驟 3-3)
> - 使用範本繼承，以建立跨頁面使用的標題和瀏覽列 (步驟 3-4)

## <a name="step-3-1-become-familiar-with-item-templates"></a>步驟 3-1：熟悉項目範本

當您開發 Flask 應用程式時，通常會新增許多 Python、HTML、CSS 和 JavaScript 檔案。 針對每一種檔案類型 (以及開發可能需要的其他檔案，例如 *web.config*)，Visual Studio 都提供方便您著手的 [項目範本](python-item-templates.md)。

若要查看可用的範本，請移至 [方案總管]，以滑鼠右鍵按一下您要建立項目的資料夾，選取 [加入] > [新項目]：

![Visual Studio 中的加入新項目對話方塊](media/flask/step03-add-new-item-dialog.png)

若要使用範本，請選取所需的範本、指定檔案名稱，然後選取 [確定]。 以這種方式加入項目，會將檔案自動加入您的 Visual Studio 專案，並為原始檔控制標記變更。

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>問題：Visual Studio 如何知道應提供哪些項目範本？

回答：Visual Studio 專案檔 (*.pyproj*) 包含將它標示為 Python 專案的專案類型識別碼。 Visual Studio 會使用此類型的識別碼，以便只顯示適用於專案類型的項目範本。 如此一來，Visual Studio 便可為許多專案類型提供豐富的項目範本，而無須要求您每次都要查看整理範本。

## <a name="step-3-2-serve-static-files-from-your-app"></a>步驟 3-2：從您的應用程式提供靜態檔案

在使用 Python (使用任何架構) 建置的 Web 應用程式中，您的 Python 檔案一律在 Web 主機伺服器上執行，絕對不會傳輸到使用者的電腦。 不過，其他檔案 (例如 CSS 和 JavaScript) 則只由瀏覽器使用，因此主機伺服器只會以原樣來傳遞這些檔案。 這類檔案稱為「靜態」檔案，且 Flask 可以自動傳遞這些檔案，而無需您撰寫任何程式碼。 例如，在 HTML 檔案內，您可以直接使用專案中的相對路徑來參考靜態檔案。 此步驟的第一個部分會將 CSS 檔案新增到您現有的頁面範本。

需要從程式碼傳遞靜態檔案 (例如透過 API 端點實作) 時，Flask 會提供一個便利的方法，讓您使用名為 *static* 的資料夾 (在專案根目錄中) 中相對路徑來參考檔案。 此步驟的第二個部分會使用一個簡單的靜態資料檔來示範該方法。

在上述任一情況下，只要您喜歡，都可以將檔案組織在 *static* 下。

### <a name="use-a-static-file-in-a-template"></a>在範本中使用靜態檔案

1. 在 **方案總管** 中，以滑鼠右鍵按一下 Visual Studio 專案中的 [ **HelloFlask** ] 資料夾 **，選取 [新增**  >  **資料夾**]，並為資料夾命名 `static` 。

1. 以滑鼠右鍵按一下 **static** 資料夾，並選取 [新增] > [新增項目]。 在出現的對話方塊中，選取 **樣式** 表單範本、為檔案命名 `site.css` ，然後選取 **[確定]**。 **site.css** 檔案會出現在專案中，並在編輯器中開啟。 您的資料夾結構應該與下列影像類似：

    ![方案總管中所顯示的靜態檔案結構](media/flask/step03-static-file-structure.png)

1. 將 *site.css* 的內容取代為下列程式碼並儲存檔案：

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. 將應用程式 *templates/index.html* 檔案的內容取代為下列程式碼，其中會將步驟 2 中所使用的 `<strong>` 項目取代為參考 `message` 樣式類別的 `<span>`。 以這種方式使用樣式類別，可讓您在設定元素的樣式時獲得更大彈性。

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            <link rel="stylesheet" type="text/css" href="/static/site.css" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. 執行專案，以觀察其結果。 完成時，請停止應用程式，然後視需要將變更認可至原始檔控制 (如[步驟 2](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)所述)。

### <a name="serve-a-static-file-from-code"></a>從程式碼提供靜態檔案

Flask 提供一個稱為 `serve_static_file` 的函式，您可以從程式碼呼叫此函式來參考專案 *static* 資料夾內的任何檔案。 下列程序會建立一個簡單的 API 端點，傳回靜態資料檔案。

1. 如果您尚未建立 *static* 資料夾，請建立此資料夾：在 [方案總管] 中，於 Visual Studio 專案的 [HelloFlask] 資料夾上按一下滑鼠右鍵，選取 [新增] > [新增資料夾]，然後將資料夾命名為 `static`。

1. 在 *static* 資料夾中，使用下列內容 (無意義的範例資料) 來建立一個名為 *data.json* 的 JSON 資料檔：

    ```json
    {
        "01": {
            "note" : "Data is very simple because we're demonstrating only the mechanism."
        }
    }
    ```

1. 在 *views.py* 中，新增一個具有 /api/data 路由且使用 `send_static_file` 方法來傳回靜態資料檔的函式：

    ```python
    @app.route('/api/data')
    def get_data():
      return app.send_static_file('data.json')
    ```

1. 執行應用程式，然後瀏覽至 /api/data 端點以查看是否已傳回靜態檔案。 完成時，請停止應用程式。

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>問題：組織靜態檔案有任何慣例嗎？

回答：您可以依偏好將其他的 CSS、JavaScript 和 HTML 檔案新增至您的 *static* 資料夾。 組織靜態檔案的一般方式是建立名為 *fonts*、*scripts* 和 *content* 的子資料夾 (針對樣式表和任何其他檔案)。

### <a name="question-how-do-i-handle-url-variables-and-query-parameters-in-an-api"></a>問題：如何處理 API 中的 URL 變數和查詢參數？

答：請參閱步驟1-4 中的解答 [：問題： Flask 如何與變數 URL 路由和查詢參數搭配運作？](learn-flask-visual-studio-step-01-project-solution.md#qa-url-variables)

## <a name="step-3-3-add-a-page-to-the-app"></a>步驟 3-3：將頁面加入應用程式

將其他頁面加入應用程式意義如下：

- 加入定義檢視的 Python 函式。
- 加入網頁標記的範本。
- 將必要的路由新增至 Flask 專案的 *urls.py* 檔案。

下列步驟會將 [About] (關於) 頁面新增至 "HelloFlask" 專案，並從首頁連結至該頁面：

1. 在 [方案總管] 中，以滑鼠右鍵按一下 [templates] 資料夾，選取 [新增] > [新增項目]選取 [HTML Page] (HTML 頁面) 項目範本、將檔案命名為 `about.html`，然後選取 [確定]。

    > [!Tip]
    > 如果 [新增項目] 命令未出現在 [新增] 功能表上，請確定您已停止應用程式，如此 Visual Studio 才會結束偵錯模式。

1. 將 *about.html* 的內容取代為下列標記 (您會在步驟 3-4 中將首頁的明確連結取代為簡單的導覽列)：

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            <link rel="stylesheet" type="text/css" href="/static/site.css" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. 開啟應用程式的 *views.py* 檔案，然後新增使用範本且名為 `about` 的函式：

    ```python
    @app.route('/about')
    def about():
        return render_template(
            "about.html",
            title = "About HelloFlask",
            content = "Example app page for Flask.")
    ```

1. 開啟 *templates/index.html* 檔案，然後將下列這一行新增到 `<body>` 項目內，以連結到 [About] \(關於\) 頁面 (同樣地，您會在步驟 3-4 中以導覽列取代此連結)：

    ```html
    <div><a href="about">About</a></div>
    ```

1. 使用 **[**  >  **全部儲存**] 功能表命令來儲存所有檔案，或只按 **Ctrl** + **Shift** + **S**。 (技術上來說並不需要此步驟，因為在 Visual Studio 中執行專案會自動儲存檔案。 不過，知道有這個命令也很好！)

1. 執行專案以觀察結果並檢查頁面之間的瀏覽。 完成時，請停止應用程式。

### <a name="question-does-the-name-of-a-page-function-matter-to-flask"></a>問題：頁面函式的名稱對 Flask 來說是否重要？

回答：否，因為它是 `@app.route` 裝飾項目，用來判斷 Flask 為其呼叫函式以產生回應的 URL。 開發人員通常會讓函式名稱與路由相符，但這類相符並非必要。

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>步驟 3-4：使用範本繼承來建立標題和瀏覽列

現代化 Web 應用程式通常使用品牌標題和導覽列來提供最重要的頁面連結、快顯功能表等等，而不會在每個頁面上提供明確的導覽連結。 不過，為了確保所有頁面上的標題和導覽列都相同，您應該不會想在每個頁面範本中重複相同的程式碼。 反之，您應該是在同一個地方定義所有頁面的共同部分。

Flask 的範本化系統 (預設為 Jinja) 提供兩種方法，可跨多個範本重複使用特定元素：包含和繼承。

- 「包含」使用 `{% include <template_path> %}` 語法，在參考範本中的特定位置插入其他頁面範本。 如果您想要以動態方式變更程式碼中的路徑，也可以使用變數。 「包含」通常用在頁面主體，用來在頁面特定位置引進共用的範本。

- 「繼承」在頁面範本開頭使用`{% extends <template_path> %}`，以指定共用基底範本，以便參考範本並接著據以建置範本。 繼承通常用來定義共用版面配置、瀏覽列和應用程式頁面的其他結構，因此參考範本只需要加入或修改名為 *blocks* (區塊) 的基底範本特定區域。

在這兩種情況下，`<template_path>` 是相對於應用程式的 *templates* 資料夾 (也允許 `../` 或 `./`)。

基底範本描述使用 `{% block <block_name> %}` 和 `{% endblock %}` 標記區塊。 若之後參考範本再對同一個區塊名稱使用標籤，其區塊內容將會覆寫基底範本的區塊內容。

下列步驟將示範繼承：

1. 在應用程式的 *templates* 資料夾中，建立稱為 *layout.html* 的新 HTML 檔案 (使用 [新增] > [新增項目] 操作功能表，或 [新增] > [HTML 網頁])，然後以下列標記取代其內容。 您可以看到此範本包含一個名為 "content" (內容) 的區塊，這是參考頁面必須全部取代的部分：

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        <link rel="stylesheet" type="text/css" href="/static/site.css" />
    </head>

    <body>
        <div class="navbar">
            <a href="/" class="navbar-brand">Hello Flask</a>
            <a href="{{ url_for('home') }}" class="navbar-item">Home</a>
            <a href="{{ url_for('about') }}" class="navbar-item">About</a>
        </div>

        <div class="body-content">
            {% block content %}
            {% endblock %}
            <hr/>
            <footer>
                <p>&copy; 2018</p>
            </footer>
        </div>
    </body>
    </html>
    ```

1. 將下列樣式新增至應用程式的 *static/site.css* 檔案 (本逐步解說並非要示範回應式設計；這些樣式只是為了產生有趣的結果)：

    ```css
    .navbar {
        background-color: lightslategray;
        font-size: 1em;
        font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
        color: white;
        padding: 8px 5px 8px 5px;
    }

    .navbar a {
        text-decoration: none;
        color: inherit;
    }

    .navbar-brand {
        font-size: 1.2em;
        font-weight: 600;
    }

    .navbar-item {
        font-variant: small-caps;
        margin-left: 30px;
    }

    .body-content {
        padding: 5px;
        font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    ```

1. 將 *templates/index.html* 修改成參考基底範本，並覆寫內容區塊。 如您所見，使用繼承會讓此範本變得更簡單：

    ```html
    {% extends "layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. 將 *templates/about.html* 修改成亦參考基底範本，並覆寫內容區塊：

    ```html
    {% extends "layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. 執行伺服器，以觀察其結果。 完成時，關閉伺服器。

    ![顯示瀏覽列的執行中應用程式](media/flask/step03-nav-bar.png)

1. 由於您對應用程式做了大幅變更，因此現在也是[將變更認可至原始檔控制](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)的好時機。

## <a name="next-steps"></a>下一步

> [!div class="nextstepaction"]
> [使用完整的 Flask Web 專案範本](learn-flask-visual-studio-step-04-full-flask-project-template.md)

## <a name="go-deeper"></a>深入了解

- [將 Web 應用程式部署至 Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- 如需了解更多 Jinja 範本的功能 (例如控制流程)，請參閱 [Jinja 範本設計工具文件](http://jinja.palletsprojects.com/en/2.10.x/templates/) \(英文\) (jinja.pocoo.org)
- 如需有關使用 `url_for`的詳細資料，請參閱 Flask 應用程式物件文件內的 [url_for](https://flask.palletsprojects.com/en/1.0.x/api/#flask.url_for)(英文\) (flask.pocoo.org)
- GitHub 上的教學課程原始程式碼：[Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask) \(英文\)
