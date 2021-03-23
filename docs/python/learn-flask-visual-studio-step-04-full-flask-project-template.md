---
title: Visual Studio 中的了解 Flask 教學課程步驟 4，Web 專案範本
titleSuffix: ''
description: 逐步解說 Visual Studio 專案內容中的 Flask 基本知識，特別是「Flask Web 專案」和「Flask/Jade Web 專案」範本所提供的功能。
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7926a7983e43545ad47e8bc975f051821c108c18
ms.sourcegitcommit: f1dff6c4532c43b0444aa12ea57e90bb7dba6fba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2021
ms.locfileid: "104806000"
---
# <a name="step-4-use-the-full-flask-web-project-template"></a>步驟 4：使用完整的 Flask Web 專案範本

**上一個步驟：[提供靜態檔案、新增頁面，以及使用範本繼承](learn-flask-visual-studio-step-03-serve-static-files-add-pages.md)**

既然您已透過利用 Visual Studio 的「空白 Flask 應用程式專案」範本來建置應用程式以探索 Flask 的基本知識，現在便可輕鬆了解「Flask Web 專案」範本所產生更完整應用程式。

現在在這個步驟中，您將要：

> [!div class="checklist"]
> - 使用「Flask Web 專案」範本來建立更完整的 Flask Web 應用程式，並檢查專案結構 (步驟 4-1)
> - 了解專案範本所建立的檢視和頁面範本，其中包含繼承自基底頁面範本及採用靜態 JavaScript 程式庫 (例如 jQuery 和 Bootstrap) 的三個頁面 (步驟 4-2)
> - 了解範本所提供的 URL 路由 (步驟 4-3)

本文也適用於「Flask/Jade Web 專案」範本，此範本會使用 Jade (而非 Jinja) 範本化引擎來產生與「Flask Web 專案」的應用程式相同的應用程式。 本文結尾包含額外的詳細資料。

## <a name="step-4-1-create-a-project-from-the-template"></a>步驟 4-1：從範本建立專案

1. 在 Visual Studio 中，移至 **方案總管**，以滑鼠右鍵按一下本教學課程稍早建立的 **LearningFlask** 方案，然後選取 [**加入**  >  **新專案**]。  (或者，如果您想要使用新的方案，請 **選取 [** 檔案  >  **新增**  >  **專案**]。 ) 

1. 在 [新增專案] 對話方塊中，搜尋並選取 [ **Flask Web 專案** ] 範本，呼叫 "FlaskWeb" 專案，然後選取 **[確定]**。

1. 由於該範本再次包含 *requirements.txt* 檔案，因此 Visual Studio 會詢問要在何處安裝這些相依性。 選擇 [安裝至虛擬環境] 選項，然後在 [新增虛擬環境] 對話方塊中，選取 [建立] 並接受預設值。

1. 一旦 Visual Studio 完成虛擬環境的設定之後，請將 **FlaskWeb** 專案設定為 Visual Studio 方案的預設專案，方法是以滑鼠右鍵按一下 **方案總管** 中的專案，然後選取 [ **設定為啟始專案**]。 以粗體字型顯示的起始專案，會在您啟動偵錯工具時執行。

    ![將 FlaskWeb 專案顯示為啟始專案的 [方案總管]](media/flask/step04-second-project-in-solution-set-as-startup-project.png)

1. 選取 [ **Debug**  >  **開始調試**] (**F5**) 或使用工具列上的 [ **Web 服務器**] 按鈕來執行伺服器：

    ![Visual Studio 中的 [執行網頁伺服器] 工具列按鈕](media/flask/run-web-server-toolbar-button.png)

1. 範本建立的應用程式有三個頁面，分別是 Home (首頁)、About (關於) 和 Contact (連絡)，您可以使用瀏覽列在它們之間來回瀏覽。 請花一兩分鐘的時間檢查應用程式的不同組件。 若要透過 [登入] 命令來驗證應用程式，請使用先前建立的進階使用者認證。

    ![Flask Web 專案應用程式的完整瀏覽器檢視](media/flask/step04-full-app-desktop-view.png)

1. 「Flask Web 專案」範本所建立的應用程式會針對容納行動版型規格的回應式配置使用 Bootstrap。 若要查看此回應性，請將瀏覽器調整為較窄的檢視，使內容以垂直方式轉譯，且瀏覽列會變為功能表圖示：

    ![Flask Web 專案應用程式的行動 (窄) 檢視](media/flask/step04-full-app-mobile-view.png)

1. 您可以讓這個應用程式繼續執行，在接下來的各節中都會用到它。

    如果您想停止應用程式並 [認可對原始檔控制所做的變更](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)，請先開啟 [Team Explorer] 中的 [變更] 頁面，接著在虛擬環境的資料夾 (可能是 **env**) 上按一下滑鼠右鍵，然後選取 [略過這些本機項目]。

### <a name="examine-what-the-template-creates"></a>檢查範本建立的項目

