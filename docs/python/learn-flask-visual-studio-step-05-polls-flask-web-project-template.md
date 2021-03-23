---
title: Visual Studio 中的了解 Flask 教學課程步驟 5，Polls 專案範本
titleSuffix: ''
description: 逐步解說 Visual Studio 專案內容中的 Flask 基本知識，特別是「投票 Flask Web 專案」和「投票 Flask/Jade Web 專案」範本的功能。
ms.date: 01/07/2019
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
monikerRange: vs-2017
ms.workload:
- python
- data-science
ms.openlocfilehash: fd67e527ccf62de17dc15a5415f573c9622a51e9
ms.sourcegitcommit: f1dff6c4532c43b0444aa12ea57e90bb7dba6fba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805974"
---
# <a name="step-5-use-the-polls-flask-web-project-template"></a>步驟 5：使用 Polls Flask Web 專案範本

**上一個步驟：[使用完整的 Flask Web 專案範本](learn-flask-visual-studio-step-04-full-flask-project-template.md)**

在了解 Visual Studio 的「Flask Web 專案」範本之後，您現在可以研究一下第三個 Flask 範本「投票 Flask Web 專案」，此專案以相同的程式碼基底為基礎。

在這個步驟中，您將了解如何：

> [!div class="checklist"]
> - 從範本建立專案並將資料庫初始化 (步驟 5-1)
> - 了解資料模型 (步驟 5-2)
> - 了解支援資料存放區 (步驟 5-3)
> - 了解投票詳細資料和結果檢視 (步驟 5-4)

