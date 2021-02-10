---
title: 使用命令列參數來安裝 Visual Studio
titleSuffix: ''
description: 了解如何使用命令列參數來控制或自訂您的 Visual Studio 安裝。
ms.date: 10/22/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d5bea30b8a046be55ba49a1cc1dbf12e3093585f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935651"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>使用命令列參數來安裝 Visual Studio

當您從命令提示字元安裝 Visual Studio 時，可以使用各種命令列參數來控制或自訂安裝。 您可以從命令列執行下列動作：

- 使用預先選取的特定選項開始安裝。
- 自動化安裝程序。
- 建立安裝檔案的快取 (配置)，以供稍後使用。

命令列選項會搭配安裝程式啟動載入器使用，這是起始下載程式的小型 (1 MB) 檔。 當您從 Visual Studio 網站下載時，啟動載入器是第一個啟動的可執行檔。

::: moniker range="vs-2017"

若要取得 Visual Studio 2017 的啟動載入器，請參閱 [**Visual Studio 舊版**](https://visualstudio.microsoft.com/vs/older-downloads/) 下載頁面，以取得如何進行這項操作的詳細資訊。

::: moniker-end

::: moniker range="vs-2019"

您可以從下列連結，直接連結到要安裝之產品版本的最新版啟動載入器：

- [Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)
- [Visual Studio 2019 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019+rc)

::: moniker-end


啟動載入器檔案應符合或類似下列其中一個檔案名：

* vs_enterprise.exe
* vs_professional.exe
* vs_community.exe

>[!TIP]
>如果您先前已下載啟動載入器檔案，而且想要驗證其版本，請參閱以下說明。 在 Windows 中，開啟檔案總管，以滑鼠右鍵按一下啟動載入器檔案，選擇 [ **屬性**]，選擇 [ **詳細資料** ] 索引標籤，然後查看 **產品版本** 號碼。 若要將該號碼符合 Visual Studio 的版本，請參閱 [Visual Studio 組建編號和發行日期](visual-studio-build-numbers-and-release-dates.md) ] 頁面。

## <a name="command-line-parameters"></a>命令列參數

 Visual Studio 命令列參數區分大小寫。

> 語法： `vs_enterprise.exe [command] <options>...`

`vs_enterprise.exe`針對您要安裝的產品版本，適當地取代。  (或者，您可以使用 `vs_installer.exe` 。 ) 

>[!TIP]
> 如需如何使用命令列安裝 Visual Studio 的更多範例，請參閱[命令列參數範例](command-line-parameter-examples.md)頁面。

::: moniker range="vs-2017"

| **命令** | **說明** |
| ----------------------- | --------------- |
| (空白) | 安裝產品。 |
| `modify` | 修改所安裝的產品。 |
| `update` | 更新所安裝的產品。 |
| `repair` | 修復所安裝的產品。 |
| `uninstall` | 解除安裝所安裝的產品。 |
| `export` | **15.9 版的新** 功能：將安裝選取專案匯出至安裝設定檔。 **注意**：只能搭配 vs_installer.exe 使用。 |

::: moniker-end

::: moniker range="vs-2019"

| **命令** | **說明** |
| ----------------------- | --------------- |
| (空白) | 安裝產品。 |
| `modify` | 修改所安裝的產品。 |
| `update` | 更新所安裝的產品。 |
| `repair` | 修復所安裝的產品。 |
| `uninstall` | 解除安裝所安裝的產品。 |
| `export` | 將安裝選取項目匯出至安裝組態檔。 **注意**：只能搭配 vs_installer.exe 使用。 |

::: moniker-end

## <a name="install-options"></a>安裝選項

::: moniker range="vs-2017"

