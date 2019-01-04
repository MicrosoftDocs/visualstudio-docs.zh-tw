---
title: IDebugCoreServer3::DiagnoseWebDebuggingError |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1ba22bb5f8f20446b87236a4784b02e7ad2eb41e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990749"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
若要判斷為什麼 auto-attach 的嘗試失敗。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DiagnoseWebDebuggingError(  
   LPCWSTR pszUrl  
);  
```  
  
```csharp  
int DiagnoseWebDebuggingError(  
   string pszUrl  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszUrl`  
 [in]目前未使用;一律應該設為 null 的值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。 以下是其他常見的傳回碼：  
  
|程式碼|描述|  
|----------|-----------------|  
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|無法判斷為何無法啟動偵錯的遠端伺服器。|  
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|無法偵錯在遠端伺服器上，可能是因為權限不足，或因為未啟用 DEBUG 動詞命令。|  
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Web 伺服器已經鎖定，並會封鎖 DEBUG 動詞命令，才能啟用偵錯。|  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)