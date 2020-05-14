---
title: 特定命令使用的位標誌 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffa1fd8bf025d665977e87dc8b88da724ade5a8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740007"
---
# <a name="bitflags-used-by-specific-commands"></a>特定指令使用的位元號
可以通過在單個值中設置一個或多個位來修改原始程式碼管理外掛程式 API 中許多函數的行為。 這些值稱為位標誌。 此處詳細介紹了原始程式碼管理外掛程式 API 使用的各種位標誌,由使用它們的函數分組。

## <a name="checked-out-flag"></a>簽出旗標
 可以為[SccAdd](../extensibility/sccadd-function.md)或[SccCheckin](../extensibility/scccheckin-function.md)設置此標誌。

|旗標|值|描述|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|保持檔簽出狀態。|

## <a name="add-flags"></a>新增旗標
 這些標誌由[SccAdd](../extensibility/sccadd-function.md)使用。

|旗標|值|描述|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|原始程式碼管理外掛程式應自動檢測檔是文本還是二進位檔案。|
|`SCC_FILETYPE_TEXT`|0x01|檔案類型是文字。|
|`SCC_FILETYPE_BINARY`|0x04|檔類型是二進位的。 **注意:**`SCC_FILETYPE_TEXT``SCC_FILETYPE_BINARY`和 標誌是互斥的。   完全設置一個或兩個。|
|`SCC_ADD_STORELATEST`|0x02|僅存儲最新版本(無增量)。|

## <a name="diff-flags"></a>差異標誌
 [SccDiff](../extensibility/sccdiff-function.md)使用這些標誌來定義差異操作的範圍。 標誌`SCC_DIFF_QD_xxx`是互斥的。 如果指定了其中任何一個,則不提供視覺反饋。 在「快速差異」(QD)中,外掛程式不會確定檔的不同方式,僅當檔不同時。 如果未指定這些標誌,則執行"視覺差異";如果未指定這些標誌,則執行「視覺差異」。。」。"。"未指定任何標誌。計算並顯示詳細的文件差異。 如果不支援請求的 QD,外掛程式將移動到下一個最佳外掛程式。 例如,如果 IDE 請求校驗和,而外掛程式不支援它,則外掛程式執行完整內容檢查(仍然比可視顯示快得多)。

|旗標|值|描述|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|忽略大小寫差異。|
|`SCC_DIFF_IGNORESPACE`|0x0004|忽略空白差異。 **註:** `SCC_DIFF_IGNORECASE`和`SCC_DIFF_IGNORESPACE`標誌是可選的位標誌。|
|`SCC_DIFF_QD_CONTENTS`|0x0010|通過比較整個文件內容進行 QD。|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|按校驗和進行QD。|
|`SCC_DIFF_QD_TIME`|0x0040|按檔日期/時間戳的 QD。|
|`SCC_DIFF_QUICK_DIFF`|0x0070|這是用於檢查所有 QD 位標誌的蒙版。 它不應傳遞到函數中;三個 QD 位標誌是互斥的。 QD 始終表示不顯示 UI。|

## <a name="populatelist-flag"></a>填滿清單旗標
 此標誌由`fOptions`參數中的[SccPopulateList](../extensibility/sccpopulatelist-function.md)使用。

|旗標|值|描述|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|IDE 傳遞的是目錄,而不是檔。|

## <a name="populatedirlist-flags"></a>填充 DirList 標誌
 這些標誌由`fOptions`參數中的[SccpopulateDirList](../extensibility/sccpopulatedirlist-function.md)使用。

|選項值|值|描述|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|只檢查目錄的一個級別(這是預設值)。|
|SCC_PDL_RECURSIVE|0x0001|遞歸地檢查每個給定目錄下的所有目錄。|
|SCC_PDL_INCLUDEFILES|0x0002|在檢查過程中包括檔名。|

## <a name="openproject-flags"></a>開啟項目旗標
 這些標誌由`dwFlags`參數中的[SccOpenProject](../extensibility/sccopenproject-function.md)使用。

|選項值|值|描述|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|如果源控制項中不存在專案,請創建它。 如果未設定此標誌,則提示使用者創建專案(除非`SCC_OP_SILENTOPEN`指定了標誌)。|
|SCC_OP_SILENTOPEN|0x00000002L|不要提示使用者創建專案;因此,不提示使用者創建專案。只是傳`SCC_E_UNKNOWNPROJECT`回 。|

## <a name="get-flags"></a>取得標誌
 這些標誌由[SccGet](../extensibility/sccget-function.md)和[SccCheckout](../extensibility/scccheckout-function.md)使用。

|旗標|值|描述|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|IDE 傳遞目錄,而不是檔:獲取這些目錄中的所有檔。|
|`SCC_GET_RECURSIVE`|0x00000002L|IDE 正在傳遞目錄:獲取這些目錄及其所有子目錄。|

## <a name="noption-values"></a>nOption 值
 這些標誌由`nOption`參數中的[SccSetOption](../extensibility/sccsetoption-function.md)使用。

|旗標|值|描述|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|設置事件佇列的狀態。|
|`SCC_OPT_USERDATA`|0x00000002L|為`SCC_OPT_NAMECHANGEPFN`指定用戶數據。|
|`SCC_OPT_HASCANCELMODE`|0x0000003L|IDE 可以處理取消。|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|為名稱更改設置回調。|
|`SCC_OPT_SCCCHECKOUTONLY`|0x0000005L|禁用原始碼管理外掛程式 UI 簽出,並且不設置工作目錄。|
|`SCC_OPT_SHARESUBPROJ`|0x0000006L|從原始程式碼管理系統添加以指定工作目錄。 如果關聯專案是直接的後代,請嘗試共用到其中。|

## <a name="dwval-bitflags"></a>dwVal 位元
 這些標誌由`dwVal`參數中的[SccSetOption](../extensibility/sccsetoption-function.md)使用。

|旗標|值|描述|依`nOption`數值使用|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|掛起事件佇列活動。|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|啟用事件佇列日誌記錄。|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L|( 預設 )沒有取消模式;如果需要,外掛程式必須提供。|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1L|IDE 句柄取消。|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L|( 預設 )可以從外掛程式 UI 簽出;請從外掛程式 UI 中籤出。工作目錄已設置。|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1L|沒有外掛程式 UI 簽出,沒有工作目錄。|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>另請參閱
- [原始程式管理外掛程式](../extensibility/source-control-plug-ins.md)