「Flask Web 專案」範本會建立下面的結構。 這些內容與您在先前步驟中建立的內容非常相似。 差異在於「Flask Web 專案」範本的 *static* 資料夾有較多結構，因為它包含用於回應式設計的 jQuery 和 Bootstrap。 此範本也會新增 [Contact] \(連絡人\) 頁面。 整體說來，如果您已依照本教學課程中先前的步驟進行操作，應該會熟悉來自此範本的所有內容。

- 專案根中的檔案：
  - *runserver.py*：可在開發伺服器上執行應用程式的指令碼。
  - *requirements.txt*：包含 Flask 0.x 的相依性。
- *FlaskWeb* 資料夾包含所有應用程式檔案：
  - init.py 會將應用程式程式碼標示為 Python 模組、建立 Flask 物件，以及匯入應用程式的視圖。 *\_ \_ \_ \_*
  - *views.py* 包含用以轉譯頁面的程式碼。
  - *static* 資料夾包含名為 *content* (CSS 檔案)、*fonts* (字型檔案) 及 *scripts* (JavaScript 檔案) 的子資料夾。
  - *templates* 資料夾針對每個擴充 *layout.html* 的特定頁面，包含 *layout.html* 基底範本，以及 *about.html*、*contact.html* 和 *index.html*。

### <a name="question-is-it-possible-to-share-a-virtual-environment-between-visual-studio-projects"></a>問題：Visual Studio 專案之間是否可以共用虛擬環境？

答：可以，不過這麼做的時候要注意到不同專案經過一段時間後可能會使用不同的套件。因此，共用的虛擬環境必須針對使用該虛擬環境的所有專案，包含所有相關的套件。

不過，若要使用現有的虛擬環境，請執行下列作業：

1. 在 Visual Studio 中提示安裝相依性時，請選取 [我將自行安裝] 選項。
1. 在 [方案總管] 中的 [Python 環境] 節點上按一下滑鼠右鍵，然後選取 [新增現有虛擬環境]。
1. 瀏覽並選取包含虛擬環境的資料夾，然後選取 [確定]。

## <a name="step-4-2-understand-the-views-and-page-templates-created-by-the-project-template"></a>步驟 4-2：了解專案範本所建立的檢視和頁面範本

如同您在執行專案時所見，應用程式包含三個檢視：Home (首頁)、About (關於) 和 Contact (連絡)。 這些檢視的程式碼可在 *FlaskWeb/views.py* 中找到。 每個檢視函式在呼叫 `flask.render_template` 時，會單純地使用範本路徑與可變引數清單以提供值給範本。 例如，[About] \(關於\) 頁面會由 `about` 函式處理 (其裝飾項目會提供 URL 路由)：

```python
@app.route('/about')
def about():
    """Renders the about page."""
    return render_template(
        'about.html',
        title='About',
        year=datetime.now().year,
        message='Your application description page.'
    )
```

`home` 和 `contact` 函式幾乎相同，具有相同裝飾項目和些微不同的引數。

範本會位於應用程式的 *templates* 資料夾中。 基底範本 *layout.html* 是最廣泛的範本。 它參考所有必要的靜態檔案 (JavaScript 和 CSS)、定義可供其他頁面複寫且名稱為 "content" (內容) 的區塊，以及提供名為 "scripts" (指令碼) 的區塊。 下列加註的摘錄來自 *layout.html*，顯示這些特定區域：

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />

    <!-- Define a viewport for Bootstrap's responsive rendering -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ title }} - My Flask Application</title>

    <link rel="stylesheet" type="text/css" href="/static/content/bootstrap.min.css" />
    <link rel="stylesheet" type="text/css" href="/static/content/site.css" />
    <script src="/static/scripts/modernizr-2.6.2.js"></script>
</head>

<body>
    <!-- Navbar omitted -->

    <div class="container body-content">
        <!-- "content" block that pages are expected to override -->
        {% block content %}{% endblock %}
        <hr />
        <footer>
            <p>&copy; {{ year }} - My Flask Application</p>
        </footer>
    </div>

    <!-- Additional scripts; use the "scripts" block to add page-specific scripts.  -->
    <script src="/static/scripts/jquery-1.10.2.js"></script>
    <script src="/static/scripts/bootstrap.js"></script>
    <script src="/static/scripts/respond.js"></script>
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

## <a name="the-flaskjade-web-project-template"></a>Flask/Jade Web 專案範本

如本文開頭所述，Visual Studio 提供「Flask/Jade Web 專案」範本，此範本所建立的應用程式會與「Flask Web 專案」所產生的應用程式看起來完全相同。 主要的差異在於，它使用 Jade 範本化引擎，這是 Jinja 的延伸模組，能夠以更簡潔的語言實作相同的概念。 例如，具體而言，Jade 使用關鍵字，而不是包含在 {% %} 分隔符號中的標記，並可讓您使用關鍵字來參考 CSS 樣式和 HTML 元素。

