---
title: IDebugProgram2::Continue |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5c90c456c4825ea9da054f7e78621493cc90a648
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
會繼續執行此程式從已停止的狀態。 會保留任何先前的執行狀態 （例如步驟），並在程式啟動重新執行。  
  
> [!NOTE]
>  這個方法已被取代。 使用[繼續](../../../extensibility/debugger/reference/idebugprocess3-continue.md)方法改為。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Continue(   
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Continue(   
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pThread`  
 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，代表在執行緒。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 此程式正在進行偵錯程式數目，不論哪一個程式所產生的 「 停止 」 事件上呼叫這個方法。 實作必須保留先前的執行狀態 （例如步驟），並繼續執行，就好像它永遠不會具有停止之前完成之前執行。 也就是說，如果此程式中的執行緒正在執行之工作的步驟移轉作業，而且已停止，因為某些其他程式停止，而且而呼叫這個方法，程式必須完成原始進入作業。  
  
> [!WARNING]
>  不會停止事件或直接 （同步） 事件，以傳送[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)時處理這個呼叫，否則偵錯工具可能會停止回應。  
  
## <a name="see-also"></a>請參閱  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)