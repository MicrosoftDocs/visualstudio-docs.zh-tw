---
title: 原始檔控制外掛程式 API 函式 |Microsoft Docs
description: 瞭解原始檔控制外掛程式 API 提供的函式，這些函式必須由原始檔控制外掛程式來執行。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4f93ddff78aa151218d0b46d017e4631d9489e44
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899598"
---
# <a name="source-control-plug-in-api-functions"></a>原始檔控制外掛程式 API 函式
原始檔控制外掛程式 API 提供下列函式，這些函式必須由原始檔控制外掛程式根據此 API 來執行。 這項參考會詳細說明每個函式的簽章，以及與位旗標和其他參數相關聯的語法。

## <a name="initialization-and-housekeeping-functions"></a>初始化和維護功能

|函式|描述|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|關閉專案。|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|提示使用者提供指定命令的 advanced 選項。|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|傳回原始檔控制外掛程式的版本。|
|[SccInitialize](../extensibility/sccinitialize-function.md)|初始化原始檔控制外掛程式。 它會針對外掛程式的每個實例呼叫一次。|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|開啟專案。|
|[SccSetOption](../extensibility/sccsetoption-function.md)|用來設定各種不同選項的泛型函數。 每個選項的開頭都 `SCC_OPT_xxx` 是，而且有自己的定義值集合。|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|當原始檔控制外掛程式需要插即用時呼叫一次。|

## <a name="core-source-control-functions"></a>核心原始檔控制功能

|函式|描述|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|將完整路徑名稱所指定的檔案陣列加入至原始檔控制系統。|
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|允許使用者流覽已在原始檔控制系統中的檔案，然後將這些檔案設為目前專案的一部分。|
|[SccCheckin](../extensibility/scccheckin-function.md)|簽入檔案的陣列。|
|[SccCheckout](../extensibility/scccheckout-function.md)|簽出檔案的陣列。|
|[SccDiff](../extensibility/sccdiff-function.md)|顯示以完整路徑名稱和原始檔控制下的版本指定的本機使用者檔案之間的差異。|
|[SccGet](../extensibility/sccget-function.md)|抓取一組檔案的唯讀複本。|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|透過) 檢查呼叫者要求 (的檔案狀態 `SccQueryInfo` 。|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|導致原始檔控制外掛程式提示使用者輸入對外掛程式有意義的專案路徑。|
|[SccHistory](../extensibility/scchistory-function.md)|顯示完整本機檔案名陣列的歷程記錄。|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|檢查檔案清單中的目前狀態。 此外，當檔案不 `pfnPopulate` 符合的準則時，也會使用函式來通知呼叫端 `nCommand` 。|
|[SccProperties](../extensibility/sccproperties-function.md)|顯示完整檔案的屬性。|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|檢查目前狀態的完整檔案清單。|
|[SccRemove](../extensibility/sccremove-function.md)|從原始檔控制系統移除完整檔案的陣列。|
|[SccRename](../extensibility/sccrename-function.md)|將指定的檔案重新命名為原始檔控制系統中的新名稱。|
|[SccRunScc](../extensibility/sccrunscc-function.md)|存取原始檔控制系統的各種功能。|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|復原檔陣列的簽出。|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>支援其他功能的函式 (版本1.2 的原始檔控制外掛程式 API) 
 這組函式會定義原始檔控制外掛程式 API 1.2 版中包含的其他功能。 它們可讓您存取更先進的原始檔控制功能。

|函式|描述|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|啟動批次作業。|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|在現有的父專案下建立具有指定名稱的子專案。|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|顯示完整路徑名稱和原始檔控制資料庫位置所指定的本機使用者目錄之間的差異。|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|檢查完整目錄清單中的目前狀態。|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|結束批次作業。|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|傳回指定專案的父路徑 (專案必須存在) 。|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|檢查是否允許在檔案上進行多次簽出。|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|檢查外掛程式是否會建立 MSSCCPRJ.SCC。SCC 檔。|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>支援 Advanced 功能的函式 (1.3 版的原始檔控制外掛程式 API) 
 這組函式會定義原始檔控制外掛程式 API 1.3 版中包含的其他功能。 它們可讓您存取更先進的原始檔控制功能。

|函式|描述|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|將檔案清單從原始檔控制加入至目前的專案。|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|從沒有使用者介面的原始檔控制中取出檔案清單。|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|抓取原始檔控制中不同于本機檔案的檔案清單。|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|抓取旗標，這些旗標會指定原始檔控制外掛程式所支援的擴充功能。|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|抓取使用者特定的選項。|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|檢查位於原始檔控制下的專案或專案中的目錄和檔案清單。 每個找到的目錄和檔案名都會傳遞至回呼函式。|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|檢查對檔案清單所做的名稱變更。 每個檔案名都會傳遞至具有其變更狀態的回撥函數。|

## <a name="requirements"></a>規格需求
 標頭： scc。h

 依預設，環境 SDK common include 資料夾中提供的 (*[磁片磁碟機]* \Program Files\VSIP 8.0 \ EnvSDK\common\inc;此外，也會在具有 MSSCCI 範例的 VSIP 資料夾中提供 *[磁片磁碟機]* \Program Files\VSIP 8.0 \ MSSCCI) 。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
- [建立原始檔控制外掛程式](../extensibility/internals/creating-a-source-control-plug-in.md)
