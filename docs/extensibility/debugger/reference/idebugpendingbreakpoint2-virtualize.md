---
title: "IDebugPendingBreakpoint2::Virtualize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2::Virtualize"
helpviewer_keywords: 
  - "虛擬化方法"
  - "IDebugPendingBreakpoint2::Virtualize 方法"
ms.assetid: 58c8e9a5-4494-47c2-bddb-56f628da6a2d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPendingBreakpoint2::Virtualize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

切換虛擬化的狀態的暫止中斷點。  當暫止中斷點虛擬化時，偵錯引擎會嘗試將其繫結，每次新的程式碼載入程式。  
  
## 語法  
  
```cpp#  
HRESULT Virtualize(   
   BOOL fVirtualize  
);  
```  
  
```cpp#  
int Virtualize(   
   int fVirtualize  
);  
```  
  
#### 參數  
 `fVirtualize`  
 \[in\]設定為非零值 \(`TRUE`\) 要虛擬化的暫止中斷點，或為零 \(`FALSE`\) 若要關閉虛擬化。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  傳回`E_BP_DELETED`如果已刪除中斷點。  
  
## 備註  
 每次載入的程式碼，則會繫結虛擬化的中斷點。  
  
## 範例  
 下列範例會示範如何實作這個方法，如`CPendingBreakpoint`物件，公開 \(expose\) [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)介面。  
  
```cpp#  
HRESULT CPendingBreakpoint::Virtualize(BOOL fVirtualize)    
{    
   HRESULT hr;    
  
   // Verify that the pending breakpoint has not been deleted. If deleted,   
   // then return hr = E_BP_DELETED.    
   if (m_state.state != PBPS_DELETED)    
   {    
      if (fVirtualize)    
      {    
         // Set the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS   
         // structure.    
         SetFlag(m_state.flags, PBPSF_VIRTUALIZED);    
      }    
      else    
      {    
         // Clear the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS   
         // structure.    
         ClearFlag(m_state.flags, PBPSF_VIRTUALIZED);    
      }    
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
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)