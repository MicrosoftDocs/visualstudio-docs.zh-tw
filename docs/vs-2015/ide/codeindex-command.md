---
title: CodeIndex 命令 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 624a2a735032342d4eb47e2393ecae3ea3247891
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "54797290"
---
# <a name="codeindex-command"></a>CodeIndex 命令
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用 **CodeIndex** 命令管理 Team Foundation Server 上的程式碼索引。 例如，您可能會想要重設索引以修正 CodeLens 資訊，或關閉索引以調查伺服器效能問題。  
  
 **必要權限**  
  
 您必須是 **Team Foundation Administrators** 安全性群組的成員，才能使用 **CodeIndex** 命令。 請參閱 [Team Foundation Server 的權限參考](http://msdn.microsoft.com/library/39997de5-b7fb-4777-b779-07de0543abe6)。  
  
> [!NOTE]
>  即使使用系統管理認證登入，您依然必須開啟更高權限的命令提示字元視窗才能執行此命令。 您也必須從 Team Foundation 應用程式層執行這個命令。  
  
## <a name="syntax"></a>語法  
  
```  
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]  
```  
  
#### <a name="parameters"></a>參數  
  
|**引數**|**描述**|  
|------------------|---------------------|  
|`CollectionName`|指定 Team 專案集合的名稱。 如果名稱包含空格，請為名稱加上引號，例如，"Fabrikam Web Site"。|  
|`CollectionId`|指定 Team 專案集合的識別號碼。|  
|`ServerPath`|指定程式碼檔案的路徑。|  
  
|**選項**|**描述**|  
|----------------|---------------------|  
|**/indexingStatus**|顯示程式碼索引服務的狀態和組態。|  
|**/setIndexing:**[ on &#124; off &#124; keepupOnly ]|-   **on**：開始為所有變更集編製索引。<br />-   **off**：停止為變更集編製索引。<br />-   **keepupOnly**：停止為先前建立的變更集編製索引，並且開始僅為新變更集編製索引。|  
|**/ignoreList:**[ add &#124; remove &#124; removeAll &#124; view ] `ServerPath`<br /><br /> 您可以在伺服器路徑的開頭、結尾或兩端使用萬用字元 (*)。|指定您不要編製索引之程式碼檔及其路徑的清單。<br /><br /> -   **add**：將您不要編製索引的檔案，新增到忽略的檔案清單中。<br />-   **remove**：從忽略的檔案清單中，移除您要編製索引的檔案。<br />-   **removeAll**：清除忽略的檔案清單，並開始為所有的檔案編製索引。<br />-   **view**：查看未編製索引的所有檔案。|  
|**/listLargeFiles [/fileCount:** `FileCount` **/minSize:** `MinSize`]|顯示超過指定大小 (KB) 的指定檔案數。 然後，您就可以使用 **/ignoreList** 選項來排除這些檔案，不為其編製索引。|  
|**/reindexAll**|清除先前索引資料，並重新開始編製索引。|  
|**/destroyCodeIndex [/noPrompt]**|刪除程式碼索引，並移除所有索引資料。 如果您使用 **/noPrompt** 選項，則不需要確認。|  
|**/temporaryDataSizeLimit**:[ view &#124; <`SizeInGBs`> &#124; disable ]|控制處理變更集時，CodeLens 會建立多少暫存資料。 預設限制為 2 GB。<br /><br /> -   **view**：顯示目前的大小限制。<br />-   `SizeInGBs`：變更大小限制。<br />-   **disable**：移除大小限制。<br /><br /> 在 CodeLens 處理新的變更集之前，會先檢查此限制。 如果暫存資料超過此限制，CodeLens 將會暫停處理舊的變更集，而不是新的變更集。 清理資料並降到低於此限制之後，CodeLens 就會重新開始處理。 每天會自動執行一次清理。 這表示，在開始執行清理之前，暫存資料可能會超過此限制。|  
|**/indexHistoryPeriod**:[ view &#124; all &#124; <`NumberOfMonths`> ]|控制將歷程記錄編製索引的時間長度。 這會影響 CodeLens 向您顯示的記錄數量。 預設限制為 12 個月。 這表示 CodeLens 只會顯示最近 12 個月內的歷程記錄。<br /><br /> -   **view**：顯示目前的月數。<br />-   **all**：編製索引所有歷程記錄。<br />-   `NumberOfMonths`：變更用於將歷程記錄編製索引的月數。|  
|**/collectionName:** `CollectionName`|指定要在哪個名稱的 Team 專案集合上執行 **CodeIndex** 命令。 如果未使用 **/CollectionId**，則此為必要項。|  
|**/collectionId:** `CollectionId`|指定要在哪個識別碼的 Team 專案集合上執行 **CodeIndex** 命令。 如果未使用 **/CollectionName**，則此為必要項。|  
  
## <a name="examples"></a>範例  
  
> [!NOTE]
>  此處所描述的範例公司、組織、產品、網域名稱、電子郵件地址、商標、人員、地點與事件均屬虛構。  並非影射任何真實的公司、組織、產品、網域名稱、電子郵件地址、商標、人員、地點或事件。  
  
 若要查看程式碼索引狀態和組態：  
  
```  
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Web Site"  
```  
  
 若要開始為索引所有變更集編製索引：  
  
```  
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Web Site"  
```  
  
 若要停止為先前建立的變更集編製索引，並且開始只為新變更集編製索引：  
  
```  
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Web Site"  
```  
  
 若要找出最多 50 個大於 10 KB 的檔案：  
  
```  
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Web Site"  
```  
  
 若要從索引排除特定檔案，並將它加入至忽略的檔案清單：  
  
```  
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Web Site/Catalog.cs" /collectionName:"Fabrikam Web Site"  
```  
  
 查看未編製索引的所有檔案：  
  
```  
TFSConfig CodeIndex /ignoreList:view  
```  
  
 若要清除先前編製索引的資料，並重新開始編製索引：  
  
```  
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Web Site"  
```  
  
 若要儲存所有變更集記錄：  
  
```  
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Web Site"  
```  
  
 若要移除 CodeLens 暫存資料的大小限制，並繼續編製索引，而不管暫存資料大小：  
  
```  
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Web Site"  
```  
  
 若要刪除經過確認的程式碼索引：  
  
```  
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Web Site"  
```  
  
## <a name="see-also"></a>請參閱  
 [使用 TFSConfig 管理伺服器組態](http://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62)   
 [命令列工具 (適用於 TFS)](http://msdn.microsoft.com/be8c997a-b97b-4e59-97f5-04db0a601a6c)
