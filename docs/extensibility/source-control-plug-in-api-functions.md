---
title: "原始檔控制外掛程式 API 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: beaab13c76b3d50f97662e66c1f72dc83161e96d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-plug-in-api-functions"></a>原始檔控制外掛程式 API 函式
原始檔控制外掛程式 API 提供下列功能，必須由原始檔控制外掛程式依據這個應用程式開發介面實作。 每個函式和語意的簽章相關聯的位元旗標，此參考中的詳細說明其他參數。  
  
## <a name="initialization-and-housekeeping-functions"></a>初始設定和維護函式  
  
|功能|描述|  
|--------------|-----------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|關閉專案。|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|提示使用者提供對於指定的命令的進階選項。|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|傳回版本的原始檔控制外掛程式。|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|初始化原始檔控制外掛程式。 它會呼叫一次針對每個外掛程式執行個體。|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|開啟專案。|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|泛型的函式，用來設定各種不同的選項。 每個選項開頭`SCC_OPT_xxx`而且有它自己組定義的值。|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|呼叫一次當原始檔控制外掛程式需要已被拔除。|  
  
## <a name="core-source-control-functions"></a>核心原始檔控制功能  
  
|功能|描述|  
|--------------|-----------------|  
|[SccAdd](../extensibility/sccadd-function.md)|將陣列的原始檔控制系統的完整的路徑名稱所指定的檔案。|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|可讓使用者瀏覽已在原始檔控制系統中的檔案，然後將這些檔案目前的專案。|  
|[SccCheckin](../extensibility/scccheckin-function.md)|簽入的檔案陣列。|  
|[SccCheckout](../extensibility/scccheckout-function.md)|簽出的檔案陣列。|  
|[SccDiff](../extensibility/sccdiff-function.md)|顯示本機使用者的完整的路徑名稱和原始檔控制下的版本所指定的檔案之間的差異。|  
|[SccGet](../extensibility/sccget-function.md)|擷取一組檔案的唯讀副本。|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|會檢查呼叫端要求有關的檔案狀態 (透過`SccQueryInfo`)。|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|會造成原始檔控制外掛程式，以提示使用者輸入有意義的外掛程式的專案路徑。|  
|[SccHistory](../extensibility/scchistory-function.md)|顯示完整的本機檔案名稱的陣列的歷程記錄。|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|會檢查其目前狀態的檔案清單。 此外，使用`pfnPopulate`函式的檔案不相符的準則時，通知呼叫端`nCommand`。|  
|[SccProperties](../extensibility/sccproperties-function.md)|顯示完整的檔案屬性。|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|會檢查其目前狀態的完整檔案清單。|  
|[SccRemove](../extensibility/sccremove-function.md)|從原始檔控制系統中移除完整格式的檔案的陣列。|  
|[SccRename](../extensibility/sccrename-function.md)|新名稱重新命名指定的檔案，在原始檔控制系統中。|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|會存取原始檔控制系統功能的完整範圍。|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|復原簽出檔案的陣列。|  
  
## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>支援的額外功能 （1.2 版的原始檔控制外掛程式 API） 的函式  
 此群組的函式定義的原始檔控制外掛程式 API 1.2 版中包含的其他功能。 它們提供更進階的原始檔控制功能和功能的存取。  
  
|功能|描述|  
|--------------|-----------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|啟動批次作業。|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|建立具有指定名稱的現有父專案底下的子專案。|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|顯示指定完整的路徑名稱和原始檔控制資料庫位置的本機使用者的目錄之間的差異。|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|會檢查完整的目錄清單及其目前狀態。|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|結束批次作業。|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|傳回父路徑指定的專案 （專案必須存在）。|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|檢查是否允許多重簽出檔案。|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|檢查是否外掛程式會建立 MSSCCPRJ。SCC 檔案。|  
  
## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>支援進階的功能 （1.3 版的原始檔控制外掛程式 API） 的函式  
 此群組的函式定義的原始檔控制外掛程式 API 1.3 版中包含的其他功能。 它們提供更進階的原始檔控制功能和功能的存取。  
  
|功能|描述|  
|--------------|-----------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|從原始檔控制加入目前專案的檔案清單。|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|從沒有使用者介面的原始檔控制中擷取檔案的清單。|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|擷取原始檔控制中，不同於本機檔案的檔案的清單。|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|擷取旗標，指定原始檔控制外掛程式所支援的擴充的功能。|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|擷取使用者特定的選項。|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|會檢查目錄和檔案的專案或在原始檔控制的專案中的清單。 找到的每個目錄和檔案名稱傳遞至回呼函式。|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|會檢查檔案的清單名稱變更。 每個檔案名稱會傳遞至其變更狀態的回呼函式。|  
  
## <a name="requirements"></a>需求  
 標頭： scc.h  
  
 (環境 SDK 中提供的通用資料夾中，預設包含*[磁碟機]*\Program Files\VSIP 8.0\EnvSDK\common\inc; MSSCCI 範例中，VSIP 資料夾中也提供*[磁碟機]*\ProgramFiles\VSIP 8.0\MSSCCI)。  
  
## <a name="see-also"></a>請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)   
 [建立原始檔控制外掛程式](../extensibility/internals/creating-a-source-control-plug-in.md)