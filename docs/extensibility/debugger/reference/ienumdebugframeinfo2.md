---
title: IEnumDebugFrameInfo2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 858250c3c951880cf905ea6ee150f1ff61008204
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31123914"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
這個介面會列舉[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎 (DE) 會實作這個介面可提供一份結構描述目前的呼叫堆疊。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 Visual Studio 呼叫[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)若要取得此介面，每當中斷點，例外狀況或停止，就會發生在程式中進行偵錯。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IEnumDebugFrameInfo2`。  
  
|方法|描述|  
|------------|-----------------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|擷取指定的數目的[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)列舉順序中的結構。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|略過指定的數目的[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)列舉順序中的結構。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|列舉序列重設為開頭。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態相同。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|取得數目[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)中查看的列舉值的結構。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 會處理中斷點、 例外狀況或使用者產生的暫停正在進行偵錯程式的第一個步驟中取得此介面。 清單[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構代表目前的呼叫堆疊，在清單的結尾呼叫目前函式呼叫的清單，最舊的函式開頭。 每個`FRAMEINFO`代表堆疊框架，其中的運算式可以評估，而且在查看本機變數的內容。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)