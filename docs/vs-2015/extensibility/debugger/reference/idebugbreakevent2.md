---
title: IDebugBreakEvent2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 98e8c1b1669b3fdd1f442c6987e4e9d2b9fc4835
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675384"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面會告知會話 debug manager (SDM) 已成功完成非同步中斷。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 DE 會執行這個介面，以支援程式中的使用者分隔。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的物件上執行， (SDM 使用[QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)來存取 `IDebugEvent2` 介面) 。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 當使用者要求正在進行正在進行偵錯工具的程式暫停時，SDM 會呼叫 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) 。 當程式已順利暫停時，就會將事件取消 `IDebugBreakEvent2` 。 這個事件是在附加至所要進行的程式時，使用 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送。  
  
## <a name="remarks"></a>備註  
 例如，使用者可以選取 [**調試**程式] 功能表上的 [**全部中斷**] 命令，以中斷正在執行無限迴圈的程式。 SDM 會告知程式，藉由呼叫 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)來停止。 當程式最後停止時，就會傳送 [取消] `IDebugBreakEvent2` 。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
