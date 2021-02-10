---
title: 適用於 Python 的 Web 應用程式範本
description: Visual Studio 提供使用 Bottle、Flask 和 Django 架構的 Python Web 應用程式範本，其支援包括偵錯組態並發佈到 Azure App Service。
ms.date: 01/28/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 1f6376978826afc2946cfac25ab635d0b7533dc4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939535"
---
# <a name="python-web-application-project-templates"></a>Python Web 應用程式專案範本

Visual Studio 中的 Python 支援透過專案範本以及偵錯啟動器 (其可針對處理各種架構進行設定)，在 Bottle、Flask 和 Django 架構中開發 Web 專案。 這些範本包含 *requirements.txt* 檔案，以宣告所需的相依性。 從這些範本的其中之一建立專案時，Visual Studio 會提示您安裝那些套件 (請參閱本文稍後的[安裝專案需求](#install-project-requirements))。

針對 Pyramid 這類其他架構，您也可以使用一般的 [Web 專案] 範本。 在此情況下，沒有架構會隨範本安裝。 相反地，請將必要套件安裝至您要針對專案使用的環境中 (請參閱 [[Python 環境] 視窗 - [套件] 索引標籤](python-environments-window-tab-reference.md#packages-tab))。

如需將 Python Web 應用程式部署至 Azure 的資訊，請參閱[發佈至 Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)。

## <a name="use-a-project-template"></a>使用專案範本

您 **可以使用 [** 檔案  >  **新增**  >  **專案**] 從範本建立專案。 若要查看 Web 專案的範本，請選取對話方塊左側的 **Python**  >  **web** 。 然後選取您選擇的範本，提供專案和方案的名稱，設定方案目錄和 Git 存放庫的選項，然後選取 [確定]。

![Web 應用程式的 [新專案] 對話方塊](media/projects-new-project-dialog-web.png)

先前提及的一般 [Web 專案] 範本只提供空白 Visual Studio 專案，而且除了作為 Python 專案之外，不會包含任何程式碼和假設。 如需 [Azure 雲端服務] 範本的詳細資料，請參閱[適用於 Python 的 Azure 雲端服務專案](python-azure-cloud-service-project-template.md)。

所有其他的專案都是以 Bottle、Flask 或 Django Web 架構為基礎，且分為三個一般群組，如以下小節所述。 由這些範本之一所建立的應用程式，都會包含在本機對應用程式進行執行與偵錯的必要程式碼。 每一個範本也都會提供必要的 [WSGI 應用程式物件](https://www.python.org/dev/peps/pep-3333/) (python.org)，以便搭配生產網頁伺服器使用。

### <a name="blank-group"></a>空白群組

所有 **空白的 \<framework> Web 專案** 範本都會建立一個專案，其中包含更多或較少的未定案程式碼，以及在 *requirements.txt* 檔案中宣告的必要相依性。

| 範本 | 描述 |
| --- | --- |
| **空白 Bottle Web 專案** | 在 *app.py* 中產生精簡應用程式，並包含 `/` 的首頁，以及使用非常短的內嵌頁面範本來回應 `<name>` 的 `/hello/<name>` 頁面。 |
| **空白 Django Web 專案** | 產生具核心 Django 網站架構，但不含 Django 應用程式的 Django 網站。 如需詳細資訊，請參閱 [Django 範本](python-django-web-application-project-template.md)和[學習 Django 步驟 1](learn-django-in-visual-studio-step-01-project-and-solution.md)。 |
| **空白 Flask Web 專案** | 產生一個精簡應用程式，其中含有 `/` 的單一 "Hello World!" 頁面。 此應用程式類似按照[快速入門：使用 Visual Studio 建立您的第一個 Python Web 應用程式](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)中詳細步驟操作的結果。 另請參閱[學習 Flask 步驟 1](learn-flask-visual-studio-step-01-project-solution.md)。

### <a name="web-group"></a>Web 群組

不論選擇的架構為何，所有 **\<Framework> Web 專案** 範本都會建立具有相同設計的入門 Web 應用程式。 該應用程式具有 [首頁]、[關於] 和 [連絡] 頁面，且包含使用 Bootstrap 的瀏覽列和回應式設計。 每個應用程式都已適當設定為提供靜態檔案 (CSS、JavaScript 和字型)，並使用適用於該架構的頁面範本機制。

| 範本 | 描述 |
| --- | --- |
| **瓶 Web 專案** | 產生其靜態檔案會包含在 *static* 資料夾中，且經由 *app.py* 中程式碼處理的應用程式。 個別頁面的路由會包含在 *routes.py* 中，且 *views* 資料夾會包含頁面範本。|
| **Django Web 專案** | 產生 Django 專案和含三個頁面、驗證支援，以及 SQLite 資料庫 (但不含資料模型) 的 Django 應用程式。 如需詳細資訊，請參閱 [Django 範本](python-django-web-application-project-template.md)和[學習 Django 步驟 4](learn-django-in-visual-studio-step-04-full-django-project-template.md)。 |
| **Flask Web 專案** | 產生其靜態檔案會包含在 *static* 資料夾中的應用程式。 *views.py* 中的程式碼會處理路由，而使用 Jinja 引擎的頁面範本則會包含在 *templates* 資料夾中。 *runserver.py* 檔案會提供啟動程式碼。 請參閱[學習 Flask 步驟 4](learn-flask-visual-studio-step-04-full-flask-project-template.md)。 |
| **Flask/Jade Web 專案** | 產生與 **Flask Web 專案** 範本相同的應用程式，但使用 Jinja 範本化引擎的 Jade 延伸模組。 |

### <a name="polls-group"></a>投票群組

**投票 \<framework> Web 專案** 範本會建立入門 web 應用程式，讓使用者可以透過此應用程式來對不同的投票問題進行投票。 每個應用程式都建置在 [Web] 專案範本的結構上，以使用資料庫來管理投票和使用者回應。 應用程式會包含適當的資料模型，以及會從 *samples.json* 檔案載入投票項目的特殊應用程式頁面 (/seed)。

| 範本 | 描述 |
| --- | --- |
| **投票 Bottle Web 專案** | 產生能針對記憶體內資料庫、MongoDB 或 Azure 資料表儲存體執行的應用程式，這是使用 `REPOSITORY_NAME` 環境變數來設定。 資料模型和資料存放區程式碼會包含在 *models* 資料夾中，且 *settings.py* 檔案會包含程式碼以決定要使用哪個資料存放區。 |
| **投票 Django Web 專案** | 會產生 Django 專案和包含三個頁面及 SQLite 資料庫的 Django 應用程式。 包含對 Django 系統管理介面的自訂項目，以允許已驗證的系統管理員建立及管理投票。 如需詳細資訊，請參閱 [Django 範本](python-django-web-application-project-template.md)和[學習 Django 步驟 6](learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)。 |
| **投票 Flask Web 專案** | 產生能針對記憶體內資料庫、MongoDB 或 Azure 資料表儲存體執行的應用程式，這是使用 `REPOSITORY_NAME` 環境變數來設定。 資料模型和資料存放區程式碼會包含在 *models* 資料夾中，且 *settings.py* 檔案會包含程式碼以決定要使用哪個資料存放區。 該應用程式針對頁面範本會使用 Jinja 引擎。 請參閱[學習 Flask 步驟 5](learn-flask-visual-studio-step-05-polls-flask-web-project-template.md)。 |
| **投票 Flask/Jade Web 專案** | 產生與 **投票 Flask Web 專案** 範本相同的應用程式，但使用 Jinja 範本化引擎的 Jade 延伸模組。 |

## <a name="install-project-requirements"></a>安裝專案需求

從架構特定的範本建立專案時，系統會顯示對話方塊來協助您使用 pip 安裝必要的套件。 另外也建議您針對 Web 專案使用[虛擬環境](selecting-a-python-environment-for-a-project.md#use-virtual-environments)，如此當您發佈網站時，就會包含正確的相依性：

![安裝專案範本所需之封裝的對話方塊](media/template-web-requirements-txt-wizard.png)

如果您使用原始檔控制，通常會省略虛擬環境資料夾，因為該環境可以僅使用 *requirements.txt* 來重新建立。 排除該資料夾的最佳方法，是先在上方所示的提示中選取 [我會自行安裝它們]，然後在建立虛擬環境之前停用自動認可。 如需詳細資料，請參閱[學習 Django 教學課程：步驟 1-2 和 1-3](learn-django-in-visual-studio-step-01-project-and-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository)，以及[學習 Flask 教學課程 - 步驟 1-2 和 1-3](learn-flask-visual-studio-step-01-project-solution.md#step-1-2-examine-the-git-controls-and-publish-to-a-remote-repository)。

部署至 Microsoft Azure App Service 時，請選取 Python 的版本作為[網站延伸模組](./managing-python-on-azure-app-service.md?view=vs-2019&preserve-view=true)，並手動安裝套件。 此外，由於從 Visual Studio 部署時，Azure App Service **不會** 自動從 *requirements.txt* 檔案安裝套件，請依照 [aka.ms/PythonOnAppService](managing-python-on-azure-app-service.md) 上的設定詳細資料進行。

Microsoft Azure 雲端服務「確實」支援 *requirements.txt* 檔案。 如需詳細資料，請參閱 [Azure 雲端服務專案](python-azure-cloud-service-project-template.md)。

## <a name="debugging"></a>偵錯

當啟動 Web 專案以進行偵錯時，Visual Studio 會在隨機的連接埠上啟動本機 Web 伺服器，並將您的預設瀏覽器開啟至該位址和連接埠。 若要指定其他選項，請以滑鼠右鍵按一下專案、選取 [ **屬性**]，然後選取 [ **Web 啟動器** ] 索引標籤：

![一般 Web 範本的 Web 啟動器屬性](media/template-web-launcher-properties.png)

在 [偵錯] 群組中：

- **搜尋路徑**、**指令碼引數**、**解譯器引數** 及 **解譯器路徑**：這些選項與 [標準偵錯](debugging-python-in-visual-studio.md)的選項相同。
- **啟動 URL**：指定在瀏覽器中開啟的 URL。 其預設為 `localhost`。
- **連接埠號碼**：在未於 URL 中指定連接埠的情況下，要使用的連接埠 (Visual Studio 預設會自動選取一個)。 此設定可讓您覆寫 `SERVER_PORT` 環境變數的預設值，該預設值是範本用來設定本機偵錯伺服器要接聽的連接埠。

[執行伺服器命令] 和 [偵錯伺服器命令] 群組中的屬性 (下圖所示的為後者) 會決定網頁伺服器的啟動方式。 因為許多架構要求使用目前專案外部的指令碼，您可以在這裡設定指令碼，而啟始模組的名稱可以當作參數傳遞。

- **命令**：可以是 Python 指令碼 (*\*.py* 檔案)、模組名稱 (也就是 `python.exe -m module_name`) 或單一程式碼行 (也就是 `python.exe -c "code"`)。 下拉式清單中的值會指出所要使用的類型。
- **引數**︰這些引數會緊跟著命令在命令列上傳遞。
- **環境**： \<NAME> = \<VALUE> 指定環境變數之配對的行分隔清單。 這些變數是在所有可修改環境的屬性 (例如連接埠號碼和搜尋路徑) 之後設定，因此可能會覆寫這些值。

任何的專案屬性或環境變數都可以使用 MSBuild 語法指定，例如：`$(StartupFile) --port $(SERVER_PORT)`。
`$(StartupFile)` 是啟始檔案的相對路徑，而 `{StartupModule}` 是啟始檔案的可匯入名稱。 `$(SERVER_HOST)` 和 `$(SERVER_PORT)` 是一般環境變數，會自動由 [啟動 URL] 和 [連接埠號碼] 屬性設定，或是由 [環境] 屬性設定。

> [!Note]
> [執行伺服器命令] 中的值會搭配 [偵錯] > [啟動伺服器] 命令或 **Ctrl**+**F5** 使用；[偵錯伺服器命令] 群組中的值則是搭配 [偵錯] > [啟動偵錯伺服器] 命令或 **F5** 使用。

### <a name="sample-bottle-configuration"></a>範例 Bottle 設定

[Bottle Web 專案] 範本包含會執行必要設定的未定案程式碼。 不過，匯入的 Bottle 應用程式可能不會包括此程式碼，在這種情況下，下列設定會使用已安裝的 `bottle` 模組啟動應用程式：

- [執行伺服器命令] 群組：
  - **命令**： `bottle` (模組) 
  - **引數**： `--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- [偵錯伺服器命令] 群組：
  - **命令**： `bottle` (模組) 
  - **引數** `--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

使用 Visual Studio 進行偵錯時，不建議使用 `--reload` 選項。

### <a name="sample-pyramid-configuration"></a>範例 Pyramid 設定

Pyramid 應用程式目前最適合使用 `pcreate` 命令列工具建立。 一旦建立應用程式之後，就可以使用 [ [**從現有的 Python 程式碼**](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files) ] 範本匯入該應用程式。 這麼做之後，請選取 [一般 Web 專案] 自訂項目來設定選項。 這些設定會假設 Pyramid 已經安裝到位於 `..\env` 的虛擬環境。

- [偵錯] 群組：
  - **伺服器埠**： 6543 (或 *.ini* 檔案中設定的任何內容) 

- [執行伺服器命令] 群組：
  - 命令：`..\env\scripts\pserve-script.py` (指令碼)
  - 引數：`Production.ini`

- [偵錯伺服器命令] 群組：
  - 命令：`..\env\scripts\pserve-script.py` (指令碼)
  - 引數：`Development.ini`

> [!Tip]
> 您可能需要設定專案的 [工作目錄] 屬性，因為 Pyramid 應用程式通常會位在專案根資料夾的下一層資料夾中。

### <a name="other-configurations"></a>其他設定

如果您有另一個架構的設定想要共用，或是想要求另一個架構的設定，請在 [GitHub 上提出問題](https://github.com/Microsoft/PTVS/issues)。

## <a name="convert-a-project-to-azure-cloud-service"></a>將專案轉換成 Azure 雲端服務

[ **轉換成 Microsoft Azure 雲端服務專案** ] 命令 (下圖) 將雲端服務專案新增至您的方案。 此專案包括要使用之虛擬機器和服務的部署設定及組態。 使用雲端專案上的 [發行] 命令以部署至雲端服務；Python 專案上的 [發行] 命令仍然會部署至網站。 如需詳細資訊，請參閱 [Azure 雲端服務專案](python-azure-cloud-service-project-template.md)。

![[轉換為 Microsoft Azure 雲端服務專案] 命令](media/template-web-convert-menu.png)

## <a name="see-also"></a>另請參閱

- [Python 項目範本參考](python-item-templates.md)
- [發佈至 Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)