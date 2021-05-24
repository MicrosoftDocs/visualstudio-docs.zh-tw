---
title: Visual Studio 步驟2、視圖和頁面範本中的學習 Django 教學課程
titleSuffix: ''
description: 逐步解說 Visual Studio 專案內容中的 Django 基本知識，特別是建立應用程式及使用檢視與範本的步驟。
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18, SEO-VS-2020
ms.workload:
- python
- data-science
ms.openlocfilehash: 196b15dff25681a23c05118a02f19109e09e3959
ms.sourcegitcommit: 5fe2462ffc33c7ece9cf3a179fb598354c916e1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2021
ms.locfileid: "110320468"
---
# <a name="step-2-create-a-django-app-with-views-and-page-templates"></a>步驟 2：使用檢視與頁面範本建立 Django 應用程式

**上一個步驟：[建立 Visual Studio 專案和解決方案](learn-django-in-visual-studio-step-01-project-and-solution.md)**

目前，您的 Visual Studio 專案中只有 Django *專案* 的網站層級元件，該專案可執行一或多個 Django *應用程式*。 下一個步驟是建立您第一個具有單一網頁的應用程式。

在這個步驟中，您現在將了解如何：

> [!div class="checklist"]
> - 建立具有單一網頁的 Django 應用程式 (步驟 2-1)
> - 從 Django 專案執行應用程式 (步驟 2-2)
> - 使用 HTML 轉譯檢視 (步驟 2-3)
> - 使用 Django 頁面範本轉譯檢視 (步驟 2-4)

## <a name="step-2-1-create-an-app-with-a-default-structure"></a>步驟 2-1：建立具有預設結構的應用程式

Django 應用程式是個別的 Python 套件，其中包含具特定用途的相關檔案集。 Django 專案可包含任意數目的應用程式，這反映出 Web 主機可從單一網域名稱提供任意數目的個別進入點。 例如，針對 contoso.com 網域的 Django 專案可能包含三個應用程式，分別用於 `www.contoso.com`、support.contoso.com 及 docs.contoso.com。 在此情況下，Django 專案會處理網站層級 URL 路由與設定 (於其 *urls.py* 與 *settings.py* 檔案中)，同時每個應用程式都會透過其內部路由、檢視、模型、靜態檔案及系統管理介面，擁有屬於自己的獨特樣式與行為。

Django 應用程式通常會以一組標準的檔案作為開始。 Visual Studio 提供項目範本以初始化 Django 專案內的 Django 應用程式，並提供具相同用途的整合式功能表命令：

- 範本：在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [加入] > [新項目]。 在 [ **加入新專案** ] 對話方塊中，選取 [ **Django 1.9 應用程式** ] 範本，在 [ **名稱** ] 欄位中指定應用程式名稱，然後選取 **[確定]**。

- 整合式命令：在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [加入] > [Django 應用程式]。 此命令會提示您輸入名稱，並建立 Django 1.9 應用程式。

    ![新增 Django 應用程式的功能表命令](media/django/step02-add-django-app-command.png)

使用任一種方法來建立名為 "HelloDjangoApp" 的應用程式。 結果是專案中會出現具有該名稱的資料夾，並包含下表所述的項目。

![[方案總管] 中的 Django 應用程式檔案](media/django/step02-django-app-in-solution-explorer.png)