Visual Studio 也提供「投票 Flask/Jade Web 專案」範本，此範本會產生相同的應用程式，但使用適用於 Jinja 範本化引擎的 Jade 延伸模組。 如需詳細資料，請參閱[步驟 4 - Flask/Jade Web 專案範本](learn-flask-visual-studio-step-04-full-flask-project-template.md#the-flaskjade-web-project-template)。

## <a name="step-5-1-create-the-project"></a>步驟 5-1：建立專案

1. 在 Visual Studio 中，移至 **方案總管**，以滑鼠右鍵按一下本教學課程稍早建立的 **LearningFlask** 方案，然後選取 [**加入**  >  **新專案**]。  (或者，如果您想要使用新的方案，請 **選取 [** 檔案  >  **新增**  >  **專案**]。 ) 

1. 在 [新增專案] 對話方塊中，搜尋並選取 [ **投票 Flask Web 專案** ] 範本，呼叫 "命名為 flaskpolls" 專案，然後選取 **[確定]**。

1. 一如 Visual Studio 中的其他專案範本，「投票 Flask Web 專案」範本也有 *requirements.txt* 檔案，Visual Studio 會詢問您這些相依性的安裝位置。 選擇 [安裝至虛擬環境] 選項，然後在 [新增虛擬環境] 對話方塊中，選取 [建立] 並接受預設值。 (此範本需要 Flask、azure-storage 與 pymongo 套件，「投票 Flask/Jade Web 專案」還需要 pyjade)。

1. 在 **方案總管** 中以滑鼠右鍵按一下該專案，然後選取 [**設定為啟始專案**]，將 **命名為 flaskpolls** 專案設定為 Visual Studio 方案的預設專案。 以粗體字型顯示的起始專案，會在您啟動偵錯工具時執行。

1. 選取 [ **Debug**  >  **開始調試**] (**F5**) 或使用工具列上的 [ **Web 服務器**] 按鈕來執行伺服器：

    ![Visual Studio 中的 [執行網頁伺服器] 工具列按鈕](media/django/run-web-server-toolbar-button.png)

1. 範本建立的應用程式有三個頁面，分別是首頁、關於和連絡人，您可以使用上面瀏覽列，在它們之間來回瀏覽。 請花一或兩分鐘的時間來檢查應用程式各個不同部分 ([About] \(關於\) 和 [Contact] \(連絡人\) 頁面與「Flask Web 專案」很類似，因此不進一步討論)。

    ![「投票 Flask Web 專案」應用程式的完整檢視](media/flask/step06-full-app-view.png)

1. 在首頁上，[Create Sample Polls] \(建立範例投票項目\) 按鈕會以 *models/samples.json* 頁面所述的三種不同投票將應用程式資料存放區初始化。 此應用程式預設會使用記憶體內部資料庫 (如 [About] \(關於\) 頁面所示)，每次重新啟動應用程式時都會重設此資料庫。 此應用程式也包含與「Azure 儲存體」和 Mongo DB 搭配運作的程式碼，如本文稍後所述。

1. 在您將資料存放區初始化之後，即可在不同的投票項目中進行投票，如首頁所示 (為了簡潔起見，已省略導覽列和頁尾)：

    ![將資料存放區初始化後的「投票」應用程式檢視](media/flask/step06-polls-initialized.png)

1. 選取投票項目便會顯示其特定選項：

    ![投票項目的投票介面](media/flask/step06-polls-voting-interface.png)

1. 投票之後，應用程式會顯示結果頁面並可讓您重新投票：

    ![投票後的結果檢視](media/flask/step06-polls-results.png)

1. 您可以讓這個應用程式繼續執行，在接下來的各節中都會用到它。

    如果您想停止應用程式並 [認可對原始檔控制所做的變更](learn-flask-visual-studio-step-02-create-app.md#commit-to-source-control)，請先開啟 [Team Explorer] 中的 [變更] 頁面，接著在虛擬環境的資料夾 (可能是 **env**) 上按一下滑鼠右鍵，然後選取 [略過這些本機項目]。

### <a name="examine-the-project-contents"></a>檢查專案內容

如前文所述， 如果您已瀏覽 Visual Studio 中的其他專案範本，則對於從「投票 Flask Web 專案」範本建立的專案內容，應該會相當熟悉。 本文章中的其他步驟會歸納更重大的修改和增添，也就是資料模型和其他檢視。

## <a name="step-5-2-understand-the-data-models"></a>步驟 5-2：了解資料模型

應用程式的資料模型是名為輪詢和 Choice 的 Python 類別，其定義于 *模型/ \_ \_ init \_ \_ . .py* 中。 Poll 代表問題，而其 Choice 執行個體的集合則代表可用的解答。 Poll 也保有投票總數 (針對任何選項)，以及可計算用來產生檢視之統計資料的方法：

```python
class Poll(object):
    """A poll object for use in the application views and repository."""
    def __init__(self, key=u'', text=u''):
        """Initializes the poll."""
        self.key = key
        self.text = text
        self.choices = []
        self.total_votes = None

    def calculate_stats(self):
        """Calculates some statistics for use in the application views."""
        total = 0
        for choice in self.choices:
            total += choice.votes
        for choice in self.choices:
            choice.votes_percentage = choice.votes / float(total) * 100 \
                if total > 0 else 0
        self.total_votes = total

class Choice(object):
    """A poll choice object for use in the application views and repository."""
    def __init__(self, key=u'', text=u'', votes=0):
        """Initializes the poll choice."""
        self.key = key
        self.text = text
        self.votes = votes
        self.votes_percentage = None
```

這些資料模型是一般抽象概念，可讓應用程式的檢視針對不同類型的支援資料存放區 (下一個步驟中會說明) 運作。

## <a name="step-5-3-understand-the-backing-data-stores"></a>步驟 5-3：了解支援資料存放區

「投票 Flask Web 專案」範本所建立的應用程式可以在記憶體內部資料存放區、Azure 資料表儲存體中或 Mongo DB 資料庫中執行。

資料儲存體機制的運作方式如下：

1. 指定存放庫類型時，會透過 `REPOSITORY_NAME` 環境變數指定，此環境變數可以設定為 "memory"、"azuretablestore" 或 "mongodb"。 *settings.py* 中的些許程式碼會擷取名稱，所使用的預設值為 "memory"。 如果您想要變更支援存放區，就必須設定環境變數，然後重新啟動應用程式。

    ```python
    from os import environ
    REPOSITORY_NAME = environ.get('REPOSITORY_NAME', 'memory')
    ```

1. *settings.py* 程式碼會接著將 `REPOSITORY_SETTINGS` 物件初始化。 如果您想要使用 Azure 資料表存放區或 Mongo DB，就必須先在其他位置將這些資料存放區初始化，然後設定必要的環境變數來告訴應用程式如何連線到這些存放區：

    ```python
    if REPOSITORY_NAME == 'azuretablestorage':
        REPOSITORY_SETTINGS = {
            'STORAGE_NAME': environ.get('STORAGE_NAME', ''),
            'STORAGE_KEY': environ.get('STORAGE_KEY', ''),
            'STORAGE_TABLE_POLL': environ.get('STORAGE_TABLE_POLL', 'polls'),
            'STORAGE_TABLE_CHOICE': environ.get('STORAGE_TABLE_CHOICE', 'choices'),
        }
    elif REPOSITORY_NAME == 'mongodb':
        REPOSITORY_SETTINGS = {
            'MONGODB_HOST': environ.get('MONGODB_HOST', None),
            'MONGODB_DATABASE': environ.get('MONGODB_DATABASE', 'polls'),
            'MONGODB_COLLECTION': environ.get('MONGODB_COLLECTION', 'polls'),
        }
    elif REPOSITORY_NAME == 'memory':
        REPOSITORY_SETTINGS = {}
    else:
        raise ValueError('Unknown repository.')
    ```

1. 在 *views.py* 中，應用程式會使用資料存放區的名稱和設定來呼叫 Factory 方法，以將 `Repository` 物件初始化：

    ```python
    from FlaskPolls.models import PollNotFound
    from FlaskPolls.models.factory import create_repository
    from FlaskPolls.settings import REPOSITORY_NAME, REPOSITORY_SETTINGS

    repository = create_repository(REPOSITORY_NAME, REPOSITORY_SETTINGS)
    ```

1. `factory.create_repository` 方法可在 *models\factory.py* 中找到，它會匯入適當的存放庫模組，然後建立 `Repository` 執行個體：

    ```python
    def create_repository(name, settings):
        """Creates a repository from its name and settings. The settings
        is a dictionary where the keys are different for every type of repository.
        See each repository for details on the required settings."""
        if name == 'azuretablestorage':
            from .azuretablestorage import Repository
        elif name == 'mongodb':
            from .mongodb import Repository
        elif name == 'memory':
            from .memory import Repository
        else:
            raise ValueError('Unknown repository.')

        return Repository(settings)
    ```

1. 每個資料存放區特定的 `Repository` 類別實作可在 *models\azuretablestorage.py*、*models\mongodb.py* 和 *models\memory.py* 中找到。 Azure 儲存體實作使用 azure-storage 套件；Mongo DB 實作則使用 pymongo 套件。 如步驟 5-1 中所述，這兩個套件都包含在專案範本的 *requirements.txt* 檔案中。 探索相關詳細資料將留給讀者作為習題。

簡言之，`Repository` 類別會提取資料存放區的細節，而應用程式則是會在執行階段使用環境變數，來選取並設定要使用三個實作中的哪一個。

如果想要支援專案範本所提供三個資料存放區以外的資料存放區，可使用下列步驟來新增支援：

1. 將 *memory.py* 複製到新檔案，以便為您提供 `Repository` 類別的基本介面。
1. 將類別的實作修改成符合您正在使用資料存放區的需求。
1. 修改 *factory.py* 來新增另一個 `elif` 案例，以辨識所新增資料存放區的名稱及匯入適當的模組。
1. 修改 *settings.py* 以辨識 `REPOSITORY_NAME` 環境變數中的另一個名稱，並相應地將 `REPOSITORY_SETTINGS` 初始化。

### <a name="seed-the-data-store-from-samplesjson"></a>從 samples.json 植入資料存放區

一開始，任何選擇的資料存放區都不會包含任何輪詢，因此應用程式的首頁會顯示「 **沒有可用的輪詢** 」和「 **建立範例輪詢** 」按鈕的訊息。 不過，選取該按鈕之後，檢視就會變更為顯示可用的投票項目。 這個切換會透過 *templates\index.html* 中的條件式標籤進行 (為了簡潔起見，已省略一些空白行)：

```html
{% extends "layout.html" %}
{% block content %}
<h2>{{title}}.</h2>

{% if polls %}
<table class="table table-hover">
    <tbody>
        {% for poll in polls %}
        <tr>
            <td>
                <a href="/poll/{{poll.key}}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<p>No polls available.</p>
<br />
<form action="/seed" method="post">
    <button class="btn btn-primary" type="submit">Create Sample Polls</button>
</form>
{% endif %}
{% endblock %}
```

範本中的 `polls` 變數來自對 `repository.get_polls` 的呼叫，這會在資料存放區初始化之後，才會傳回資料。

選取 [Create Sample Polls] \(建立範例投票項目\) 按鈕會瀏覽至 /seed URL。 該路由的處理常式是在 *views.py* 中定義的：

```python
@app.route('/seed', methods=['POST'])
def seed():
    """Seeds the database with sample polls."""
    repository.add_sample_polls()
    return redirect('/')
```

對 `repository.add_sample_polls()` 的呼叫最後會成為您所選資料存放區的其中一個特定 `Repository` 實作。 每個實作為呼叫 `_load_samples_json` *\_ \_ \_ \_ .py* 中的方法，以將檔案 *models\samples.js* 載入至記憶體中，然後逐一查看該資料，以 `Poll` `Choice` 在資料存放區中建立必要的和物件。

該程序完成之後，`seed` 方法中的 `redirect('/')` 陳述式就會瀏覽回首頁。 由於 `repository.get_polls` 現在會傳回資料物件，因此 *templates\index.html* 中的條件式標籤現在會轉譯成包含投票項目的資料表。

### <a name="question-how-does-one-add-new-polls-to-the-app"></a>問題：要如何將新投票項目新增到應用程式？

回答：透過專案範本提供的應用程式不包含新增或編輯投票項目的機能。 您可以修改 *models\samples.json* 以建立新的初始化資料，但這麼做將意謂著重設資料存放區。 若要實作編輯功能，您必須使用可建立必要 `Choice` 和 `Poll` 執行個體的方法來延伸 `Repository` 類別介面，然後在使用這些方法的額外頁面上實作 UI。

## <a name="step-5-4-understand-the-poll-detail-and-results-views"></a>步驟 5-4：了解投票詳細資料和結果檢視

「投票 Flask Web 專案」和「投票 Flask/Jade Web 專案」範本所產生的大多數檢視 (例如 [About] \(關於\) 和 [Contact] \(連絡人\) 頁面的檢視) 與您稍早在本教學課程中所使用、由「Flask Web 專案」(或「Flask/Jade Web 專案」) 範本建立的檢視非常相似。 在上一節中，您也了解了如何實作首頁來顯示初始化按鈕或投票項目清單。

這裡剩下的就是檢查投票 (詳細資料) 及個別投票項目的結果檢視。

當您從首頁選取輪詢時，應用程式會流覽至 URL/poll/， \<key\> 其中索引 *鍵* 是輪詢的唯一識別碼。 在 *views.py* 中，您會看到已指派 `details` 函式來處理 GET 和要求的該項 URL 路由。 您也會看到在 URL 路由中使用 `<key>` 會將任何該形式的路由對應至相同的函式，並產生該相同名稱之函式的引數：

```python
@app.route('/poll/<key>', methods=['GET', 'POST'])
def details(key):
    """Renders the poll details page."""
    error_message = ''
    if request.method == 'POST':
        try:
            choice_key = request.form['choice']
            repository.increment_vote(key, choice_key)
            return redirect('/results/{0}'.format(key))
        except KeyError:
            error_message = 'Please make a selection.'

    return render_template(
        'details.html',
        title='Poll',
        year=datetime.now().year,
        poll=repository.get_poll(key),
        error_message=error_message,
    )
```

為了顯示投票項目 (GET 要求)，此函式會直接呼叫 *templates\details.html* 來逐一查看投票項目的`choices` 陣列，為每個項目建立一個選項按鈕。

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% if error_message %}
<p class="text-danger">{{error_message}}</p>
{% endif %}

<form action="/poll/{{poll.key}}" method="post">
    {% for choice in poll.choices %}
    <div class="radio">
        <label>
            <input type="radio" name="choice" id="choice{{choice.key}}" value="{{choice.key}}" />
            {{ choice.text }}
        </label>
    </div>
    {% endfor %}
    <br />
    <button class="btn btn-primary" type="submit">Vote</button>
</form>

{% endblock %}
```

由於 [Vote] \(投票\) 按鈕包含 `type="submit"`，因此選取它會產生 POST 要求，此要求會送回給再次路由傳送至 `details` 的同一個 URL。 不過這次，它會從表單資料中解壓縮選擇，並重新導向至/results/ \<choice\> 。

/Results/ \<key\> URL 接著會路由傳送至 `results` *views.py* 中的函式，然後呼叫輪詢的方法， `calculate_stats` 並針對轉譯採用 *templates\results.html* ：

```python
@app.route('/results/<key>')
def results(key):
    """Renders the results page."""
    poll = repository.get_poll(key)
    poll.calculate_stats()
    return render_template(
        'results.html',
        title='Results',
        year=datetime.now().year,
        poll=poll,
    )
```

*results.html* 範本本身只會逐一查看投票項目的選項，並為每個選項產生一個進度列：

```html
{% extends "layout.html" %}

{% block content %}

<h2>{{poll.text}}</h2>
<br />

{% for choice in poll.choices %}
<div class="row">
    <div class="col-sm-5">{{choice.text}}</div>
    <div class="col-sm-5">
        <div class="progress">
            <div class="progress-bar" role="progressbar" aria-valuenow="{{choice.votes}}" aria-valuemin="0" aria-valuemax="{{poll.total_votes}}" style="width: {{choice.votes_percentage}}%;">
                {{choice.votes}}
            </div>
        </div>
    </div>
</div>
{% endfor %}

<br />
<a class="btn btn-primary" href="/poll/{{poll.key}}">Vote again?</a>

{% endblock %}
```

## <a name="next-steps"></a>下一步

> [!Note]
> 如果您一直在致力於為本教學課程中的原始檔控制，研究出自己的 Visual Studio 方案，現在是另一次做出貢獻的好機會。 您的方案應與 GitHub 上的教學課程原始程式碼相吻合：[Microsoft/python-sample-vs-learning-flask](https://github.com/Microsoft/python-sample-vs-learning-flask)。

您現在已探索完 Visual Studio 中的「空白 Flask Web 專案」、「Flask[/Jade] Web 專案」及「投票 Flask[/Jade] Web 專案」範本的全部內容。 您已了解 Flask 的所有基本知識 (例如檢視、範本及路由)，也了解了如何使用支援資料存放區。 現在，您應該能夠利用所需的任何檢視和模型，開始建立自己的 Web 應用程式。

在開發電腦上執行 Web 應用程式，只是開放客戶使用應用程式過程中的一個環結而已。 接下來的步驟可能包括下列的事項：

- 將 Web 應用程式部署到生產伺服器，例如 Azure App Service。 請參閱[發佈至 Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)。

- 新增使用另一個生產環境層級資料存放區 (例如 PostgreSQL、MySQL 及 SQL Server；這些全都可以裝載在 Azure 上) 的存放庫實作。 您也可以使用 [Azure SDK for Python](/azure/python/) 來除了搭配 Cosmos DB 運作之外，也可以搭配 Azure 儲存體服務 (例如資料表和 Blob) 運作。

- 在 Azure DevOps 此類的服務上設定持續整合/持續部署管線。 除了操作原始檔控制 (透過 Azure Repos、GitHub 或其他位置)，您可以設定 Azure DevOps 專案來自動執行單元測試作為發行必要條件，另外也請設定管線來部署至預備伺服器，以便進行傳統測試，之後再部署至生產環境伺服器中。 此外，Azure DevOps 還會與 App Insights 等監視解決方案整合，並使用敏捷式規劃工具來關閉整個週期。 如需詳細資訊，請參閱[使用 Azure DevOps 專案建立 Python 的 CI/CD 管線](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true)，以及一般的[Azure DevOps 文件](/azure/devops/?view=vsts&preserve-view=true)。
