---
title: "IDebugEngine2::CreatePendingBreakpoint | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::CreatePendingBreakpoint"
helpviewer_keywords: 
  - "IDebugEngine2::CreatePendingBreakpoint"
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::CreatePendingBreakpoint
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

建立暫止中斷點，偵錯引擎 \(DE\) 中。  
  
## 語法  
  
```cpp#  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```c#  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### 參數  
 `pBPRequest`  
 \[in\][IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)物件，描述要建立的暫止中斷點。  
  
 `ppPendingBP`  
 \[\] out傳回[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)物件，代表的暫止中斷點。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  通常會傳回`E_FAIL`如果`pBPRequest`參數不符合任何語言支援的 if DE `pBPRequest`參數不正確或不完整。  
  
## 備註  
 暫止中斷點基本上是由許多繫結中斷點，程式碼所需的所有資訊。  這個方法所傳回的暫止中斷點未繫結至程式碼，直到[繫結](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) ，會呼叫方法。  
  
 每一個暫止中斷點的使用者組，工作階段偵錯管理員 \(SDM\) 呼叫這個方法中每個附加的 DE。  它是由驗證中斷點是程式執行於該 DE 有效 DE。  
  
 在使用者上設定中斷點的程式碼行，DE 時可用來繫結至最接近的一行，對應到這段程式碼的文件中的中斷點。  這可讓使用者在多行陳述式的第一行設定中斷點，但將其繫結 \(所有的程式碼屬性在偵錯資訊\) 的最後一行。  
  
## 範例  
 下列範例會示範如何實作這個方法，如`CProgram`物件。  實作 DE `IDebugEngine2::CreatePendingBreakpoint`將無法再所有電話都轉接至這個方法的實作每個程式中。  
  
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
  
## 請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [繫結](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)