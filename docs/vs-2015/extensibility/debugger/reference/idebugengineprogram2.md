---
title: IDebugEngineProgram2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2c265cbfc89d0b637b1d2f37a3e3b9e948a8dd8f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687792"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面提供多執行緒的調試支援。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 偵錯工具引擎會執行這個介面，以支援多個執行緒的同時偵錯工具。 此介面會在執行 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 介面的相同物件上進行。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 使用 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 從介面取得這個介面 `IDebugProgram2` 。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法 `IDebugEngineProgram2` 。  
  
|方法|描述|  
|------------|-----------------|  
|[停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|停止在此程式中執行的所有線程。|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|監看執行 (或停止監看執行) 發生在指定的執行緒上。|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|允許 (或不允許在指定的執行緒上執行) 運算式評估，即使程式已停止也是如此。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 會呼叫此介面來回應 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 事件，並設定程式的「監看式執行緒步驟」和「監看執行緒上的運算式評估」狀態。 每當程式停止時，就會呼叫[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) ;這個方法可讓程式有機會終止所有線程。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
