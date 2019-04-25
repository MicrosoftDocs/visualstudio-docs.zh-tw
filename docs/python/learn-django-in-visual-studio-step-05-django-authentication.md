---
title: Visual Studio 中的了解 Django 教學課程步驟 5，驗證
titleSuffix: ''
description: 逐步解說 Visual Studio 專案內容中的 Django 基本知識，特別是 [Django Web 專案] 範本所提供的驗證功能。
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: bdc76b0a7b9d3f74da77b317faf31dae83706f04
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62957841"
---
# <a name="step-5-authenticate-users-in-django"></a>步驟 5：在 Django 中驗證使用者

**上一步：[使用完整的 Django Web 專案範本](learn-django-in-visual-studio-step-04-full-django-project-template.md)**

因為 Web 應用程式一般都需要驗證，所以 [Django Web 專案] 範本會包含基本的驗證流程。 (本教學課程步驟 6 中所討論的 [投票 Django Web 專案] 範本也包含相同的流程)。使用任何 Django 專案範本時，Visual Studio 會在 Django 專案的 *settings.py* 中包含驗證所需的所有模組。

在這個步驟中，您將了解：

> [!div class="checklist"]
> - 如何使用 Visual Studio 範本中所提供的驗證流程 (步驟 5-1)

## <a name="step-5-1-use-the-authentication-flow"></a>步驟 5-1：使用驗證流程

下列步驟會進行驗證流程，並說明所有涉及的專案部分：

1. 如果您尚未遵循專案根目錄之 *readme.html* 檔案中的指示來建立進階使用者 (系統管理員) 帳戶，請立即建立。

1. 使用 [偵錯] > [開始偵錯] (**F5**) 在 Visual Studio 中執行應用程式。 當應用程式出現在瀏覽器中時，觀察到瀏覽列的右上角出現 [登入]。

    ![Django Web 專案應用程式頁面上的登入控制項](media/django/step05-login-control.png)

1. 開啟 *templates/app/layout.html*，然後觀察到 `<div class="navbar ...>` 項目包含標籤 `{% include app/loginpartial.html %}`。 `{% include %}` 標籤會指示 Django 的範本化系統，以便在包含的範本中此位置提取所包含檔案的內容。

1. 開啟 *templates/app/loginpartial.html*，然後觀察到其如何搭配使用條件式標籤 `{% if user.is_authenticated %}` 及 `{% else %}` 標籤，以根據使用者是否已經驗證來轉譯不同的 UI 項目：

    ```html
    {% if user.is_authenticated %}
    <form id="logoutForm" action="/logout" method="post" class="navbar-right">
        {% csrf_token %}
        <ul class="nav navbar-nav navbar-right">
            <li><span class="navbar-brand">Hello {{ user.username }}!</span></li>
            <li><a href="javascript:document.getElementById('logoutForm').submit()">Log off</a></li>
        </ul>
    </form>

    {% else %}

    <ul class="nav navbar-nav navbar-right">
        <li><a href="{% url 'login' %}">Log in</a></li>
    </ul>

    {% endif %}
    ```

1. 由於您初次啟動應用程式時還沒有已驗證的使用者，所以此範本程式碼只會轉譯針對相對路徑 "login" 的 [登入] 連結。 如上節所示的 *urls.py* 中所指定，該路由會對應至 `django.contrib.auth.views.login` 檢視。 該檢視會收到下列資料：

    ```python
    {
        'template_name': 'app/login.html',
        'authentication_form': app.forms.BootstrapAuthenticationForm,
        'extra_context':
        {
            'title': 'Log in',
            'year': datetime.now().year,
        }
    }
    ```

    此處的 `template_name` 會識別登入頁面的範本，在此案例中為 *templates/app/login.html*。 `extra_context` 屬性會新增至提供給範本的預設內容資料。 最後，`authentication_form` 會指定要與登入搭配使用的表單類別；在範本中它會顯示為 `form` 物件。 預設值是 `AuthenticationForm` (來自 `django.contrib.auth.views`)；Visual Studio 專案範本會改為使用應用程式 *forms.py* 檔案中所定義的表單：

    ```python
    from django import forms
    from django.contrib.auth.forms import AuthenticationForm
    from django.utils.translation import ugettext_lazy as _

    class BootstrapAuthenticationForm(AuthenticationForm):
        """Authentication form which uses boostrap CSS."""
        username = forms.CharField(max_length=254,
                                   widget=forms.TextInput({
                                       'class': 'form-control',
                                       'placeholder': 'User name'}))
        password = forms.CharField(label=_("Password"),
                                   widget=forms.PasswordInput({
                                       'class': 'form-control',
                                       'placeholder':'Password'}))
    ```

    如您所見，此表單類別是衍生自 `AuthenticationForm`，並特別覆寫使用者名稱與密碼欄位，以新增預留位置文字。 Visual Studio 範本是在假設您想要自訂表單 (例如新增密碼強度驗證) 的前提下包括此明確程式碼。