::: moniker range="vs-2017"
| 項目 | 描述 |
| --- | --- |
| **\_\_\_ \_ .py** | 此檔案會將應用程式識別為套件。 |
| **遷移** | Django 儲存指令碼的資料夾，這些指令碼會更新資料庫以配合對模型所做的變更。 接著，Django 的移轉工具會對任何舊版資料庫套用必要的變更，以使它符合目前的模型。 透過使用移轉，您可以專注於模型上，並讓 Django 處理基礎資料庫結構描述。 步驟6會討論遷移;目前，該資料夾只會包含 *\_ \_ \_ \_ .py* 檔案， (表示該資料夾定義自己的 Python 套件) 。 |
| **templates** | Django 頁面範本的資料夾，在與應用程式名稱相符的資料夾內包含單一檔案 *index.html*。  (在 Visual Studio 2017 15.7 和更早版本中，檔案會直接包含在 *範本* 中，而步驟2-4 則會指示您建立子資料夾。 ) 範本是可在其中新增資訊以動態轉譯頁面的 HTML 區塊。 頁面範本「變數」(例如 *index.html* 中的 `{{ content }}`) 是動態值的預留位置，如本文稍後所述 (步驟 2)。 Django 應用程式通常會將其範本置於名稱與應用程式名稱相符的子資料夾中，來為範本建立命名空間。 |
| **admin.py** | 在其中擴充應用程式系統管理介面的 Python 檔案 (請參閱步驟 6)，用來植入和編輯資料庫中的資料。 此檔案一開始只包含陳述式 `from django.contrib import admin`。 根據預設，Django 是透過 Django 專案中的 *settings.py* 檔案來包含標準系統管理介面，您可以藉由取消註解 *urls.py* 中的現有項目來開啟它。 |
| **apps.py** | Python 檔案，定義應用程式的設定類別 (請參閱本表後面的內容)。 |
| **models.py** | 模型是由函式識別的資料物件，檢視會透過它和應用程式基礎資料庫互動 (請參閱步驟 6)。 Django 提供資料庫連線層，使應用程式本身不需要處理那些詳細資料。 *models.py* 檔案是建立模型的預設位置，而且一開始只包含陳述式 `from django.db import models`。 |
| **tests.py** | Python 檔案，包含單元測試的基本結構。 |
| **views.py** | 檢視就是一般所認知的網頁，會接收 HTTP 要求並傳回 HTTP 回應。 檢視通常會轉譯成網頁瀏覽器知道如何顯示的 HTML，但檢視不一定需要顯示出來 (例如以中繼形式呈現)。 檢視是由負責轉譯 HTML 以傳送至瀏覽器的 Python 函式所定義。 *views.py* 檔案是建立檢視的預設位置，而且一開始只包含陳述式 `from django.shortcuts import render`。 |
::: moniker-end

