---
title: 搭配 Python 使用 CookieCutter 範本
description: Visual Studio 支援圖形 Cookiecutter 延伸模組來探索適用於 Python 程式碼的範本，並從這些範本建立專案。
ms.date: 01/28/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 08ae2e13f094535eae0447cc3b8d4acf4c806a99
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920614"
---
# <a name="use-the-cookiecutter-extension"></a>使用 Cookiecutter 延伸模組

[Cookiecutter (英文)](https://cookiecutter.readthedocs.io/en/latest/) 提供尋找範本、輸入範本選項和建立專案及檔案的圖形化使用者介面。 它隨附於 Visual Studio 2017 和更新版本，並可在舊版的 Visual Studio 中另行安裝。

Cookiecutter 需要 Python 3.3 或更新版本 (32 位元或 64 位元) 或 Anaconda 3 4.2 或更新版本 (32 位元或 64 位元)。 如果沒有適合的 Python 解譯器，Visual Studio 會顯示警告。 如果您在 Visual Studio 正在執行時安裝 Python 解譯器，請選取 [Cookiecutter] 工具列上的 [ **首頁** ] 按鈕，以偵測新安裝的解譯器。 (請參閱 [Python 環境](managing-python-environments-in-visual-studio.md)以取得環境的一般資訊)。

安裝之後，選取 [ **View**  >  **Cookiecutter Explorer** ] 開啟其視窗：

![Cookiecutter 主視窗](media/cookiecutter-overview.png)

## <a name="cookiecutter-workflow"></a>Cookiecutter 工作流程

Cookiecutter 的使用程序包含瀏覽和選取範本、將其複製到本機電腦、設定選項，然後從該範本建立程式碼，如下列各節所述。

### <a name="browse-templates"></a>瀏覽範本

Cookiecutter 首頁會顯示可選擇的範本清單，並分為下列群組︰

| 群組 | 描述 |
| --- | --- |
| **已安裝** | 已安裝到本機電腦的範本。 使用線上範本時，其存放庫會自動複製到 *~/.cookiecutters* 的子資料夾。 您可以透過按下 **Delete** 來刪除選取的已安裝範本。 |
| **建議需求** | 從建議的摘要載入的範本。 預設摘要是由 Microsoft 組織。 如需自訂摘要的詳細資訊，請參閱下列 [Cookiecutter 選項](#cookiecutter-options)。 |
| **GitHub** | Cookiecutter 關鍵字的 GitHub 搜尋結果。 從 GitHub 傳回的結果會經過重新編頁，如果還有其他結果，[載入更多 (Load More)] 會出現在清單的結尾。 |
| **Custom** | 在搜尋方塊中輸入自訂位置時，它會顯示在此群組。 您可以輸入 GitHub 存放庫的完整路徑，或輸入本機磁碟上的資料夾完整路徑。 |

### <a name="cloning"></a>複製

當您選取一個範本並按 [下一步 (Next)] 時，Cookiecutter 會建立工作用的本機複本。

如果您從 [建議] 或 [GitHub] 群組選取範本，或在搜尋方塊中輸入自訂 URL 並選取該範本，系統即會將其複製並安裝到您的本機電腦上。 如果在先前的 Visual Studio 工作階段中已安裝該範本，則會自動刪除它並複製最新版本。

如果您從 [已安裝] 群組選取範本，或在搜尋方塊中輸入自訂資料夾路徑並選取該範本，Visual Studio 會載入該範本而不複製。

> [!Important]
> Cookiecutter 範本會複製到單一資料夾 *~/.cookiecutters* 之下。 每個子資料夾會以 Git 存放庫的名稱命名，不包括 GitHub 使用者名稱。 如果您複製不同作者但名稱相同的不同範本，可能會發生衝突。 在此情況下，Cookiecutter 會禁止您以名稱相同的不同範本覆寫現有的範本。 若要安裝其他範本，您必須先刪除現有的範本。

### <a name="set-template-options"></a>設定範本選項

在本機安裝範本之後，Cookiecutter 會顯示選項頁面，您可在該處指定您希望 Cookiecutter 於何處產生檔案及其他選項︰

![Cookiecutter 選項頁面](media/cookiecutter-template-options.png)

每個 Cookiecutter 範本都會定義自己的一組選項，並指定每個選項的預設值 (在每個輸入欄位中顯示為建議的文字)。 預設值可以是程式碼片段 (通常在它是使用其他選項的動態值時)。

您可以利用使用者組態檔為特定選項自訂預設值。 當 Cookiecutter 延伸模組偵測到使用者組態檔時，它會以使用者組態的預設值覆寫範本的預設值。 Cookiecutter 文件的[User Config](https://cookiecutter.readthedocs.io/en/latest/advanced/user_config.html) (使用者組態) 一節對此行為有相關討論。

如果此範本指定在程式碼產生後執行特定的 Visual Studio 工作，會顯示一個額外的 [完成時執行額外工作 (Run additional tasks on completion)] 選項，可讓您選擇退出那些工作。 最常用的工作是開啟網頁瀏覽器、在編輯器中開啟檔案及安裝相依項目等。

### <a name="create"></a>建立

設定選項之後，請選取 [建立] 來產生程式碼 (如果輸出資料夾不是空的，會出現警告)。 如果您熟悉範本的輸出，而且不介意覆寫檔案，您可以關閉此警告。 否則，請選取 [取消 (Cancel)]、指定空白資料夾，並手動將建立的檔案複製到非空白的輸出資料夾。

順利建立檔案之後，Cookiecutter 會提供在 [方案總管] 中開啟檔案的選項：

![顯示 [方案總管] 命令的 Cookiecutter](media/cookiecutter-files-created.png)

## <a name="cookiecutter-options"></a>Cookiecutter 選項

Cookiecutter 選項可透過 [**工具**  >  **選項**]  >  **Cookiecutter** 取得：

![Cookiecutter 選項](media/cookiecutter-tools-options.png)

| 選項 | Description |
| --- | --- |
| **建議的摘要 URL** | 建議的範本摘要的位置。 它可以是 URL 或本機檔案的路徑。 將 URL 留白，會使用 Microsoft 組織的預設摘要。 摘要提供簡單的範本位置清單 (以新行區隔)。 若要要求變更已組織的摘要，請針對 [GitHub 上的來源 (英文)](https://github.com/Microsoft/PTVS/blob/master/Python/Product/Cookiecutter/CookiecutterFeed.txt) 提出提取要求。 |
| **顯示說明** | 控制 Cookiecutter 視窗頂端的說明資訊列的可見性。 |

## <a name="optimize-cookiecutter-templates-for-visual-studio"></a>最佳化 Visual Studio 的 Cookiecutter 範本

如需撰寫 Cookiecutter 範本的基本概念，請參閱 [Cookiecutter 文件](https://cookiecutter.readthedocs.io/en/latest/first_steps.html)。 Visual Studio 的 Cookiecutter 延伸模組支援為 Cookiecutter v1.4 建立的範本。

範本變數的預設轉譯方式取決於資料類型 (字串或清單)︰

- 字串：變數名稱的標籤、可輸入值的文字方塊，以及顯示預設值的浮水印。 文字方塊上的工具提示會顯示預設值。
- 清單：變數名稱的標籤、可選取值的下拉式方塊。 下拉式方塊上的工具提示會顯示預設值。

透過在 Visual Studio 特定 (且由 Cookiecutter CLI 忽略) 的 *cookiecutter.json* 檔案中指定額外的中繼資料，可針對此轉譯做改善。 所有屬性都是選擇性的︰

| 屬性 | 描述 |
| --- | --- |
| 標籤 | 指定變數的編輯器上方顯示的內容，取代變數的名稱。 |
| Description | 指定編輯控制項上顯示的工具提示，取代該變數的預設值。 |
| URL | 將標籤變更成超連結，並含有一個顯示 URL 的工具提示。 選取超連結，就會將使用者的預設瀏覽器開啟至該 URL。 |
| 選取器 | 可自訂變數的編輯器。 目前支援下列選取器︰<ul><li>`string`︰標準文字方塊，字串的預設值。</li><li>`list`︰標準下拉式方塊，清單的預設值。</li><li>`yesno`︰可在 `y` 和 `n` 之間選擇的下拉式方塊，適用於字串。</li><li>`odbcConnection`：包含 **[...] 按鈕的** 文字方塊，會顯示資料庫連接對話方塊。</li></ul> |

範例：

```json
{
    "site_name": "web-app",
    "python_version": ["3.5.2", "2.7.12"],
    "use_azure": "y",

    "_visual_studio": {
        "site_name": {
            "label": "Site name",
            "description": "E.g. <site-name>.azurewebsites.net (can only contain alphanumeric characters and `-`)"
        },
        "python_version": {
            "label": "Python version",
            "description": "The version of Python to run the site on"
        },
        "use_azure" : {
            "label": "Use Azure",
            "description": "Include Azure deployment files",
            "selector": "yesno",
            "url": "https://azure.microsoft.com"
        }
    }
}
```

### <a name="run-visual-studio-tasks"></a>執行 Visual Studio 工作

Cookiecutter 有一個稱為 *Post-Generate Hook* (產生後置掛勾) 的功能，可在產生檔案之後執行任意 Python 程式碼。 雖然有彈性，卻不能輕鬆存取 Visual Studio。

例如，您可能想在 Visual Studio 編輯器或其網頁瀏覽器中開啟檔案，或是觸發會提示使用者建立虛擬環境並安裝套件需求的 Visual Studio UI。

針對這些情況，Visual Studio 會在 *cookiecutter.json* 中尋找擴充的中繼資料，該中繼資料描述在使用者於 [方案總管] 開啟產生的檔案後或檔案加入現有的專案後要執行的命令 (同樣地，使用者可以透過清除範本選項中的 [完成時執行其他工作]，選擇不要執行工作)。

範例：

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": "{{cookiecutter._output_folder_path}}\\readme.txt"
    },
    {
        "name": "Cookiecutter.ExternalWebBrowser",
        "args": "https://docs.microsoft.com"
    },
    {
        "name": "Python.InstallProjectRequirements",
        "args": "{{cookiecutter._output_folder_path}}\\dev-requirements.txt"
    }
]
```

命令是依名稱指定，而且應使用非當地語系化 (英文) 名稱在 Visual Studio 的當地語系化安裝上操作。 您可以在 Visual Studio **命令** 視窗中測試和探索命令名稱。

如果您想傳遞單一引數，請將其指定為字串，如上一個範例所示。

如果您不需要傳遞引數，請將它保留為空字串，或從 JSON 省略：

```json
"_visual_studio_post_cmds": [
    {
        "name": "View.WebBrowser"
    }
]
```

使用多個引數的陣列。 針對參數，請將參數和其值分割成不同的引數，並使用適當引用。 例如：

```json
"_visual_studio_post_cmds": [
    {
        "name": "File.OpenFile",
        "args": [
            "{{cookiecutter._output_folder_path}}\\read me.txt",
            "/e:",
            "Source Code (text) Editor"
        ]
    }
]
```

引數可以參考其他 Cookiecutter 變數。 在上述範例中，內部的 `_output_folder_path` 變數用以組成所產生檔案的絕對路徑。

請注意，只有在加入檔案到現有專案時，`Python.InstallProjectRequirements` 命令才有效。 此限制的存在，是因為命令是由 [方案總管] 中的 Python 專案處理，而在 [方案總管] - [資料夾檢視] 中沒有可接收訊息的專案。 我們希望移除未來版本 (的限制，並在一般) 中提供更好的 **資料夾檢視** 支援。

## <a name="troubleshooting"></a>疑難排解

### <a name="error-loading-template"></a>載入範本時發生錯誤

有些範本可能在其 *cookiecutter.json* 中使用無效的資料類型，例如布林值。 選取範本資訊窗格中的 [問題] 連結，將這類執行個體報告給範本作者。

### <a name="hook-script-failed"></a>Hook 指令碼失敗

有些範本可能使用與 Cookiecutter UI 不相容的產生後置指令碼。 例如，查詢使用者輸入的指令碼將因為沒有終端機主控台而失敗。

### <a name="hook-script-not-supported-on-windows"></a>Windows 上不支援 Hook 指令碼

如果後置指令碼為 *.sh*，它可能未與您 Windows 電腦上的應用程式建立關聯。 您可能會看到 Windows 對話方塊，要求您在 Windows 市集尋找相容的應用程式。

### <a name="templates-with-known-issues"></a>含有已知問題的範本

複製失敗：

- **wildfish/cookiecutter-django-crud** (子資料夾名稱中有無效字元 `|`)
- **cookiecutter-pyvanguard** (子資料夾名稱中有無效字元 `|`)

載入失敗：

- **chrisdev/wagtail-cookiecutter-foundation-cookiecutter-foundation** (在 *cookiecutter.js上* 使用布林類型) 
- **quintoandar/cookiecutter-android** (沒有範本資料夾)

執行失敗：

- **iknite/cookiecutter-ansible-role** (後置 Hook 指令碼需要主控台輸入)
- **benregn/cookiecutter-django-ansible** (Jinja 錯誤)

使用 bash (不嚴重)：

- **openstack-dev/cookiecutter**
