---
title: 使用命令列參數來安裝 Visual Studio
titleSuffix: ''
description: 了解如何使用命令列參數來控制或自訂您的 Visual Studio 安裝。
ms.date: 4/16/2021
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 23c83611e7663d35b229517f1e0224eb4ae7bb57
ms.sourcegitcommit: 367a2d9df789aa617abaa09b0cd0a18db7357d0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107800807"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>使用命令列參數來安裝 Visual Studio

當您以程式設計方式或從命令提示字元安裝 Visual Studio 時，您可以使用各種命令列參數來控制或自訂安裝，以執行下列動作：

- 使用預先選取的特定選項和行為，在用戶端上開始安裝。
- 自動化安裝程序。
- 建立或維護產品檔案的網路設定，以安裝或更新用戶端電腦。

命令列選項可以搭配安裝程式啟動載入器使用，這是起始下載程式的小型 (~ 1 MB) 檔案，或部署至 [Microsoft Update 類別目錄](https://catalog.update.microsoft.com)的系統管理員更新套件。 

::: moniker range="vs-2017"

若要取得 Visual Studio 2017 15.9 版的啟動載入器，請移至 [**Visual Studio 的舊版**](https://visualstudio.microsoft.com/vs/older-downloads/) 頁面，並下載下列其中一個啟動載入器檔案：

| 版本 | 檔案名稱 |
|-------------|-----------------------|
|Visual Studio Enterprise 2017 15.9 版 | vs_enterprise.exe |
|Visual Studio Professional 2017 15.9 版 | vs_professional.exe |
|Visual Studio Build Tools 2017 15.9 版  | vs_buildtools.exe |

::: moniker-end

::: moniker range="vs-2019"

您可以從 Visual Studio 的 [ [下載] 頁面](https://visualstudio.microsoft.com/downloads) 或 [Visual Studio 2019 發行](https://docs.microsoft.com/visualstudio/releases/2019/history#installing-an-earlier-release) 版頁面，取得所選版本和 Visual Studio 版本的 Visual Studio 2019 啟動載入器。 您的安裝程式檔案（或啟動載入器）將符合或類似下列其中一項：

| 版本                    | 檔案                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio 2019 Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019)     |
| Visual Studio 2019 Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019) |
| Visual Studio 2019 Build Tools   | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019)     |
| Visual Studio 2019 Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019)  |

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>如果您先前已下載啟動載入器檔案，而且想要確認它的版本，請參閱。 在 Windows 中，開啟檔案總管，以滑鼠右鍵按一下啟動載入器檔案，選擇 [ **屬性**]，選擇 [ **詳細資料** ] 索引標籤，然後查看 **產品版本** 號碼。 若要將該號碼符合 Visual Studio 的版本，請參閱 [Visual Studio 組建編號和發行日期](visual-studio-build-numbers-and-release-dates.md) ] 頁面。

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>如果您先前已下載啟動載入器檔案，而且想要驗證其版本，請參閱以下說明。 在 Windows 中，開啟檔案總管，以滑鼠右鍵按一下啟動載入器檔案，選擇 [ **屬性**]，選擇 [ **詳細資料** ] 索引標籤，然後查看 **產品版本** 號碼。 若要將該號碼符合 Visual Studio 的版本，請參閱 [Visual Studio 2019 版本](https://docs.microsoft.com/visualstudio/releases/2019/history) 頁面。

::: moniker-end

您可以移至 [Microsoft Update 目錄](https://catalog.update.microsoft.com)、搜尋您要安裝的更新，然後按 [下載] 按鈕，以取得系統管理員更新。 系統管理員更新會假設電腦上已安裝 Visual Studio。 套用系統管理員更新不會起始全新安裝。

## <a name="bootstrapper-commands-and-command-line-parameters"></a>啟動載入器命令和命令列參數

當您以程式設計方式叫用 Visual Studio 啟動載入器以安裝產品或維護配置時，第一個參數是命令 (動詞) 的指令，以描述要執行的作業。 後續的選擇性命令列參數，其前面都加上兩個虛線 (--) ，進一步定義應該如何執行該作業。 所有 Visual Studio 命令列參數都不區分大小寫，而在 [命令列參數範例](command-line-parameter-examples.md) 頁面上可以找到其他範例。

語法範例： `vs_enterprise.exe [command] <optional parameters>...`

| **命令** | **說明** |
| ----------------------- | --------------- |
| (空白) | 預設命令會安裝產品，並用於所有版面配置維護作業。 |
| `modify` | 修改所安裝的產品。 |
| `update` | 更新所安裝的產品。 |
| `repair` | 修復所安裝的產品。 |
| `uninstall` | 解除安裝所安裝的產品。 |
| `export` | 將安裝選取項目匯出至安裝組態檔。 **注意**：只能搭配 vs_installer.exe 使用。 |


| **參數** | **說明** |
| ----------------------- | --------------- |
| `--installPath <dir>` | 針對預設的 install 命令，此參數是 **選擇性** 的，並且會描述在用戶端電腦上安裝實例的位置。 若為更新或修改之類的其他命令，則 **需要** 此參數，並代表要處理之實例的安裝目錄。 |
| `--add <one or more workload or component IDs>` | **選擇性**：在安裝或修改命令期間，此可重複參數會指定一或多個要新增的工作負載或元件識別碼。 安裝成品的必要元件，但不安裝建議或選用元件。 您可以使用 `--includeRecommended` 和/或參數來全域控制其他元件 `--includeOptional` 。 若要包含多個工作負載或元件，請重複 `--add` 命令 (例如 `--add Workload1 --add Workload2`)。 若要進行更精細的控制，可將 `;includeRecommended` 或 `;includeOptional` 附加到識別碼 (例如 `--add Workload1;includeRecommended` 或 `--add Workload2;includeRecommended;includeOptional`)。 如需詳細資訊，請參閱[工作負載與元件識別碼](workload-and-component-ids.md)頁面。 |
| `--remove <one or more workload or component IDs>` | **選擇性**：在 modify 命令期間，此可重複參數會指定要移除的一或多個工作負載或元件識別碼。 它補充和行為類似于 `--add` 參數。 |
| `--addProductLang <language-locale>` | **選擇性**：在安裝或修改命令期間，此可重複參數會指定應隨產品安裝的 UI 語言套件。 如果不存在，安裝會使用對應于電腦地區設定的語言套件。 如需詳細資訊，請參閱此頁面上的[語言地區設定清單](#list-of-language-locales)一節。|
| `--removeProductLang <language-locale>` | **選擇性**：在安裝或修改命令期間，此可重複參數會決定應該從產品移除的 UI 語言套件。  它補充和行為類似于 `--addProductLang` 參數。 |
| `--in <path>` | **選擇性**：可包含設定的 [回應](automated-installation-with-response-file.md) 檔 URI 或路徑。 |
| `--all` | **選擇性**：在安裝或修改命令期間，此參數會導致安裝產品的所有工作負載和元件。 |
| `--allWorkloads` | **選擇性**：在安裝或修改命令期間，此參數會安裝所有工作負載和元件，但不會安裝建議或選擇性元件。 |
| `--includeRecommended` | **選擇性**：在安裝或修改命令期間，此參數包含已安裝之任何工作負載的建議元件，但不包含選擇性元件。 使用 `--allWorkloads` 或 `--add` 指定工作負載。 |
| `--includeOptional` | **選擇性**：在安裝或修改命令期間，此參數包含已安裝之任何工作負載的選擇性元件，但不包含建議元件。 使用 `--allWorkloads` 或 `--add` 指定工作負載。  |
| `--quiet, -q` | **選擇性**：搭配任何命令使用時，此參數可防止在執行命令時顯示任何使用者介面。 |
| `--passive, -p` | **選擇性**：此參數會以非互動方式顯示使用者介面。 此參數與 (互斥，事實上) 參數的覆寫 `--quiet` 。  |
| `--norestart` | **選擇性**：此參數必須與 `--passive` 或 `--quiet` 參數配對。  在安裝、更新或修改命令期間，新增 `--norestart` 參數將會延遲任何必要的重新開機。 |
| `--force` | **選擇性**：此參數會強制 Visual Studio 關閉，即使有任何 Visual Studio 進程正在使用中。 |
| `--installWhileDownloading` | **選擇性**：在安裝、更新或修改命令期間，此參數可讓 Visual Studio 同時下載並安裝產品。 這是預設體驗。 |
| `--downloadThenInstall` | **選擇性**：在安裝、更新或修改命令期間，此參數會強制 Visual Studio 在安裝之前先下載所有檔案。 它與 `--installWhileDownloading` 參數互斥。 |
| `--nickname <name>` | **選擇性**：在安裝命令期間，此參數會定義要指派給所安裝產品的昵稱。 昵稱長度不可超過10個字元。  |
| `--productKey` | **選擇性**：在安裝命令期間，此參數會定義要用於已安裝產品的產品金鑰。 它是以格式或的25個英數位元所組成 `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` `xxxxxxxxxxxxxxxxxxxxxxxxx` 。 |
| `--help, --?, -h, -?` | 顯示此頁面的離線版本。 |
| `--config <path>` | **選擇性**：在安裝或修改作業期間，這會根據先前儲存的安裝設定檔來決定要新增的工作負載和元件。 這項作業是附加的，如果檔案中沒有任何工作負載或元件，則不會將它移除。 此外，也不會新增未套用至產品的專案。 在匯出作業期間，這會決定安裝組態檔的儲存位置。 |


> [!IMPORTANT]
> 指定多個不同的工作負載或元件或語言時，您 `--add` 必須 `--remove` 針對每個專案重複或命令列參數。

## <a name="layout-command-and-command-line-parameters"></a>版面配置命令和命令列參數
所有版面建構管理作業都會假設命令是預設的安裝， (空白) 。 因此，所有版面建構管理作業的開頭都必須是初始的必要 `--layout` 參數。  下表描述您可以使用命令列來建立或更新版面配置的其他參數。

| **版面配置參數** | **說明** |
| ----------------------- | --------------- |
| `--layout <dir>` | 指定要建立或更新離線安裝快取的目錄。 如需詳細資訊，請參閱[建立 Visual Studio 的網路型安裝](create-a-network-installation-of-visual-studio.md)。|
| `--lang <one or more language-locales>` | **選擇性**：搭配使用 `--layout`，以指定語言的資源套件來準備離線安裝快取。 如需詳細資訊，請參閱此頁面上的[語言地區設定清單](#list-of-language-locales)一節。|
| `--add <one or more workload or component IDs>` | **選擇性**︰一或多個要新增的工作負載或元件識別碼。 安裝成品的必要元件，但不安裝建議或選用元件。 您可以使用 `--includeRecommended` 和/或 `--includeOptional`，以全域控制其他元件。 若要進行更精細的控制，可將 `;includeRecommended` 或 `;includeOptional` 附加到識別碼 (例如 `--add Workload1;includeRecommended` 或 `--add Workload2;includeOptional`)。 如需詳細資訊，請參閱[工作負載與元件識別碼](workload-and-component-ids.md)頁面。 <br/>**注意**：如果使用了 `--add`，則只會下載特定的工作負載和元件及其相依性。 如果 `--add` 未指定，則會將所有工作負載和元件下載至版面配置。|
| `--includeRecommended` | **選用**：包含已安裝之任何工作負載的建議元件，但不包含選擇性元件。 使用 `--allWorkloads` 或 `--add` 指定工作負載。 |
| `--includeOptional` | **選擇性**︰包含配置中所包含之任何工作負載的建議和選擇性元件。 使用 `--add` 指定工作負載。  |
| `--keepLayoutVersion` | **選擇性**：將變更套用至版面配置，而不更新版面配置的版本。 |
| `--verify` | **選擇性**：驗證版面配置的內容。 會列出任何損毀或遺失的檔案。 |
| `--fix` | **選擇性**：驗證版面配置的內容。  如果有任何檔案損毀或遺失，則會重新下載。 必須有網際網路存取權才可修正配置。 |
| `--clean <one or more paths to catalogs>` | **選擇性**：從已更新為較新版本的版面配置中移除舊版元件。 |

| **Advanced layout 參數** | **說明** |
| ----------------------- | --------------- |
| `--channelId <id>` | **選擇性**：要安裝執行個體的通道識別碼。 這是安裝命令的必要項，而且如果指定了其他命令，則會忽略 `--installPath` 。 |
| `--channelUri <uri>` | **選擇性**：通道資訊清單的 URI。 如果不想要更新， `--channelUri` 可指向不存在的檔案 (例如，--channelUri C:\doesntExist.chman) 。 這可用於安裝命令;其他命令會忽略它。 |
| `--installChannelUri <uri>` | **選用**：要用於安裝之通道資訊清單的 URI。 `--channelUri` 指定的 URI (指定 `--installChannelUri` 時必須指定) 會用來偵測更新。 這可用於安裝命令;其他命令會忽略它。 |
| `--installCatalogUri <uri>` | **選用**：要用於安裝之目錄資訊清單的 URI。 如有指定，通道管理員會嘗試從此 URI 下載目錄資訊清單，再於安裝通道資訊清單中使用此 URI。 此參數可用來支援離線安裝，在此安裝中會使用已下載的產品目錄來建立配置快取。 這可用於安裝命令;其他命令會忽略它。 |
| `--productId <id>` | **選擇性**：即將安裝之實例的產品識別碼。 這會在正常的安裝狀況中預先填入。 |
| `--wait` | **選擇性**︰處理序會在安裝完成後才傳回結束代碼。 這適用於自動化安裝的情況，在此情況下，使用者必須等候安裝完成，才能處理該安裝的傳回碼。 |
| `--locale <language-locale>` | **選擇性**︰變更安裝程式本身的使用者介面顯示語言。 設定將會予以保留。 如需詳細資訊，請參閱此頁面上的[語言地區設定清單](#list-of-language-locales)一節。|
| `--cache` | **選擇性**：如果存在，套件將會在安裝之後保留，以供後續修復之用。 這會覆寫要用於後續安裝、修復或修改的全域原則設定。 預設原則是快取套件。 若是解除安裝命令，則會略過此項。 如需詳細資訊，請參閱如何[停用或移動套件快取](disable-or-move-the-package-cache.md)。 |
| `--nocache` | **選用**：如果存在，套件將會在安裝或修復之後刪除。 只有在需要時才會再次下載，並在使用之後再次刪除。 這會覆寫要用於後續安裝、修復或修改的全域原則設定。 預設原則是快取套件。 若是解除安裝命令，則會略過此項。 如需詳細資訊，請參閱如何[停用或移動套件快取](disable-or-move-the-package-cache.md)。 |
| `--noUpdateInstaller` | **選擇性**：如果有的話，會在指定 quiet 時防止安裝程式自行更新。 如果在需要安裝程式更新時指定具有無訊息的 noUpdateInstaller，則安裝程式會讓命令失敗，並傳回非零結束代碼。 |
| `--noWeb` | **選擇性**：如果有的話，Visual Studio 安裝程式會使用版面配置目錄中的檔案來安裝 Visual Studio。 如果使用者嘗試安裝不在版面配置中的元件，安裝程式會失敗。  如需詳細資訊，請參閱[從網路安裝部署](create-a-network-installation-of-visual-studio.md)。 <br/><br/> **重要**：此參數不會阻止 Visual Studio 安裝程式檢查是否有更新。 如需詳細資訊，請參閱[控制網路型 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)。 |
| `--path <name>=<path>` | **選用**：用來指定安裝的自訂安裝路徑。 支援的路徑名稱為 shared、cache 和 install。 |
| `--path cache=<path>` | **選用**：使用您指定的位置來下載安裝檔案。 此位置只能在第一次安裝 Visual Studio 時設定。 範例： `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **選用**：包含並存 Visual Studio 安裝的共用檔案。 某些工具和 SDK 會安裝到此磁碟機上的位置，而其他一些項目則可能會覆寫此設定並安裝到其他磁碟機。 範例： `--path shared="C:\VS\shared"` <br/><br/>**重要**：這只能設定一次，並在第一次安裝 Visual Studio 時設定。 |
| `--path install=<path>` | **選擇性**：相當於 `–-installPath` 。 特別是 `--installPath "C:\VS"` 與 `--path install="C:\VS"` 相等。 一次只能使用其中一個命令。 |

## <a name="administrator-update-command-and-command-line-parameters"></a>系統管理員更新命令和命令列參數
如果您將系統管理員更新從 [Microsoft Update 目錄](https://catalog.update.microsoft.com) 下載到用戶端電腦上的安裝目錄，則可以按兩下檔案以套用更新。 您也可以開啟命令視窗，並傳遞下列一些參數來變更預設行為。 

如果您要透過 Microsoft 端點管理員 (SCCM) 來部署系統管理員更新，您可以使用下列參數修改套件以調整行為。 您也可以透過用戶端電腦上的設定檔來控制參數。 如需詳細資訊，請參閱設定 [系統管理員更新的方法](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update)

請注意，所有系統管理員更新參數都是在「更新」內容中執行。

| **系統管理員更新參數** | **說明** |
| ----------------------- | --------------- |
| `--installerUpdateArgs [optional parameters]` | 此參數會作為與系統管理員更新案例相關之特定參數的「傳遞陣列」。 針對此用途啟用的選擇性參數為： <br/><br/> `--quiet`：這是系統管理員更新的預設體驗，此處會列出其完整性。 <br/> `--passive`：此參數會覆寫 `--quiet` 參數。  它會讓 UI 以非互動式的方式出現。 <br/>`--norestart`：此參數必須與或搭配使用 `--quiet` `--passive` ，而且會導致任何必要的重新啟動延遲。 <br/>`--noWeb`：此參數可防止 Visual Studio 檢查網際網路上的產品更新。 <br/>`--force`：此參數會強制關閉 Visual Studio，即使 Visual Studio 正在使用中亦同。 請小心使用此參數，因為這可能會導致工作遺失。 使用者內容中必須使用這個參數。 <br/>`--installWhileDownloading`：此參數可讓 Visual Studio 同時下載並安裝產品。 這是系統管理員更新的預設體驗，此處會列出其完整性。 <br/>`--downloadThenInstall`：此參數會強制 Visual Studio 先下載所有檔案，再進行安裝。 它與 `--installWhileDownloading` 參數互斥。 |
| `--checkPendingReboot` | 如果電腦上有擱置中的重新開機，則不論哪個應用程式可能造成此更新，都將中止更新。 預設值是不檢查擱置的重新開機。 |


語法範例： `visualstudioupdate-16.9.0to16.9.4.exe --installerUpdateArgs=--force,--noWeb --checkPendingReboot`

## <a name="list-of-workload-ids-and-component-ids"></a>工作負載識別碼和元件識別碼清單

如需依 Visual Studio 產品排序的工作負載和元件識別碼清單，請參閱 [Visual Studio 工作負載和元件識別碼](workload-and-component-ids.md)頁面。

## <a name="list-of-language-locales"></a>語言地區設定清單

| **語言地區設定** | **Language** |
| ----------------------- | --------------- |
| Cs-cz | 捷克文 |
| De-de | 德文 |
| En-us | 英文 |
| Es-es | 西班牙文 |
| Fr-fr | 法文 |
| It-it | 義大利文 |
| Ja-jp | 日文 |
| Ko-kr | 韓文 |
| Pl-pl | 波蘭文 |
| Pt-br | 葡萄牙文 - 巴西 |
| Ru-ru | 俄文 |
| Tr-tr | 土耳其文 |
| Zh-cn | 中文 - 簡體 |
| Zh-tw | 中文 - 繁體 |

## <a name="error-codes"></a>錯誤碼

根據作業的結果，`%ERRORLEVEL%` 環境變數將會設定為下列其中一個值：

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

每個作業會在 `%TEMP%` 目錄中產生幾個記錄檔，顯示安裝進度。 依日期將資料夾排序，然後分別針對啟動載入器、安裝程式應用程式和安裝程式引擎尋找開頭為 `dd_bootstrapper`、`dd_client` 和 `dd_setup` 的檔案。

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>另請參閱

- [Visual Studio 安裝的命令列參數範例](command-line-parameter-examples.md)
- [建立 Visual Studio 的離線安裝](create-an-offline-installation-of-visual-studio.md)
- [使用回應檔自動安裝 Visual Studio](automated-installation-with-response-file.md)
- [Visual Studio 工作負載與元件識別碼](workload-and-component-ids.md)
