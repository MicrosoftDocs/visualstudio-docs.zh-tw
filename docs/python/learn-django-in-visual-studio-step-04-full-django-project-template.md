---
title: Visual Studio 中的了解 Django 教學課程步驟 4，Web 專案範本
titleSuffix: ''
description: 逐步解說 Visual Studio 專案環境中的 Django 基本知識，尤其是 Django Web 專案範本提供的功能。
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 3c0a0f0f4e009d689a69e840b31281e65bc5a0e2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942551"
---
# <a name="step-4-use-the-full-django-web-project-template"></a>步驟 4：使用完整的 Django Web 專案範本

**上一個步驟：[提供靜態檔案、新增頁面，以及使用範本繼承](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)**

您已透過 Visual Studio 的「空白 Django Web 專案」範本來建置應用程式，因而探索 Django 的基本知識，現在就可以輕鬆地了解由「Django Web 專案」範本所產生的較完整應用程式。

現在在這個步驟中，您將要：

> [!div class="checklist"]
> - 使用「Django Web 專案」範本來建立更完整的 Django Web 應用程式，並檢查專案結構 (步驟 4-1)
> - 了解專案範本所建立的檢視和頁面範本，其中包含繼承自基底頁面範本及採用靜態 JavaScript 程式庫 (例如 jQuery 和 Bootstrap) 的三個頁面 (步驟 4-2)
> - 了解範本所提供的 URL 路由 (步驟 4-3)

範本也提供基本驗證，這會在步驟 5 中說明。

## <a name="step-4-1-create-a-project-from-the-template"></a>步驟 4-1：從範本建立專案

1. 在 Visual Studio 中，移至 **方案總管**，以滑鼠右鍵按一下本教學課程稍早建立的 **LearningDjango** 方案，然後選取 [**加入**  >  **新專案**]。  (或者，如果您想要使用新的方案，請 **選取 [** 檔案  >  **新增**  >  **專案**]。 ) 

1. 在 [新增專案] 對話方塊中，搜尋並選取 [Django Web 專案] 範本，接著呼叫 "DjangoWeb" 專案，然後選取 [確定]。

1. 由於該範本再次包含 *requirements.txt* 檔案，因此 Visual Studio 會詢問要在何處安裝這些相依性。 選擇 [安裝至虛擬環境] 選項，然後在 [新增虛擬環境] 對話方塊中，選取 [建立] 並接受預設值。

1. Visual Studio 設定好虛擬環境後，請遵循所顯示 *readme.html* 中的指示來建立 Django 進階使用者 (也就是系統管理員)。 只需以滑鼠右鍵按一下 Visual Studio 專案，然後選取 [ **Python**  >  **Django 建立超級使用者**] 命令，然後遵循提示。 請務必記下您的使用者名稱和密碼，因為當您執行應用程式的驗證功能時會用到。

1. 您可以在 [方案總管] 中的 **DjangoWeb** 專案上按一下滑鼠右鍵，然後選取 [設定為啟始專案]，即可將該專案設定為 Visual Studio 方案的預設專案。 以粗體字型顯示的起始專案，會在您啟動偵錯工具時執行。

    ![方案總管將 DjangoWeb 專案顯示為啟始專案](media/django/step04-second-project-in-solution-set-as-startup-project.png)

1. 選取 [ **Debug**  >  **開始調試**] (**F5**) 或使用工具列上的 [ **Web 服務器**] 按鈕來執行伺服器：

    ![Visual Studio 中的 [執行網頁伺服器] 工具列按鈕](media/django/run-web-server-toolbar-button.png)

1. 範本建立的應用程式有三個頁面，分別是 Home (首頁)、About (關於) 和 Contact (連絡)，您可以使用瀏覽列在它們之間來回瀏覽。 請花一兩分鐘的時間檢查應用程式的不同組件。 若要透過 [登入] 命令來驗證應用程式，請使用先前建立的進階使用者認證。

    ![Django Web 專案應用程式的完整瀏覽器檢視](media/django/step04-full-app-desktop-view.png)

