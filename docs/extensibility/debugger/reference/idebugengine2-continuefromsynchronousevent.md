---
title: "IDebugEngine2::ContinueFromSynchronousEvent |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2::ContinueFromSynchronousEvent
helpviewer_keywords: IDebugEngine2::ContinueFromSynchronousEvent
ms.assetid: 9a57dfcd-df8e-4be5-b1fe-bd853e3c6bb2
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cb28083d62ad200152cac0b49f99a06a693f34dd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine2continuefromsynchronousevent"></a>IDebugEngine2::ContinueFromSynchronousEvent
工作階段的偵錯管理員 (SDM) 表示同步偵錯事件，先前傳送到 SDM，偵錯引擎 (DE) 已接收並處理呼叫。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ContinueFromSynchronousEvent(   
   IDebugEvent2* pEvent  
);  
```  
  
```csharp  
HRESULT ContinueFromSynchronousEvent(   
   IDebugEvent2 pEvent  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pEvent`  
 [in][IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)物件，代表從中偵錯工具現在應該會繼續先前傳送同步事件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 DE 必須驗證它所代表事件的來源`pEvent`參數。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法來簡單`CEngine`實作物件[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)介面。  
  
```cpp  
HRESULT CEngine::ContinueFromSynchronousEvent(IDebugEvent2* pEvent)  
{  
   HRESULT hr;  
  
   // Create a pointer to a unique event interface defined for batch file  
   // breaks.    
   IAmABatchFileEvent *pBatEvent;  
   // Check for successful query for the unique batch file event  
   // interface.  
   if (SUCCEEDED(pEvent->QueryInterface(IID_IAmABatchFileEvent,  
                                       (void **)&pBatEvent)))  
   {  
      // Release the result of the QI.  
      pBatEvent->Release();  
      // Check thread message for notification to continue.  
      if (PostThreadMessage(GetCurrentThreadId(),  
                            WM_CONTINUE_SYNC_EVENT,  
                            0,  
                            0))  
      {    
         hr = S_OK;  
      }  
      else  
      {  
         hr = HRESULT_FROM_WIN32(GetLastError());  
      }  
   }  
   else  
   {  
      hr = E_INVALIDARG;  
   }  
   return hr;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)