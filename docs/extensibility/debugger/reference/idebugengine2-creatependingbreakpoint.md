---
title: IDebugEngine2::CreatePendingBreakpoint |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a0813e077d8bdc2ba024dc932a6cb571b1b2fed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
偵錯引擎 (DE) 中建立暫止中斷點。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```csharp  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pBPRequest`  
 [in][IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)描述建立的暫止中斷點的物件。  
  
 `ppPendingBP`  
 [out]傳回[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)表示暫止中斷點物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 通常會傳回`E_FAIL`如果`pBPRequest`參數不符合任何支援的語言的 if DE`pBPRequest`參數是無效或不完整。  
  
## <a name="remarks"></a>備註  
 暫止中斷點是資訊的本質上的所有中斷點繫結至程式碼所需集合。 從這個方法傳回的暫止中斷點未繫結至程式碼直到[繫結](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)方法呼叫。  
  
 針對每個暫止中斷點的使用者集合，工作階段的偵錯管理員 (SDM) 呼叫這個方法在每個附加 DE。 這是由 DE 驗證中斷點適用於該 DE 中執行的程式。  
  
 當使用者程式碼行上設定中斷點時，DE 是可用來將中斷點繫結至最接近的一行相當於這個程式碼的文件中。 這可讓使用者在多行陳述式的第一行設定中斷點，但將它繫結 （所有的程式碼屬性中的偵錯資訊） 的最後一行。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法來簡單`CProgram`物件。 DE 實作`IDebugEngine2::CreatePendingBreakpoint`無法將此方法的實作每個程式中的所有呼叫。  
  
```  
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)     
{    
  
   // Create and initialize the CPendingBreakpoint object.  
   CComObject<CPendingBreakpoint> *pPending;    
   CComObject<CPendingBreakpoint>::CreateInstance(&pPending);    
   pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);    
   return pPending->QueryInterface(ppPendingBP);    
}    
```  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [繫結](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)