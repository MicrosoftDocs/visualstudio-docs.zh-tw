---
title: Visual Studio 中的了解 Django 教學課程步驟 3，靜態檔案和頁面
titleSuffix: ''
description: 逐步解說 Visual Studio 專案環境中的 Django 基本知識，特別示範如何提供靜態檔案、將頁面加入應用程式，以及使用範本繼承
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7aabfa91f7f6c6204919c4a06d2d3080b5174c5f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942577"
---
# <a name="step-3-serve-static-files-add-pages-and-use-template-inheritance-with-django-app"></a>步驟3：提供靜態檔案、新增頁面，以及搭配 Django 應用程式使用範本繼承

**上一個步驟：[使用檢視與頁面範本來建立 Django 應用程式](learn-django-in-visual-studio-step-02-create-an-app.md)**

在本教學課程的先前步驟中，您已學會如何建立具有單一獨立式 HTML 頁面的最小 Django 應用程式。 不過，現代化 Web 應用程式通常是由許多網頁所組成，並且利用 CSS 和 JavaScript 檔案等共用資源來提供一致的樣式和行為。

在這個步驟中，您將了解如何：

> [!div class="checklist"]
> - 使用 Visual Studio 項目範本，為可重複使用的程式碼 (步驟 3-1) 新增不同類型的檔案
> - 設定 Django 專案以提供靜態檔案 (步驟 3-2)
> - 將額外頁面加入應用程式 (步驟 3-3)
> - 使用範本繼承，以建立跨頁面使用的標題和瀏覽列 (步驟 3-4)

## <a name="step-3-1-become-familiar-with-item-templates"></a>步驟 3-1：熟悉項目範本

當您開發 Django 應用程式時，通常會加入許多 Python、HTML、CSS 和 JavaScript 檔案。 針對每一種檔案類型 (以及開發可能需要的其他檔案，例如 *web.config*)，Visual Studio 都提供方便您著手的 [項目範本](python-item-templates.md)。

若要查看可用的範本，請移至 [方案總管]，以滑鼠右鍵按一下您要建立項目的資料夾，選取 [加入] > [新項目]：

![Visual Studio 中的加入新項目對話方塊](media/django/step03-add-new-item-dialog.png)

若要使用範本，請選取所需的範本、指定檔案名稱，然後選取 [確定]。 以這種方式加入項目，會將檔案自動加入您的 Visual Studio 專案，並為原始檔控制標記變更。

### <a name="question-how-does-visual-studio-know-which-item-templates-to-offer"></a>問題：Visual Studio 如何知道應提供哪些項目範本？

回答：Visual Studio 專案檔 (*.pyproj*) 包含將它標示為 Python 專案的專案類型識別碼。 Visual Studio 會使用此類型的識別碼，以便只顯示適用於專案類型的項目範本。 如此一來，Visual Studio 便可為許多專案類型提供豐富的項目範本，而無須要求您每次都要查看整理範本。

## <a name="step-3-2-serve-static-files-from-your-app"></a>步驟 3-2：從您的應用程式提供靜態檔案

在使用 Python (使用任何架構) 建置的 Web 應用程式中，您的 Python 檔案一律在 Web 主機伺服器上執行，絕對不會傳輸到使用者的電腦。 不過，其他檔案 (例如 CSS 和 JavaScript) 則只由瀏覽器使用，因此主機伺服器只會以原樣來傳遞這些檔案。 這類檔案稱為「靜態」檔案，且 Django 可以自動傳遞這些檔案，而您無需撰寫任何程式碼。

Django 專案預設設定為從應用程式的 *static* 資料夾提供靜態檔案，這要歸功於 Django 專案 *settings.py* 中的這幾行設定：

```python
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/1.9/howto/static-files/

STATIC_URL = '/static/'

STATIC_ROOT = posixpath.join(*(BASE_DIR.split(os.path.sep) + ['static']))
```

