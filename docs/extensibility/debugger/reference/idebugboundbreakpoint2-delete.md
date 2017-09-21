---
title: "IDebugBoundBreakpoint2::Delete | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::Delete"
helpviewer_keywords: 
  - "Delete 方法"
  - "IDebugBoundBreakpoint2::Delete 方法"
ms.assetid: 7088dc66-f24a-446f-a52a-397d02457a41
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugBoundBreakpoint2::Delete
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

刪除中斷點。  
  
## 語法  
  
```cpp#  
HRESULT Delete(   
   void   
);  
```  
  
```c#  
int Delete();  
```  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  傳回`E_BP_DELETED`如果繫結的中斷點物件的狀態會設定為`BPS_DELETED` \(屬於[BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)列舉型別\)。  
  
## 範例  
 下列範例會示範如何實作這個方法，如`CBoundBreakpoint`物件，公開 \(expose\) [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)介面。  
  
```  
HRESULT CBoundBreakpoint::Delete(void)    
{    
   HRESULT hr;    
  
   // Verify that the bound breakpoint has not been   
   // deleted. If deleted, then return hr = E_BP_DELETED.    
   if (m_state != BPS_DELETED)    
   {    
      m_pInterp->RemoveBreakpoint(m_sbstrDoc, this);    
  
      // Change the state of the breakpoint to BPS_DELETED.    
      m_state = BPS_DELETED;    
      hr = S_OK;    
   }    
   else    
   {    
      hr = E_BP_DELETED;    
   }    
  
   return hr;    
}     
```  
  
## 請參閱  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)