1. 當您巡覽至登入頁面時，應用程式會轉譯 *login.html* 範本。 變數 `{{ form.username }}` 與 `{{ form.password }}` 會轉譯來自 `BootstrapAuthenticationForm` 的 `CharField` 表單。 還有一個可顯示驗證錯誤的內建區段，以及適用於社交登入的現成元素，如果您選擇新增那些服務的話。

    ```html
    {% extends "app/layout.html" %}

    {% block content %}

    <h2>{{ title }}</h2>
    <div class="row">
        <div class="col-md-8">
            <section id="loginForm">
                <form action="." method="post" class="form-horizontal">
                    {% csrf_token %}
                    <h4>Use a local account to log in.</h4>
                    <hr />
                    <div class="form-group">
                        <label for="id_username" class="col-md-2 control-label">User name</label>
                        <div class="col-md-10">
                            {{ form.username }}
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="id_password" class="col-md-2 control-label">Password</label>
                        <div class="col-md-10">
                            {{ form.password }}
                        </div>
                    </div>
                    <div class="form-group">
                        <div class="col-md-offset-2 col-md-10">
                            <input type="hidden" name="next" value="/" />
                            <input type="submit" value="Log in" class="btn btn-default" />
                        </div>
                    </div>
                    {% if form.errors %}
                    <p class="validation-summary-errors">Please enter a correct user name and password.</p>
                    {% endif %}
                </form>
            </section>
        </div>
        <div class="col-md-4">
            <section id="socialLoginForm"></section>
        </div>
    </div>

    {% endblock %}
    ```

1. 當您提交表單時，Django 會嘗試驗證您的認證 (例如進階使用者的認證)。 如果驗證失敗，您會留在目前的頁面上，但 `form.errors` 會設為 true。 如果驗證成功，Django 會瀏覽至 "next" 欄位中的相對 URL `<input type="hidden" name="next" value="/" />`，在此案例中為首頁 (`/`)。

1. 現在，當首頁再次轉譯時，`user.is_authenticated` 屬性在轉譯 *loginpartial.html* 範本時為 true。 因此，您會看見 **Hello (使用者)** 訊息和 **Log off**。 您可以在應用程式的其他部分使用 `user.is_authenticated` 來檢查驗證。

    ![Django Web 專案應用程式頁面上的 Hello 訊息與登出控制項](media/django/step05-logoff-control.png)

1. 若要檢查驗證的使用者是否被授權存取特定資源，您必須從您的資料庫擷取使用者特定權限。 如需詳細資訊，請參閱[使用 Django 驗證系統](https://docs.djangoproject.com/en/2.0/topics/auth/default/#permissions-and-authorization) (Django 文件)。

1. 其中進階使用者或系統管理員，皆被授權使用相對 URL "/admin/" 與 "/admin/doc/" 來存取內建的 Django 系統管理員介面。 若要啟用這些介面，請執行下列作業：

    1. 將 docutils Python 套件安裝到您的環境。 要這麼做的好方法是將 docutils 新增至 *requirements.txt* 檔案，然後在 [方案總管] 中，依序展開專案、[Python 環境] 節點，然後以滑鼠右鍵按一下您使用的環境，選取 [從 requirements.txt 安裝]。

    1. 開啟 Django 專案的 *urls.py*，然後移除下列項目的預設註解：

        ```python
        from django.conf.urls import include
        from django.contrib import admin
        admin.autodiscover()

        # ...
        urlpatterns = [
            # ...
            url(r'^admin/doc/', include('django.contrib.admindocs.urls')),
            url(r'^admin/', include(admin.site.urls)),
        ]
        ```

    1. 在 Django 專案的 *settings.py* 檔案中，巡覽至 `INSTALLED_APPS` 集合，並新增 `'django.contrib.admindocs'`。

    1. 當您重新啟動應用程式時，便可以巡覽至 "/admin/" 與 "/admin/doc/"，並執行如建立其他使用者帳戶的工作。

        ![Django 系統管理員介面](media/django/step05-administrator-interface.png)

1. 驗證流程的最後一部分就是登出。 如您在 *loginpartial.html* 中所見，[登出] 連結只會針對相對 URL "/login" 執行 POST，這是由內建檢視 `django.contrib.auth.views.logout` 所處理。 此檢視不會顯示任何 UI，而會直接巡覽至首頁 (如 "^logout$" 模式的 *urls.py* 中所示)。 如果您想要顯示登出頁面，請先如下所示變更 URL 模式，以新增 "template_name" 屬性並移除 "next_page" 屬性：

    ```python
    url(r'^logout$',
        django.contrib.auth.views.logout,
        {
            'template_name': 'app/loggedoff.html',
            # 'next_page': '/',
        },
        name='logout')
    ```

    然後，建立具有下列 (最少) 內容的 *templates/app/loggedoff.html*：

    ```html
    {% extends "app/layout.html" %}
    {% block content %}
    <h3>You have been logged off</h3>
    {% endblock %}
    ```

    結果如下所示：

    ![新增的登出頁面](media/django/step05-logged-off-page.png)

1. 當您全部完成時，請停止伺服器，並再次將變更認可至原始檔控制。

### <a name="question-what-is-the-purpose-of-the--csrftoken--tag-that-appears-in-the-form-elements"></a>問題：\<form\> 項目中出現的 {% csrf_token %} 標籤有什麼用途？

回答：`{% csrf_token %}` 標籤包含 Django 的內建[跨網站偽造要求 (csrf) 保護](https://docs.djangoproject.com/en/2.0/ref/csrf/) (Django 文件)。 您通常會將此標籤新增至任何涉及 POST、PUT 或 DELETE 要求方法的項目 (例如表單)。 然後，範本轉譯函式 (`render`) 會插入必要的保護。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [使用投票 Django Web 專案範本](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)

## <a name="go-deeper"></a>深入了解

- [Django 中的使用者驗證](https://docs.djangoproject.com/en/2.0/topics/auth/) \(英文\) (docs.djangoproject.com)
- GitHub 上的教學課程原始程式碼：[Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
