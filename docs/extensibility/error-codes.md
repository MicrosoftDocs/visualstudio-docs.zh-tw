---
title: 錯誤代碼 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34072f6ddbd632f83dd308c6cb63427e02bb110b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711847"
---
# <a name="error-codes"></a>錯誤碼
當原始程式碼管理外掛程式 API 函數傳回錯誤時,它應該是以下錯誤代碼之一。 所有錯誤均為負數,警告或資訊錯誤代碼為正,成功為 0。

|錯誤碼|值|描述|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|外掛程式支援分兩個步驟從原始程式碼管理中添加檔。 有關詳細資訊,請參閱[SccSetOption](../extensibility/sccsetoption-function.md)。|
|`SCC_I_FILEDIFFERS`|6|本地檔與原始程式碼管理資料庫中的檔不同(例如[,SccDiff](../extensibility/sccdiff-function.md)可能會返回此值)。|
|`SCC_I_RELOADFILE`|5|在原始程式碼管理操作期間更改了本地檔;如果可能,IDE 應重新載入該檔。|
|`SCC_I_FILENOTAFFECTED`|4|該文件不受影響。|
|`SCC_I_PROJECTCREATED`|3|專案是在原始程式碼管理操作期間創建的(例如,在指定標誌時調用[SccOpenProject](../extensibility/sccopenproject-function.md)時`SCC_OP_CREATEIFNEW`)。|
|`SCC_I_OPERATIONCANCELED`|2|作業已取消。|
|`SCC_I_ADV_SUPPORT`|1|外掛程式支援指定命令的進階選項。 有關詳細資訊,請參閱[SccGet 命令選項](../extensibility/sccgetcommandoptions-function.md)。|
|`SCC_OK`|0|成功。|
|`SCC_E_INITIALIZEFAILED`|-1|錯誤:初始化失敗。|
|`SCC_E_UNKNOWNPROJECT`|-2|錯誤:專案未知。|
|`SCC_E_COULDNOTCREATEPROJECT`|-3|錯誤:無法建立專案。|
|`SCC_E_NOTCHECKEDOUT`|-4|錯誤:未簽出該檔。|
|`SCC_E_ALREADYCHECKEDOUT`|-5|錯誤:檔已簽出。|
|`SCC_E_FILEISLOCKED`|-6|錯誤:檔已鎖定。|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|錯誤:檔已完全簽出。|
|`SCC_E_ACCESSFAILURE`|-8|訪問原始程式碼管理系統時出現問題,可能是由於網路或爭用問題。 建議重試。|
|`SCC_E_CHECKINCONFLICT`|-9|錯誤:簽入期間存在衝突。|
|`SCC_E_FILEALREADYEXISTS`|-10|錯誤:該檔已存在。|
|`SCC_E_FILENOTCONTROLLED`|-11|錯誤:檔不受原始程式碼管理。|
|`SCC_E_FILEISCHECKEDOUT`|-12|錯誤:檔已簽出。|
|`SCC_E_NOSPECIFIEDVERSION`|-13|錯誤:沒有指定的版本。|
|`SCC_E_OPNOTSUPPORTED`|-14|錯誤:不支援該操作。|
|`SCC_E_NONSPECIFICERROR`|-15|非特定錯誤。|
|`SCC_E_OPNOTPERFORMED`|-16|錯誤,未執行操作。|
|`SCC_E_TYPENOTSUPPORTED`|-17|錯誤:原始程式碼控制系統不支援檔的類型,例如二進位檔案。|
|`SCC_E_VERIFYMERGE`|-18|檔已自動合併,但未選中,因為它正在等待用戶驗證。|
|`SCC_E_FIXMERGE`|-19|檔已自動合併,但由於合併衝突必須手動解決,因此尚未簽入。|
|`SCC_E_SHELLFAILURE`|-20|外殼故障導致錯誤。|
|`SCC_E_INVALIDUSER`|-21|錯誤:使用者無效。|
|`SCC_E_PROJECTALREADYOPEN`|-22|錯誤:專案已打開。|
|`SCC_E_PROJSYNTAXERR`|-23|專案語法錯誤。|
|`SCC_E_INVALIDFILEPATH`|-24|錯誤:檔案路徑無效。|
|`SCC_E_PROJNOTOPEN`|-25|錯誤:專案未打開。|
|`SCC_E_NOTAUTHORIZED`|-26|錯誤:使用者無權執行此操作。|
|`SCC_E_FILESYNTAXERR`|-27|檔語法錯誤。|
|`SCC_E_FILENOTEXIST`|-28|錯誤,本地檔不存在。|
|`SCC_E_CONNECTIONFAILURE`|-29|錯誤:連接失敗。|
|`SCC_E_UNKNOWNERROR`|-30|未知的錯誤。|
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|後台獲取操作當前正在進行中。|

## <a name="macros-provided-for-quick-checking"></a>快速檢查的巨集

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>備註
 當作為參數傳遞的本地檔不存在時,所有原始程式碼管理外掛程式 API 函數[(SccAdd、Scc Checkin](../extensibility/sccadd-function.md)和[SccDiff](../extensibility/sccdiff-function.md)除外)都有望成功。 [SccCheckin](../extensibility/scccheckin-function.md) 例如,IDE可能會對工作資料夾中不存在但存在於原始程式碼管理系統中的檔發出對[SccCheckout 或](../extensibility/scccheckout-function.md) [SccUn 簽出的](../extensibility/sccuncheckout-function.md)調用。 此調用將成功。 只有在工作資料夾或原始程式碼管理系統中沒有檔時,該功能才應失敗。

 當工作資料夾中的檔不存在`SccAdd``SccCheckin`時 ,某些函`SCC_E_FILENOTEXIST`數( 如 和 )應特別返回。 如果函數對原始程式碼管理系統中的有效檔名進行操作,則當工作檔不存在時,其他函數應成功。

 原始程式碼管理外掛程式不應對工作資料夾中的文件的許可權做出任何假設,即使該外掛程式在某些操作期間將文件標記為唯讀。 工作資料夾中的檔案可以在外掛程式控制程式之外移動、刪除和更改。

## <a name="see-also"></a>另請參閱
- [原始程式管理外掛程式](../extensibility/source-control-plug-ins.md)