| **安裝選項** | **說明** |
| ----------------------- | --------------- |
| `--installPath <dir>` | 要操作之執行個體的安裝目錄。 若是安裝命令，這是 **選擇性的**，而且是執行個體的安裝位置。 若是其他命令，這是 **必要的**，而且是先前已安裝執行個體的安裝位置。 |
| `--addProductLang <language-locale>` | **選擇性**︰在安裝或修改作業期間，這會決定要安裝到產品的 UI 語言套件。 它可在命令列上出現多次，以新增多個語言套件。 如果未出現，則會使用電腦地區設定來安裝。 如需詳細資訊，請參閱此頁面上的[語言地區設定清單](#list-of-language-locales)一節。|
| `--removeProductLang <language-locale>` | **選擇性**︰在安裝或修改作業期間，這會決定要從產品移除的 UI 語言套件。 它可在命令列上出現多次，以新增多個語言套件。 如需詳細資訊，請參閱此頁面上的[語言地區設定清單](#list-of-language-locales)一節。|
| `--add <one or more workload or component IDs>` | **選擇性**︰一或多個要新增的工作負載或元件識別碼。 安裝成品的必要元件，但不安裝建議或選用元件。 您可以使用 `--includeRecommended` 和/或 `--includeOptional`，以全域控制其他元件。 若要包含多個工作負載或元件，請重複 `--add` 命令 (例如 `--add Workload1 --add Workload2`)。 若要進行更精細的控制，可將 `;includeRecommended` 或 `;includeOptional` 附加到識別碼 (例如 `--add Workload1;includeRecommended` 或 `--add Workload2;includeRecommended;includeOptional`)。 如需詳細資訊，請參閱[工作負載與元件識別碼](workload-and-component-ids.md)頁面。 如有必要，您可以重複此選項。|
| `--remove <one or more workload or component IDs>` | **選擇性**：要移除的一或多個工作負載或元件識別碼。 如需詳細資訊，請參閱[工作負載和元件識別碼 (英文)](workload-and-component-ids.md) 頁面。 如有必要，您可以重複此選項。|
| `--in <path>` | **選擇性**：回應檔的 URI 或路徑。  |
| `--all` | **選擇性**︰是否要安裝產品的所有工作負載和元件。 |
| `--allWorkloads` | **選擇性**︰安裝所有工作負載及元件，但不安裝建議或選擇性元件。 |
| `--includeRecommended` | **選用**：包含已安裝之任何工作負載的建議元件，但不包含選擇性元件。 使用 `--allWorkloads` 或 `--add` 指定工作負載。 |
| `--includeOptional` | **選用**：包含已安裝之任何工作負載的選擇性元件，但不包含建議的元件。 使用 `--allWorkloads` 或 `--add` 指定工作負載。  |
| `--quiet, -q` | **選用**：執行安裝時不顯示任何使用者介面。 |
| `--passive, -p` | **選擇性**：顯示使用者介面，但不向使用者要求任何互動。 |
| `--norestart` | **選擇性**：如果有的話，具有或的命令將 `--passive` `--quiet` 不會自動重新開機電腦 (如有必要) 。  如果未指定 `--passive` 或 `--quiet`，則會略過此選項。  |
| `--nickname <name>` | **選用**：這會定義要指派給所安裝產品的昵稱。 昵稱長度不可超過10個字元。  |
| `--productKey` | **選擇性**：這會定義要用於已安裝產品的產品金鑰。 它是以格式或的25個英數位元所組成 `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` `xxxxxxxxxxxxxxxxxxxxxxxxx` 。 |
| `--help, --?, -h, -?` | 顯示此頁面的離線版本。 |
| `--config <path>` | **選擇性** 和 **15.9 的新功能**：在安裝或修改作業期間，這會根據先前儲存的安裝組態檔，來決定要新增的工作負載和元件。 這項作業是附加的，如果檔案中沒有任何工作負載或元件，則不會將它移除。 此外，也不會新增未套用至產品的專案。 在匯出作業期間，這會決定安裝組態檔的儲存位置。 |

::: moniker-end

::: moniker range="vs-2019"

| **安裝選項** | **說明** |
| ----------------------- | --------------- |
| `--installPath <dir>` | 要操作之執行個體的安裝目錄。 若是安裝命令，這是 **選擇性的**，而且是執行個體的安裝位置。 若是其他命令，這是 **必要的**，而且是先前已安裝執行個體的安裝位置。 |
| `--addProductLang <language-locale>` | **選擇性**︰在安裝或修改作業期間，這會決定要安裝到產品的 UI 語言套件。 它可在命令列上出現多次，以新增多個語言套件。 如果未出現，則會使用電腦地區設定來安裝。 如需詳細資訊，請參閱此頁面上的[語言地區設定清單](#list-of-language-locales)一節。|
| `--removeProductLang <language-locale>` | **選擇性**︰在安裝或修改作業期間，這會決定要從產品移除的 UI 語言套件。 它可在命令列上出現多次，以新增多個語言套件。 如需詳細資訊，請參閱此頁面上的[語言地區設定清單](#list-of-language-locales)一節。|
| `--add <one or more workload or component IDs>` | **選擇性**︰一或多個要新增的工作負載或元件識別碼。 安裝成品的必要元件，但不安裝建議或選用元件。 您可以使用 `--includeRecommended` 和/或 `--includeOptional`，以全域控制其他元件。 若要包含多個工作負載或元件，請重複 `--add` 命令 (例如 `--add Workload1 --add Workload2`)。 若要進行更精細的控制，可將 `;includeRecommended` 或 `;includeOptional` 附加到識別碼 (例如 `--add Workload1;includeRecommended` 或 `--add Workload2;includeRecommended;includeOptional`)。 如需詳細資訊，請參閱[工作負載與元件識別碼](workload-and-component-ids.md)頁面。 如有必要，您可以重複此選項。|
| `--remove <one or more workload or component IDs>` | **選擇性**：要移除的一或多個工作負載或元件識別碼。 如需詳細資訊，請參閱[工作負載和元件識別碼 (英文)](workload-and-component-ids.md) 頁面。 如有必要，您可以重複此選項。|
| `--in <path>` | **選擇性**：回應檔的 URI 或路徑。  |
| `--all` | **選擇性**︰是否要安裝產品的所有工作負載和元件。 |
| `--allWorkloads` | **選擇性**︰安裝所有工作負載及元件，但不安裝建議或選擇性元件。 |
| `--includeRecommended` | **選用**：包含已安裝之任何工作負載的建議元件，但不包含選擇性元件。 使用 `--allWorkloads` 或 `--add` 指定工作負載。 |
| `--includeOptional` | **選用**：包含已安裝之任何工作負載的選擇性元件，但不包含建議的元件。 使用 `--allWorkloads` 或 `--add` 指定工作負載。  |
| `--quiet, -q` | **選用**：執行安裝時不顯示任何使用者介面。 |
| `--passive, -p` | **選擇性**：顯示使用者介面，但不向使用者要求任何互動。 |
| `--norestart` | **選擇性**：如果有的話，具有或的命令將 `--passive` `--quiet` 不會自動重新開機電腦 (如有必要) 。  如果未指定 `--passive` 或 `--quiet`，則會略過此選項。  |
| `--nickname <name>` | **選用**：這會定義要指派給所安裝產品的昵稱。 昵稱長度不可超過10個字元。  |
| `--productKey` | **選擇性**：這會定義要用於已安裝產品的產品金鑰。 它是以格式或的25個英數位元所組成 `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` `xxxxxxxxxxxxxxxxxxxxxxxxx` 。 |
| `--help, --?, -h, -?` | 顯示此頁面的離線版本。 |
| `--config <path>` | **選擇性**：在安裝或修改作業期間，這會根據先前儲存的安裝設定檔來決定要新增的工作負載和元件。 這項作業是附加的，如果檔案中沒有任何工作負載或元件，則不會將它移除。 此外，也不會新增未套用至產品的專案。 在匯出作業期間，這會決定安裝組態檔的儲存位置。 |

::: moniker-end

> [!IMPORTANT]
> 指定多個工作負載和元件時，您必須針對每個項目重複 `--add` 或 `--remove` 命令列參數。

## <a name="layout-options"></a>配置選項

::: moniker range="vs-2017"

| **配置選項** | **說明** |
| ----------------------- | --------------- |
| `--layout <dir>` | 指定一個目錄以建立離線安裝快取。 如需詳細資訊，請參閱[建立 Visual Studio 的網路型安裝](create-a-network-installation-of-visual-studio.md)。|
| `--lang <one or more language-locales>` | **選擇性**：搭配使用 `--layout`，以指定語言的資源套件來準備離線安裝快取。 如需詳細資訊，請參閱此頁面上的[語言地區設定清單](#list-of-language-locales)一節。|
| `--add <one or more workload or component IDs>` | **選擇性**︰一或多個要新增的工作負載或元件識別碼。 安裝成品的必要元件，但不安裝建議或選用元件。 您可以使用 `--includeRecommended` 和/或 `--includeOptional`，以全域控制其他元件。 若要進行更精細的控制，可將 `;includeRecommended` 或 `;includeOptional` 附加到識別碼 (例如 `--add Workload1;includeRecommended` 或 `--add Workload2;includeOptional`)。 如需詳細資訊，請參閱[工作負載與元件識別碼](workload-and-component-ids.md)頁面。 <br/>**注意**：如果使用了 `--add`，則只會下載特定的工作負載和元件及其相依性。 如果 `--add` 未指定，則會將所有工作負載和元件下載至版面配置。|
| `--includeRecommended` | **選用**：包含已安裝之任何工作負載的建議元件，但不包含選擇性元件。 使用 `--allWorkloads` 或 `--add` 指定工作負載。 |
| `--includeOptional` | **選擇性**︰包含配置中所包含之任何工作負載的建議和選擇性元件。 使用 `--add` 指定工作負載。  |
| `--keepLayoutVersion` | **版本 15.3 的新功能，選擇性**：無須更新配置的版本，即可將變更套用至配置。 |
| `--verify` | **版本 15.3 的新功能，選擇性**：驗證配置的內容。 會列出任何損毀或遺失的檔案。 |
| `--fix` | **版本 15.3 的新功能，選擇性**：驗證配置的內容。 如果有任何檔案損毀或遺失，則會重新下載。 必須有網際網路存取權才可修正配置。 |
| `--clean <one or more paths to catalogs>` | **版本 15.3 的新功能，選擇性**：從已更新為較新版的配置中移除舊版元件。 |

| **進階安裝選項** | **說明** |
| ----------------------- | --------------- |
| `--channelId <id>` | **選擇性**：要安裝執行個體的通道識別碼。 這是安裝命令的必要項，而且如果指定了其他命令，則會忽略 `--installPath` 。 |
| `--channelUri <uri>` | **選擇性**：通道資訊清單的 URI。 如果不想要更新， `--channelUri` 可指向不存在的檔案 (例如，--channelUri C:\doesntExist.chman) 。 這可用於安裝命令;其他命令會忽略它。 |
| `--installChannelUri <uri>` | **選用**：要用於安裝之通道資訊清單的 URI。 `--channelUri` 指定的 URI (指定 `--installChannelUri` 時必須指定) 會用來偵測更新。 這可用於安裝命令;其他命令會忽略它。 |
| `--installCatalogUri <uri>` | **選用**：要用於安裝之目錄資訊清單的 URI。 如有指定，通道管理員會嘗試從此 URI 下載目錄資訊清單，再於安裝通道資訊清單中使用此 URI。 此參數可用來支援離線安裝，在此安裝中會使用已下載的產品目錄來建立配置快取。 這可用於安裝命令;其他命令會忽略它。 |
| `--productId <id>` | **選擇性**：要安裝之執行個體的產品識別碼。 這會在正常的安裝狀況中預先填入。 |
| `--wait` | **選擇性**︰處理序會在安裝完成後才傳回結束代碼。 這適用於自動化安裝的情況，在此情況下，使用者必須等候安裝完成，才能處理該安裝的傳回碼。 |
| `--locale <language-locale>` | **選擇性**︰變更安裝程式本身的使用者介面顯示語言。 設定將會予以保留。 如需詳細資訊，請參閱此頁面上的[語言地區設定清單](#list-of-language-locales)一節。|
| `--cache` | **15.2 的新功能，選擇性**︰如果存在，套件將會在安裝之後加以保留，以利後續修復。 這會覆寫要用於後續安裝、修復或修改的全域原則設定。 預設原則是快取套件。 若是解除安裝命令，則會略過此項。 如需詳細資訊，請參閱如何[停用或移動套件快取](disable-or-move-the-package-cache.md)。 |
| `--nocache` | **版本 15.2 的新功能，選擇性**︰如果套件存在，會在安裝或修復之後刪除。 只有在需要時才會再次下載，並在使用之後再次刪除。 這會覆寫要用於後續安裝、修復或修改的全域原則設定。 預設原則是快取套件。 若是解除安裝命令，則會略過此項。 如需詳細資訊，請參閱如何[停用或移動套件快取](disable-or-move-the-package-cache.md)。 |
| `--noUpdateInstaller` | **15.2 的新功能，選擇性**︰如果存在，則在指定無訊息時會防止安裝程式更新它自己。 如果在需要安裝程式更新時指定具有無訊息的 noUpdateInstaller，則安裝程式會讓命令失敗，並傳回非零結束代碼。 |
| `--noWeb` | **15.3 的新功能，選擇性**：如果有的話，Visual Studio 安裝程式會使用版面配置目錄中的檔案來安裝 Visual Studio。 如果使用者嘗試安裝不在版面配置中的元件，安裝程式會失敗。  如需詳細資訊，請參閱[從網路安裝部署](create-a-network-installation-of-visual-studio.md)。 <br/><br/> **重要**：此參數不會阻止 Visual Studio 安裝程式檢查是否有更新。 如需詳細資訊，請參閱[控制網路型 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)。 |
| `--path <name>=<path>` | **15.7 的新功能，選擇性**：用來指定安裝的自訂安裝路徑。 支援的路徑名稱為 shared、cache 和 install。 |
| `--path cache=<path>` | **15.7 的新功能，選擇性**：使用您指定用於下載安裝檔案的位置。 此位置只能在第一次安裝 Visual Studio 時設定。 範例： `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **15.7 的新功能，選擇性**：包含並存 Visual Studio 安裝的共用檔案。 某些工具和 SDK 會安裝到此磁碟機上的位置，而其他一些項目則可能會覆寫此設定並安裝到其他磁碟機。 範例： `--path shared="C:\VS\shared"` <br><br>重要：此項目只能在第一次安裝 Visual Studio 時設定一次。 |
| `--path install=<path>` | **15.7 的新功能，選擇性**：相當於 `–-installPath`。 特別是 `--installPath "C:\VS"` 與 `--path install="C:\VS"` 相等。 一次只能使用其中一個命令。 |

::: moniker-end

::: moniker range="vs-2019"

| **配置選項** | **說明** |
| ----------------------- | --------------- |
| `--layout <dir>` | 指定一個目錄以建立離線安裝快取。 如需詳細資訊，請參閱[建立 Visual Studio 的網路型安裝](create-a-network-installation-of-visual-studio.md)。|
| `--lang <one or more language-locales>` | **選擇性**：搭配使用 `--layout`，以指定語言的資源套件來準備離線安裝快取。 如需詳細資訊，請參閱此頁面上的[語言地區設定清單](#list-of-language-locales)一節。|
| `--add <one or more workload or component IDs>` | **選擇性**︰一或多個要新增的工作負載或元件識別碼。 安裝成品的必要元件，但不安裝建議或選用元件。 您可以使用 `--includeRecommended` 和/或 `--includeOptional`，以全域控制其他元件。 若要進行更精細的控制，可將 `;includeRecommended` 或 `;includeOptional` 附加到識別碼 (例如 `--add Workload1;includeRecommended` 或 `--add Workload2;includeOptional`)。 如需詳細資訊，請參閱[工作負載與元件識別碼](workload-and-component-ids.md)頁面。 <br/>**注意**：如果使用了 `--add`，則只會下載特定的工作負載和元件及其相依性。 如果 `--add` 未指定，則會將所有工作負載和元件下載至版面配置。|
| `--includeRecommended` | **選用**：包含已安裝之任何工作負載的建議元件，但不包含選擇性元件。 使用 `--allWorkloads` 或 `--add` 指定工作負載。 |
| `--includeOptional` | **選擇性**︰包含配置中所包含之任何工作負載的建議和選擇性元件。 使用 `--add` 指定工作負載。  |
| `--keepLayoutVersion` | **選擇性**：將變更套用至版面配置，而不更新版面配置的版本。 |
| `--verify` | **選擇性**：驗證版面配置的內容。 會列出任何損毀或遺失的檔案。 |
| `--fix` | **選擇性**：驗證版面配置的內容。  如果有任何檔案損毀或遺失，則會重新下載。 必須有網際網路存取權才可修正配置。 |
| `--clean <one or more paths to catalogs>` | **選擇性**：從已更新為較新版本的版面配置中移除舊版元件。 |

| **進階安裝選項** | **說明** |
| ----------------------- | --------------- |
| `--channelId <id>` | **選擇性**：要安裝執行個體的通道識別碼。 這是安裝命令的必要項，而且如果指定了其他命令，則會忽略 `--installPath` 。 |
| `--channelUri <uri>` | **選擇性**：通道資訊清單的 URI。 如果不想要更新， `--channelUri` 可指向不存在的檔案 (例如，--channelUri C:\doesntExist.chman) 。 這可用於安裝命令;其他命令會忽略它。 |
| `--installChannelUri <uri>` | **選用**：要用於安裝之通道資訊清單的 URI。 `--channelUri` 指定的 URI (指定 `--installChannelUri` 時必須指定) 會用來偵測更新。 這可用於安裝命令;其他命令會忽略它。 |
| `--installCatalogUri <uri>` | **選用**：要用於安裝之目錄資訊清單的 URI。 如有指定，通道管理員會嘗試從此 URI 下載目錄資訊清單，再於安裝通道資訊清單中使用此 URI。 此參數可用來支援離線安裝，在此安裝中會使用已下載的產品目錄來建立配置快取。 這可用於安裝命令;其他命令會忽略它。 |
| `--productId <id>` | **選擇性**：要安裝之執行個體的產品識別碼。 這會在正常的安裝狀況中預先填入。 |
| `--wait` | **選擇性**︰處理序會在安裝完成後才傳回結束代碼。 這適用於自動化安裝的情況，在此情況下，使用者必須等候安裝完成，才能處理該安裝的傳回碼。 |
| `--locale <language-locale>` | **選擇性**︰變更安裝程式本身的使用者介面顯示語言。 設定將會予以保留。 如需詳細資訊，請參閱此頁面上的[語言地區設定清單](#list-of-language-locales)一節。|
| `--cache` | **選擇性**：如果存在，套件將會在安裝之後保留，以供後續修復之用。 這會覆寫要用於後續安裝、修復或修改的全域原則設定。 預設原則是快取套件。 若是解除安裝命令，則會略過此項。 如需詳細資訊，請參閱如何[停用或移動套件快取](disable-or-move-the-package-cache.md)。 |
| `--nocache` | **選用**：如果存在，套件將會在安裝或修復之後刪除。 只有在需要時才會再次下載，並在使用之後再次刪除。 這會覆寫要用於後續安裝、修復或修改的全域原則設定。 預設原則是快取套件。 若是解除安裝命令，則會略過此項。 如需詳細資訊，請參閱如何[停用或移動套件快取](disable-or-move-the-package-cache.md)。 |
| `--noUpdateInstaller` | **選擇性**：如果有的話，會在指定 quiet 時防止安裝程式自行更新。 如果在需要安裝程式更新時指定具有無訊息的 noUpdateInstaller，則安裝程式會讓命令失敗，並傳回非零結束代碼。 |
| `--noWeb` | **選擇性**：如果有的話，Visual Studio 安裝程式會使用版面配置目錄中的檔案來安裝 Visual Studio。 如果使用者嘗試安裝不在版面配置中的元件，安裝程式會失敗。  如需詳細資訊，請參閱[從網路安裝部署](create-a-network-installation-of-visual-studio.md)。 <br/><br/> **重要**：此參數不會阻止 Visual Studio 安裝程式檢查是否有更新。 如需詳細資訊，請參閱[控制網路型 Visual Studio 部署的更新](controlling-updates-to-visual-studio-deployments.md)。 **16.3.5 版的新** 功能：此參數可防止錯誤並使用離線安裝和更新來改善效能。|
| `--path <name>=<path>` | **選用**：用來指定安裝的自訂安裝路徑。 支援的路徑名稱為 shared、cache 和 install。 |
| `--path cache=<path>` | **選用**：使用您指定的位置來下載安裝檔案。 此位置只能在第一次安裝 Visual Studio 時設定。 範例： `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **選用**：包含並存 Visual Studio 安裝的共用檔案。 某些工具和 SDK 會安裝到此磁碟機上的位置，而其他一些項目則可能會覆寫此設定並安裝到其他磁碟機。 範例： `--path shared="C:\VS\shared"` <br><br>重要：此項目只能在第一次安裝 Visual Studio 時設定一次。 |
| `--path install=<path>` | **選擇性**：相當於 `–-installPath` 。 特別是 `--installPath "C:\VS"` 與 `--path install="C:\VS"` 相等。 一次只能使用其中一個命令。 |

::: moniker-end

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