為了啟用 Jade，專案範本會先在 *requirements.txt* 中包含 pyjade 套件。

應用程式的 *\_ \_ init \_ \_ . .py* 檔案包含一行

```python
app.jinja_env.add_extension('pyjade.ext.jinja.PyJadeExtension')
```

在 *templates* 資料夾中，您會看到 *.jade* 檔案而不是 *.html* 範本，而 *views.py* 中的檢視會在其對 `flask.render_template` 的呼叫中參考這些檔案。 除此之外，檢視程式碼都相同。

開啟其中一個 *.jade* 檔案時，您將可看到以更簡潔方式表達的範本。 例如，以下是「Flask/Jade Web 專案」所建立 *templates/layout.jade* 的內容：

```jade
doctype html
html
  head
    meta(charset='utf-8')
    meta(name='viewport', content='width=device-width, initial-scale=1.0')
    title #{title} - My Flask/Jade Application
    link(rel='stylesheet', type='text/css', href='/static/content/bootstrap.min.css')
    link(rel='stylesheet', type='text/css', href='/static/content/site.css')
    script(src='/static/scripts/modernizr-2.6.2.js')
  body
    .navbar.navbar-inverse.navbar-fixed-top
      .container
        .navbar-header
          button.navbar-toggle(type='button', data-toggle='collapse', data-target='.navbar-collapse')
            span.icon-bar
            span.icon-bar
            span.icon-bar
          a.navbar-brand(href='/') Application name
        .navbar-collapse.collapse
          ul.nav.navbar-nav
            li
              a(href='/') Home
            li
              a(href='/about') About
            li
              a(href='/contact') Contact
    .container.body-content
      block content
      hr
      footer
        p &copy; #{year} - My Flask/Jade Application

    script(src='/static/scripts/jquery-1.10.2.js')
    script(src='/static/scripts/bootstrap.js')
    script(src='/static/scripts/respond.js')

    block scripts
```

而以下是 *templates/about.jade* 的內容，其中顯示使用 `#{ <name>}` 來作為預留位置：

```jade
extends layout

block content
  h2 #{title}.
  h3 #{message}
  p Use this area to provide additional information.
```

請隨意進行 Jinja 和 Jade 語法實驗，以了解哪個語法最適合您。

## <a name="next-steps"></a>下一步

::: moniker range="vs-2017"
- [投票 Flask Web 專案範本](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md)
::: moniker-end

::: moniker range=">=vs-2019"
> [!Note]
> 如果您一直在致力於為本教學課程中的原始檔控制，研究出自己的 Visual Studio 方案，現在是另一次做出貢獻的好機會。 您的方案應與 GitHub 上的教學課程原始程式碼相吻合：[Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)。

您現在已探索完 Visual Studio 中的「空白 Flask Web 專案」、「Flask[/Jade] Web 專案」及「投票 Flask[/Jade] Web 專案」範本的全部內容。 您已了解 Flask 的所有基本知識 (例如檢視、範本及路由)，也了解了如何使用支援資料存放區。 現在，您應該能夠利用所需的任何檢視和模型，開始建立自己的 Web 應用程式。

在開發電腦上執行 Web 應用程式，只是開放客戶使用應用程式過程中的一個環結而已。 接下來的步驟可能包括下列的事項：

- 將 Web 應用程式部署到生產伺服器，例如 Azure App Service。 請參閱[發佈至 Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)。

- 新增使用另一個生產環境層級資料存放區 (例如 PostgreSQL、MySQL 及 SQL Server；這些全都可以裝載在 Azure 上) 的存放庫實作。 您也可以使用 [Azure SDK for Python](/azure/python/) 來除了搭配 Cosmos DB 運作之外，也可以搭配 Azure 儲存體服務 (例如資料表和 Blob) 運作。

- 在 Azure DevOps 此類的服務上設定持續整合/持續部署管線。 除了操作原始檔控制 (透過 Azure Repos、GitHub 或其他位置)，您可以設定 Azure DevOps 專案來自動執行單元測試作為發行必要條件，另外也請設定管線來部署至預備伺服器，以便進行傳統測試，之後再部署至生產環境伺服器中。 此外，Azure DevOps 還會與 App Insights 等監視解決方案整合，並使用敏捷式規劃工具來關閉整個週期。 如需詳細資訊，請參閱[使用 Azure DevOps 專案建立 Python 的 CI/CD 管線](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true)，以及一般的[Azure DevOps 文件](/azure/devops/?view=vsts&preserve-view=true)。
::: moniker-end

## <a name="go-deeper"></a>深入了解

- [撰寫您的第一個 Flask 應用程式，第 4 部分 - 表單和一般檢視](https://docs.djangoproject.com/en/2.0/intro/tutorial04/) \(英文\) (docs.djangoproject.com)
- [Jade 在 GitHub (檔) ](https://github.com/liuliqiang/pyjade) (github.com) 
- GitHub 上的教學課程原始程式碼：[Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask) \(英文\)
