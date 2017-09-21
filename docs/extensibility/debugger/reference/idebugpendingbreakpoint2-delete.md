---
title: "IDebugPendingBreakpoint2::Delete | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2::Delete"
helpviewer_keywords: 
  - "IDebugPendingBreakpoint2::Delete 方法"
  - "Delete 方法"
ms.assetid: 4cb5ed81-6f0c-41ce-a770-5adb6b4bf5d9
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPendingBreakpoint2::Delete
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

刪除此暫止中斷點，並從其繫結的所有中斷點。  
  
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
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  傳回`E_BP_DELETED`如果已刪除中斷點。  
  
## 範例  
 下列範例會示範如何實作這個方法，如`CPendingBreakpoint`實作物件[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)介面。  
  
```cpp#  
HRESULT CPendingBreakpoint::Delete(void)    
{    
   HRESULT hr;    
  
   // Verify that the pending breakpoint has not been deleted. If deleted,    
   // then return hr = E_BP_DELETED.    
   if (m_state.state != PBPS_DELETED)    
   {    
      // If the pending breakpoint has bound and has an associated bound   
      // breakpoint, delete and release the bound breakpoint and set the   
      // pointer to NULL.    
      if (m_pBoundBP)    
      {    
         m_pBoundBP->Delete();    
         m_pBoundBP->Release();    
         m_pBoundBP = NULL;    
      }    
      // If the pending breakpoint did not bind and has an associated   
      // error breakpoint, release the error breakpoint and set the   
      // pointer to NULL.   
      if (m_pErrorBP)    
      {    
         m_pErrorBP->Release();    
         m_pErrorBP = NULL;    
      }    
  
      // Set the PENDING_BP_STATE in the PENDING_BP_STATE_INFO structure   
      // to deleted.     
      m_state.state = PBPS_DELETED;    
   }    
   else    
   {    
      hr = E_BP_DELETED;    
   }    
  
   return hr;    
}    
```  
  
## 請參閱  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)