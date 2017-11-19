---
title: "IDebugCanStopEvent2::CanStop |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCanStopEvent2::CanStop
helpviewer_keywords: IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9008410831d3c2c7b6e93d4f35a1d08914a5336
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
要在目前的程式碼位置停止或繼續執行，只會告知偵錯引擎 (DE)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```csharp  
int CanStop (   
   int fCanStop  
);  
```  
  
#### <a name="parameters"></a>參數  
 `fCanStop`  
 [in]非零 (`TRUE`) 如果 DE 應該停止在目前的程式碼位置; 否則為零 (`FALSE`)。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個事件的接收者通常會呼叫[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)方法，以判斷 DE 想要停止的原因，然後呼叫`IDebugCanStopEvent2::CanStop`方法與適當的回應。  
  
 如果 DE 停止時，它會傳送描述停止原因的事件。 通常有兩個事件，傳送時，由使用者或訊號中斷[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)介面，以及所代表的中斷點事件[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)介面。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)