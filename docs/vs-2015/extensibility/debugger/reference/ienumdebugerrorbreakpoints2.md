---
title: IEnumDebugErrorBreakpoints2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 95d001c0072442d07ae12f773a26290a95a2f7f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68178478"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面列舉暫止中斷點相關聯的錯誤中斷點。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumDebugErrorBreakpoints2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 偵錯引擎 (DE) 會實作這個介面做為其支援中斷點的一部分。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 Visual Studio 呼叫[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)若要取得此介面，表示清單中的中斷點無法繫結，或[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)來取得這個介面，表示中斷點的清單未繫結。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IEnumDebugErrorBreakpoints2`。  
  
|方法|描述|  
|------------|-----------------|  
|[下一個](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|擷取指定的數目的列舉型別序列中的錯誤中斷點。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|略過指定的數目的列舉型別序列中的錯誤中斷點。|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|將列舉型別序列重設到開頭。|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|建立列舉值，包含目前的列舉值相同的列舉型別狀態。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|取得列舉值中的錯誤中斷點的數目。|  
  
## <a name="remarks"></a>備註  
 這個介面會保留一份[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)介面，其中每個描述，可能不會繫結，以及為何它可能不會繫結的中斷點。 Visual Studio 會使用`IEnumDebugErrorBreakpoint2`介面，以更新顯示在 IDE 中的中斷點。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
