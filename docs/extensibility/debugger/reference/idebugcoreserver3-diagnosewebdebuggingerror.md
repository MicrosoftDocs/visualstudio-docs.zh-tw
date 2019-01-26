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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96a57d2dc3274a1373f5cfa3641c4702b0a1429c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929597"
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