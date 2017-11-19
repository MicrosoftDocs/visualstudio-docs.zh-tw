---
title: "特定的命令所使用的位元旗標 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, bitflags used by specific commands
ms.assetid: 37969977-6f7d-45c9-ba03-1306ae71f5d1
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e66d0f67e3774b1cbc908bb6b1bd13884a1d3171
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="bitflags-used-by-specific-commands"></a>特定的命令所使用的位元旗標
藉由單一值中設定一個或多個位元可以修改的原始檔控制外掛程式 API 中的函式的行為。 這些值稱為位元旗標。 原始檔控制外掛程式 API 所使用的位元各種的旗標的詳細資訊，所使用的函式分組。  
  
## <a name="checked-out-flag"></a>簽出旗標  
 這個旗標可以設定任何[SccAdd](../extensibility/sccadd-function.md)或[SccCheckin](../extensibility/scccheckin-function.md)。  
  
|旗標|值|說明|  
|----------|-----------|-----------------|  
|`SCC_KEEP_CHECKEDOUT`|0x1000|保留簽出檔案。|  
  
## <a name="add-flags"></a>加入旗標  
 這些旗標由[SccAdd](../extensibility/sccadd-function.md)。  
  
|旗標|值|說明|  
|----------|-----------|-----------------|  
|`SCC_FILETYPE_AUTO`|0x00|原始檔控制外掛程式應該自動偵測檔案是否為文字或二進位檔。|  
|`SCC_FILETYPE_TEXT`|0x01|檔案類型為文字。|  
|`SCC_FILETYPE_BINARY`|0x04|檔案類型是二進位檔案。 **注意：** `SCC_FILETYPE_TEXT`和`SCC_FILETYPE_BINARY`旗標互斥。   設定一個或兩者皆非。|  
|`SCC_ADD_STORELATEST`|0x02|儲存最新版本只 (沒有 delta)。|  
  
## <a name="diff-flags"></a>差異比對的旗標  
 [SccDiff](../extensibility/sccdiff-function.md)來定義範圍的差異作業會使用這些旗標。 `SCC_DIFF_QD_xxx`旗標互斥。 如果其中任何一個指定，沒有視覺回應就是要提供。 在 「 快速差異 」 (QD)，外掛程式不會判斷檔案的不同，只有在不同的方式。 如果沒有任何這些旗標指定，則是 「 visual 差異比對";詳細的檔案的差異會計算並顯示。 如果不支援要求的 QD，外掛程式移到下一個最佳提案。 比方說，如果 IDE 要求總和檢查碼，而且外掛程式不支援它，外掛程式未完整內容檢查 （仍速度，比視覺顯示）。  
  
|旗標|值|說明|  
|----------|-----------|-----------------|  
|`SCC_DIFF_IGNORECASE`|0x0002|忽略大小寫差異。|  
|`SCC_DIFF_IGNORESPACE`|0x0004|表示忽略空白字元的差異。 **注意：** `SCC_DIFF_IGNORECASE`和`SCC_DIFF_IGNORESPACE`旗標是選擇性的位元旗標。|  
|`SCC_DIFF_QD_CONTENTS`|0x0010|QD 藉由比較整個檔案內容。|  
|`SCC_DIFF_QD_CHECKSUM`|0x0020|QD 的總和檢查碼。|  
|`SCC_DIFF_QD_TIME`|0x0040|QD 檔案的日期/時間戳記。|  
|`SCC_DIFF_QUICK_DIFF`|0x0070|這是用來檢查所有 QD 位元旗標遮罩。 不應該傳遞至函式。三個的 QD 位元旗標互斥。 QD 一律表示不顯示 UI。|  
  
## <a name="populatelist-flag"></a>PopulateList 旗標  
 這個旗標由[SccPopulateList](../extensibility/sccpopulatelist-function.md)中`fOptions`參數。  
  
|旗標|值|說明|  
|----------|-----------|-----------------|  
|`SCC_PL_DIR`|0x00000001L|IDE 傳遞不是檔案的目錄。|  
  