您可以在 *static* 中使用偏好的任何資料夾結構來組織檔案，然後使用該資料夾內的相對路徑來參考檔案。 為了示範此流程，下列步驟會將 CSS 檔案新增至應用程式，然後在 *index.html* 範本中使用該樣式表：

1. 在 [方案總管] 中，以滑鼠右鍵按一下 Visual Studio 專案的 **HelloDjangoApp** 資料夾，選取 [新增] > [新增資料夾]，並將資料夾命名為 `static`。

1. 以滑鼠右鍵按一下 **static** 資料夾，並選取 [新增] > [新增項目]。 在出現的對話方塊中，選取 **樣式** 表單範本、為檔案命名 `site.css` ，然後選取 **[確定]**。 **site.css** 檔案會出現在專案中，並在編輯器中開啟。 您的資料夾結構應該與下列影像類似：

    ![方案總管中所顯示的靜態檔案結構](media/django/step03-static-file-structure.png)

1. 將 *site.css* 的內容取代為下列程式碼並儲存檔案：

    ```css
    .message {
        font-weight: 600;
        color: blue;
    }
    ```

1. 將應用程式的 *templates/HelloDjangoApp/index.html* 檔案的內容取代為下列程式碼，其中會將步驟 2 中所使用的 `<strong>` 項目取代為參考 `message` 樣式類別的 `<span>`。 以這種方式使用樣式類別，可讓您在設定元素的樣式時獲得更大彈性。 (若您在使用 VS 2017 15.7 及更舊版本時，尚未將 *index.html* 移至 *templates* 中的子資料夾內，請參閱步驟 2-4 中的 [範本命名空間](learn-django-in-visual-studio-step-02-create-an-app.md#template-namespacing)。)

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load staticfiles %} <!-- Instruct Django to load static files -->
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <span class="message">{{ message }}</span>{{ content }}
        </body>
    </html>
    ```

1. 執行專案，以觀察其結果。 完成時停止伺服器，並判斷是否認可您的變更至原始檔控制 (如 [步驟 2](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control) 中的說明)。

### <a name="question-what-is-the-purpose-of-the--load-staticfiles--tag"></a>問題：{% load staticfiles %} 標籤的用途是什麼？

答：需要有 `{% load staticfiles %}` 這一行，才能在 `<head>` 和 `<body>` 之類的元素中參考靜態檔案。 本節顯示的範例中，"staticfiles" 是指自訂 Django 範本標籤集，它可讓您使用 `{% static %}` 語法來參照靜態檔案。  如果沒有 `{% load staticfiles %}`，則在應用程式執行時會出現例外狀況。

### <a name="question-are-there-any-conventions-for-organizing-static-files"></a>問題：組織靜態檔案有任何慣例嗎？

回答：您可以依偏好將其他的 CSS、JavaScript 和 HTML 檔案新增至您的 *static* 資料夾。 組織靜態檔案的一般方式是建立名為 *fonts*、*scripts* 和 *content* 的子資料夾 (針對樣式表和任何其他檔案)。 在各種情況中，請記得要將那些資料夾包含在 `{% static %}` 參考中的檔案相對路徑。

### <a name="question-can-i-complete-the-same-task-without-using-the--load-staticfiles--tag"></a>問題：我是否可以在不使用 {% load staticfiles%} 標記的情況下完成相同的工作？

答：是的，您可以。

```html
<html>
    <head>
        <title>{{ title }}</title>
        <link rel="stylesheet" type="text/css" href="../../static/site.css" />
    </head>
    <body>
        <span class="message">{{ message }}</span>{{ content }}
    </body>
</html>
```

## <a name="step-3-3-add-a-page-to-the-app"></a>步驟 3-3：將頁面加入應用程式

將其他頁面加入應用程式意義如下：

- 加入定義檢視的 Python 函式。
- 加入網頁標記的範本。
- 將必要的路由新增至 Django 專案的 *urls.py* 檔案。

下列步驟會將 "About" (關於) 頁面加入 "HelloDjangoApp" ，並從首頁連結至該頁面：

1. 在 [方案總管] 中，以滑鼠右鍵按一下 **templates/HelloDjangoApp** 資料夾，選取 [新增][新增項目] > ，選取 [HTML 網頁] 項目範本，將檔案命名為 `about.html`，然後選取 [確定]。

    > [!Tip]
    > 如果 [新項目] 命令未出現在 [加入] 功能表上，請確認您已停止伺服器，這樣 Visual Studio 就會結束偵錯模式。

1. 將 *about.html* 的內容取代為下列標記 (您會在步驟 3-4 中將首頁的明確連結取代為簡單的導覽列)：

    ```html
    <html>
        <head>
            <title>{{ title }}</title>
            {% load staticfiles %}
            <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
        </head>
        <body>
            <div><a href="home">Home</a></div>
            {{ content }}
        </body>
    </html>
    ```

1. 開啟應用程式的 *views.py* 檔案，然後新增使用範本且名為 `about` 的函式：

    ```python
    def about(request):
        return render(
            request,
            "HelloDjangoApp/about.html",
            {
                'title' : "About HelloDjangoApp",
                'content' : "Example app page for Django."
            }
        )
    ```

1. 開啟 Django 專案的 *urls.py* 檔案，然後將下列這一行新增至 `urlPatterns` 陣列：

    ```python
    url(r'^about$', HelloDjangoApp.views.about, name='about'),
    ```

1. 開啟 *templates/HelloDjangoApp/index.html* 檔案，然後將下列這一行新增至 `<body>` 項目底下，以連結到 [About] \(關於\) 頁面 (同樣地，您會在步驟 3-4 中將此連結取代為導覽列)：

    ```html
    <div><a href="about">About</a></div>
    ```

1. 使用 **[**  >  **全部儲存**] 功能表命令來儲存所有檔案，或只按 **Ctrl** + **Shift** + **S**。 (技術上來說並不需要此步驟，因為在 Visual Studio 中執行專案會自動儲存檔案。 不過，知道有這個命令也很好！)

1. 執行專案以觀察結果並檢查頁面之間的瀏覽。 完成時，關閉伺服器。

### <a name="question-i-tried-using-index-for-the-link-to-the-home-page-but-it-didnt-work-why"></a>問題：我嘗試使用 "index" (索引) 於首頁連結，但無法運作。 為什麼？

答：雖然在 *views.py* 中的檢視函式的名稱是 `index`，但是 Django 專案中 *urls.py* 檔案的 URL 路由模式並不包含符合 "index" (索引) 字串的規則運算式。 若要符合該字串，您必須為 `^index$` 模式新增另一個項目。

如下一節所示，最好是在頁面範本中使用 `{% url '<pattern_name>' %}` 標籤來參考模式的 *name* (名稱)，在此情況下，Django 會為您建立適當的 URL。 例如，將 *about.html* 中的 `<div><a href="home">Home</a></div>` 取代為 `<div><a href="{% url 'index' %}">Home</a></div>`。 此處使用 'index' (索引) 得以運作是因為 *urls.py* 中的第一個 URL 模式事實上是名為 'index' (因為 `name='index'` 引數之故)。 您也可以使用 'home' (首頁) 來參考第二個模式。

## <a name="step-3-4-use-template-inheritance-to-create-a-header-and-nav-bar"></a>步驟 3-4：使用範本繼承來建立標題和瀏覽列

現代化 Web 應用程式通常使用品牌標題和導覽列來提供最重要的頁面連結、快顯功能表等等，而不會在每個頁面上提供明確的導覽連結。 不過，為了確保所有頁面上的標題和導覽列都相同，您應該不會想在每個頁面範本中重複相同的程式碼。 反之，您應該是在同一個地方定義所有頁面的共同部分。

Django 的範本化系統提供兩個方法，可跨多個範本重複使用特定元素：包含和繼承。

- 「包含」使用 `{% include <template_path> %}` 語法，在參考範本中的特定位置插入其他頁面範本。 如果您想要以動態方式變更程式碼中的路徑，也可以使用變數。 「包含」通常用在頁面主體，用來在頁面特定位置引進共用的範本。

- 「繼承」在頁面範本開頭使用`{% extends <template_path> %}`，以指定共用基底範本，以便參考範本並接著據以建置範本。 繼承通常用來定義共用版面配置、瀏覽列和應用程式頁面的其他結構，因此參考範本只需要加入或修改名為 *blocks* (區塊) 的基底範本特定區域。

在這兩種情況下，`<template_path>` 是相對於應用程式的 *templates* 資料夾 (也允許 `../` 或 `./`)。

基底範本使用 `{% block <block_name> %}` 和 `{% endblock %}` 標籤來描述區塊。 如果參考範本接著使用具有相同區塊名稱的標籤，則其區塊內容將覆寫基底範本的區塊內容。

下列步驟將示範繼承：

1. 在應用程式的 *templates/HelloDjangoApp* 資料夾中，建立稱為 *layout.html* 的新 HTML 檔案 (使用 [新增] > [新增項目] 操作功能表，或 [新增] > [HTML 網頁])，然後以下列標記取代其內容。 您可以看到此範本包含一個名為 "content" (內容) 的區塊，這是參考頁面必須全部取代的部分：

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8" />
        <title>{{ title }}</title>
        {% load staticfiles %}
        <link rel="stylesheet" type="text/css" href="{% static 'site.css' %}" />
    </head>

    <body>
        <div class="navbar">
           <a href="/" class="navbar-brand">Hello Django</a>
           <a href="{% url 'home' %}" class="navbar-item">Home</a>
           <a href="{% url 'about' %}" class="navbar-item">About</a>
        </div>

        <div class="body-content">
    {% block content %}{% endblock %}
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

1. 將 *templates/HelloDjangoApp/index.html* 修改成參考基底範本，並覆寫內容區塊。 如您所見，使用繼承會讓此範本變得更簡單：

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    <span class="message">{{ message }}</span>{{ content }}
    {% endblock %}
    ```

1. 將 *templates/HelloDjangoApp/about.html* 修改成亦參考基底範本，並覆寫內容區塊：

    ```html
    {% extends "HelloDjangoApp/layout.html" %}
    {% block content %}
    {{ content }}
    {% endblock %}
    ```

1. 執行伺服器，以觀察其結果。 完成時，關閉伺服器。

    ![顯示瀏覽列的執行中應用程式](media/django/step03-nav-bar.png)

1. 由於您對應用程式做了大幅變更，因此現在也是[認可您的變更至原始檔控制](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)的好時機。

## <a name="next-steps"></a>下一步

> [!div class="nextstepaction"]
> [使用完整的 Django Web 專案範本](learn-django-in-visual-studio-step-04-full-django-project-template.md)

## <a name="go-deeper"></a>深入了解

- [將 Web 應用程式部署至 Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [撰寫您的第一個 Django 應用程式，第 3 部分 (檢視)](https://docs.djangoproject.com/en/2.0/intro/tutorial03/) \(英文\) (docs.djangoproject.com)
- 如需了解更多 Django 範本的功能，例如控制流程，請參閱 [Django 範本語言](https://docs.djangoproject.com/en/2.0/ref/templates/language/) \(英文\) (docs.djangoproject.com)
- 如需使用 `{% url %}` 標籤的完整詳細資料，請參閱 [Django 範本的內建範本標籤和篩選參考](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/) \(英文\) (docs.djangoproject.com) 中的 [url](https://docs.djangoproject.com/en/2.0/ref/templates/builtins/#url) \(英文\)
- GitHub 上的教學課程原始程式碼：[Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
