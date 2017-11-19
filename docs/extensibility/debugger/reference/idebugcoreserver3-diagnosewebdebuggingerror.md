---
title: "IDebugCoreServer3::DiagnoseWebDebuggingError |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords: IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f25a3c9069836d748b8390df97e1fc39ae7aea06
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
嘗試判斷為何 auto-attach 失敗。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DiagnoseWebDebuggingError(  
   LPCWSTR pszUrl  
);  
```  
  
```csharp  
int DiagnoseWebDebuggingError(  
   string pszUrl  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszUrl`  
 [in]目前未使用。應一律設為 null 值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 其他常見的傳回碼如下：  
  
|程式碼|說明|  
|----------|-----------------|  
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|無法判斷遠端伺服器啟動偵錯失敗的原因。|  
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|無法偵錯在遠端伺服器上，可能是因為權限不足，或因為未啟用偵錯動詞命令。|  
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|網頁伺服器已經鎖定，並且封鎖 DEBUG 動詞命令，才能啟用偵錯。|  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)