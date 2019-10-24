---
title: 原始檔控制外掛程式 API 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 57e451ebb4693e7742208ab6a375fa7d50563a17
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719889"
---
# <a name="source-control-plug-in-api-functions"></a>原始檔控制外掛程式 API 函式
原始檔控制外掛程式 API 提供下列函式，這些函式必須由原始檔控制外掛程式根據此 API 來執行。 此參考中會詳細說明每個函式的簽章，以及與位旗標和其他參數相關聯的語義。

## <a name="initialization-and-housekeeping-functions"></a>初始化和維護功能

|功能|描述|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|關閉專案。|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|提示使用者提供指定命令的 advanced 選項。|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|傳回原始檔控制外掛程式的版本。|
|[SccInitialize](../extensibility/sccinitialize-function.md)|初始化原始檔控制外掛程式。 每個外掛程式實例會呼叫一次。|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|開啟專案。|
|[SccSetOption](../extensibility/sccsetoption-function.md)|用來設定各種不同選項的泛型函數。 每個選項的開頭都是 `SCC_OPT_xxx`，而且有自己定義的一組值。|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|當原始檔控制外掛程式必須被拔掉時呼叫一次。|

## <a name="core-source-control-functions"></a>核心原始檔控制函數

|功能|描述|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|將完整路徑名稱所指定的檔案陣列加入至原始檔控制系統。|
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|允許使用者流覽已在原始檔控制系統中的檔案，然後將這些檔案設為目前專案的一部分。|
|[SccCheckin](../extensibility/scccheckin-function.md)|檢查檔案的陣列。|
|[SccCheckout](../extensibility/scccheckout-function.md)|簽出檔案的陣列。|
|[SccDiff](../extensibility/sccdiff-function.md)|顯示完整路徑名稱所指定的本機使用者檔案與原始檔控制之下的版本之間的差異。|
|[SccGet](../extensibility/sccget-function.md)|抓取一組檔案的唯讀複本。|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|檢查呼叫者已詢問的檔案狀態（透過 `SccQueryInfo`）。|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|導致原始檔控制外掛程式提示使用者輸入對外掛程式有意義的專案路徑。|
|[SccHistory](../extensibility/scchistory-function.md)|顯示完整本機檔案名陣列的歷程記錄。|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|檢查檔案的清單，以瞭解其目前的狀態。 此外，當檔案不符合 `nCommand` 的準則時，會使用 `pfnPopulate` 函數來通知呼叫者。|
|[SccProperties](../extensibility/sccproperties-function.md)|顯示完整檔案的屬性。|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|檢查完整檔案的清單，以瞭解其目前的狀態。|
|[SccRemove](../extensibility/sccremove-function.md)|從原始檔控制系統中移除完整檔案的陣列。|
|[SccRename](../extensibility/sccrename-function.md)|將指定的檔案重新命名為原始檔控制系統中的新名稱。|
|[SccRunScc](../extensibility/sccrunscc-function.md)|存取原始檔控制系統的完整功能範圍。|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|復原檔案陣列的簽出。|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>支援額外功能的函式（原始檔控制外掛程式 API 的版本1.2）
 此函式群組會定義原始檔控制外掛程式 API 版本1.2 中包含的其他功能。 它們可讓您存取更先進的原始檔控制特性和功能。

|功能|描述|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|啟動批次作業。|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|在現有的父專案底下，建立具有指定名稱的子專案。|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|顯示完整路徑名稱和原始檔控制資料庫位置所指定的本機使用者目錄之間的差異。|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|檢查完整目錄的清單，以瞭解其目前的狀態。|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|結束批次作業。|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|傳回指定專案的父路徑（專案必須存在）。|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|檢查是否允許在檔案上執行多次簽出。|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|檢查外掛程式是否會建立 MSSCCPRJ.SCC。SCC 檔案。|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>支援 Advanced 功能的函式（原始檔控制外掛程式 API 的版本1.3）
 此函式群組會定義原始檔控制外掛程式 API 版本1.3 中包含的其他功能。 它們可讓您存取更先進的原始檔控制特性和功能。

|功能|描述|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|將檔案清單從原始檔控制加入至目前的專案。|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|在沒有使用者介面的情況下，從原始檔控制中抓取檔案清單。|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|抓取原始檔控制中與本機檔案不同的檔案清單。|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|抓取指定原始檔控制外掛程式支援之擴充功能的旗標。|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|抓取使用者特定選項。|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|檢查位於原始檔控制之下的專案或專案中的目錄和檔案清單。 找到的每個目錄和檔案名都會傳遞至回呼函式。|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|檢查對檔案清單所做的名稱變更。 每個檔案名都會傳遞至回呼函式及其變更狀態。|

## <a name="requirements"></a>需求
 標頭： scc. h

 （在環境 SDK common include 資料夾中提供，預設的 *[drive]* \Program Files\VSIP 8.0 \ EnvSDK\common\inc; 也在具有 MSSCCI 範例的 VSIP 資料夾中提供， *[drive]* \PROGRAM Files\VSIP 8.0 \ MSSCCI）。

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
- [建立原始檔控制外掛程式](../extensibility/internals/creating-a-source-control-plug-in.md)