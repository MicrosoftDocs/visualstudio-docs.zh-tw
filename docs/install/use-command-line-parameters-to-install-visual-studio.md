---
title: "使用命令列參數安裝 Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 223750aef8d997c6ae017f49ea0a9522bdba72bc
ms.openlocfilehash: 2b702407996fd104b62d9b8c6874d7914d7bd2e8
ms.contentlocale: zh-tw
ms.lasthandoff: 08/10/2017

---
# <a name="use-command-line-parameters-to-install-visual-studio-2017"></a>使用命令列參數來安裝 Visual Studio 2017
當您從命令提示字元安裝 Visual Studio 2017 時，可以使用各種命令列參數來控制或自訂安裝。 您可以從命令列執行下列動作：

- 使用預先選取的特定選項開始安裝。
- 自動化安裝程序。
- 建立安裝檔案的快取 (配置)，以供稍後使用。

命令列選項會搭配安裝程式啟動載入器使用，這是起始下載程序的小型檔案 (約 1 MB)。 當您從 Visual Studio 網站下載時，啟動載入器是第一個啟動的可執行檔。 您可以從下列連結，取得適用於您要安裝之產品版本最新版啟動載入器的直接連結：

* [Visual Studio 2017 Enterprise](https://aka.ms/vs/15/release/vs_enterprise.exe)
* [Visual Studio 2017 Professional](https://aka.ms/vs/15/release/vs_professional.exe)
* [Visual Studio 2017 Community](https://aka.ms/vs/15/release/vs_community.exe)

## <a name="list-of-command-line-parameters"></a>命令列參數清單  
 Visual Studio 命令列參數區分大小寫。

> 語法：`vs_enterprise.exe [command] <options>...`

(根據您要安裝的產品版本，適當地取代 `vs_enterprise.exe`。 如需範例，請參閱[命令列參數範例](command-line-parameter-examples.md)頁面)。

| **命令** | **說明** |
| ----------------------- | --------------- |
| (空白) | 安裝產品。 |
| `modify` | 修改所安裝的產品。 |
| `update` | 更新所安裝的產品。 |
| `repair` | 修復所安裝的產品。 |
| `uninstall` | 解除安裝所安裝的產品。 |

| **安裝選項** | **說明** |
| ----------------------- | --------------- |
| `--installPath <dir>` | 要操作之執行個體的安裝目錄。 若是安裝命令，這是**選擇性的**，而且是執行個體的安裝位置。 若是其他命令，這是**必要的**，而且是先前安裝之執行個體的安裝位置。 |
| `--addProductLang <language-locale>` | **選擇性**︰在安裝或修改作業期間，這會決定要安裝到產品的 UI 語言套件。 它可在命令列上出現多次，以新增多個語言套件。 如果不存在，安裝將會使用電腦地區設定。 如需詳細資訊，請參閱此頁面上的[語言地區設定清單](#list-of-language-locales)一節。|
| `--removeProductLang <language-locale>` | **選擇性**︰在安裝或修改作業期間，這會決定要從產品移除的 UI 語言套件。 它可在命令列上出現多次，以新增多個語言套件。 如需詳細資訊，請參閱此頁面上的[語言地區設定清單](#list-of-language-locales)一節。|
| `--add <workload or component ID>` | **選擇性**：要新增的工作負載或元件識別碼。 安裝成品的必要元件，但不安裝建議或選用元件。 您可以使用 `--includeRecommended` 和/或 `--includeOptional`，以全域控制其他元件。 若要進行更精細的控制，可將 `;includeRecommended` 或 `;includeOptional` 附加到識別碼 (例如 `--add Workload1;includeRecommended` 或 `--add Workload2;includeRecommended;includeOptional`)。 如需詳細資訊，請參閱[工作負載和元件識別碼 (英文)](workload-and-component-ids.md) 頁面。 如有必要，您可以重複此選項。|
| `--remove <workload or component ID>` | **選擇性**：要移除的工作負載或元件識別碼。 如需詳細資訊，請參閱[工作負載和元件識別碼 (英文)](workload-and-component-ids.md) 頁面。 如有必要，您可以重複此選項。|
| `--in <path>` | **選擇性**︰回應檔的 URI 或路徑。  |
| `--all` | **選擇性**︰是否要安裝產品的所有工作負載和元件。 |
| `--allWorkloads` | **選擇性**︰安裝所有工作負載及其必要元件，但不安裝建議或選擇性元件。 |
| `--includeRecommended` | **選擇性**︰包含所安裝之任何工作負載的建議元件，但不包含選擇性元件。 使用 `--allWorkloads` 或 `--add` 指定工作負載。 |
| `--includeOptional` | **選擇性**︰包含所安裝之任何工作負載的選擇性元件，但不包含建議元件。 使用 `--allWorkloads` 或 `--add` 指定工作負載。  |
| `--quiet, -q` | **選擇性**︰執行安裝時不顯示任何使用者介面。 |
| `--passive, -p` | **選擇性**︰顯示使用者介面，但不向使用者要求任何互動。 |
| `--norestart` | **選擇性**︰如果存在，與 `--passive` 或 `--quiet` 搭配的命令將不會自動重新啟動電腦 (如有必要)。 如果未指定 `--passive` 或 `--quiet`，則會略過此選項。  |
| `--nickname <name>` | **選擇性**︰這會定義要指派給所安裝產品的暱稱。 暱稱的長度不能大於 10 個字元。  |
| `--productKey` | **選擇性**︰這會定義要用於所安裝產品的產品金鑰。 此金鑰是以 `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` 或 `xxxxxxxxxxxxxxxxxxxxxxxxx` 格式，由 25 個英數字元構成的。 |
| `--help, --?, -h, -?` | 顯示此頁面的離線版本。 |

> 注意︰指定多個工作負載和元件時，您必須針對每個項目重複 `--add` 或 `--remove` 命令列參數。

| **配置選項** | **說明** |
| ----------------------- | --------------- |
| `--layout <dir>` | 指定一個目錄以建立離線安裝快取。 如需詳細資訊，請參閱[建立 Visual Studio 的網路型安裝](create-a-network-installation-of-visual-studio.md)。|
| `--lang <one or more language-locales>` | **選擇性**：搭配使用 `--layout`，以指定語言的資源套件來準備離線安裝快取。 如需詳細資訊，請參閱此頁面上的[語言地區設定清單](#list-of-language-locales)一節。|
| `--add <one or more workload or component IDs>` | **選擇性**︰一或多個要新增的工作負載或元件識別碼。 安裝成品的必要元件，但不安裝建議或選用元件。 您可以使用 `--includeRecommended` 和/或 `--includeOptional`，以全域控制其他元件。 若要進行更精細的控制，可將 `;includeRecommended` 或 `;includeOptional` 附加到識別碼 (例如 `--add Workload1;includeRecommended` 或 `--add Workload2;includeOptional`)。 如需詳細資訊，請參閱[工作負載和元件識別碼 (英文)](workload-and-component-ids.md) 頁面。 <br/>**注意**：如果使用了 `--add`，將只會下載特定的工作負載和元件及其相依性。 如果未指定 `--add`，即會將所有的工作負載和元件下載至配置。|
| `--includeRecommended` | **選擇性**︰包含所安裝之任何工作負載的建議元件，但不包含選擇性元件。 使用 `--allWorkloads` 或 `--add` 指定工作負載。 |
| `--includeOptional` | **選擇性**︰包含配置中所包含之任何工作負載的建議和選擇性元件。 使用 `--add` 指定工作負載。  |

| **進階安裝選項** | **說明** |
| ----------------------- | --------------- |
| `--channelId <id>` | **選擇性**：將安裝之執行個體的通道識別碼。 這對安裝命令是必要的，對其他指定了 `--installPath` 的命令則會予以略過。 |
| `--channelUri <uri>` | **選擇性**︰通道資訊清單的 URI。 此選項可用於安裝命令，但針對其他命令則會予以略過。 |
| `--installChannelUri <uri>` | **選擇性**︰要用於安裝之通道資訊清單的 URI。 以 `--channelUri` 指定的 URI (指定 `--installChannelUri` 時必須指定) 將用來偵測更新。 如果不需要更新，就必須指定沒有引數的 `--channelUri`。 此選項可用於安裝命令，但針對其他命令則會予以略過。 |
| `--installCatalogUri <uri>` | **選擇性**︰要用於安裝之目錄資訊清單的 URI。 如果指定，通道管理員會嘗試從此 URI 下載目錄資訊清單，再於安裝通道資訊清單中使用此 URI。 此參數可用來支援離線安裝，在此安裝中會使用已下載的產品目錄來建立配置快取。 此選項可用於安裝命令，但針對其他命令則會予以略過。 |
| `--productId <id>` | **選擇性**：要安裝之執行個體的產品識別碼。 在一般安裝情況中會預先填入此識別碼。 |
| `--wait` | **選擇性**︰處理序會等候安裝完成，然後才傳回結束代碼。 這適用於自動化安裝的情況，在此情況下，使用者必須等候安裝完成，才能處理該安裝的傳回碼。 |
| `--locale <language-locale>` | **選擇性**︰變更安裝程式本身的使用者介面顯示語言。 設定將會予以保留。 如需詳細資訊，請參閱此頁面上的[語言地區設定清單](#list-of-language-locales)一節。|
| `--cache` | **15.2 的新功能，選擇性**︰如果存在，套件將會在安裝之後加以保留，以利後續修復。 這將會覆寫要用於後續安裝、修復或修改的全域原則設定。 預設原則是快取套件。 若是解除安裝命令，則會略過此項。 如需詳細資訊，請參閱如何[停用或移動套件快取](disable-or-move-the-package-cache.md)。 |
| `--nocache` | **15.2 的新功能，選擇性**︰如果存在，套件將會在安裝或修復之後刪除。 只有在需要時才會再次下載它們，並於使用過後再次刪除。 這將會覆寫要用於後續安裝、修復或修改的全域原則設定。 預設原則是快取套件。 若是解除安裝命令，則會略過此項。 如需詳細資訊，請參閱如何[停用或移動套件快取](disable-or-move-the-package-cache.md)。 |
| `--noUpdateInstaller` | **15.2 的新功能，選擇性**︰如果存在，則在指定無訊息時會防止安裝程式更新它自己。 如果在需要安裝程式更新時指定具有無訊息的 noUpdateInstaller，則安裝程式會讓命令失敗，並傳回非零結束代碼。 |

## <a name="list-of-workload-ids-and-component-ids"></a>工作負載識別碼和元件識別碼清單
如需依 Visual Studio 產品排序的工作負載和元件識別碼清單，請參閱 [Visual Studio 2017 工作負載和元件識別碼](workload-and-component-ids.md)頁面。

## <a name="list-of-language-locales"></a>語言地區設定清單
| **語言地區設定** | **語言** |
| ----------------------- | --------------- |
| cs-CZ | 捷克文 |
| de-DE | 德文 |
| zh-TW | 英文 |
| es-ES | 西班牙文 |
| fr-FR | 法文 |
| it-IT | 義大利文 |
| ja-JP | 日文 |
| ko-KR | 韓文 |
| pl-PL | 波蘭文 |
| pt-BR | 葡萄牙文 - 巴西 |
| ru-RU | 俄文 |
| tr-TR | 土耳其文 |
| zh-CN | 簡體中文 |
| zh-TW | 繁體中文 |

## <a name="error-codes"></a>錯誤碼
根據作業的結果，`%ERRORLEVEL%` 環境變數將會設定為下列其中一個值：

| **值** | **結果** |
| --------- | ---------- |
| 0 | 作業成功完成 |
| 3010 | 作業成功完成，但安裝需要重新開機才能使用 |
| 其他 | 發生失敗狀況 - 請檢查記錄檔以取得詳細資訊 |

每個作業會在 `%TEMP%` 目錄中產生幾個記錄檔，以指出安裝進度。 依日期排序資料夾，然後分別針對啟動載入器、安裝程式應用程式和安裝程式引擎尋找開頭為 `dd_bootstrapper`、`dd_client` 和 `dd_setup` 的檔案。

## <a name="see-also"></a>請參閱

 * [安裝 Visual Studio 2017](install-visual-studio.md)
 * [建立 Visual Studio 2017 的離線安裝](create-an-offline-installation-of-visual-studio.md)
 * [Visual Studio 2017 安裝的命令列參數範例](command-line-parameter-examples.md)
 * [使用回應檔自動安裝 Visual Studio](automated-installation-with-response-file.md)
 * [回報 Visual Studio 2017 的問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

