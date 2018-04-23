---
title: IDebugProgram2::Attach |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aff1e5f6c887b42b6f49e0c8cfa426cade814006
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
將附加至程式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pCallback`  
 [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)来用於偵錯事件通知的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 下表顯示一些可能發生的錯誤代碼。  
  
|值|描述|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|指定的程式已附加偵錯工具。|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Attach 程序期間，發生安全性違規。|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|桌面的程式無法附加至偵錯工具。|  
  
## <a name="remarks"></a>備註  
 偵錯引擎 (DE) 永遠不會呼叫此方法來附加至程式。 如果在程式的位址空間中，執行 DE [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法呼叫。 如果 DE 執行中工作階段偵錯管理員 (SDM) 位址空間，[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)