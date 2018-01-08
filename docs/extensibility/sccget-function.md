---
title: "SccGet 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGet
helpviewer_keywords: SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 73f5c55b39d855eb084206ef27e2254d50377b86
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="sccget-function"></a>SccGet 函式
此函式會擷取一或多個檔案，以檢視及編譯，但不是用於編輯的複本。 在大多數系統中，檔案會標記為唯讀。  
  
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
  
#### <a name="parameters"></a>參數  
 pvContext  
 [in]內容結構的原始檔控制外掛程式。  
  
 hWnd  
 [in]原始檔控制外掛程式之任何它所提供的對話方塊，可以使用為父代 IDE 視窗的控制代碼。  
  
 nFiles  
 [in]中指定的檔案數目`lpFileNames`陣列。  
  
 lpFileNames  
 [in]要擷取檔案的完整名稱的陣列。  
  
 fOptions  
 [in]命令旗標 (`SCC_GET_ALL`， `SCC_GET_RECURSIVE`)。  
  
 pvOptions  
 [in]原始檔控制外掛程式特定選項。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|取得作業成功。|  
|SCC_E_FILENOTCONTROLLED|檔案不在原始檔控制中。|  
|SCC_E_OPNOTSUPPORTED|原始檔控制系統不支援這項作業。|  
|SCC_E_FILEISCHECKEDOUT|無法取得目前使用者已簽出檔案。|  
|SCC_E_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_NOSPECIFIEDVERSION|指定無效的版本或日期/時間。|  
|SCC_E_NONSPECIFICERROR|不明確的失敗。檔案已不會同步處理。|  
|SCC_I_OPERATIONCANCELED|在完成之前，取消作業。|  
|SCC_E_NOTAUTHORIZED|使用者沒有執行這項作業。|  
  
## <a name="remarks"></a>備註  
 此函式呼叫計數與要擷取的檔案名稱的陣列。 如果在 IDE 通過旗標`SCC_GET_ALL`，這表示中的項目`lpFileNames`不是檔案，而目錄，並在指定的目錄中的原始檔控制下的所有檔案都是要擷取。  
  
 `SCC_GET_ALL`旗標可以結合`SCC_GET_RECURSIVE`旗標來擷取指定的目錄中的所有檔案和所有的子目錄。  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE`永遠不會傳遞而且`SCC_GET_ALL`。 另外請注意，是否目錄 C:\A 和 C:\A\B 同時傳遞遞迴上取得，C:\A\B 和其所有子目錄會實際擷取兩次。 負責在 IDE — 並不是原始檔控制外掛程式，以確定這類的重複項目會保留從陣列。  
  
 最後，即使原始檔控制外掛程式指定`SCC_CAP_GET_NOUI`上初始化時，指出它並沒有 Get 命令的使用者介面，以擷取檔案 IDE 仍可能會呼叫此函式的旗標。 旗標就是指，IDE 不會顯示 Get 功能表項目以及，外掛程式不提供任何 UI。  
  
## <a name="renaming-and-sccget"></a>重新命名和 SccGet  
 狀況： 使用者簽出檔案，比方說，a.txt 並加以修改。 A.txt 可以簽入之前，第二個使用者重新命名為 b.txt 原始檔控制資料庫中的 a.txt、 簽出 b.txt，便會進行一些修改檔案，與簽入檔案。 第一位使用者想要讓第一位使用者將自己的本機版本的 a.txt 檔案重新命名為 b.txt，並取得新的檔案，第二個使用者所做的變更。 不過，本機快取，可追蹤的版本號碼仍然認為 a.txt 的第一個版本都會儲存在本機，因此原始檔控制無法解析的差異。  
  
 有兩種方式可解決這種情況下，本機快取的原始檔控制版本會與原始檔控制資料庫同步處理變成：  
  
1.  不允許重新命名目前已取出原始檔控制資料庫中的檔案。  
  
2.  執行 「 刪除舊 」 後面接著 「 新加入 」 的對等項目。 下列演算法是一種方式完成這項作業。  
  
    1.  呼叫[SccQueryChanges](../extensibility/sccquerychanges-function.md)若要了解重新命名為 b.txt 原始檔控制資料庫中的 a.txt 函式。  
  
    2.  將本機 a.txt 重新命名為 b.txt。  
  
    3.  呼叫`SccGet`a.txt 和 b.txt 函式。  
  
    4.  因為 a.txt 不存在於原始檔控制資料庫中，本機版本快取會清除遺漏 a.txt 版本資訊。  
  
    5.  本機 b.txt 檔案的內容會合併 b.txt 檔案簽出。  
  
    6.  更新的 b.txt 檔案現在可以簽入。  
  
## <a name="see-also"></a>請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)