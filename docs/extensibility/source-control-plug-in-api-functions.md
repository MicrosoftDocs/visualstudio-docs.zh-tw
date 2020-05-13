---
title: 原始程式碼管理外掛程式 API 功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce685729dda8750d772e244398b736cff4951b72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699914"
---
# <a name="source-control-plug-in-api-functions"></a>原始檔控制外掛程式 API 函式
原始程式碼管理外掛程式 API 提供以下功能,必須由原始程式碼管理外掛程式根據此 API 實現。 此參考中詳細介紹了每個函數的簽名以及與位標誌和其他參數關聯的語義。

## <a name="initialization-and-housekeeping-functions"></a>初始化和家政功能

|函式|描述|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|關閉專案。|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|提示用戶為給定命令提供高級選項。|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|返回原始程式碼管理外掛程式的版本。|
|[SccInitialize](../extensibility/sccinitialize-function.md)|初始化原始碼管理外掛程式。 對於外掛程式的每個實例,調用一次。|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|打開專案。|
|[SccSetOption](../extensibility/sccsetoption-function.md)|用於設置各種選項的通用函數。 每個選項都從`SCC_OPT_xxx`並有自己的定義值集開始。|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|當需要拔下原始程式碼管理外掛程式時調用一次。|

## <a name="core-source-control-functions"></a>核心源碼管理功能

|函式|描述|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|將完全限定的路徑名稱指定的檔案陣組添加到原始程式碼管理系統。|
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|允許使用者流覽原始程式碼管理系統中已有的文件,然後將這些文件作為當前專案的一部分。|
|[SccCheckin](../extensibility/scccheckin-function.md)|簽入文件陣列。|
|[SccCheckout](../extensibility/scccheckout-function.md)|簽出文件陣列。|
|[SccDiff](../extensibility/sccdiff-function.md)|顯示由完全限定的路徑名稱指定的本地使用者檔與原始程式碼管理下的版本之間的差異。|
|[SccGet](../extensibility/sccget-function.md)|檢索一組檔的唯讀複本。|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|檢查呼叫方詢問的檔案的狀態(通過`SccQueryInfo`)。|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|使原始程式碼管理外掛程式提示使用者輸入對外掛程式有意義的專案路徑。|
|[SccHistory](../extensibility/scchistory-function.md)|顯示完全限定的本地檔名陣列紀錄。|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|檢查檔案清單的目前狀態。 此外,當檔與`pfnPopulate`的條件`nCommand`不匹配時,使用函數通知調用方。|
|[SccProperties](../extensibility/sccproperties-function.md)|顯示完全限定檔的屬性。|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|檢查完全限定檔的清單,以尋找其當前狀態。|
|[SccRemove](../extensibility/sccremove-function.md)|從原始碼管理系統中移除完全限定檔的陣列。|
|[SccRename](../extensibility/sccrename-function.md)|將給定檔重新命名為原始碼管理系統中的新名稱。|
|[SccRunScc](../extensibility/sccrunscc-function.md)|訪問原始程式碼管理系統的全部功能。|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|撤銷檔案的簽出。|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>支援額外功能的功能 (原始碼管理外掛程式 API 的版本 1.2)
 這組函數定義了原始程式碼管理外掛程式 API 版本 1.2 中包含的其他功能。 它們提供對更高級原始程式碼管理特性和功能的訪問。

|函式|描述|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|啟動批處理操作。|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|在現有父專案下創建具有給定名稱的子專案。|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|顯示由完全限定的路徑名稱指定的本地使用者目錄和原始程式碼管理資料庫位置之間的差異。|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|檢查完全限定的目錄的清單,以檢查其當前狀態。|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|結束批處理操作。|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|返回給定專案的父路徑(項目必須存在)。|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|檢查是否允許對文件進行多次簽出。|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|檢查外掛程式是否會創建 MSSCCPRJ。SCC 檔。|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>支援進階功能的功能 (原始碼管理外掛程式 API 的版本 1.3)
 這組函數定義了原始程式碼管理外掛程式 API 版本 1.3 中包含的其他功能。 它們提供對更高級原始程式碼管理特性和功能的訪問。

|函式|描述|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|將檔案清單從原始程式碼管理到當前專案。|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|在沒有使用者介面的情況下從原始程式碼管理中檢索檔案清單。|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|檢索源代碼管理中與本地檔案不同的檔案的清單。|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|檢索指定原始程式碼管理外掛程式支援的擴充功能的標誌。|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|檢索特定於用戶的選項。|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|檢查受原始碼管理的項目或專案中的目錄和檔案的清單。 找到的每個目錄和檔名都傳遞給回調函數。|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|檢查對檔案清單所做的名稱更改。 每個檔名都傳遞給具有更改狀態的回調函數。|

## <a name="requirements"></a>需求
 標題: scc.h

 (在環境 SDK 中提供常見資料夾,預設情況下 *[驅動器]*[程式檔]VSIP 8.0\EnvSDK_common_inc;也隨 MSSCCI 示例在 VSIP 資料夾中提供 *[驅動器]*[程式檔]VSIP 8.0_MSSCCI)。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
- [建立原始檔控制外掛程式](../extensibility/internals/creating-a-source-control-plug-in.md)
