---
title: 特定命令所使用的位旗標 |Microsoft Docs
description: 瞭解原始檔控制外掛程式 API 所使用的位旗標，並依使用這些 API 的函式進行組織。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 41f070d61e547724b3067a9f4a1980d658fc30be
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097288"
---
# <a name="bitflags-used-by-specific-commands"></a>特定命令所使用的位旗標
您可以藉由在單一值中設定一或多個位，來修改原始檔控制外掛程式 API 中許多函數的行為。 這些值稱為位旗標。 原始檔控制外掛程式 API 所使用的各種位旗標詳述于此處，並依使用它們的函式進行分組。

## <a name="checked-out-flag"></a>簽出旗標
 您可以針對 [SccAdd](../extensibility/sccadd-function.md) 或 [SccCheckin](../extensibility/scccheckin-function.md)設定這個旗標。

|旗標|值|描述|
|----------|-----------|-----------------|
|`SCC_KEEP_CHECKEDOUT`|0x1000|將檔案保持簽出。|

## <a name="add-flags"></a>新增旗標
 [SccAdd](../extensibility/sccadd-function.md)會使用這些旗標。

|旗標|值|描述|
|----------|-----------|-----------------|
|`SCC_FILETYPE_AUTO`|0x00|原始檔控制外掛程式應該會自動偵測檔案是文字或二進位檔。|
|`SCC_FILETYPE_TEXT`|0x01|檔案類型為 text。|
|`SCC_FILETYPE_BINARY`|0x04|檔案類型為 binary。 **注意：** `SCC_FILETYPE_TEXT`和 `SCC_FILETYPE_BINARY` 旗標彼此互斥。   只設定一或兩個。|
|`SCC_ADD_STORELATEST`|0x02|只儲存最新版本 (沒有任何差異) 。|

## <a name="diff-flags"></a>差異旗標
 [SccDiff](../extensibility/sccdiff-function.md)會使用這些旗標來定義差異作業的範圍。 `SCC_DIFF_QD_xxx`旗標彼此互斥。 如果指定了任何一個，則不會提供任何視覺效果的意見反應。 在「快速差異」 (QD) 中，外掛程式不會判斷檔案的不同之處，只有在不同的情況下才會決定。 如果未指定這些旗標，則會完成「視覺化差異」;系統會計算並顯示詳細的檔案差異。 如果要求的 QD 不受支援，則外掛程式會移至下一個最佳的設定。 比方說，如果 IDE 要求總和檢查碼，而且外掛程式不支援總和檢查碼，則外掛程式會進行全內容檢查， (還是比視覺顯示) 快得多。

|旗標|值|描述|
|----------|-----------|-----------------|
|`SCC_DIFF_IGNORECASE`|0x0002|忽略大小寫差異。|
|`SCC_DIFF_IGNORESPACE`|0x0004|略過空白字元的差異。 **注意：** `SCC_DIFF_IGNORECASE` 和 `SCC_DIFF_IGNORESPACE` 旗標是選擇性的位旗標。|
|`SCC_DIFF_QD_CONTENTS`|0x0010|藉由比較整個檔案內容來 QD。|
|`SCC_DIFF_QD_CHECKSUM`|0x0020|依總和檢查碼 QD。|
|`SCC_DIFF_QD_TIME`|0x0040|依檔案日期/時間戳記來 QD。|
|`SCC_DIFF_QUICK_DIFF`|0x0070|這是用來檢查所有 QD 位旗標的遮罩。 它不應該傳遞至函式;這三個 QD 位旗標是互斥的。 QD 一律表示不顯示 UI。|

## <a name="populatelist-flag"></a>PopulateList 旗標
 參數中的 [SccPopulateList](../extensibility/sccpopulatelist-function.md) 會使用此旗標 `fOptions` 。

|旗標|值|描述|
|----------|-----------|-----------------|
|`SCC_PL_DIR`|0x00000001L|IDE 正在傳遞目錄，而不是檔案。|

## <a name="populatedirlist-flags"></a>PopulateDirList 旗標
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)會在參數中使用這些旗標 `fOptions` 。

|選項值|值|描述|
|------------------|-----------|-----------------|
|SCC_PDL_ONELEVEL|0x0000|只檢查目錄的一個目錄層級 (這是預設) 。|
|SCC_PDL_RECURSIVE|0x0001|以遞迴方式檢查每個指定目錄下的所有目錄。|
|SCC_PDL_INCLUDEFILES|0x0002|在檢查程式中包含檔案名。|

## <a name="openproject-flags"></a>File.openproject 旗標
 [SccOpenProject](../extensibility/sccopenproject-function.md)會在參數中使用這些旗標 `dwFlags` 。

|選項值|值|描述|
|------------------|-----------|-----------------|
|SCC_OP_CREATEIFNEW|0x00000001L|如果專案不存在於原始檔控制中，請加以建立。 如果未設定此旗標，則會提示使用者建立 (除非 `SCC_OP_SILENTOPEN`) 指定旗標。|
|SCC_OP_SILENTOPEN|0x00000002L|不要提示使用者建立專案;只傳回 `SCC_E_UNKNOWNPROJECT` 。|

## <a name="get-flags"></a>取得旗標
 [SccGet](../extensibility/sccget-function.md)和[SccCheckout](../extensibility/scccheckout-function.md)會使用這些旗標。

|旗標|值|描述|
|----------|-----------|-----------------|
|`SCC_GET_ALL`|0x00000001L|IDE 會傳遞目錄，而不是檔案：取得這些目錄中的所有檔案。|
|`SCC_GET_RECURSIVE`|0x00000002L|IDE 會傳遞目錄：取得這些目錄及其所有子目錄。|

## <a name="noption-values"></a>nOption 值
 [SccSetOption](../extensibility/sccsetoption-function.md)會在參數中使用這些旗標 `nOption` 。

|旗標|值|描述|
|----------|-----------|-----------------|
|`SCC_OPT_EVENTQUEUE`|0x00000001L|設定事件佇列的狀態。|
|`SCC_OPT_USERDATA`|0x00000002L|指定的使用者資料 `SCC_OPT_NAMECHANGEPFN` 。|
|`SCC_OPT_HASCANCELMODE`|0x00000003L|IDE 可以處理取消。|
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|設定名稱變更的回呼。|
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|停用原始檔控制外掛程式 UI 簽出，並不要設定工作目錄。|
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|從原始檔控制系統加入，以指定工作目錄。 如果是直接的子系，請嘗試共用到相關聯的專案。|

## <a name="dwval-bitflags"></a>dwVal 位旗標
 [SccSetOption](../extensibility/sccsetoption-function.md)會在參數中使用這些旗標 `dwVal` 。

|旗標|值|描述|依 `nOption` 值使用|
|----------|-----------|-----------------|-----------------------------|
|`SCC_OPT_EQ_DISABLE`|0x00L|暫停事件佇列活動。|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_EQ_ENABLE`|0x01L|啟用事件佇列記錄。|`SCC_OPT_EVENTQUEUE`|
|`SCC_OPT_HCM_NO`|0L| (預設) 沒有取消模式;如有需要，外掛程式必須提供。|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_HCM_YES`|1L|IDE 會處理取消。|`SCC_OPT_HASCANCELMODE`|
|`SCC_OPT_SCO_NO`|0L| (預設值) 確定從外掛程式 UI 簽出;工作目錄已設定。|`SCC_OPT_SCCCHECKOUTONLY`|
|`SCC_OPT_SCO_YES`|1L|沒有任何外掛程式 UI 簽出，沒有工作目錄。|`SCC_OPT_SCCCHECKOUTONLY`|

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
