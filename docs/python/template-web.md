---
title: "Visual Studio 中的 Python Web 專案範本 | Microsoft Docs"
ms.custom: 
ms.date: 07/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 401e7725-8be5-4e67-862c-bf0690a529e3
caps.latest.revision: "11"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 2a21c43e039d9a1109f1870516e9b3d4ea3c644b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="python-web-project-templates"></a>Python Web 專案範本

Visual Studio 中的 Python 支援透過專案範本以及偵錯啟動器 (其可針對處理各種架構進行設定)，在 Bottle、Flask 和 Django 架構中開發 Web 專案。 針對 Pyramid 等其他架構，您也可以使用一般的「Web 專案」範本。

Visual Studio 不包含這些架構本身。 您必須以滑鼠右鍵按一下專案，並選取 [Python] > [安裝/升級架構] 來個別安裝架構。

執行時，從範本 (透過 [檔案] > [新增] > [專案] 存取) 建立的專案會搭配隨機選取的本機連接埠啟動網頁伺服器，於偵錯期間開啟您的預設瀏覽器，並允許直接發佈至 Microsoft Azure。

![新增 Web 專案範本](media/template-web-new-project.png)

Bottle、Flask 和 Django 範本各自都包含一個含有一些頁面及靜態檔案的起始網站。 此程式碼足以用來在本機 (其中某些設定需要從環境取得) 執行伺服器並進行偵錯，以及部署至 Microsoft Azure (其中必須提供 [WSGI 應用程式 (英文)](http://www.python.org/dev/peps/pep-3333/) 物件)。

從架構特定的範本建立專案時，系統會顯示對話方塊來協助您使用 pip 安裝必要的套件。 另外也建議您針對 Web 專案使用[虛擬環境](python-environments.md#virtual-environments)，如此當您發佈網站時，就會包含正確的相依性：

![安裝專案範本所需之封裝的對話方塊](media/template-web-requirements-txt-wizard.png)

部署至 Microsoft Azure App Service 時，請選取 Python 的版本作為[網站延伸模組](https://aka.ms/PythonOnAppService)，並手動安裝套件。 此外，由於從 Visual Studio 部署時，Azure App Service 「不會」自動從 `requirements.txt` 檔案安裝封裝，請依照 [aka.ms/PythonOnAppService (英文)](https://aka.ms/PythonOnAppService) 上的設定詳細資料進行。

Microsoft Azure 雲端服務「確實」支援 `requirements.txt` 檔案。 如需詳細資料，請參閱 [Azure 雲端服務專案](template-azure-cloud-service.md)。

## <a name="debugging"></a>偵錯

當啟動 Web 專案進行偵錯時，Visual Studio 會在本機啟動網頁伺服器，然後開啟預設瀏覽器並移至該位址及連接埠。 若要指定其他選項，請以滑鼠右鍵按一下專案，選取 [屬性]，並選取 [Web 啟動器] 索引標籤：

  ![一般 Web 範本的 Web 啟動器屬性](media/template-web-launcher-properties.png)

在 [偵錯] 群組中：

- **搜尋路徑**、**指令碼引數**、**解譯器引數**和**解譯器路徑**：這些選項與[一般偵錯](debugging.md)所使用的相同
- **啟動 URL**：指定在瀏覽器中開啟的 URL。 預設值為 `localhost`。
- **連接埠號碼**：在未於 URL 中指定連接埠的情況下，要使用的連接埠 (Visual Studio 預設會自動選取一個)。 此設定可讓您覆寫 `SERVER_PORT` 環境變數的預設值，該預設值是範本用來設定本機偵錯伺服器要接聽的連接埠。

[執行伺服器命令] 和 [偵錯伺服器命令] 群組中的屬性 (下圖所示的為後者) 會決定 Web 伺服器的啟動方式。 因為許多架構要求使用目前專案外部的指令碼，您可以在這裡設定指令碼，而啟始模組的名稱可以當作參數傳遞。

- **命令**：可以是 Python 指令碼 (`*.py` 檔案)、模組名稱 (也就是 `python.exe -m module_name`) 或單一程式碼行 (也就是 `python.exe -c "code"`)。 下拉式清單中的值會指出是上述哪種類型。
- **引數**︰這些引數會緊跟著命令在命令列上傳遞。
- **環境**︰以新行來分隔的 `NAME=VALUE` 配對清單，可指定環境變數。 這些變數是在所有可修改環境的屬性 (例如連接埠號碼和搜尋路徑) 之後設定，因此可能會覆寫這些值。

任何的專案屬性或環境變數都可以使用 MSBuild 語法指定，例如：`$(StartupFile) --port $(SERVER_PORT)`。
`$(StartupFile)` 是啟始檔案的相對路徑，而 `{StartupModule}` 是啟始檔案的可匯入名稱。 `$(SERVER_HOST)` 和 `$(SERVER_PORT)` 是一般環境變數，會自動由 [啟動 URL] 和 [連接埠號碼] 屬性設定，或是由 [環境] 屬性設定。

> [!Note]
> [執行伺服器命令] 中的值會搭配 [偵錯] > [啟動伺服器] 命令或 Ctrl-F5 使用；[偵錯伺服器命令] 群組中的值則是搭配 [偵錯] > [啟動偵錯伺服器] 命令或 F5 使用。


### <a name="sample-bottle-configuration"></a>範例 Bottle 設定

Bottle Web 專案範本包括會執行必要設定的未定案程式碼。 不過，匯入的 Bottle 應用程式可能不會包括此程式碼，在這種情況下，下列設定會使用已安裝的 `bottle` 模組啟動應用程式：

- [執行伺服器命令] 群組：
    - **命令**：`bottle` (模組)
    - **引數**：`--bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

- [偵錯伺服器命令] 群組：
    - **命令**：`bottle` (模組)
    - **引數**：`--debug --bind=%SERVER_HOST%:%SERVER_PORT% {StartupModule}:app`

使用 Visual Studio 進行偵錯時，不建議使用 `--reload` 選項。

### <a name="sample-pyramid-configuration"></a>範例 Pyramid 設定

Pyramid 應用程式目前最適合使用 `pcreate` 命令列工具建立。 一旦建立應用程式，便可以使用[從現有的 Python 程式碼](python-projects.md#creating-a-project-from-existing-files)範本匯入該應用程式。 這麼做之後，請選取 [一般 Web 專案] 自訂項目來設定選項。 這些設定會假設 Pyramid 已經安裝到位於 `..\env` 的虛擬環境。

- [偵錯] 群組：
    - **伺服器連接埠**：6543 (或是 .ini 檔案中設定的值)

- [執行伺服器命令] 群組：
    - 命令：`..\env\scripts\pserve-script.py` (指令碼)
    - 引數：`Production.ini`

- [偵錯伺服器命令] 群組：
    - 命令：`..\env\scripts\pserve-script.py` (指令碼)
    - 引數：`Development.ini`

> [!Tip]
> 您可能必須設定專案的 [工作目錄] 屬性，因為 Pyramid 應用程式的層級通常會比來源樹狀結構的最上層目錄再深一層。


### <a name="other-configurations"></a>其他設定

如果您有另一個架構的設定想要共用，或是想要求另一個架構的設定，請在 [GitHub 上提出問題](https://github.com/Microsoft/PTVS/issues)。

## <a name="publishing-to-azure-app-service"></a>發佈至 Azure App Service

有兩種主要方式可以發佈至 Azure App Service。 首先，來自原始檔控制的部署可以使用與其他語言相同的方式使用，如 [Azure 文件](http://azure.microsoft.com/en-us/documentation/articles/web-sites-publish-source-control/)中所述。 若要直接從 Visual Studio 發佈，請以滑鼠右鍵按一下專案，然後選取 [發佈]：

![專案操作功能表上的 [發佈] 命令](media/template-web-publish-command.png)

選取命令之後，精靈會逐步引導您完成建立網站或匯入發佈設定，預覽已修改的檔案，然後發佈至遠端伺服器。

當您在 App Service 上建立網站時，需要安裝 Python 以及您網站所需的所有套件。 您可以先發行網站，但它在您設定 Python 之後才會執行。

若要在 App Service 上安裝 Python，建議您使用[網站擴充功能 (英文)](http://www.siteextensions.net/packages?q=Tags%3A%22python%22) (siteextensions.net)。 這些延伸模組是 Python [正式版本](https://www.python.org) 的複本，並已針對 Azure App Service 最佳化並重新封裝。

網站延伸模組可以透過 [Azure 入口網站](https://portal.azure.com/)進行部署。 針對 App Service 選取 [開發工具] > [延伸模組] 刀鋒視窗，並選取 [新增]，然後捲動清單以尋找 Python 項目：

![在 Azure 入口網站上新增網站擴充功能](media/template-web-site-extensions.png)

如果您使用 JSON 部署範本，您可以將網站擴充功能指定為網站的資源：

```json
{
    "resources": [
    {
        "apiVersion": "2015-08-01",
        "name": "[parameters('siteName')]",
        "type": "Microsoft.Web/sites",
        ...
    },
    "resources": [
    {
        "apiVersion": "2015-08-01",
        "name": "python352x64",
        "type": "siteextensions",
        "properties": { },
        "dependsOn": [
            "[resourceId('Microsoft.Web/sites', parameters('siteName'))]"
        ]
    },
    ...
}
```

最後，您可以透過[開發主控台 (英文)](https://github.com/projectkudu/kudu/wiki/Kudu-console) 登入，並從該處安裝網站擴充功能。

目前，安裝封裝的建議方式，是在安裝網站擴充功能後使用開發主控台，並直接執行 PIP。 使用 Python 的完整路徑非常重要，否則您可能會執行錯誤版本的 Python，而且您通常並不需要使用虛擬環境。 例如: 

```
c:\Python35\python.exe -m pip install -r D:\home\site\wwwroot\requirements.txt

c:\Python27\python.exe -m pip install -r D:\home\site\wwwroot\requirements.txt
```

部署到 Azure App Service 後，您的網站會在 Microsoft IIS 後方執行。 若要讓您的網站搭配 IIS 運作，您至少需要新增 `web.config` 檔案。 有可用的範本可供一些常見的部署目標使用，您可以以滑鼠右鍵按一下專案並選取 [新增] > [新增項目]\(請參閱下方的對話方塊) 來取得它們，而且您可以輕鬆地修改這些設定以用於其他用途。 如需可用組態設定的資訊，請參閱 [IIS Configuration Reference](https://www.iis.net/configreference) (IIS 設定參考)。

![Azure 項目範本](media/template-web-azure-items.png)

可用的項目包括︰

- Azure web.config (FastCGI)：新增 `web.config` 檔案，適用於您的應用程式提供 [WSGI (英文)](https://wsgi.readthedocs.io/en/latest/) 物件以處理傳入連線的情況。
- Azure web.config (HttpPlatformHandler)：新增 `web.config` 檔案，適用於您的應用程式針對傳入連線接聽通訊端的情況。
- Azure 靜態檔案 web.config：當您有上述其中一個 `web.config` 檔案時，請將該檔案新增至子目錄，以排除它不讓應用程式進行處理。
- Azure 遠端偵錯 web.config：新增透過 WebSockets 進行遠端偵錯的必要檔案。
- Web 角色支援檔案：包含雲端服務 Web 角色的預設部署指令碼。
- 背景工作角色角色支援檔案：包含雲端服務背景工作角色的預設部署及啟動指令碼。

如果您將偵錯 `web.config` 範本新增到專案，並計劃使用 Python 遠端偵錯，則必須使用 [偵錯] 設定來發行網站。 此設定不同於目前使用中的方案組態，且一律預設為 [發行]。 若要變更它，請開啟 [設定] 索引標籤，並使用發佈精靈的 [設定] 下拉式方塊 (如需建立並部署至 Azure Web Apps 的詳細資訊，請參閱 [Azure 文件](https://azure.microsoft.com/develop/python/))：

![正在變更發佈設定](media/template-web-publish-config.png)

[轉換為 Microsoft Azure 雲端服務專案] 命令 (如下圖) 會將雲端服務專案新增至您的方案。 此專案包括要使用之虛擬機器和服務的部署設定及組態。 使用雲端專案上的 [發行] 命令以部署至雲端服務；Python 專案上的 [發行] 命令仍然會部署至網站。 如需詳細資料，請參閱 [Azure 雲端服務專案](template-azure-cloud-service.md)。

![[轉換為 Microsoft Azure 雲端服務專案] 命令](media/template-web-convert-menu.png)
