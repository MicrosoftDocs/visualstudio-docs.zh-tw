---
title: Visual Studio 中的了解 Django 教學課程步驟 6，Polls 投票專案範本
titleSuffix: ''
description: 以 Django Visual Studio 專案做背景，逐步解說 Django 的基礎知識，我們將重點介紹 Polls Django Web 專案的各項功能，例如自訂管理功能。
ms.date: 11/19/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 5e524232eed7e4044454c57fc4fcaa30c6e2a8a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942473"
---
# <a name="step-6-use-the-polls-django-web-project-template"></a>步驟 6：使用投票 Django Web 專案範本

**上一個步驟： [在 Django 中驗證使用者](learn-django-in-visual-studio-step-05-django-authentication.md)**

在了解 Visual Studio 的「Django Web 專案」 範本之後，讓我們介紹第三個 Django 範本 - 投票 Django Web 專案，它是利用相同的程式碼基底設計而成的，為各位示範如何與資料庫搭配使用。

在這個步驟中，您將了解如何：

> [!div class="checklist"]
> - 利用範本來建立專案，並初始化資料庫 (步驟 6-1)
> - 了解資料模型 (步驟 6-2)
> - 套用遷移 (步驟 6-3)
> - 了解專案範本建立的檢視和頁面範本 (步驟 6-4)
> - 建立自訂的管理介面 (步驟 6-5)