## <a name="populatedirlist-flags"></a>PopulateDirList 旗標  
 這些旗標由[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)中`fOptions`參數。  
  
|選項值|值|說明|  
|------------------|-----------|-----------------|  
|SCC_PDL_ONELEVEL|0x0000|檢查只有一個層級的目錄 （這是預設值） 的目錄。|  
|SCC_PDL_RECURSIVE|0x0001|以遞迴方式檢查每個指定的目錄底下的所有目錄。|  
|SCC_PDL_INCLUDEFILES|0x0002|檢查處理序中包含檔案名稱。|  
  
## <a name="openproject-flags"></a>OpenProject 旗標  
 這些旗標由[SccOpenProject](../extensibility/sccopenproject-function.md)中`dwFlags`參數。  
  
|選項值|值|說明|  
|------------------|-----------|-----------------|  
|SCC_OP_CREATEIFNEW|0x00000001L|如果專案不存在原始檔控制中，建立它。 如果未設定此旗標，提示使用者来建立專案 (除非`SCC_OP_SILENTOPEN`指定旗標)。|  
|SCC_OP_SILENTOPEN|0x00000002L|不提示使用者建立專案。僅以傳回`SCC_E_UNKNOWNPROJECT`。|  
  
## <a name="get-flags"></a>取得旗標  
 這些旗標由[SccGet](../extensibility/sccget-function.md)和[SccCheckout](../extensibility/scccheckout-function.md)。  
  
|旗標|值|說明|  
|----------|-----------|-----------------|  
|`SCC_GET_ALL`|0x00000001L|IDE 會傳遞目錄，而不複製檔案： 取得這些目錄中的所有檔案。|  
|`SCC_GET_RECURSIVE`|0x00000002L|IDE 會傳遞目錄： 取得這些目錄和其所有子目錄。|  
  
## <a name="noption-values"></a>nOption 值  
 這些旗標由[SccSetOption](../extensibility/sccsetoption-function.md)中`nOption`參數。  
  
|旗標|值|說明|  
|----------|-----------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|0x00000001L|設定事件佇列的狀態。|  
|`SCC_OPT_USERDATA`|0x00000002L|指定的使用者資料`SCC_OPT_NAMECHANGEPFN`。|  
|`SCC_OPT_HASCANCELMODE`|0x00000003L|IDE 可以處理取消 5d|  
|`SCC_OPT_NAMECHANGEPFN`|0x00000004L|設定名稱變更的回呼。|  
|`SCC_OPT_SCCCHECKOUTONLY`|0x00000005L|停用原始檔控制外掛程式 UI 簽出和未設定工作目錄。|  
|`SCC_OPT_SHARESUBPROJ`|0x00000006L|加入原始檔控制系統，來指定工作目錄。 嘗試共用到相關聯的專案，如果其直屬下階。|  
  
## <a name="dwval-bitflags"></a>在 dwVal 位元旗標  
 這些旗標由[SccSetOption](../extensibility/sccsetoption-function.md)中`dwVal`參數。  
  
|旗標|值|說明|使用`nOption`值|  
|----------|-----------|-----------------|-----------------------------|  
|`SCC_OPT_EQ_DISABLE`|0x00L|暫止事件佇列活動。|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_EQ_ENABLE`|0x01L|啟用事件佇列記錄。|`SCC_OPT_EVENTQUEUE`|  
|`SCC_OPT_HCM_NO`|0L|（預設值）有無取消 5d; 模式。外掛程式必須視需要提供。|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_HCM_YES`|1 L|IDE 會處理取消 5d;。|`SCC_OPT_HASCANCELMODE`|  
|`SCC_OPT_SCO_NO`|0L|（預設值）確定要從外掛程式 UI; 簽出設定工作目錄。|`SCC_OPT_SCCCHECKOUTONLY`|  
|`SCC_OPT_SCO_YES`|1 L|沒有外掛程式 UI 簽出，沒有工作目錄。|`SCC_OPT_SCCCHECKOUTONLY`|  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)