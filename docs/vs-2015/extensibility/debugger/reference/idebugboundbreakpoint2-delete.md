---
title: IDebugBoundBreakpoint2::Delete |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBoundBreakpoint2::Delete
helpviewer_keywords:
- Delete method
- IDebugBoundBreakpoint2::Delete method
ms.assetid: 7088dc66-f24a-446f-a52a-397d02457a41
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 482dfa163983c29b431286ac0282ddeb30778368
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490824"
---
# <a name="idebugboundbreakpoint2delete"></a>IDebugBoundBreakpoint2::Delete
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugBoundBreakpoint2::Delete](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugboundbreakpoint2-delete)。  
  
刪除中斷點。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Delete(   
   void   
);  
```  
  
```csharp  
int Delete();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。 傳回`E_BP_DELETED`如果繫結的中斷點物件的狀態設為`BPS_DELETED`(屬於[BP_STATE](../../../extensibility/debugger/reference/bp-state.md)列舉型別)。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法來簡單`CBoundBreakpoint`公開的物件[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)介面。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)

