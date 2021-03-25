---
title: 功能旗標 |Microsoft Docs
description: 瞭解 SCC_CAP_xxx 旗標，這些旗標表示原始檔控制外掛程式的功能，以及表示擴充功能的 SCC_EXCAP_xxx 旗標。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 12acefb99de787d55bc0f932757dde5ea928c6cb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094922"
---
# <a name="capability-flags"></a>功能旗標
SCC_CAP_ *xxx* 旗標是用來表示原始檔控制外掛程式功能的位旗標。 SCC_EXCAP_ *xxx* 旗標是遞增旗標，表示擴充的功能並解析為整數值。

|功能代碼|值|描述|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001L|支援 [SccRemove](../extensibility/sccremove-function.md) 和命令。|
|`SCC_CAP_RENAME`|0x00000002L|支援 [SccRename](../extensibility/sccrename-function.md) 和命令。|
|`SCC_CAP_DIFF`|0x00000004L|支援 [SccDiff](../extensibility/sccdiff-function.md) 和命令。|
|`SCC_CAP_HISTORY`|0x00000008L|支援 [SccHistory](../extensibility/scchistory-function.md) 和命令。|
|`SCC_CAP_PROPERTIES`|0x00000010L|支援 [SccProperties](../extensibility/sccproperties-function.md) 和命令。|
|`SCC_CAP_RUNSCC`|0x00000020L|支援 [SccRunScc](../extensibility/sccrunscc-function.md) 和命令。|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|支援 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) 和命令。|
|`SCC_CAP_QUERYINFO`|0x00000080L|支援 [SccQueryInfo](../extensibility/sccqueryinfo-function.md) 和命令。|
|`SCC_CAP_GETEVENTS`|0x00000100L|支援 [SccGetEvents](../extensibility/sccgetevents-function.md) 和命令。|
|`SCC_CAP_GETPROJPATH`|0x00000200L|支援 [SccGetProjPath](../extensibility/sccgetprojpath-function.md) 和命令。|
|`SCC_CAP_ADDFROMSCC`|0x00000400L|支援 [SccAddFromScc](../extensibility/sccaddfromscc-function.md) 和命令。|
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|支援簽出時的留言。|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|支援簽入的批註。|
|`SCC_CAP_COMMENTADD`|0x00002000L|支援新增的批註。|
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|支援移除時的批註。|
|`SCC_CAP_TEXTOUT`|0x00008000L|將文字寫入 IDE 提供的輸出函數。|
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|支援儲存不具差異的檔案。|
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|支援多個檔案歷程記錄。|
|`SCC_CAP_IGNORECASE`|0x00800000L|支援不區分大小寫的檔案比較。|
|`SCC_CAP_IGNORESPACE`|0x01000000L|支援忽略泛空白字元的檔案比較。|
|`SCC_CAP_POPULATELIST`|0x02000000L|支援尋找額外的檔案。|
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|支援建立專案的批註。|
|`SCC_CAP_DIFFALWAYS`|0x10000000L|在 [控制項] 下，支援所有狀態的差異。|
|`SCC_CAP_GET_NOUI`|0x20000000L|外掛程式不支援 Get 的 UI，但 IDE 仍可呼叫 [SccGet](../extensibility/sccget-function.md)。|
|`SCC_CAP_REENTRANT`|0x40000000L|外掛程式是可重入和安全線程。 在1.0 版中，沒有任何外掛程式被視為可重新進入和安全線程。 如果1.1 外掛程式設定此位，則允許主機平行開啟多個專案。|

## <a name="capability-bits-added-in-version-12"></a>版本1.2 中新增的功能位

|功能代碼|值|描述|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|支援 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)。|
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|支援 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)。|
|`SCC_CAP_BATCH`|0x00040000L|支援 [SccBeginBatch](../extensibility/sccbeginbatch-function.md) 和 [SccEndBatch](../extensibility/sccendbatch-function.md)。|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|支援 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)。|
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|支援 [SccDirDiff](../extensibility/sccdirdiff-function.md)。|
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|支援檔案和 [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)上的多個簽出。|
|`SCC_CAP_SCCFILE`|0x80000000L|支援 *mssccprj.scc* (受限於使用者/系統管理員覆寫) 和 [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)。|

## <a name="capability-bits-added-in-version-13"></a>版本1.3 中新增的功能位
 這些旗標一次傳遞至 [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) 函式，以判斷是否支援此功能。

|擴充功能程式碼|值|描述|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|支援 `SCC_CHECKOUT_LOCALVER` 簽出的選項。|
|`SCC_EXCAP_BACKGROUND_GET`|2|支援 [SccBackgroundGet](../extensibility/sccbackgroundget-function.md)。|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|支援 [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)。|
|`SCC_EXCAP_POPULATELIST_DIR`|4|支援尋找額外的目錄。|
|`SCC_EXCAP_QUERYCHANGES`|5|支援列舉檔案變更。|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|支援 [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)。|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|支援 [SccGetUserOption](../extensibility/sccgetuseroption-function.md)。|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|支援在多個執行緒上呼叫 SccQueryInfo。|
|`SCC_EXCAP_REMOVE_DIR`|9|支援 SccRemoveDir 函數。|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|可以刪除已簽出的檔案。|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|可以重新命名已簽出的檔案。|

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
