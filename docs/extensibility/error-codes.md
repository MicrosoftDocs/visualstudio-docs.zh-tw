---
title: 錯誤碼 |Microsoft Docs
description: 本文包含原始檔控制外掛程式 API 函式的錯誤碼、值和描述清單。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eedc9311bcafdd4241e065b40079abed3977dcef
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898301"
---
# <a name="error-codes"></a>錯誤碼
當原始檔控制外掛程式 API 函式傳回錯誤時，預期會是下列其中一個錯誤碼。 所有錯誤都是否定的、警告或參考用的錯誤碼是正面的，成功則為0。

|錯誤碼|值|描述|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|外掛程式支援在兩個步驟中從原始檔控制新增檔案。 如需詳細資訊，請參閱 [SccSetOption](../extensibility/sccsetoption-function.md)。|
|`SCC_I_FILEDIFFERS`|6|本機檔案與原始檔控制資料庫中的檔案不同 (例如， [SccDiff](../extensibility/sccdiff-function.md) 可能會傳回此值) 。|
|`SCC_I_RELOADFILE`|5|本機檔案在原始檔控制作業期間已變更;IDE 應該盡可能重載該檔案。|
|`SCC_I_FILENOTAFFECTED`|4|檔案不會受到影響。|
|`SCC_I_PROJECTCREATED`|3|專案是在原始檔控制作業期間建立 (例如，呼叫 [SccOpenProject](../extensibility/sccopenproject-function.md) 時， `SCC_OP_CREATEIFNEW`) 指定旗標時。|
|`SCC_I_OPERATIONCANCELED`|2|作業已取消。|
|`SCC_I_ADV_SUPPORT`|1|外掛程式支援指定命令的 advanced 選項。 如需詳細資訊，請參閱 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)。|
|`SCC_OK`|0|成功。|
|`SCC_E_INITIALIZEFAILED`|-1|錯誤：初始化失敗。|
|`SCC_E_UNKNOWNPROJECT`|-2|錯誤：專案未知。|
|`SCC_E_COULDNOTCREATEPROJECT`|-3|錯誤：無法建立專案。|
|`SCC_E_NOTCHECKEDOUT`|-4|錯誤：檔案未簽出。|
|`SCC_E_ALREADYCHECKEDOUT`|-5|錯誤：檔案已簽出。|
|`SCC_E_FILEISLOCKED`|-6|錯誤：檔案已鎖定。|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|錯誤：以獨佔方式簽出檔案。|
|`SCC_E_ACCESSFAILURE`|-8|存取原始檔控制系統時發生問題，可能是因為網路或爭用問題。 建議您重試。|
|`SCC_E_CHECKINCONFLICT`|-9|錯誤：簽入時發生衝突。|
|`SCC_E_FILEALREADYEXISTS`|-10|錯誤：檔案已經存在。|
|`SCC_E_FILENOTCONTROLLED`|-11|錯誤：檔案不在原始檔控制之下。|
|`SCC_E_FILEISCHECKEDOUT`|12-01.2.2|錯誤：檔案已簽出。|
|`SCC_E_NOSPECIFIEDVERSION`|-13|錯誤：沒有指定的版本。|
|`SCC_E_OPNOTSUPPORTED`|-14|錯誤：不支援此作業。|
|`SCC_E_NONSPECIFICERROR`|-15|模糊的錯誤。|
|`SCC_E_OPNOTPERFORMED`|-16|錯誤，未執行操作。|
|`SCC_E_TYPENOTSUPPORTED`|-17|錯誤：原始碼控制系統不支援檔案的類型（例如，二進位）。|
|`SCC_E_VERIFYMERGE`|-18|檔案已自動合併，但尚未檢查，因為它正在等待使用者驗證。|
|`SCC_E_FIXMERGE`|-19|檔案已自動合併，但因為合併衝突必須手動解決，所以尚未簽入。|
|`SCC_E_SHELLFAILURE`|-20|因為 shell 失敗而發生錯誤。|
|`SCC_E_INVALIDUSER`|-21|錯誤：使用者無效。|
|`SCC_E_PROJECTALREADYOPEN`|-22|錯誤：專案已開啟。|
|`SCC_E_PROJSYNTAXERR`|-23|專案語法錯誤。|
|`SCC_E_INVALIDFILEPATH`|-24|錯誤：檔案路徑無效。|
|`SCC_E_PROJNOTOPEN`|-25|錯誤：專案未開啟。|
|`SCC_E_NOTAUTHORIZED`|-26|錯誤：使用者未獲授權執行這項操作。|
|`SCC_E_FILESYNTAXERR`|-27|檔語法錯誤。|
|`SCC_E_FILENOTEXIST`|-28-preview|錯誤，本機檔案不存在。|
|`SCC_E_CONNECTIONFAILURE`|-29|錯誤：發生連接失敗。|
|`SCC_E_UNKNOWNERROR`|-30|未知的錯誤。|
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31-preview|背景取得作業正在進行中。|

## <a name="macros-provided-for-quick-checking"></a>為快速檢查提供的宏

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>備註
 所有的原始檔控制外掛程式 API 函式 (除了 [SccAdd](../extensibility/sccadd-function.md)、 [SccCheckin](../extensibility/scccheckin-function.md)和 [SccDiff](../extensibility/sccdiff-function.md)) 都應該會在工作資料夾中沒有以引數傳遞的本機檔案不存在時，才會成功。 例如，IDE 可能會發出呼叫 [SccCheckout](../extensibility/scccheckout-function.md) 或 [SccUncheckout](../extensibility/sccuncheckout-function.md) 的檔案，該檔案不存在於工作資料夾中，但是存在於原始檔控制系統中。 此呼叫會成功。 只有當工作資料夾或原始檔控制系統中沒有檔案時，預期的函式才會失敗。

 `SccAdd` `SccCheckin` `SCC_E_FILENOTEXIST` 當工作資料夾中的檔案不存在時，特定的函式（例如和）應該特別傳回。 當工作檔案不存在時，如果函式在原始檔控制系統中是以有效的檔案名運作，則其他函式預期會成功。

 原始檔控制外掛程式不應針對工作資料夾中的檔案許可權進行任何假設，即使外掛程式在某些作業期間已將檔案標示為唯讀。 您可以在外掛程式的控制項之外，移動、刪除和變更工作資料夾中的檔案。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式](../extensibility/source-control-plug-ins.md)
