---
title: SccGet 函式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f8317405c52850eceb816b958718835c029c6c4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068297"
---
# <a name="sccget-function"></a>SccGet 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此函式會擷取一或多個檔案，來檢視和編譯，但不是用於編輯的複本。 在大部分的系統中，檔案會標記為唯讀。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
SCCRTN SccGet(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>參數  
 pvContext  
 [in]Context 結構的原始檔控制外掛程式。  
  
 hWnd  
 [in]原始檔控制外掛程式時，可以使用當做父代上，它會提供任何對話方塊 IDE 視窗的控制代碼。  
  
 nFiles  
 [in]中指定的檔案數目`lpFileNames`陣列。  
  
 lpFileNames  
 [in]要擷取檔案的完整名稱的陣列。  
  
 fOptions  
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
>  `SCC_GET_RECURSIVE` 永遠不會傳遞而且`SCC_GET_ALL`。 另請注意，是否目錄 C:\A 和 C:\A\B 同時傳遞遞迴取得，C:\A\B 及其所有子目錄會實際擷取兩次。 是 IDE 的責任，並不是原始檔控制外掛程式，藉此確定這類的重複項目會保留從陣列。  
  
 最後，即使原始檔控制外掛程式指定`SCC_CAP_GET_NOUI`上初始化時，表示它並沒有 Get 命令的使用者介面，以擷取檔案 IDE 仍可能會呼叫此函式的旗標。 旗標只是表示，IDE 不會顯示取得功能表項目，而且，外掛程式不需要提供任何 UI。  
  
## <a name="renaming-and-sccget"></a>重新命名和 SccGet  
 狀況： 使用者簽出檔案，比方說，a.txt，並修改它。 A.txt 可以簽入之前，第二個使用者重新命名為 b.txt 原始檔控制資料庫中的 a.txt、 簽出 b.txt，便會進行一些修改檔案，和簽入的檔案。 第一位使用者想要讓第一位使用者將其本機版本的 a.txt 檔案重新命名為 b.txt 並取得新的檔案，第二個使用者所做的變更。 不過，會持續追蹤的版本號碼的本機快取仍然認為 a.txt 的第一個版本都會儲存在本機，因此原始檔控制無法解析的差異。  
  
 有兩種方式可解決本機快取的原始檔控制版本會與原始檔控制資料庫不同步變成這種情況：  
  
1. 不允許重新命名目前已簽出原始檔控制資料庫中的檔案。  
  
2. 執行 「 刪除舊 」 後面接著 「 新增 」 的對等項目。 下列演算法是一種方式完成這項作業。  
  
    1. 呼叫[SccQueryChanges](../extensibility/sccquerychanges-function.md)若要了解重新命名為 b.txt 原始檔控制資料庫中的 a.txt 函式。  
  
    2. 將本機 a.txt 重新命名為 b.txt。  
  
    3. 呼叫`SccGet`a.txt 和 b.txt 函式。  
  
    4. 因為 a.txt 不存在於原始檔控制資料庫中，會將本機版本快取清除遺漏的 a.txt 版本資訊。  
  
    5. 正在簽出 b.txt 檔案會合併本機 b.txt 檔案的內容。  
  
    6. 更新的 b.txt 檔案現在可以簽入。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)
