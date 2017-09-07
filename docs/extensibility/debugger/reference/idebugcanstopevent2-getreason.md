---
title: "IDebugCanStopEvent2::GetReason |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: b5d4c50b407406ea9a5d878decf859b8ab70863d
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
取得為什麼偵錯引擎 (DE) 想要停止的原因。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```csharp  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pcr`  
 [out]傳回值，從[CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)列舉，描述這個事件的原因。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 通常會呼叫這個方法之前[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)方法，讓呼叫端可以決定是否要傳遞非零 (`TRUE`) 至`IDebugCanStopEvent2::CanStop`方法。  
  
 可以停止的原因是`CANSTOP_ENTRYPOINT`，這表示 DE 已達到的進入點，或`CANSTOP_STEPIN`，這表示 DE 已逐步執行函式。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
