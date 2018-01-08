---
title: "SccDiff 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccDiff
helpviewer_keywords: SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 832d80c3ca49cc03c4a66b6a4cf931dd40686c82
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="sccdiff-function"></a>SccDiff 函式
此函式會顯示 （或選擇性地只會檢查） 目前的檔案 （位於本機磁碟上） 和最後一個簽入的版本之間的差異，在來源控制系統。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccDiff(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LPCSTR    lpFileName,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>參數  
 pvContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 hWnd  
 [in]原始檔控制外掛程式之任何它所提供的對話方塊，可以使用為父代 IDE 視窗的控制代碼。  
  
 lpFileName  
 [in]要求不同的檔案名稱。  
  
 fOptions  
 [in]命令旗標。 如需詳細資訊，請參閱 < 備註 >。  
  
 pvOptions  
 [in]原始檔控制外掛程式特定選項。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|工作複製與伺服器版本都相同。|  
|SCC_I_FILESDIFFERS|使用的複本不同於原始檔控制下的版本。|  
|SCC_I_RELOADFILE|需要重新載入檔案或專案。|  
|SCC_E_FILENOTCONTROLLED|檔案不在原始檔控制中。|  
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項作業。|  
|SCC_E_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_NONSPECIFICERROR|不明確的失敗。無法取得檔案的差異。|  
|SCC_E_FILENOTEXIST|找不到本機檔案。|  
  
## <a name="remarks"></a>備註  
 此函式有兩種不同的用途。 根據預設，它會顯示清單中變更的檔案。 原始檔控制外掛程式開啟它自己的視窗中選擇，以顯示在磁碟上的使用者的檔案與原始檔控制下的檔案的最新版本之間的差異的格式。  
  
 或者，在 IDE 可能只需要判斷檔案是否已變更。 例如，IDE，可能需要判斷它是否安全簽出檔案，而不通知使用者。 在此情況下，IDE 會傳入`SCC_DIFF_CONTENTS`旗標。 原始檔控制外掛程式必須檢查檔案在磁碟上，位元組的對原始檔控制的檔案，並傳回值，指出兩個檔案是否不同，而不會向使用者顯示任何項目。  
  
 做為效能最佳化，原始檔控制外掛程式可能會使用總和檢查碼或時間戳記，而不是由呼叫的位元組的比較為基礎的替代方案`SCC_DIFF_CONTENTS`： 比較的下列形式會很明顯地更快但較不可靠。 並非所有的原始檔控制系統可能會支援這些替代的比較方法，而且外掛程式可能需要切換回內容比較。 所有的原始檔控制外掛程式，至少必須支援內容比較。  
  
> [!NOTE]
>  快速差異旗標互斥。 能夠傳遞任何旗標，但不能同時將多個傳遞。 `SCC_DIFF_QUICK_DIFF`這遮罩，它結合了所有旗標，可用於測試，但它應該永遠不會當做參數傳遞。  
  
|`fOption`|意義|  
|---------------|-------------|  
|SCC_DIFF_IGNORECASE|（可用於快速或視覺效果的差異） 的比較不區分大小寫。|  
|SCC_DIFF_IGNORESPACE|會忽略空白字元 （可用於快速或視覺效果的差異）。|  
|SCC_DIFF_QD_CONTENTS|以無訊息方式比較位元組的檔案。|  
|SCC_DIFF_QD_CHECKSUM|以無訊息方式比較透過總和檢查碼時支援檔案。 如果不支援，會回復為內容的比較。|  
|SCC_DIFF_QD_TIME|以無訊息方式比較透過支援時，其時間戳記的檔案。 如果不支援，會回復為內容的比較。|  
  
## <a name="see-also"></a>請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)