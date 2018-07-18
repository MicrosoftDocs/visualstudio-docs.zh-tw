---
title: 錯誤代碼 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6feb9bfa3b2adb437fd03b5c0b8d4448df4b6f50
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130770"
---
# <a name="error-codes"></a>錯誤碼
原始檔控制外掛程式 API 函式會傳回錯誤，預期為下列錯誤碼。 所有的錯誤是負數，警告或參考用錯誤代碼是正數，以及成功是 0。  
  
|錯誤碼|值|描述|  
|----------------|-----------|-----------------|  
|`SCC_I_SHARESUBPROJOK`|7|將檔案從兩個步驟中的原始檔控制外掛程式的支援。 如需詳細資訊，請參閱[SccSetOption](../extensibility/sccsetoption-function.md)。|  
|`SCC_I_FILEDIFFERS`|6|本機檔案是不同於原始檔控制資料庫中的檔案 (例如， [SccDiff](../extensibility/sccdiff-function.md)可能會傳回此值)。|  
|`SCC_I_RELOADFILE`|5|在 原始檔控制作業; 期間變更本機檔案IDE 應該盡可能重新載入檔案。|  
|`SCC_I_FILENOTAFFECTED`|4|檔案不受影響。|  
|`SCC_I_PROJECTCREATED`|3|原始檔控制作業期間所建立的專案 (例如，在呼叫期間[SccOpenProject](../extensibility/sccopenproject-function.md)時`SCC_OP_CREATEIFNEW`指定旗標)。|  
|`SCC_I_OPERATIONCANCELED`|2|已取消操作。|  
|`SCC_I_ADV_SUPPORT`|1|外掛程式支援的進階選項指定的命令。 如需詳細資訊，請參閱[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)。|  
|`SCC_OK`|0|成功。|  
|`SCC_E_INITIALIZEFAILED`|-1|錯誤： 無法初始化。|  
|`SCC_E_UNKNOWNPROJECT`|-2|錯誤： 專案是未知的。|  
|`SCC_E_COULDNOTCREATEPROJECT`|-3|錯誤： 無法建立專案。|  
|`SCC_E_NOTCHECKEDOUT`|-4|錯誤： 檔案未簽出。|  
|`SCC_E_ALREADYCHECKEDOUT`|-5|錯誤： 檔案已簽出。|  
|`SCC_E_FILEISLOCKED`|-6|錯誤： 檔案已鎖定。|  
|`SCC_E_FILEOUTEXCLUSIVE`|-7|錯誤： 檔案以獨佔方式簽出。|  
|`SCC_E_ACCESSFAILURE`|-8|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|`SCC_E_CHECKINCONFLICT`|-9|錯誤： 發生衝突時簽入。|  
|`SCC_E_FILEALREADYEXISTS`|-10|錯誤： 檔案已經存在。|  
|`SCC_E_FILENOTCONTROLLED`|-11|錯誤： 檔案不是原始檔控制之下。|  
|`SCC_E_FILEISCHECKEDOUT`|-12|錯誤： 簽出檔案。|  
|`SCC_E_NOSPECIFIEDVERSION`|-13|錯誤： 沒有指定的版本。|  
|`SCC_E_OPNOTSUPPORTED`|-14|錯誤： 不支援此作業。|  
|`SCC_E_NONSPECIFICERROR`|-15|不明確的錯誤。|  
|`SCC_E_OPNOTPERFORMED`|-16|無法執行錯誤，這項操作。|  
|`SCC_E_TYPENOTSUPPORTED`|-17|錯誤： 原始檔控制系統不支援檔案類型，例如，二進位。|  
|`SCC_E_VERIFYMERGE`|-18|檔案已經自動合併，但未擱置的使用者驗證後，所以已檢查。|  
|`SCC_E_FIXMERGE`|-19|檔案已經自動合併，但未發生合併衝突必須以手動方式解決，因此簽入。|  
|`SCC_E_SHELLFAILURE`|-20|因為 shell 失敗時發生錯誤。|  
|`SCC_E_INVALIDUSER`|-21|錯誤： 使用者不正確。|  
|`SCC_E_PROJECTALREADYOPEN`|-22|錯誤： 已經開啟專案。|  
|`SCC_E_PROJSYNTAXERR`|-23|專案的語法錯誤。|  
|`SCC_E_INVALIDFILEPATH`|-24|錯誤： 檔案路徑無效。|  
|`SCC_E_PROJNOTOPEN`|-25|錯誤： 專案未開啟。|  
|`SCC_E_NOTAUTHORIZED`|-26|錯誤： 使用者沒有執行這項作業。|  
|`SCC_E_FILESYNTAXERR`|-27|檔案的語法錯誤。|  
|`SCC_E_FILENOTEXIST`|-28|錯誤時，本機檔案不存在。|  
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
 所有的原始檔控制外掛程式 API 函式 (除了[SccAdd](../extensibility/sccadd-function.md)， [SccCheckin](../extensibility/scccheckin-function.md)，和[SccDiff](../extensibility/sccdiff-function.md)) 預期會成功，當執行動作時做為引數傳遞的本機檔案存在於工作資料夾中。 例如，在 IDE 可能會發出呼叫[SccCheckout](../extensibility/scccheckout-function.md)或[SccUncheckout](../extensibility/sccuncheckout-function.md)不存在於工作資料夾，但存在於原始檔控制系統中的檔案上。 此呼叫會成功。 只有當沒有檔案或 原始檔控制系統中的工作資料夾函式預期會失敗。  
  
 某些函式，例如`SccAdd`和`SccCheckin`，應該明確傳回`SCC_E_FILENOTEXIST`工作資料夾中的檔案並不存在。 其他函式都必須成功時的工作檔案不存在，如果函式在原始檔控制系統操作上有效的檔案名稱。  
  
 原始檔控制外掛程式應該在工作資料夾中進行任何假設檔案的權限，即使外掛程式有唯讀檔案的某些作業期間。 可以移動、 刪除及隨插即用中的控制之外變更過的工作資料夾中的檔案。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)