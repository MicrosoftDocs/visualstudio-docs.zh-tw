---
title: Help Content Manager 的命令列引數
description: '使用 Help Content Manager 的命令列引數 ( # A0) 來指定如何部署和管理本機說明內容。'
ms.date: 11/01/2017
ms.topic: reference
ms.assetid: 3aa9890a-1147-42ba-adea-17935d184038
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 905284d69d23971771eecd9da6cef5c5051f36ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944273"
---
# <a name="command-line-arguments-for-the-help-content-manager"></a>Help Content Manager 的命令列引數

您可以使用 Help Content Manager (*HlpCtntMgr.exe*) 的命令列引數，來指定如何部署和管理本機說明內容。 您必須以系統管理員權限來執行命令列工具的指令碼，您無法以服務方式執行這些指令碼。 使用本工具可執行下列工作：

- 從磁碟或雲端新增或更新本機說明內容。

- 移除本機說明內容。

- 移動本機說明內容的存放區。

- 以無訊息模式加入、更新、移除或移動本機說明內容。

語法：

```cmd
HlpCtntmgr.exe /operation Value /catalogname CatalogName /locale Locale /sourceuri InstallationPoint
```

例如：

```cmd
hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us /sourceuri d:\productDocumentation\HelpContentSetup.msha
```

>[!NOTE]
> Visual Studio 2017 和 Visual Studio 2019 的目錄名稱都是 VisualStudio15。 這可能是非預期的，但這是因為兩個 Visual Studio 版本都使用相同的說明檢視器。

## <a name="switches-and-arguments"></a>參數和引數

下表定義的參數和引數可讓您在 Help Content Manager 的命令列工具使用：

