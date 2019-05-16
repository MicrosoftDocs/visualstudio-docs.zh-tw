---
title: IDebugEngineProgram2 | Microsoft Docs
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687792"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個介面會提供多執行緒偵錯支援。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 偵錯引擎會實作這個介面來支援多個執行緒同時進行偵錯。 這個介面實作的相同物件上實作[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 使用[QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)若要取得從這個介面`IDebugProgram2`介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugEngineProgram2`。  
  
|方法|描述|  
|------------|-----------------|  
|[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|停止執行此程式中的所有執行緒。|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|監看的執行 （或執行監看的停止） 指定的執行緒上發生。|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|允許 （或不允許） 即使程式停止，在指定的執行緒上發生的運算式評估。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 會呼叫這個介面，以回應[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件，以及設定程式的 「 執行緒步驟監看式 」 和 「 監看式的運算式評估在執行緒 」 狀態。 [停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)時呼叫的程式是要停止; 這個方法可讓程式終止所有的執行緒有機會。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
