---
title: 錯誤代碼 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e3dc26b8dd2e17e201cf760db68d0faf7e231ed
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56688022"
---
# <a name="error-codes"></a>錯誤碼
原始檔控制外掛程式 API 函式會傳回錯誤，它應該是其中一個下列的錯誤代碼。 所有的錯誤是負數，警告或參考用錯誤代碼為正數，並成功則為 0。

|錯誤碼|值|描述|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|將檔案加入從兩個步驟中的原始檔控制外掛程式的支援。 如需詳細資訊，請參閱 < [SccSetOption](../extensibility/sccsetoption-function.md)。|
|`SCC_I_FILEDIFFERS`|6|本機檔案是不同於原始檔控制資料庫中的檔案 (例如[SccDiff](../extensibility/sccdiff-function.md)可能會傳回此值)。|
|`SCC_I_RELOADFILE`|5|在 原始檔控制作業; 期間變更本機檔案IDE 應該盡可能重新載入檔案。|
|`SCC_I_FILENOTAFFECTED`|4|檔案不受影響。|
|`SCC_I_PROJECTCREATED`|3|在原始檔控制作業期間建立的專案 (例如，在呼叫期間[SccOpenProject](../extensibility/sccopenproject-function.md)當`SCC_OP_CREATEIFNEW`指定旗標)。|
|`SCC_I_OPERATIONCANCELED`|2|作業已取消。|
|`SCC_I_ADV_SUPPORT`|1|指定的命令的進階選項的外掛程式支援。 如需詳細資訊，請參閱 < [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)。|
|`SCC_OK`|0|成功。|
|`SCC_E_INITIALIZEFAILED`|-1|錯誤： 初始化失敗。|
|`SCC_E_UNKNOWNPROJECT`|-2|錯誤： 專案是未知的。|
|`SCC_E_COULDNOTCREATEPROJECT`|-3|錯誤： 無法建立專案。|
|`SCC_E_NOTCHECKEDOUT`|-4|錯誤： 檔案未簽出。|
|`SCC_E_ALREADYCHECKEDOUT`|-5|錯誤： 檔案已簽出。|
|`SCC_E_FILEISLOCKED`|-6|錯誤： 檔案已鎖定。|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|錯誤： 檔案以獨佔方式簽出。|
|`SCC_E_ACCESSFAILURE`|-8|發生問題，存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|
|`SCC_E_CHECKINCONFLICT`|-9|錯誤： 發生衝突時簽入。|
|`SCC_E_FILEALREADYEXISTS`|-10|錯誤： 檔案已經存在。|
|`SCC_E_FILENOTCONTROLLED`|-11|錯誤： 檔案不在原始檔控制中。|
|`SCC_E_FILEISCHECKEDOUT`|-12|錯誤： 檔案已簽出。|
|`SCC_E_NOSPECIFIEDVERSION`|-13|錯誤： 沒有指定的版本。|
|`SCC_E_OPNOTSUPPORTED`|-14|錯誤： 不支援此作業。|
|`SCC_E_NONSPECIFICERROR`|-15|不明確的錯誤。|
|`SCC_E_OPNOTPERFORMED`|-16|未執行錯誤，這項操作。|
|`SCC_E_TYPENOTSUPPORTED`|-17|錯誤： 原始檔控制系統不支援檔案類型，例如二進位。|
|`SCC_E_VERIFYMERGE`|-18|檔案已經自動合併，但因為它是擱置的使用者驗證尚未簽。|
|`SCC_E_FIXMERGE`|-19|檔案已經自動合併，但尚未簽因合併衝突必須以手動方式解決。|
|`SCC_E_SHELLFAILURE`|-20|因為 shell 失敗的錯誤。|
|`SCC_E_INVALIDUSER`|-21|錯誤： 使用者不正確。|
|`SCC_E_PROJECTALREADYOPEN`|-22|錯誤： 專案已經開啟。|
|`SCC_E_PROJSYNTAXERR`|-23|專案的語法錯誤。|
|`SCC_E_INVALIDFILEPATH`|-24|錯誤： 檔案路徑無效。|
|`SCC_E_PROJNOTOPEN`|-25|錯誤： 專案未開啟。|
|`SCC_E_NOTAUTHORIZED`|-26|錯誤： 使用者未獲授權執行此作業。|
|`SCC_E_FILESYNTAXERR`|-27|檔案的語法錯誤。|
|`SCC_E_FILENOTEXIST`|-28|錯誤，將本機檔案不存在。|
|`SCC_E_CONNECTIONFAILURE`|-29|錯誤： 發生連接失敗。|
|`SCC_E_UNKNOWNERROR`|-30|未知的錯誤。|
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|背景取得作業目前正在進行中。|

## <a name="macros-provided-for-quick-checking"></a>提供的快速檢查巨集

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>備註
 所有的原始檔控制外掛程式 API 函式 (除了[SccAdd](../extensibility/sccadd-function.md)， [SccCheckin](../extensibility/scccheckin-function.md)，和[SccDiff](../extensibility/sccdiff-function.md)) 應該傳遞為引數的本機檔案執行時成功沒有工作資料夾中。 比方說，IDE 可能會發出呼叫[SccCheckout](../extensibility/scccheckout-function.md)或是[SccUncheckout](../extensibility/sccuncheckout-function.md)不存在於 [工作] 資料夾中，但存在於原始檔控制系統中的檔案。 這個呼叫會成功。 只有在沒有工作資料夾中，或在原始檔控制系統中的檔案時，才函式預期會失敗。

 某些函式，例如`SccAdd`並`SccCheckin`，特別應該傳回`SCC_E_FILENOTEXIST`工作資料夾中的檔案不存在的時。 其他函式都必須成功時的工作檔案不存在，如果函式在原始檔控制系統對有效的檔案名稱。

 原始檔控制外掛程式在即使外掛程式有唯讀檔案的某些作業期間，應該在 [工作] 資料夾中中, 進行檔案的權限的任何假設。 可以移動、 刪除及隨插即用中的控制項外變更的工作資料夾中的檔案。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)