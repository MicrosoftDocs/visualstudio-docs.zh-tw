---
title: SccUncheckout 函式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6362025f63e4e4f470a7fe107365a59ef99e1e17
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62800298"
---
# <a name="sccuncheckout-function"></a>SccUncheckout 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此函式會復原先前的簽出作業，藉此將選取的檔案或檔案的內容還原到之前簽出的狀態。 對檔案進行簽出之後的所有變更都都會遺失。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
SCCRTN SccUncheckout (  
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
 [in]原始檔控制外掛程式的內容結構。  
  
 hWnd  
 [in]原始檔控制外掛程式時，可以使用當做父代上，它會提供任何對話方塊 IDE 視窗的控制代碼。  
  
 nFiles  
 [in]中指定的檔案數目`lpFileNames`陣列。  
  
 lpFileNames  
 [in]要復原簽出檔案的完整格式的本機路徑名稱的陣列。  
  
 fOptions  
 [in]（未使用） 的命令旗標。  
  
 pvOptions  
 [in]原始檔控制外掛程式特定選項。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|復原簽出成功。|  
|SCC_E_FILENOTCONTROLLED|選取的檔案不在原始檔控制之下。|  
|SCC_E_ACCESSFAILURE|發生問題，存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_NONSPECIFICERROR|不明確的失敗。 復原簽出失敗。|  
|SCC_E_NOTCHECKEDOUT|使用者沒有簽出檔案。|  
|SCC_E_NOTAUTHORIZED|若要執行這項作業不允許的使用者。|  
|SCC_E_PROJNOTOPEN|無法從原始檔控制開啟專案。|  
|SCC_I_OPERATIONCANCELED|作業已完成前取消。|  
  
## <a name="remarks"></a>備註  
 這項作業後`SCC_STATUS_CHECKEDOUT`和`SCC_STATUS_MODIFIED`旗標會同時清除復原簽出已執行所在的檔案。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
