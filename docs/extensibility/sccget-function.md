---
title: SccGet 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 089b0f56292dfdeb56eb770a5cec5abf6c0d6b82
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869410"
---
# <a name="sccget-function"></a>SccGet 函式
此函式會擷取一或多個檔案，來檢視和編譯，但不是用於編輯的複本。 在大部分的系統中，檔案會標記為唯讀。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccGet(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
### <a name="parameters"></a>參數  
 pvContext  
 [in]Context 結構的原始檔控制外掛程式。  
  
 hWnd  
 [in]原始檔控制外掛程式時，可以使用當做父代上，它會提供任何對話方塊 IDE 視窗的控制代碼。  
  
 nFiles  
 [in]中指定的檔案數目`lpFileNames`陣列。  
  
 lpFileNames  
 [in]要擷取檔案的完整名稱的陣列。  
  
 Stored  
 [in]命令旗標 (`SCC_GET_ALL`， `SCC_GET_RECURSIVE`)。  
  
 pvOptions  
 [in]原始檔控制外掛程式特定選項。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|取得作業的成功。|  
|SCC_E_FILENOTCONTROLLED|檔案不是原始檔控制之下。|  
|SCC_E_OPNOTSUPPORTED|原始檔控制系統不支援這項作業。|  
|SCC_E_FILEISCHECKEDOUT|無法取得使用者目前已簽出檔案。|  
|SCC_E_ACCESSFAILURE|發生問題，存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_NOSPECIFIEDVERSION|指定無效的版本或日期/時間。|  
|SCC_E_NONSPECIFICERROR|不明確的失敗;檔案已不會同步處理。|  
|SCC_I_OPERATIONCANCELED|在完成之前取消作業。|  
|SCC_E_NOTAUTHORIZED|使用者未獲授權執行此作業。|  
  
## <a name="remarks"></a>備註  
 此函式呼叫計數與要擷取的檔案名稱的陣列。 如果 IDE 通過旗標`SCC_GET_ALL`，這表示中的項目`lpFileNames`並不是檔案的目錄，並包含要擷取之指定的目錄中的原始檔控制下的所有檔案。  
  
 `SCC_GET_ALL`旗標可以結合`SCC_GET_RECURSIVE`旗標，以擷取指定的目錄中的所有檔案和所有的子目錄。  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE` 永遠不會傳遞而且`SCC_GET_ALL`。 此外，請注意，如果目錄*C:\A*並*C:\A\B*兩者都傳遞遞迴 get 上, *C:\A\B*和所有子目錄會實際都擷取兩次。 是 IDE 的責任，並不是原始檔控制外掛程式，藉此確定這類的重複項目會保留從陣列。  
  
 最後，即使原始檔控制外掛程式指定`SCC_CAP_GET_NOUI`上初始化時，表示它並沒有 Get 命令的使用者介面，以擷取檔案 IDE 仍可能會呼叫此函式的旗標。 旗標只是表示，IDE 不會顯示取得功能表項目，而且，外掛程式不需要提供任何 UI。  
  
## <a name="rename-files-and-sccget"></a>重新命名檔案和 SccGet  
 狀況： 使用者簽出檔案，例如*a.txt*，並修改它。 再*a.txt*才能簽入，第二個使用者重新命名*a.txt*來*b.txt*在原始檔控制資料庫中，簽出*b.txt*，可讓某些修改檔案，並檢查該檔案。 第一位使用者想要讓第一位使用者會重新命名其本機版本，第二個使用者所做的變更*a.txt*的檔案*b.txt*並取得新的檔案。 不過，會持續追蹤的版本號碼的本機快取仍然認為第一版*a.txt*都會儲存在本機，因此原始檔控制無法解析的差異。  
  
 有兩種方式可解決本機快取的原始檔控制版本會與原始檔控制資料庫不同步變成這種情況：  
  
1.  不允許重新命名目前已簽出原始檔控制資料庫中的檔案。  
  
2.  執行 「 刪除舊 」 後面接著 「 新增 」 的對等項目。 下列演算法是一種方式完成這項作業。  
  
    1.  呼叫[SccQueryChanges](../extensibility/sccquerychanges-function.md)函式，以了解重新命名*a.txt*來*b.txt*原始檔控制資料庫中。  
  
    2.  重新命名本機*a.txt*要*b.txt*。  
  
    3.  呼叫`SccGet`函式兩者*a.txt*並*b.txt*。  
  
    4.  因為*a.txt*不存在的本機版本快取清除遺漏的原始檔控制資料庫中，在*a.txt*版本資訊。  
  
    5.  *B.txt*簽出的檔案會本機內容與合併*b.txt*檔案。  
  
    6.  已更新*b.txt*檔案現在簽入。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)
