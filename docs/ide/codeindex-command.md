---
title: CodeIndex 命令
description: 瞭解如何使用 CodeIndex 命令來管理 Azure DevOps Server (先前稱為 Team Foundation Server) 的程式碼索引。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 47875bcece910433a1d20ad66867acd7fdbee8d8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841916"
---
# <a name="codeindex-command"></a>CodeIndex 命令

使用 **CodeIndex** 命令管理 Team Foundation Server 上的程式碼索引。 例如，您可能會想要重設索引以修正 CodeLens 資訊，或關閉索引以調查伺服器效能問題。

## <a name="required-permissions"></a>所需的權限

您必須是 **Team Foundation Administrators** 安全性群組的成員，才能使用 **CodeIndex** 命令。 請參閱 [Permissions and groups defined for Azure DevOps Services and TFS](/azure/devops/organizations/security/permissions?view=vsts&preserve-view=true) (針對 Azure DevOps Services 和 TFS 定義的權限和群組)。

> [!NOTE]
> 即使使用系統管理認證登入，您依然必須開啟更高權限的命令提示字元視窗才能執行此命令。 您也必須從 Team Foundation 應用程式層執行這個命令。

## <a name="syntax"></a>語法

```cmd
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]
```

### <a name="parameters"></a>參數

|**Argument**|**說明**|
|------------------| - |
|`CollectionName`|指定專案集合的名稱。 如果名稱包含空格，請為名稱加上引號，例如，"Fabrikam Website"。|
|`CollectionId`|指定專案集合的識別號碼。|
|`ServerPath`|指定程式碼檔案的路徑。|

|**選項**|**說明**|
|----------------| - |
|**/indexingStatus**|顯示程式碼索引服務的狀態和組態。|
|**/setIndexing:**[ on &#124; off &#124; keepupOnly ]|-   **on**：開始為所有變更集編製索引。<br />-   **off**：停止為變更集編製索引。<br />-   **keepupOnly**：停止為先前建立的變更集編製索引，並且開始僅為新變更集編製索引。|
|**/ignoreList:**[ add &#124; remove &#124; removeAll &#124; view ] `ServerPath`<br /><br /> 您可以在伺服器路徑的開頭、結尾或兩端使用萬用字元 (*)。|指定您不要編製索引之程式碼檔及其路徑的清單。<br /><br /> -   **add**：將您不要編製索引的檔案，新增到忽略的檔案清單中。<br />-   **remove**：從忽略的檔案清單中，移除您要編製索引的檔案。<br />-   **removeAll**：清除忽略的檔案清單，並開始為所有的檔案編製索引。<br />-   **view**：查看未編製索引的所有檔案。|
|**/listLargeFiles [/fileCount:** `FileCount` **/minSize:** `MinSize`]|顯示超過指定大小 (KB) 的指定檔案數。 然後，您就可以使用 **/ignoreList** 選項來排除這些檔案，不為其編製索引。|
|**/reindexAll**|清除先前索引資料，並重新開始編製索引。|
|**/destroyCodeIndex [/noPrompt]**|刪除程式碼索引，並移除所有索引資料。 如果您使用 **/noPrompt** 選項，則不需要確認。|
|**/temporaryDataSizeLimit**:[ view &#124; <`SizeInGBs`> &#124; disable ]|控制處理變更集時，CodeLens 會建立多少暫存資料。 預設限制為 2 GB。<br /><br /> -   **view**：顯示目前的大小限制。<br />-   `SizeInGBs`：變更大小限制。<br />-   **disable**：移除大小限制。<br /><br /> 在 CodeLens 處理新的變更集之前，會先檢查此限制。 如果暫存資料超過此限制，CodeLens 將會暫停處理舊的變更集，而不是新的變更集。 清理資料並降到低於此限制之後，CodeLens 就會重新開始處理。 每天會自動執行一次清理。 這表示，在開始執行清理之前，暫存資料可能會超過此限制。|
|**/indexHistoryPeriod**:[ view &#124; all &#124; <`NumberOfMonths`> ]|控制將歷程記錄編製索引的時間長度。 這會影響 CodeLens 向您顯示的記錄數量。 預設限制為 12 個月。 這表示 CodeLens 只會顯示最近 12 個月內的歷程記錄。<br /><br /> -   **view**：顯示目前的月數。<br />-   **all**：編製索引所有歷程記錄。<br />-   `NumberOfMonths`：變更用於將歷程記錄編製索引的月數。|
|**/collectionName：**`CollectionName`|指定要在哪個名稱的專案集合上執行 **CodeIndex** 命令。 如果未使用 **/CollectionId**，則此為必要項。|
|**/collectionId：**`CollectionId`|指定要在哪個識別碼的專案集合上執行 **CodeIndex** 命令。 如果未使用 **/CollectionName**，則此為必要項。|

## <a name="examples"></a>範例

> [!NOTE]
> 此處所描述之範例公司、組織、產品、網域名稱、電子郵件地址、標誌、人員、地點及事件均屬虛構，  並非影射任何真實的公司、組織、產品、網域名稱、電子郵件地址、商標、人員、地點或事件。

若要查看程式碼索引狀態和組態：

```cmd
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Website"
```

若要開始為索引所有變更集編製索引：

```cmd
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Website"
```

若要停止為先前建立的變更集編製索引，並且開始只為新變更集編製索引：

```cmd
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Website"
```

若要找出最多 50 個大於 10 KB 的檔案：

```cmd
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Website"
```

若要從索引排除特定檔案，並將它加入至忽略的檔案清單：

```cmd
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Website/Catalog.cs" /collectionName:"Fabrikam Website"
```

查看未編製索引的所有檔案：

```cmd
TFSConfig CodeIndex /ignoreList:view
```

若要清除先前編製索引的資料，並重新開始編製索引：

```cmd
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Website"
```

若要儲存所有變更集記錄：

```cmd
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Website"
```

若要移除 CodeLens 暫存資料的大小限制，並繼續編製索引，而不管暫存資料大小：

```cmd
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Website"
```

若要刪除經過確認的程式碼索引：

```cmd
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Website"
```

## <a name="see-also"></a>另請參閱

- [尋找 CodeLens 的程式碼變更和其他記錄](../ide/find-code-changes-and-other-history-with-codelens.md)
- [使用 TFSConfig 管理伺服器組態](/azure/devops/server/command-line/tfsconfig-cmd)
