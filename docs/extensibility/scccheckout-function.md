---
title: SccCheckout 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 671e4ecebb44f0910eba3bb835a6da6f9a7f3903
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137745"
---
# <a name="scccheckout-function"></a>SccCheckout 函式
提供一份完整的檔案名稱，此函式取出它們的本機磁碟機。 註解適用於所有簽出的檔案。註解引數可以是`null`字串。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccCheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>參數  
 pvContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 hWnd  
 [in]原始檔控制外掛程式之任何它所提供的對話方塊，可以使用為父代 IDE 視窗的控制代碼。  
  
 nFiles  
 [in]選取要簽出的檔案數目。  
  
 lpFileNames  
 [in]簽出檔案的完整格式的本機路徑名稱的陣列。  
  
 lpComment  
 [in]要套用至每個選取的檔案簽出的註解。  
  
 fOptions  
 [in]命令旗標 (請參閱[特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md))。  
  
 pvOptions  
 [in]原始檔控制外掛程式特定選項。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|簽出成功。|  
|SCC_E_FILENOTCONTROLLED|選取的檔案不是原始程式碼控制之下。|  
|SCC_E_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項作業。|  
|SCC_E_NONSPECIFICERROR|不明確的失敗。 檔案未簽出。|  
|SCC_E_ALREADYCHECKEDOUT|使用者已經簽出該檔案。|  
|SCC_E_FILEISLOCKED|檔案已鎖定，會禁止建立的新版本。|  
|SCC_E_FILEOUTEXCLUSIVE|另一位使用者完成獨佔簽出這個檔案。|  
|SCC_I_OPERATIONCANCELED|作業已完成前取消。|  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)