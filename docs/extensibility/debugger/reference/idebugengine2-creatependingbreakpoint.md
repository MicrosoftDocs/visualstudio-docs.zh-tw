---
title: IDebugEngine2::CreatePendingBreakpoint |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 64b01e75255f62059be4af94d9369f76d5b9f79b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53892023"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
在偵錯引擎 (DE) 中建立暫止中斷點。  
  
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
 [in][IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)描述若要建立的暫止中斷點的物件。  
  
 `ppPendingBP`  
 [out]傳回[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)表示暫止中斷點的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。 通常會傳回`E_FAIL`如果`pBPRequest`參數不符合任何支援的語言的 if DE`pBPRequest`參數是無效或不完整。  
  
## <a name="remarks"></a>備註  
 暫止中斷點是基本上是將中斷點繫結至程式碼所需的所有資訊的集合。 從這個方法傳回暫止中斷點未繫結至程式碼，直到[繫結](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)呼叫方法。  
  
 暫止中斷點的每個使用者會設定，工作階段的偵錯管理員 (SDM) 呼叫這個方法在每個附加的裝置。 若要確認中斷點是適用於該 DE 中執行的程式 DE 負責。  
  
 當使用者在程式碼行上設定中斷點時，DE 沒有繫結至最接近的一行，相當於這個程式碼的文件中的中斷點。 這可讓使用者在多行陳述式的第一行上設定中斷點，但將它繫結 （其中偵錯資訊中屬性的所有程式碼） 的最後一行。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法來簡單`CProgram`物件。 DE 實作`IDebugEngine2::CreatePendingBreakpoint`所有呼叫此方法的實作在每一個程式則就會將都轉送。  
  
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