|參數|必要？|引數|
|------------|---------------|---------------|
|/operation|是|-   **安裝** -- 從指定的安裝來源將書籍新增至本機內容存放區。<br />     這個參數需要 /booklist 引數或 /sourceURI 引數，或是兩者同時使用。 如果您未指定 /sourceURI 引數，則會把預設的 Visual Studio URI 當成安裝來源。 如果您未指定 /booklist 引數，就會安裝 /sourceUri 上的所有書籍。<br />-   **解除安裝** -- 從本機內容存放區中移除您指定的書籍。<br />     這個參數需要 /booklist 引數或 /sourceURI 引數。  如果您指定 /sourceURI 引數，則會移除所有書籍，並會忽略 /booklist 引數。<br />-   **移動** -- 將本機存放區移至您指定的路徑。 預設本機存放區路徑設定為 *% ProgramData%* 下的目錄<br />     這個參數需要 /locationPath 和 /catalogName 引數。 如果您指定無效的路徑，或磁碟機未包含足夠的可用空間來容納內容，就會在事件記錄檔中記錄錯誤訊息。<br />-   **重新整理** -- 更新已變更的主題，因為它們已安裝或最近更新過。<br />     這個參數需要 /sourceURI 引數。|
|/catalogName|是|指定內容目錄的名稱。 針對 Visual Studio 2017 和 Visual Studio 2019，這是 VisualStudio15。|
|/locale|否|指定產品地區設定，此設定用來檢視並管理目前說明檢視器執行個體的內容。 例如，您指定 `EN-US` 英文 - 美國。<br /><br /> 如果您未指定地區設定，就會使用作業系統的地區設定。 如果無法判斷該地區設定，就會使用 `EN-US`。<br /><br /> 如果您指定無效的地區設定，則會在事件記錄檔中記錄錯誤訊息。|
|/e|否|如果目前使用者具有系統管理認證，則將 Help Content Manager 的權限提高為系統管理權限。|
|/sourceURI|否|指定將內容安裝 (服務 API) 的 URL，或內容安裝檔案的路徑 (*. .msha*) 。 在 Visual Studio 2010 樣式端點中，URL 可以指向產品群組 (最上層節點) 或產品書籍 (分葉層級節點)。 您不需要在 URL 結尾包含斜線 (/)。 如果您包含結尾斜線，則它會受到適當地處理。<br /><br /> 當內容正受到管理時，如果找不到您指定的檔案、其無效或無法存取，或是網際網路連線無法使用或遭中斷，會在事件記錄檔中記錄錯誤訊息。|
|/vendor|否|指定要移除的產品內容廠商 (例如， `Microsoft`)。 這個參數的預設引數是 Microsoft。|
|/productName|否|指定要移除的書籍產品名稱。 產品名稱是在內容隨附的 *helpcontentsetup.msha. .msha* 或 *books.html* 檔案中識別。 您一次只能從一項產品中移除書籍。 若要從多個產品中移除書籍，您必須執行多個安裝。|
|/booklist|否|指定要受管理的書籍名稱，以空格分隔。 值必須符合安裝媒體上所列的書籍名稱。<br /><br /> 如果您未指定這個引數，則會安裝 /sourceURI 中所有建議的指定產品書籍。<br /><br /> 如果書籍名稱包含 1 或多個空格，請用雙引號 (") 括住，以便適當地分隔清單。<br /><br /> 如果您指定無效或無法連接的 /sourceURI，就會記錄下錯誤訊息。|
|/skuId|否|從安裝來源指定產品的庫存單位 (SKU)，並篩選 /SourceURI 參數識別的書籍。|
|/membership|否|-   **最低** -- 會根據您使用 /skuId 切換參數指定的 SKU 安裝最小一組的說明內容。 SKU 和內容集之間的對應會被公開到服務應用程式開發介面中。<br />-   **建議** -- 針對您使用 /skuId 引數指定的 SKU 安裝一組推薦的書籍。 安裝來源是服務 API 或 *。.MSHA*。<br />-   **完整** -- 針對您使用 /skuId 引數指定的 SKU 安裝一組完整的書籍。 安裝來源是服務 API 或 *。.MSHA*。|
|/locationpath|否|指定本機說明內容的預設資料夾。 您只能用這個參數安裝或移動內容。 如果您指定這個參數，則您也必須指定 /silent 參數。|
|/silent|否|安裝或移除說明內容，而不提示使用者，或顯示任何包括狀態通知區域中圖示的 UI。 輸出會記錄到 *% Temp%* 目錄中的檔案。 **重要事項：**  若要以無訊息方式安裝內容，您必須使用數位簽署 *的 .cab* 檔案，而非 *.mshc* 檔案。|
|/launchingApp|否|在沒有父應用程式時啟動說明檢視器，請定義應用程式和目錄的內容。 此切換參數的引數是 *CompanyName*、*ProductName* 和 *VersionNumber* (例如 `/launchingApp Microsoft,VisualStudio,16.0`)。<br /><br /> 若要使用 /silent 參數安裝內容，這是必要的。|
|/wait 秒|否|暫停安裝、解除安裝和重新整理作業。 如果已經為了目錄而正在進行作業，處理序會在等候指定的秒數後繼續。 使用 0 表示永遠等候。|
|/?|否|列出 Help Content Manager 命令列工具的參數及描述。|

### <a name="exit-codes"></a>結束代碼

當您以無訊息模式執行 Help Content Manager 的命令列工具時，它會傳回下列結束代碼：

```
Success = 0,

FailureToElevate = 100
InvalidCmdArgs = 101,
FailOnFetchingOnlineContent = 110,
FailOnFetchingContentFromDisk = 120,
FailOnFetchingInstalledBooks = 130,
NoBooksToUninstall = 200,
NoBooksToInstall = 300,
FailOnUninstall = 400,
FailOnInstall = 500,
FailOnMove = 600,
FailOnUpdate = 700,
FailOnRefresh = 800,
Cancelled = 900,
Others = 999,
ContentManagementDisabled = 1200,
OnlineHelpPreferenceDisabled = 1201
UpdateAlreadyRunning = 1300 - (Signals that the update didn't run because another was in progress.)
```

## <a name="see-also"></a>另請參閱

- [說明檢視器系統管理員指南](../help-viewer/administrator-guide.md)
- [Help Content Manager 覆寫](../help-viewer/behavior-overrides.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)