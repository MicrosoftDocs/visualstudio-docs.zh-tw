---
title: IEnumDebugFrameInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4ce2ce06fe26ec420f50597b0377e3f4d174eed
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006852"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
此介面列舉[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 偵錯引擎 (DE) 會實作這個介面可提供一份結構描述的目前呼叫堆疊。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 Visual Studio 呼叫[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)若要取得這個介面時的中斷點，例外狀況或停止，就會發生在程式中進行偵錯。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IEnumDebugFrameInfo2`。  
  
|方法|描述|  
|------------|-----------------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|擷取指定的數目[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)列舉型別序列中的結構。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|略過指定的數目的[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)列舉型別序列中的結構。|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|將列舉型別序列重設到開頭。|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|建立列舉值，包含目前的列舉值相同的列舉型別狀態。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|取得的數目[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)中列舉值的結構。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 會處理中斷點、 例外狀況或開啟正在偵錯之程式的使用者產生的暫停的第一個步驟中取得此介面。 清單[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構代表目前的呼叫堆疊，在清單的結尾呼叫目前函式呼叫清單和最舊的函式的開頭。 每個`FRAMEINFO`代表堆疊框架，也無法評估運算式，並探討了本機變數的內容。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)