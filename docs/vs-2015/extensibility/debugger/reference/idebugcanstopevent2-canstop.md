---
title: IDebugCanStopEvent2::CanStop |Microsoft Docs
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
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 65095961510bd80758cbf94c4d9aa8811f61a9fe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498469"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugCanStopEvent2::CanStop](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcanstopevent2-canstop)。  
  
通知要停止在目前的程式碼位置，或只是繼續執行偵錯引擎 (DE)。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 [in]非零 (`TRUE`) 如果 DE 應該停止的目前位置的程式碼; 否則為零 (`FALSE`)。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個事件的接收者通常會呼叫[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)方法，以判斷 DE 想要停止的原因，然後呼叫`IDebugCanStopEvent2::CanStop`具有適當的回應方法。  
  
 如果 DE 停止時，它會傳送描述停止的原因的事件。 通常有兩個傳送的事件，由使用者或訊號中斷[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)介面，而且所代表的中斷點事件[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)介面。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)

