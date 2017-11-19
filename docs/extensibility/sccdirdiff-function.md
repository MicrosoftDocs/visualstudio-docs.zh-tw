---
title: "SccDirDiff 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccDirDiff
helpviewer_keywords: SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea335ef6bcb2a27b4312c613062be0d365711cbc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="sccdirdiff-function"></a>SccDirDiff 函式
此函式會顯示目前的本機目錄上的用戶端磁碟 」 和 「 原始檔控制下對應的專案之間的差異。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>參數  
 pContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 hWnd  
 [in]原始檔控制外掛程式之任何它所提供的對話方塊，可以使用為父代 IDE 視窗的控制代碼。  
  
 lpDirName  
 [in]要為其顯示視覺化差異的本機目錄的完整的路徑。  
  
 將 dwFlags  
 [in]命令旗標 (請參閱 < 備註 > 一節)。  
  
 pvOptions  
 [in]原始檔控制外掛程式特定選項。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|說明|  
|-----------|-----------------|  
|SCC_OK|磁碟上的目錄是在原始程式碼控制中的專案相同。|  
|SCC_I_FILESDIFFER|在磁碟上的目錄會與原始程式碼控制中的專案不同。|  
|SCC_I_RELOADFILE|需要重新載入檔案或專案。|  
|SCC_E_FILENOTCONTROLLED|目錄不是原始程式碼控制之下。|  
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項作業。|  
|SCC_E_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|不明確的失敗。|  
|SCC_E_FILENOTEXIST|找不到本機目錄。|  
  
## <a name="remarks"></a>備註  
 此函式用來指示原始檔控制外掛程式，以便向使用者顯示的變更至指定的目錄清單。 外掛程式會自己的視窗中，開啟其的選擇，以顯示在磁碟上的使用者的目錄和版本控制下對應的專案之間差異的格式。  
  
 如果外掛程式支援比較所有的目錄時，就必須支援目錄的比較，以檔案名稱為基礎即使不支援的 「 快速 diff 」 選項即可。  
  
|`dwFlags`|解譯|  
|---------------|--------------------|  
|SCC_DIFF_IGNORECASE|不區分大小寫的比較 （可能會用來快速差異或視覺效果）。|  
|SCC_DIFF_IGNORESPACE|會忽略空白字元 （可能會用來快速差異或視覺效果）。|  
|SCC_DIFF_QD_CONTENTS|如果支援原始檔控制外掛程式，以無訊息方式比較位元組的目錄。|  
|SCC_DIFF_QD_CHECKSUM|如果外掛程式支援，以無訊息模式會比較總和檢查碼，透過目錄，或如果不支援，會回復為 SCC_DIFF_QD_CONTENTS。|  
|SCC_DIFF_QD_TIME|如果外掛程式支援，以無訊息模式會比較其時間戳記，透過目錄，或如果不支援，會回復 SCC_DIFF_QD_CHECKSUM 或 SCC_DIFF_QD_CONTENTS 上。|  
  
> [!NOTE]
>  此函式會使用相同的命令旗標，表示[SccDiff](../extensibility/sccdiff-function.md)。 不過，可以選擇原始檔控制外掛程式不支援目錄的 「 快速差異 」 作業。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)