1. 「Django Web 專案」範本所建立的應用程式使用 Bootstrap 回應式配置，以配合行動版型規格。 若要查看此回應性，請將瀏覽器調整為較窄的檢視，使內容以垂直方式轉譯，且瀏覽列會變為功能表圖示：

    ![Django Web 專案應用程式的行動 (窄) 檢視](media/django/step04-full-app-mobile-view.png)

1. 您可以讓這個應用程式繼續執行，在接下來的各節中都會用到它。

    如果您想停止應用程式並 [認可對原始檔控制所做的變更](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)，請先開啟 [Team Explorer] 中的 [變更] 頁面，接著在虛擬環境的資料夾 (可能是 **env**) 上按一下滑鼠右鍵，然後選取 [略過這些本機項目]。

### <a name="examine-what-the-template-creates"></a>檢查範本建立的項目

在最通用的情況下，「Django Web 專案」範本會建立以下結構：

- 專案根中的檔案：
  - *manage.py*：Django 系統管理公用程式。
  - *db.sqlite3*：預設 SQLite 資料庫。
  - *requirements.txt*：包含 Django 1.x 的相依性。
  - *readme.html*：建立專案後，會在 Visual Studio 中顯示的檔案。 如前一節中所述，請遵照此處的指示來建立應用程式的進階使用者 (系統管理員) 帳戶。
- *app* 資料夾包含所有應用程式檔案，包括檢視、模型、測試、表單、範本和靜態檔案 (請參閱步驟 4-2)。 您通常會重新命名此資料夾，以便使用更特定的應用程式名稱。
- *DjangoWeb* (Django project) 資料夾包含一般的 Django 專案檔： *\_ \_ init \_ \_ . .py*、 *settings.py*、 *urls.py* 和 *wsgi.py*。 藉由使用專案範本，便可針對應用程式和資料庫檔案設定好 *settings.py*，而且 *urls.py* 也會設定好所有應用程式頁面的路由，包括登入表單。

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>問題：Visual Studio 專案之間是否可以共用虛擬環境？

答：可以，不過這麼做的時候要注意到不同專案經過一段時間後可能會使用不同的套件。因此，共用的虛擬環境必須針對使用該虛擬環境的所有專案，包含所有相關的套件。

不過，若要使用現有的虛擬環境，請執行下列作業：

1. 在 Visual Studio 中提示安裝相依性時，請選取 [我將自行安裝] 選項。
1. 在 [方案總管] 中的 [Python 環境] 節點上按一下滑鼠右鍵，然後選取 [新增現有虛擬環境]。
1. 瀏覽並選取包含虛擬環境的資料夾，然後選取 [確定]。

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>步驟 4-2：了解專案範本所建立的檢視和頁面範本

如同您在執行專案時所見，應用程式包含三個檢視：Home (首頁)、About (關於) 和 Contact (連絡)。 這些檢視的程式碼可在 *app/views* 資料夾中找到。 每個檢視函式單純地使用範本和簡單字典物件的路徑來呼叫 `django.shortcuts.render`。 例如，About (關於) 頁面是由 `about` 函式所處理：

```python
def about(request):
    """Renders the about page."""
    assert isinstance(request, HttpRequest)
    return render(
        request,
        'app/about.html',
        {
            'title':'About',
            'message':'Your application description page.',
            'year':datetime.now().year,
        }
    )
```

範本位於應用程式的 *templates/app* 資料夾 (而且您通常會將 *app* 重新命名為實際應用程式的名稱)。 基底範本 *layout.html* 是最廣泛的範本。 它參考所有必要的靜態檔案 (JavaScript 和 CSS)、定義可供其他頁面複寫且名稱為 "content" (內容) 的區塊，以及提供名為 "scripts" (指令碼) 的區塊。 下列加註的摘錄來自 *layout.html*，顯示這些特定區域：

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Django Application</title>

    {% load staticfiles %}
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/bootstrap.min.css' %}" />
    <link rel="stylesheet" type="text/css" href="{% static 'app/content/site.css' %}" />
    <script src="{% static 'app/scripts/modernizr-2.6.2.js' %}"></script>
</head>
<body>
    <!-- Navbar omitted -->

    <div class="container body-content">