使用此範本所建立的專案，類似于在 Django 檔中 [撰寫您的第一個 Django 應用程式](https://docs.djangoproject.com/en/2.0/intro/tutorial01/) 教學課程所取得的內容。Web 應用程式是由公開網站所組成，可讓使用者在其中查看投票和投票，以及您可以用來管理投票的自訂系統管理介面。 它採用與 Django Web 專案範本相同的驗證系統，並實作 Django 模型，讓資料庫發揮更大的用途。相關資訊，請參閱以下各節。

## <a name="step-6-1-create-the-project-and-initialize-the-database"></a>步驟 6-1： 建立專案，並初始化資料庫

1. 在 Visual Studio 中，移至 **方案總管**，以滑鼠右鍵按一下本教學課程稍早建立的 **LearningDjango** 方案，然後選取 [**加入**  >  **新專案**]。  (或者，如果您想要使用新的方案，請 **選取 [** 檔案  >  **新增**  >  **專案**]。 ) 

1. 在 [新增專案] 對話方塊中，搜尋並選取 [ **投票 Django Web 專案** ] 範本，呼叫 ">djangopolls" 專案，然後選取 **[確定]**。

1. 與 Visual Studio 中的其他專案範本一樣，「投票 Django Web 專案」範本也包含一個 *requirements.txt* 檔案，Visual Studio 提示會詢問您要將這些相依性安裝到何處。 選擇 [安裝至虛擬環境] 選項，然後在 [新增虛擬環境] 對話方塊中，選取 [建立] 並接受預設值。

1. Python 設定好虛擬環境後，在顯示的 *readme.html* 中會有相關操作方法，請遵循指示來初始化並建立 Django 進階使用者 (也就是系統管理員)。 步驟是先以滑鼠右鍵按一下 **方案總管** 中的 **>djangopolls** 專案，選取 [ **python**  >  **Django 遷移**] 命令，然後再次以滑鼠右鍵按一下專案、選取 [ **Python**  >  **Django 建立超級使用者**] 命令，然後遵循提示進行。 (如果您試著先建立進階使用者，將會看到錯誤訊息，原因是資料庫尚未初始化)。

1. 在 **方案總管** 中以滑鼠右鍵按一下該專案，然後選取 [**設定為啟始專案**]，將 **>djangopolls** 專案設定為 Visual Studio 方案的預設專案。 以粗體字型顯示的起始專案，會在您啟動偵錯工具時執行。

1. 選取 [ **Debug**  >  **開始調試**] (**F5**) 或使用工具列上的 [ **Web 服務器**] 按鈕來執行伺服器：

    ![Visual Studio 中的 [執行網頁伺服器] 工具列按鈕](media/django/run-web-server-toolbar-button.png)

1. 範本建立的應用程式有三個頁面，分別是首頁、關於和連絡人，您可以使用上面瀏覽列，在它們之間來回瀏覽。 請花一到兩分鐘的時間來檢查應用程式各個部分 (「關於」和「連絡人」頁面與「Django Web 專案」很類似，因此不做進一步討論)。

    ![「投票 Django Web 專案」應用程式的完整瀏覽器檢視](media/django/step06-full-app-view.png)

1. 另外也選取瀏覽列中的 **管理** 連結，這樣會顯示一個登入畫面。從畫面得知，只有通過驗證的系統管理員才能操作這個系統管理介面。 使用進階使用者認證，然後會開啟 /admin 頁面。這是使用這個專案範本時，會預設啟用的頁面。

    ![「投票 Django Web 專案」應用程式的系統管理檢視](media/django/step06-polls-administrative-interface.png)

1. 您可以讓這個應用程式繼續執行，在接下來的各節中都會用到它。

    如果您想停止應用程式並 [認可對原始檔控制所做的變更](learn-django-in-visual-studio-step-02-create-an-app.md#commit-to-source-control)，請先開啟 [Team Explorer] 中的 [變更] 頁面，接著在虛擬環境的資料夾 (可能是 **env**) 上按一下滑鼠右鍵，然後選取 [略過這些本機項目]。

### <a name="examine-the-project-contents"></a>檢查專案內容

如前文所述， 如果您已瀏覽 Visual Studio 中的其他專案範本，那麼對於利用「投票 Django Web 專案」範本所建立的專案，應該有一定的了解。 本文章中的其他步驟會歸納更重大的修改和增添，也就是資料模型和其他檢視。

### <a name="question-what-does-the-django-migrate-command-do"></a>問題：Django 遷移命令有何作用？

回答：**Django 遷移** 命令專門負責執行 `manage.py migrate` 命令，然後這個命令又會執行 *app/migrations* 資料夾中先前任何未執行的指令碼。 在本案例中，這個命令會執行這個資料夾中的 *0001_initial.py* 指令碼，以便在資料庫中設定必要的結構描述。

這個遷移指令碼本身是由 `manage.py makemigrations` 命令建立的，它會掃描應用程式的 *models.py* 檔案，接著與目前的資料庫狀態進行比較，然後產生必要的指令碼來遷移資料庫結構描述，以適應目前的模型。 以後當您更新以及修改模型時，會發現這個 Django 功能非常實用。 您只需產生以及執行遷移的，便能夠讓模型與資料庫輕鬆同步。

您會在本文章的步驟 6-3 進行一次遷移。

## <a name="step-6-2-understand-data-models"></a>步驟 6-2：了解資料模型

應用程式的模型是定義在 *app/models.py* 中，名稱是 Poll 和 Choice。 每一個都是衍生自 `django.db.models.Model` 的 Python 類別，並使用 `models` 類別的方法，例如 `CharField` 和 `IntegerField`，在模型中定義欄位，而這些欄位又對應至資料庫資料行。

```python
from django.db import models
from django.db.models import Sum

class Poll(models.Model):
    """A poll object for use in the application views and repository."""
    text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')

    def total_votes(self):
        """Calculates the total number of votes for this poll."""
        return self.choice_set.aggregate(Sum('votes'))['votes__sum']

    def __unicode__(self):
        """Returns a string representation of a poll."""
        return self.text

class Choice(models.Model):
    """A poll choice object for use in the application views and repository."""
    poll = models.ForeignKey(Poll)
    text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)

    def votes_percentage(self):
        """Calculates the percentage of votes for this choice."""
        total = self.poll.total_votes()
        return self.votes / float(total) * 100 if total > 0 else 0

    def __unicode__(self):
        """Returns a string representation of a choice."""
        return self.text
```

如您所見，Poll 會在其 `text` 欄位中保留一段描述，以及在 `pub_date` 中保留一個發行日期。 這些欄位是唯一存在於資料庫輪詢的欄位;此 `total_votes` 欄位會在執行時間計算。

Choice 是透過 `poll` 欄位與 Poll 產生關聯，而且在 `text` 包含一段描述，以及在 `votes` 保留該選擇的一個計數。 `votes_percentage`欄位是在執行時間計算的，而且在資料庫中找不到。

欄位類型的完整清單是 `CharField` (有限文字) `TextField` (無限文字)、`EmailField`、`URLField`、`DateTimeField`、`IntegerField`、`DecimalField`、`BooleanField`、`ForeignKey` 和 `ManyToMany`。 每個欄位都會採用一些屬性，例如 `max_length`。 `blank=True` 屬性表示欄位是選擇性的。`null=true` 表示值是選擇性的。 另外還有一個 `choices` 屬性，它會將值限制為資料值/顯示值 tuple 陣列中旳值。 (請參閱 Django 文件中的[模型欄位參考](https://docs.djangoproject.com/en/2.0/ref/models/fields/))。

您可以使用 [SQLite 瀏覽器](https://sqlitebrowser.org/)此類的工具來檢查專案中的 *db.sqlite3* 檔案，即可確認資料庫倒底儲存什麼樣的內容。 在資料庫中，您會看到外部索引鍵欄位，例如 Choice 模型中的 `poll`，是儲存為 `poll_id`；Django 會自動處理這種對應關係。

一般來說，使用 Django 操作您的資料庫時，表示您的模型也是被獨佔操作，因此 Django 可以代表您來管理基礎資料庫。

### <a name="seed-the-database-from-samplesjson"></a>從 samples.json 為資料庫新增投票

一開始，資料庫是不包含任何投票的。 您可以使用 "/admin" URL 的系統管理介面來手動新增投票，也可以瀏覽執行中網站上的 "/seed" 頁面，然後將應用程式 *samples.json* 檔案中所定義的投票新增至資料庫。

Django 專案的 *urls.py* 有一個新增的 URL 模式 `url(r'^seed$', app.views.seed, name='seed'),`。 *app/views.py* 中的 `seed` 檢視會載入 *samples.json* 檔案，並建立必要的模型物件。 然後 Django 會在基礎資料庫中，自動建立相符的記錄。

請注意，使用 `@login_required` 裝飾項目來表示該檢視的授權層級。

```python
@login_required
def seed(request):
    """Seeds the database with sample polls."""
    samples_path = path.join(path.dirname(__file__), 'samples.json')
    with open(samples_path, 'r') as samples_file:
        samples_polls = json.load(samples_file)

    for sample_poll in samples_polls:
        poll = Poll()
        poll.text = sample_poll['text']
        poll.pub_date = timezone.now()
        poll.save()

        for sample_choice in sample_poll['choices']:
            choice = Choice()
            choice.poll = poll
            choice.text = sample_choice
            choice.votes = 0
            choice.save()

    return HttpResponseRedirect(reverse('app:home'))
```

要想查看效果，先執行這個應用程式，確定沒有任何投票存在。 接著瀏覽 "/seed" URL，當應用程式返回首頁時，您應該會看到投票了。 同樣地，您可以使用 [SQLite 瀏覽器](https://sqlitebrowser.org/)此類的工具，隨意檢查原始的 *db.sqlite3* 檔案。

![自帶種子資料庫的「投票 Django Web 專案」應用程式](media/django/step06-app-with-seeded-database.png)

### <a name="question-is-it-possible-to-initialize-the-database-using-the-django-administrative-utility"></a>問題：能不能使用 Django 系統管理公用程式來初始化資料庫？

回答： 可以的，您可以使用 [django-admin loaddata 命令](https://docs.djangoproject.com/en/2.0/ref/django-admin/#loaddata)來完成與應用程式種子頁面中相同的作業。 在完整的 Web 應用程式上進行操作時，您可以將下列兩種方法結合使用：從命令列初始化資料庫，然後將此處的種子頁面轉換成一個 API，這樣您就可以將任何其他 JSON 傳送到這個 API，不需要透過硬式編碼的檔案了。

## <a name="step-6-3-use-migrations"></a>步驟 6-3： 使用遷移

當您在建立專案之後，執行 `manage.py makemigrations` 命令 (使用 Visual Studio 中的快顯功能表)，Django 會建立 *app/migrations/0001_initial.py* 檔案。 這個檔案包含一個指令碼，可以用來建立初始的資料庫資料表。

您以後一定會對自己的模型進行變更，不過 Django 可以讓基礎資料庫結構描述保有這些最新的模型。 以下是大致的工作流程：

1. 變更 *models.py* 檔案中的模型。
1. 到 Visual Studio 中的 [方案總管]，然後在專案上按一下滑鼠右鍵，接下來依序選取 [Python] > [Django 遷移] 命令。 如先前所述，這個命令會在 *app/migrations* 中產生指令碼，以便將資料庫從目前的狀態遷移至新的狀態。
1. 若要將腳本套用至實際資料庫，請再次以滑鼠右鍵按一下專案，然後選取 [ **Python**  >  **Django 遷移**]。

Django 會追蹤哪些已套用至任何特定資料庫的遷移，所以只要您執行遷移命令，Django 就會套用任何必要的遷移。 比方說您建立新的空白資料庫，執行遷轉命令便會套用每一個遷轉指令碼，讓您擁有最新的模型。 同樣地，如果您對多個模型進行變更，並在開發電腦上產生遷移，就可以在生產伺服器上執行遷移命令，以便能夠將累積的遷移套用至生產資料庫。 Django 又會再一次只套用那些自從生產資料庫最後一次遷移之後，另外產生的遷移指令碼。

若要查看變更模型所造成的影響，請嘗試下列步驟：

1. 將下面這一行新增到 `pub_date` 欄位後面來新增一個選擇性 `author` 欄位，這樣您就可以將一個選擇性 author 欄位新增至 *app/models.py* 中的 Poll 模型：

    ```python
    author = models.CharField(max_length=100, blank=True)
    ```

1. 儲存檔案，然後以滑鼠右鍵按一下 **方案總管** 中的 **>djangopolls** 專案，然後選取 [ **Python**  >  **Django 建立遷移**] 命令。
1. 選取 [**專案**  >  **顯示所有** 檔案] 命令，以在 [**遷移**] 資料夾中查看新產生的腳本，其名稱以 **002_auto_** 開頭。 在檔案上按一下滑鼠右鍵，然後選取 [App_Data] 資料夾，然後選取 [包括在專案中]。 然後，您可以選取 [**專案**  >  **顯示所有** 檔案] 來還原原始的視圖。 (請參閱下方的第二個問題，了解這個步驟的詳細資料)。
1. 如有需要，開啟這個檔案並檢查 Django 指令碼如伺記錄模型從舊狀態到新狀態狀態之間的變動過程。
1. 再以滑鼠右鍵按一下 Visual Studio 專案，然後選取 [ **Python**  >  **Django 遷移**]，將變更套用到資料庫。
1. 如有需要，請在適當的檢視器中開啟資料庫，以確認變更。

整體來說，Django 的遷移功能表示您永遠不需要手動管理資料庫結構描述。 只要在您的模型做一些變更，接著產生遷移指令碼，然後使用遷移命令來套用這些指令碼就可以了。

### <a name="question-what-happens-if-i-forget-to-run-the-migrate-command-after-making-changes-to-models"></a>問題：萬一我對模型做了一些變更，但之後卻忘了執行遷移命令，該怎麼辦？

答：如果模型不符合資料庫中的內容，Django 會在執行時間失敗，並出現適當的例外狀況。 例如，如果您忘記遷移上一節中所示的模型變更，您會看到 **沒有此類資料行的錯誤： app_poll. 作者**：

![當模型變更尚未遷移時，就會顯示錯誤](media/django/step06-exception-when-forgetting-to-migrate.png).

### <a name="question-why-doesnt-solution-explorer-show-newly-generated-scripts-after-running-django-make-migrations"></a>問題： 為什麼執行 Djang 遷移之後，方案總管不顯示產生的新指令碼？

回答：雖然產生的新指令碼存在於 *app/migrations* 資料夾並在執行 [Django 遷移] 命令時套用了新指令碼，但因為它們未被新增至 Visual Studio 專案，所以不會自動顯示在 [方案總管] 中。 若要顯示它們，請先選取 [顯示所有檔案的 **專案**]  >  功能表命令，或下圖中所述的工具列按鈕。 這個命令會使用虛線輪廓圖示代表尚未新增至專案中的項目，讓 **方案總管** 顯示資料夾中的所有檔案。 在您想新增的檔案上按一下滑鼠右鍵，然後選取 [包含在專案中]，這樣下次您認可時，也會將它們包含在原始控制項中。

![包含在方案總管的專案命令中](media/django/step06-include-migrations-script-in-project.png)

### <a name="question-can-i-see-what-migrations-would-be-applied-before-running-the-migrate-command"></a>問題：執行遷移命令之前，有辦法知道哪些遷移會被套用嗎？

回答：可以，請使用 [django admin showmigrations 命令](https://docs.djangoproject.com/en/2.0/ref/django-admin/#showmigrations)。

## <a name="step-6-4-understand-the-views-and-page-templates-created-by-the-project-template"></a>步驟 6-4：了解專案範本建立的檢視和頁面範本

「投票 Django Web 專案」範本產生的大部分檢視，例如「關於」和「連絡人」頁面的檢視，與您稍早在本教學課程中利用「Django Web 專案」範本建立的檢視十分類似。 投票應用程式的不同處在於它的首頁會使用模型，也會新增幾個的頁面來進行投票和檢視投票結果。

首先，*urls.py* 檔案中 Django 專案 `urlpatterns` 陣列的第一行，不僅僅是一個通向應用程式檢視的路由而已。 相反地，它會提取應用程式自己的 *urls.py* 檔案：

```python
from django.conf.urls import url, include
import app.views

urlpatterns = [
    url(r'^', include('app.urls', namespace="app")),
    # ..
]
```

*app/urls.py* 檔案則包含一些更有趣的路由程式碼 (新增了說明性註解)：

```python
urlpatterns = [
    # Home page routing
    url(r'^$',
        app.views.PollListView.as_view(
            queryset=Poll.objects.order_by('-pub_date')[:5],
            context_object_name='latest_poll_list',
            template_name='app/index.html',),
        name='home'),

    # Routing for a poll page, which use URLs in the form <poll_id>/,
    # where the id number is captured as a group named "pk".
    url(r'^(?P<pk>\d+)/$',
        app.views.PollDetailView.as_view(
            template_name='app/details.html'),
        name='detail'),

    # Routing for <poll_id>/results pages, again using a capture group
    # named pk.
    url(r'^(?P<pk>\d+)/results/$',
        app.views.PollResultsView.as_view(
            template_name='app/results.html'),
        name='results'),

    # Routing for <poll_id>/vote pages, with the capture group named
    # poll_id this time, which becomes an argument passed to the view.
    url(r'^(?P<poll_id>\d+)/vote/$', app.views.vote, name='vote'),
]
```

這裡用到是更複雜的規則運算式，如果您有什麼地方不明白，可以將運算式貼到 [regex101.com](https://regex101.com/)，然後就會看到淺顯易懂的說明。 (您需要在正斜線 `/` 前面加上反斜線 `\` 以逸出正斜線；Python 不需要做逸出處理，因為字串中的 `r` 前置詞，表示 "raw")。

在 Django 中，語法 `?P<name>pattern` 會建立名為 `name` 的群組，然後當作引數而傳遞至依序顯示的檢視。 在前面顯示的程式碼中，`PollsDetailView` 和 `PollsResultsView` 會收到 `pk` 引數，而 `app.views.vote` 會收到 `poll_id` 引數。

您也可以看到大部分的檢視不光只是直接參考 *app/views.py* 中的檢視函式。 相反地，大部分會參考 `django.views.generic.ListView` 或 `django.views.generic.DetailView` 所衍生檔案中的某一個類別。 基底類別提供 `as_view` 方法，而它會使用 `template_name` 引數來識別範本。 至於用於首頁的 `ListView` 基底類別，也要有一個內含資料的 `queryset` 屬性，另外還要有一個 `context_object_name` 屬性加上變數名稱，讓您可據此參考範本中的資料，也就是本案例中的 `latest_poll_list`。

現在您可以檢查 `PollListView` 中的首頁，它在 *app/views.py* 中的定義如下：

```python
class PollListView(ListView):
    """Renders the home page, with a list of all polls."""
    model = Poll

    def get_context_data(self, **kwargs):
        context = super(PollListView, self).get_context_data(**kwargs)
        context['title'] = 'Polls'
        context['year'] = datetime.now().year
        return context
```

這裡所做的一切都是為了識別與檢視搭配使用模型 (投票)，以及覆寫 `get_context_data` 方法來將 `title` 和 `year` 新增至內容。

核心的範本 (*templates/app/index.html*) 如下所示：

```html
{% if latest_poll_list %}
<table class="table table-hover">
    <tbody>
        {% for poll in latest_poll_list %}
        <tr>
            <td>
                <a href="{% url 'app:detail' poll.id %}">{{poll.text}}</a>
            </td>
        </tr>
        {% endfor %}
    </tbody>
</table>
{% else %}
<!-- ... other content omitted ... -->
{% endif %}
```

簡而言之，這個範本會收到 `latest_poll_list` 中的 Poll 物件清單 ，然後循環執行整個清單來建立一個資料表資料列，其中會有一個指向各個投票的連結，它使用 Poll 的 `text` 值。 在 `{% url %}` 標記中，app:detail 將 `poll.id` 當作參數，然後參考 *app/urls.py* 中名為 detail 的 URL 模式。 這段程式碼的執行結果就是 Django 會建立一個使用適當模式的 URL，並將其用於連結。 這種做法會考慮到未來的適用性，也就是說您可以隨時變更這個 URL 模式，而且產生的連結會自動更新以符合現況。

*app/views.py* 中的 `PollDetailView` 和 `PollResultsView` 類別 (此處未顯示)，看起來幾乎與 `PollListView` 完全相同，不同處在於它們是衍生自 `DetailView`。 它們各自的範本 (*app/templates/details.html* 和 *app/templates/results.html*) 便會將模型的適當欄位放到不同的 HTML 控制項裡面。 *details.html* 裡面有一個獨特的部分，那就是投票的選項都包含在 HTML 表單中，當送出此表單時會針對 /vote URL 執行一次 POST。 如同前文所見，URL 模式會傳遞至 `app.views.vote`，然後實作如下 (請注意，`poll_id` 引數同樣是此檢視相關路由所使用規則運算式中的一個具名群組)：

```python
def vote(request, poll_id):
    """Handles voting. Validates input and updates the repository."""
    poll = get_object_or_404(Poll, pk=poll_id)
    try:
        selected_choice = poll.choice_set.get(pk=request.POST['choice'])
    except (KeyError, Choice.DoesNotExist):
        return render(request, 'app/details.html', {
            'title': 'Poll',
            'year': datetime.now().year,
            'poll': poll,
            'error_message': "Please make a selection.",
    })
    else:
        selected_choice.votes += 1
        selected_choice.save()
        return HttpResponseRedirect(reverse('app:results', args=(poll.id,)))
```

在這裡，這個檢視和其他頁面不一樣，它沒有自己的對應範本。 相反地，它會驗證所選的投票，而且如果投票不存在 (萬一有人輸入 vote/1a2b3c 這樣的 URL)，就會顯示 404。 然後它會確保票選的決定適用於該投票。 如果不適用，`except` 區塊只會再次顥示詳細資料頁面以及一則錯誤訊息。 如果決定有效，則這個檢視會計算投票，並重新導向至結果頁面。

## <a name="step-6-5-create-a-custom-administration-interface"></a>步驟 6-5：建立自訂的管理介面

「投票 Django Web 專」範本的最後一個部分是預設 Django 系統管理介面的自訂延伸模組，如同本文章步驟 6-1 所示。 使用者和群組管理只會有預設的介面，別無它物。 投票專案範本會增加一些功能，讓您也可以用來管理投票。

首先，Django 專案 *urls.py* 的 URL 模式會預設包含 `url(r'^admin/', include(admin.site.urls)),`；也會包含 admin/doc 模式，但會加上註解。

然後應用程式包含 *admin.py* 檔案，而且當您瀏覽系統管理介面時，Django 會自動執行這個應用程式，這要歸因於 *settings.py* 的 `INSTALLED_APPS` 陣列包含 `django.contrib.admin`。 按照專案範本的規定，這個檔案中的程式碼如下所示：

```python
from django.contrib import admin
from app.models import Choice, Poll

class ChoiceInline(admin.TabularInline):
    """Choice objects can be edited inline in the Poll editor."""
    model = Choice
    extra = 3

class PollAdmin(admin.ModelAdmin):
    """Definition of the Poll editor."""
    fieldsets = [
        (None, {'fields': ['text']}),
        ('Date information', {'fields': ['pub_date']}),
    ]
    inlines = [ChoiceInline]
    list_display = ('text', 'pub_date')
    list_filter = ['pub_date']
    search_fields = ['text']
    date_hierarchy = 'pub_date'

admin.site.register(Poll, PollAdmin)
```

如您所見，`PollAdmin` 類別是衍生自 `django.contrib.admin.ModelAdmin`，它使用 `Poll` 模型提供的名稱來自訂一些欄位並由自己管理。 Django 文件的 [ModelAdmin 選項](https://docs.djangoproject.com/en/2.0/ref/contrib/admin/#modeladmin-options)會說明這些欄位的用途。

呼叫 `admin.site.register`，然後將這個類別連接至模型 (`Poll`)，並將它包含在管理介面中。 整體結果會如下所示：

![「投票 Django Web 專案」應用程式的系統管理檢視](media/django/step06-polls-administrative-interface.png)

## <a name="next-steps"></a>下一步

> [!Note]
> 如果您一直在致力於為本教學課程中的原始檔控制，研究出自己的 Visual Studio 方案，現在是另一次做出貢獻的好機會。 您的方案應與 GitHub 上的教學課程原始程式碼相吻合：[Microsoft/python-sample-vs-learning-django](https://github.com/Microsoft/python-sample-vs-learning-django)。

您現在已探索完 Visual Studio 中的「空白 Django Web 專案」、「Django Web 專案」和「投票 Django Web 專案」 範本的全部內容。 您學會了 Django 的所有基礎知識，例如檢視和範本，也探索了路由、驗證及資料庫模型的應用。 您現在應該能夠利用所有必備的檢視和模型，建立您自己的 Web 應用程式。

在開發電腦上執行 Web 應用程式，只是開放客戶使用應用程式過程中的一個環結而已。 接下來的步驟可能包括下列的事項：

- 將 Web 應用程式部署到生產伺服器，例如 Azure App Service。 請參閱[發佈至 Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)。

- 建立名為 *templates/404.html* 的範本，以自訂 404 頁面。 如果這個範本存在，Django 就會使用它，而不使用預設範本。 如需詳細資訊，請參閱 Django 文件中的[錯誤檢視](https://docs.djangoproject.com/en/2.0/ref/views/#error-views)。

- 在 *tests.py* 中編寫單位測試；您可以在 Visual Studio 專案範本的基礎上再進行設計，而且 Django 文件中的 [Writing your first Django app, part 5 - testing](https://docs.djangoproject.com/en/2.0/intro/tutorial05/) (編寫第一個 Django 應用程式，第 5 部分 - 測試) 以及 [Testing in Django](https://docs.djangoproject.com/en/2.0/topics/testing/) (在 Django 中進行測試) 都有相關的詳細資訊。

- 將 SQLite 的應用程式變更為生產層級資料存放區，例如 PostgreSQL、MySQL 和 SQL Server (它們全部可以在 Azure 上託管)。 如同[何時使用 SQLite](https://www.sqlite.org/whentouse.html) (sqlite.org) 所述，SQLite 適合低到中等流量而且每日點擊量不足 100K 的站台，超過此限，不建議使用。 而且也只許在一台電腦上使用，因此任何多伺服器案例均不列入考慮，例如負載平衡和地理複寫。 如需 Django 支援的其他資料庫相關資訊，請參閱[資料庫安裝](https://docs.djangoproject.com/en/2.0/intro/tutorial02/#database-setup)。 您也可以使用 [Azure SDK for Python](/azure/python/) 來操作 Azure 儲存體服務，例如資料表和 blob。

- 在 Azure DevOps 此類的服務上設定持續整合/持續部署管線。 除了操作原始檔控制 (透過 Azure Repos、GitHub 或其他位置)，您可以設定 Azure DevOps 專案來自動執行單元測試作為發行必要條件，另外也請設定管線來部署至預備伺服器，以便進行傳統測試，之後再部署至生產環境伺服器中。 此外，Azure DevOps 還會與 App Insights 等監視解決方案整合，並使用敏捷式規劃工具來關閉整個週期。 如需詳細資訊，請參閱[使用 Azure DevOps 專案建立 Python 的 CI/CD 管線](/azure/devops-project/azure-devops-project-python?view=vsts&preserve-view=true)，以及一般的 [Azure DevOps 文件](/azure/devops/?view=vsts&preserve-view=true)。
