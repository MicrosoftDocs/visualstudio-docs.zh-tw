---
title: IDebugCoreServer3::DiagnoseWebDebuggingError |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 24f142a631df25cfbff8ed795736c0cbf4e59eaf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205284"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

若要判斷為什麼 auto-attach 的嘗試失敗。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
  
|程式碼|說明|  
|----------|-----------------|  
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|無法判斷為何無法啟動偵錯的遠端伺服器。|  
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|無法偵錯在遠端伺服器上，可能是因為權限不足，或因為未啟用 DEBUG 動詞命令。|  
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Web 伺服器已經鎖定，並會封鎖 DEBUG 動詞命令，才能啟用偵錯。|  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