<!-- "content" block that pages are expected to override -->
{% block content %}{% endblock %}
        <hr/>
        <footer>
            <p>&copy; {{ year }} - My Django Application</p>
        </footer>
    </div>

<!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="{% static 'app/scripts/jquery-1.10.2.js' %}"></script>
    <script src="{% static 'app/scripts/bootstrap.js' %}"></script>
    <script src="{% static 'app/scripts/respond.js' %}"></script>
{% block scripts %}{% endblock %}

</body>
</html>
```

個別頁面範本 *about.html*、*contact.html* 和 *index.html*，每個都會擴充基底範本 *layout.html*。 *about.html* 最為簡單，並顯示 `{% extends %}` 和 `{% block content %}` 標籤：

```html
{% extends "app/layout.html" %}

{% block content %}

<h2>{{ title }}.</h2>
<h3>{{ message }}</h3>

<p>Use this area to provide additional information.</p>

{% endblock %}
```

*index.html* 和 *contact.html* 使用相同的結構，並在 "content" (內容) 區塊中提供較長的內容。

*templates/app* 資料夾中也有第四個頁面 *login.html*，以及 *loginpartial.html*，這是使用 `{% include %}` 帶入到 *layout.html*。 這些範本檔案會在步驟 5 有關驗證的部分中討論。

### <a name="question-can--block--and--endblock--be-indented-in-the-django-page-template"></a>問題：在 Django 頁面範本中，{% block %} 和 {% endblock %} 可以縮排嗎？

答：可以。例如，如果您為了讓區塊標籤在對應的父元素內對齊而縮排區塊標籤，Django 頁面範本依然能運作正常。 在 Visual Studio 專案範本所產生的頁面範本中，區塊標籤不會縮排，因此您可以清楚看到區塊標籤的位置。

## <a name="step-4-3-understand-the-url-routing-created-by-the-template"></a>步驟 4-3：了解範本所建立的 URL 路由

「Django Web 專案」範本所建立之 Django 專案的 *urls.py* 檔案包含下列程式碼：

```python
from datetime import datetime
from django.conf.urls import url
import django.contrib.auth.views

import app.forms
import app.views

urlpatterns = [
    url(r'^$', app.views.home, name='home'),
    url(r'^contact$', app.views.contact, name='contact'),
    url(r'^about$', app.views.about, name='about'),
    url(r'^login/$',
        django.contrib.auth.views.login,
        {
            'template_name': 'app/login.html',
            'authentication_form': app.forms.BootstrapAuthenticationForm,
            'extra_context':
            {
                'title': 'Log in',
                'year': datetime.now().year,
            }
        },
        name='login'),
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'next_page': '/',
        },
        name='logout'),
]
```

前三個 URL 模式直接對應至應用程式 *views.py* 檔案中的 `home`、`contact` 和 `about` 檢視。 另一方面，`^login/$` 和 `^logout$` 模式則使用內建的 Django 檢視，而不使用應用程式定義的檢視。 對 `url` 方法的呼叫也會包含自訂檢視的額外資料。 步驟 5 探索這些呼叫。

### <a name="question-in-the-project-i-created-why-does-the-about-url-pattern-uses-about-instead-of-about-as-shown-here"></a>問題：在我建立的專案中，為什麼 "about" (關於) URL 模式會使用 '^about'，而不是此處所顯示的 '^about$'？

答：規則運算式中少了尾端 '$' 只是許多專案範本版本中的單純疏忽。 URL 模式可以正常運作於名為 "about" (關於) 的頁面。不過，如果少了尾端 '$'，該 URL 模式也會符合 "about=django"、"about09876"、"aboutoflaughter" 等等的 URL。 此處顯示的尾端 '$' 是為了建立只符合 "about" 的 URL 模式。

## <a name="next-steps"></a>下一步

> [!div class="nextstepaction"]
> [在 Django 中驗證使用者](learn-django-in-visual-studio-step-05-django-authentication.md)

## <a name="go-deeper"></a>深入了解

- [將 Web 應用程式部署至 Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
- [撰寫您的第一個 Django 應用程式，第 4 部分 - 表單和一般檢視](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) \(英文\) (docs.djangoproject.com)
- GitHub 上的教學課程原始程式碼：[Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