::: moniker range=">=vs-2019"
| 項目 | 描述 |
| --- | --- |
| **\_\_\_ \_ .py** | 此檔案會將應用程式識別為套件。 |
| **遷移** | Django 儲存指令碼的資料夾，這些指令碼會更新資料庫以配合對模型所做的變更。 接著，Django 的移轉工具會對任何舊版資料庫套用必要的變更，以使它符合目前的模型。 透過使用移轉，您可以專注於模型上，並讓 Django 處理基礎資料庫結構描述。 [Django 檔](https://docs.djangoproject.com/en/3.2/topics/migrations/)中會討論遷移;目前，該資料夾只會包含 *\_ \_ \_ \_ .py* 檔案， (表示該資料夾定義自己的 Python 套件) 。 |
| **templates** | Django 頁面範本的資料夾，在與應用程式名稱相符的資料夾內包含單一檔案 *index.html*。  (在 Visual Studio 2017 15.7 和更早版本中，檔案會直接包含在 *範本* 中，而步驟2-4 則會指示您建立子資料夾。 ) 範本是可在其中新增資訊以動態轉譯頁面的 HTML 區塊。 頁面範本「變數」(例如 *index.html* 中的 `{{ content }}`) 是動態值的預留位置，如本文稍後所述 (步驟 2)。 Django 應用程式通常會將其範本置於名稱與應用程式名稱相符的子資料夾中，來為範本建立命名空間。 |
| **admin.py** | Python 檔案，您可以在其中擴充應用程式的系統管理介面，用來植入和編輯資料庫中的資料。 此檔案一開始只包含陳述式 `from django.contrib import admin`。 根據預設，Django 是透過 Django 專案中的 *settings.py* 檔案來包含標準系統管理介面，您可以藉由取消註解 *urls.py* 中的現有項目來開啟它。 |
| **apps.py** | Python 檔案，定義應用程式的設定類別 (請參閱本表後面的內容)。 |
| **models.py** | 模型是由函式識別的資料物件，可透過這些資料物件和應用程式的基礎資料庫進行互動。 Django 提供資料庫連線層，使應用程式本身不需要處理那些詳細資料。 *models.py* 檔案是建立模型的預設位置，而且一開始只包含陳述式 `from django.db import models`。 |
| **tests.py** | Python 檔案，包含單元測試的基本結構。 |
| **views.py** | 檢視就是一般所認知的網頁，會接收 HTTP 要求並傳回 HTTP 回應。 檢視通常會轉譯成網頁瀏覽器知道如何顯示的 HTML，但檢視不一定需要顯示出來 (例如以中繼形式呈現)。 檢視是由負責轉譯 HTML 以傳送至瀏覽器的 Python 函式所定義。 *views.py* 檔案是建立檢視的預設位置，而且一開始只包含陳述式 `from django.shortcuts import render`。 |
::: moniker-end

使用 "HelloDjangoApp" 名稱時， *apps.py* 的內容會如下所示：

```python
from django.apps import AppConfig

class HelloDjangoAppConfig(AppConfig):
    name = 'HelloDjango'
```

### <a name="question-is-creating-a-django-app-in-visual-studio-any-different-from-creating-an-app-on-the-command-line"></a>問題：在 Visual Studio 中建立 Django 應用程式，和在命令列上建立應用程式有何不同？

答：執行 **add**  >  **Django app** 命令或使用  >  [**新增專案**] 搭配 Django 應用程式範本，會產生與 Django 命令相同的檔案 `manage.py startapp <app_name>` 。 在 Visual Studio 中建立應用程式的優點，在於應用程式資料夾與其所有檔案都會自動整合至專案。 您可以使用相同的 Visual Studio 命令，在專案中建立任何數目的應用程式。

## <a name="step-2-2-run-the-app-from-the-django-project"></a>步驟 2-2：從 Django 專案執行應用程式

此時，如果您 Visual Studio (使用工具列按鈕或 **Debug**  >  **開始調試**) ，再次執行專案，您仍會看到預設頁面。 之所以未出現任何應用程式內容，是因為您必須定義應用程式特定頁面，並將應用程式新增至 Django 專案：

1. 在 *HelloDjangoApp* 資料夾中，修改 *views.py* 以符合下面的程式碼，這會定義名為 "index" 的檢視：

    ```python
    from django.shortcuts import render
    from django.http import HttpResponse

    def index(request):
        return HttpResponse("Hello, Django!")
    ```

1. 在 *BasicProject* 資料夾 (於步驟 1 建立) 中，修改 *urls.py* 以至少符合下列程式碼 (您可以視需要保留指示性註解)：

    ```python
    from django.conf.urls import include, url
    import HelloDjangoApp.views

    # Django processes URL patterns in the order they appear in the array
    urlpatterns = [
        url(r'^$', HelloDjangoApp.views.index, name='index'),
        url(r'^home$', HelloDjangoApp.views.index, name='home'),
    ]
    ```

    每個 URL 模式都會描述 Django 路由傳送特定網站相對 URL (也就是 `https://www.domain.com/` 後面的部分) 的檢視。  中以規則運算式  為開頭的第一個項目，就是網站根目錄的路由 ("/")。 第二個項目 `^home$`會特別路由 "/home"。 您可以有針對相同檢視的任意數目路由。

1. 再次執行專案，以查看 message **Hello，Django！** 是否如檢視所定義。 當您完成時，請停止伺服器。

### <a name="commit-to-source-control"></a>認可至原始檔控制

因為您已變更並成功測試程式碼，所以現在是檢閱並認可對原始碼控制所做變更的絕佳時機。 本教學課程稍後的步驟會在適當時刻提醒您再次認可至原始檔控制，並請您返回參閱本節。

1. 選取位於 Visual Studio 底部的變更按鈕 (下面圈起處)，這會瀏覽至 [Team Explorer]。

    ![Visual Studio 狀態列上的原始檔控制變更按鈕](media/django/step02-source-control-changes-button.png)

1. 在 [Team Explorer] 中，輸入像是「建立初始 Django 應用程式」的認可訊息，然後選取 [全部認可]。 當認可完成時，您會看到在 **本機建立的訊息認可 \<hash> 。同步以與伺服器共用您的變更。** 如果您想要將變更推送至遠端存放庫，請選取 [同步]，然後選取 [傳出的認可] 底下的 [推送]。 您也可以在累積多個本機認可之後，再推送至遠端。

    ![在 [Team Explorer] 中將認可推送至遠端](media/django/step02-source-control-push-to-remote.png)

### <a name="question-what-is-the-r-prefix-before-the-routing-strings-for"></a>問題：路由字串前方的 'r' 前置詞有什麼用途？

回答：Python 中字串上的 'r' 前置詞表示「未經處理」，這會指示 Python 不逸出字串內的任何字元。 因為規則運算式會使用許多特殊字元，因此比起讓那些字串包含數個 '\\' 逸出字元，使用 'r' 前置詞能使它們更容易讀取。

### <a name="question-what-do-the--and--characters-mean-in-the-url-routing-entries"></a>問題：URL 路由項目中 ^ 與 $ 字元的意義為何？

回答：在定義 URL 模式的規則運算式中，^ 表示「行的開頭」，而 $ 則表示「行的結尾」，而 URL 同樣地是相對於網站根目錄 (`https://www.domain.com/` 後面的部分)。 規則運算式 `^$` 際上表示「空白」，因此會比對完整的 URL `https://www.domain.com/` (沒有將任何內容加入至網站根目錄)。 模式 `^home$` 會完全符合 `https://www.domain.com/home/`。 (Django 在模式比對中不會使用尾端的 /)。

如果您不在規則運算式中使用尾端的 $ (如同 `^home`)，URL 模型將會符合以 "home" 開頭的 *任何* URL，例如 "home"、"homework"、"homestead" 及 "home192837"。

若要使用不同的規則運算式進行實驗，請嘗試使用如 [pythex.org](https://www.pythex.org) \(英文\) 的 [regex101.com](https://regex101.com) \(英文\) 等線上工具。

## <a name="step-2-3-render-a-view-using-html"></a>步驟 2-3：使用 HTML 轉譯檢視

目前您在 *views.py* 中已有的 `index` 函式，只會針對網頁產生純文字 HTTP 回應。 而絕大部分的實際網頁，通常都會以含有即時資料的豐富 HTML 網頁來回應。 實際上，使用函式來定義檢視的主要原因，就是為了可以動態產生內容。

因為 `HttpResponse` 的引數只是字串，您可以視需要在字串內建置任何 HTML。 作為簡單的例子，請以下列程式碼取代 `index` 函式 (保留現有的 `from` 陳述式)，這將會使用動態內容來產生 HTML 回應，而這些內容會隨著每次重新整理網頁而更新：

```python
from datetime import datetime

def index(request):
    now = datetime.now()

    html_content = "<html><head><title>Hello, Django</title></head><body>"
    html_content += "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
    html_content += "</body></html>"

    return HttpResponse(html_content)
```

再次執行專案，以查看訊息，例如 "**Hello, Django!** on Monday, 16 April, 2018 at 16:28:10"。 重新整理網頁以更新時間，並確認內容會隨每個要求產生。 當您完成時，請停止伺服器。

> [!Tip]
> 停止和重新開機專案的快捷方式是使用 [ **Debug**  >  **重新開機**] 功能表命令 (**Ctrl** + **Shift** + **F5**) 或偵錯工具工具列上的 [**重新開機**] 按鈕：
>
> ![Visual Studio 中偵錯工具列上的重新啟動按鈕](media/debugging-restart-toolbar-button.png)

## <a name="step-2-4-render-a-view-using-a-page-template"></a>步驟 2-4：使用頁面範本轉譯檢視

以程式碼產生 HTML 的方式適用於非常小型的頁面，但隨著網頁變得更加複雜，您通常會想要將網頁的靜態 HTML 部分 (以及針對 CSS 與 JavaScript 檔案的參考) 維護為「頁面範本」，以便可以在其中插入程式碼產生的動態內容。 在上一節中，只有 `now.strftime` 呼叫中的日期與時間是動態的，這表示您可將所有其他內容置於頁面範本中。

Django 頁面範本是 HTML 區塊，可包含任意數目的取代權杖 (稱為「變數」)，這些權杖是以 `{{` 與 `}}` 分隔 (如 `{{ content }}`)。 然後，Django 的範本模組會以您在程式碼中提供的動態內容取代變數。

下列步驟示範如何使用頁面範本：

1. 在包含 Django 專案的 *BasicProject* 資料夾下，開啟 *settings.py* 檔案，然後將應用程式名稱 "HelloDjangoApp" 新增至 `INSTALLED_APPS` 清單。 將應用程式新增至清單，能告知 Django 專案具有該名稱的資料夾中包含應用程式：

    ```python
    INSTALLED_APPS = [
        'HelloDjangoApp',
        # Other entries...
    ]
    ```

1. 此外，在 *settings.py* 中，確定 `TEMPLATES` 物件包含下行 (預設已包含)，其會指示 Django 在已安裝應用程式的 *templates* 資料夾中尋找範本：

    ```json
    'APP_DIRS': True,
    ```

1. 在 *HelloDjangoApp* 資料夾中，開啟 *templates/HelloDjangoApp/index.html* 頁面範本檔案 (在 VS 2017 15.7 中則為 *templates/index.html*)，就會看到其中包含一個變數 `{{ content }}`：

    ```html
    <html>
    <head><title></title></head>

    <body>

    {{ content }}

    </body>
    </html>
    ```

1. 在 *HelloDjangoApp* 資料夾中，開啟 *views.py*，並以使用 `django.shortcuts.render` 協助程式函式的下列程式碼來取代 `index` 函式。 `render` 協助程式能提供處理頁面範本的簡化介面。 請務必保留所有現有的 `from` 陳述式。

    ```python
    from django.shortcuts import render   # Added for this step

    def index(request):
        now = datetime.now()

        return render(
            request,
            "HelloDjangoApp/index.html",  # Relative path from the 'templates' folder to the template file
            # "index.html", # Use this code for VS 2017 15.7 and earlier
            {
                'content': "<strong>Hello Django!</strong> on " + now.strftime("%A, %d %B, %Y at %X")
            }
        )
    ```

    您可以看到 `render` 的第一個引數是要求物件，而後面接著的則是應用程式 *templates* 資料夾內範本檔案的相對路徑。 在適當的情況下，範本檔案會以其所支援的檢視為名。 針對 `render` 的第三個引數，是範本所參考變數的字典。 您可以在字典中包含物件，在該情況下，範本中的變數可以參考 `{{ object.property }}`。

1. 執行專案，並觀察輸出結果。 您應該會看到和步驟 2-2 類似的訊息，表示範本運作正常。

    不過，您會觀察到在 `content` 屬性中使用的 HTML 只會轉譯為純文字，原因是 `render` 函式會自動逸出該 HTML。 自動逸出可防止意外遭受插入式攻擊：開發人員經常會透過範本預留位置從一個頁面收集輸入，再使用該輸入作為另一個頁面的值。 逸出也可作為一種提醒，就是最好將 HTML 放在頁面範本中且在程式碼外。 幸運的是，視需要建立額外變數是相當簡單的事。 例如，以 *templates* 變更 *index.html* 使其符合下列標記，以新增頁面標題，同時保留頁面範本中的所有格式設定：

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

    接著，以下列方式撰寫 `index` 檢視函式，來為頁面範本中的所有變數提供值：

    ```python
    def index(request):
        now = datetime.now()

        return render(
            request,
            "HelloDjangoApp/index.html",  # Relative path from the 'templates' folder to the template file
            # "index.html", # Use this code for VS 2017 15.7 and earlier
            {
                'title' : "Hello Django",
                'message' : "Hello Django!",
                'content' : " on " + now.strftime("%A, %d %B, %Y at %X")
            }
        )
    ```

1. 停止伺服器並重新啟動專案，然後觀察頁面現在是否正確轉譯：

    ![使用範本執行應用程式](media/django/step02-result.png)

1. <a name="template-namespacing"></a>Visual Studio 2017 15.7 版及較早版本：最後一個步驟，是將範本移到和應用程式名稱相同的子資料夾中以建立命名空間，並避免與可能會新增到專案中的其他應用程式發生潛在衝突。  (VS 2017 15.8 + 中的範本會自動為您執行此作業。 ) 也就是說，在名為 *HelloDjangoApp* 的 *範本* 中建立子資料夾，將 *index.html* 移至該子資料夾，然後修改 view 函式 `index` 以參考範本的新路徑 *HelloDjangoApp/index.html*。 接著執行專案，確認頁面轉譯正確，然後停止伺服器。

1. 將變更認可至原始檔控制，並視需要更新遠端存放庫，如[步驟 2-2](#commit-to-source-control)所述。

### <a name="question-do-page-templates-have-to-be-in-a-separate-file"></a>問題：頁面範本是否一定要位於個別檔案中？

回答：雖然範本通常會維護於個別的 HTML 檔案中，您也可以使用內嵌範本。 不過，還是建議您使用個別的檔案，以在標記和程式碼之間維持清楚的分隔。

### <a name="question-must-templates-use-the-html-file-extension"></a>問題：範本一定要使用 .html 副檔名嗎？

回答：頁面範本檔案的 *.html* 副檔名完全是選擇性的，因為您一定會在 `render` 函式的第二個引數中識別該檔案的確切相對路徑。 不過，Visual Studio (與其他編輯器) 通常會針對 *.html* 檔案為您提供程式碼完成和語法色彩等功能，其重要性超過頁面範本不一定是 HTML 的事實。

實際上，當您在處理 Django 專案時，Visual Studio 會自動偵測出您正在編輯的 HTML 檔案實際上是 Django 範本，然後提供一些自動完成功能。 例如，當您開始輸入 Django 頁面範本註解 (`{#`) 時，Visual Studio 會自動提供結尾的 `#}` 字元。 [註解選取範圍] 與 [取消註解選取範圍] 命令 (位在 [編輯] > [進階] 功能表和工具列上) 也會使用範本註解，而不是 HTML 註解。

### <a name="question-when-i-run-the-project-i-see-an-error-that-the-template-cannot-be-found-whats-wrong"></a>問題：當我執行專案時，看到找不到範本的錯誤。 出了什麼問題？

回答：如果您看到找不到範本的錯誤，請確定已將應用程式新增至 Django 專案位於 `INSTALLED_APPS` 清單的 *settings.py* 中。 若沒有該項目，Django 就不知道要查看應用程式的 *templates* 資料夾。

### <a name="question-why-is-template-namespacing-important"></a>問題：為什麼範本命名空間如此重要？

回答：當 Django 尋找在 `render` 函式中參考的範本時，它會使用所找到第一個和相對路徑相符的檔案。 如果您在相同專案中有多個 Django 應用程式，且專案範本都使用相同的資料夾結構時，很可能會有應用程式不小心用到另一個應用程式的範本。 若要避免發生這類錯誤，請一律在應用程式的 *templates* 資料夾下建立與應用程式名稱相符的子資料夾，以避免任何重複情況。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [提供靜態檔案、新增頁面，然後使用範本繼承](learn-django-in-visual-studio-step-03-serve-static-files-and-add-pages.md)

## <a name="go-deeper"></a>深入了解

- [撰寫第一個 Django 應用程式，第 1 部分 - 檢視](https://docs.djangoproject.com/en/2.0/intro/tutorial01/#write-your-first-view) \(英文\) (docs.djangoproject.com)
- 如需其他 Django 範本功能 (例如包含和繼承)，請參閱 [Django 範本語言](https://docs.djangoproject.com/en/2.0/ref/templates/language/) \(英文\) (docs.djangoproject.com)
- [inLearning 上的規則運算式訓練](https://www.linkedin.com/learning/topics/regular-expressions) \(英文\) (LinkedIn)
- GitHub 上的教學課程原始程式碼：[Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)
