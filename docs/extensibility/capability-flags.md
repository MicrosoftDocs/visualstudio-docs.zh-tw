---
title: 功能標誌 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9660cbe5a18e82974858fa4d923a38fc73e773f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739864"
---
# <a name="capability-flags"></a>功能旗標
SCC_CAP_*xxx*標誌是用於指示原始程式碼管理外掛程式功能的位標誌。 SCC_EXCAP_*xxx*標誌是增量標誌,指示擴展的功能並解析為整數值。

|功能代碼|值|描述|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001L|支援[SccRemove](../extensibility/sccremove-function.md)和命令。|
|`SCC_CAP_RENAME`|0x00000002L|支援["SccRename"](../extensibility/sccrename-function.md)和"命令"。|
|`SCC_CAP_DIFF`|0x00000004L|支援[SccDiff](../extensibility/sccdiff-function.md)和命令。|
|`SCC_CAP_HISTORY`|0x00000008L|支援[「史抄送」](../extensibility/scchistory-function.md)和「命令」。|
|`SCC_CAP_PROPERTIES`|0x00000010L|支援[Scc 屬性](../extensibility/sccproperties-function.md)和命令。|
|`SCC_CAP_RUNSCC`|0x0000020L|支援[SccRunScc](../extensibility/sccrunscc-function.md)和命令。|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|支援[SccGet 命令選項](../extensibility/sccgetcommandoptions-function.md)和命令。|
|`SCC_CAP_QUERYINFO`|0x0000080L|支援[SccQuery 資訊和](../extensibility/sccqueryinfo-function.md)命令。|
|`SCC_CAP_GETEVENTS`|0x00000100L|支援[SccGet 事件](../extensibility/sccgetevents-function.md)和命令。|
|`SCC_CAP_GETPROJPATH`|0x00000200L|支援[SccGetProjPath](../extensibility/sccgetprojpath-function.md)和命令。|
|`SCC_CAP_ADDFROMSCC`|0x00000400L|支援[SccAdd FromScc](../extensibility/sccaddfromscc-function.md)和命令。|
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|支援結帳註釋。|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|支持簽入註釋。|
|`SCC_CAP_COMMENTADD`|0x00002000L|支援對"添加"的評論。|
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|支援刪除的註釋。|
|`SCC_CAP_TEXTOUT`|0x00008000L|將文字寫入 IDE 提供的輸出函數。|
|`SCC_CAP_ADD_STORELATEST`|0x0020000L|支援存儲沒有增量的檔。|
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|支援多個文件歷史記錄。|
|`SCC_CAP_IGNORECASE`|0x0080000L|支援不區分大小寫的文件比較。|
|`SCC_CAP_IGNORESPACE`|0x0100000L|支援忽略空白的文件比較。|
|`SCC_CAP_POPULATELIST`|0x0200000L|支援查找額外的檔。|
|`SCC_CAP_COMMENTPROJECT`|0x0400000L|支援對創建項目的評論。|
|`SCC_CAP_DIFFALWAYS`|0x1000000L|如果處於控制之下,則支援所有狀態中的 diff。|
|`SCC_CAP_GET_NOUI`|0x2000000L|外掛程式不支援取得的 UI,但 IDE 仍可能呼叫[SccGet](../extensibility/sccget-function.md)。|
|`SCC_CAP_REENTRANT`|0x4000000L|外掛程式是重入和線程安全的。 在版本 1.0 中,沒有外掛程式被假定為重入和線程安全。 如果 1.1 外掛程式設定此位,則允許主機並行打開多個專案。|

## <a name="capability-bits-added-in-version-12"></a>在版本 1.2 中新增的功能位

|功能代碼|值|描述|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|支援[SccCreate 子專案](../extensibility/scccreatesubproject-function.md)。|
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|支援[SccGet 父項目路徑](../extensibility/sccgetparentprojectpath-function.md)。|
|`SCC_CAP_BATCH`|0x00040000L|支援[SccBeginBatch](../extensibility/sccbeginbatch-function.md)和[SccEndBatch](../extensibility/sccendbatch-function.md)。|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|支援[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)。|
|`SCC_CAP_DIRECTORYDIFF`|0x0010000L|支援[SccDirDiff](../extensibility/sccdirdiff-function.md)。|
|`SCC_CAP_MULTICHECKOUT`|0x0800000L|支援對檔案的多個簽出,並且[SccIs 多簽出啟用](../extensibility/sccismulticheckoutenabled-function.md)。|
|`SCC_CAP_SCCFILE`|0x8000000L|支援*MSSCCPRJ.SCC*檔(受使用者/管理員覆蓋)和[SccWillCreateSccFile。](../extensibility/sccwillcreatesccfile-function.md)|

## <a name="capability-bits-added-in-version-13"></a>在版本 1.3 中新增的功能位
 這些標誌一次傳遞一個到[SccGet 擴充功能功能](../extensibility/sccgetextendedcapabilities-function.md),以確定該功能是否受支援。

|擴充功能代碼|值|描述|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|支援簽出`SCC_CHECKOUT_LOCALVER`選項。|
|`SCC_EXCAP_BACKGROUND_GET`|2|支援[Scc 背景 。](../extensibility/sccbackgroundget-function.md)|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|支援[SccEnum 變更檔案](../extensibility/sccenumchangedfiles-function.md)。|
|`SCC_EXCAP_POPULATELIST_DIR`|4|支援查找額外的目錄。|
|`SCC_EXCAP_QUERYCHANGES`|5|支援枚舉檔更改。|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|支援[SCC 中的 Sccadd 檔案](../extensibility/sccaddfilesfromscc-function.md)。|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|支援[SccGetUserOption](../extensibility/sccgetuseroption-function.md)。|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|支援在多個線程上調用 SccQueryInfo。|
|`SCC_EXCAP_REMOVE_DIR`|9|支援 SccRemoveDir 函數。|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|可以刪除簽出的檔。|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|可以重新命名簽出的檔案。|

## <a name="see-also"></a>另請參閱
- [原始程式管理外掛程式](../extensibility/source-control-plug-ins.md)
