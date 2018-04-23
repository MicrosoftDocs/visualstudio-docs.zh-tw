---
title: IEnumDebugModules2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dd3ca02776aae4a7b4cd22485eba9827f4731d5d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
這個介面會列舉清單的模組。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumDebugModules2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎 (DE) 會實作這個介面來代表的程式載入的模組清單。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 Visual Studio 呼叫[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)取得此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IEnumDebugModules2`。  
  
|方法|描述|  
|------------|-----------------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|擷取指定的列舉順序中的模組數目。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|略過指定的列舉順序中的模組數目。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|列舉序列重設為開頭。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態相同。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|取得模組的數目。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 會使用這個介面主要是為了更新**模組**視窗。  
  
 為了在 Visual Studio 中偵錯，程式是以邏輯順序的程式碼指令可以跨模組界限，因此需要單一的模組清單[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面。 在清單中的第一個模組通常會包含相關聯的程式的初始項目點。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)