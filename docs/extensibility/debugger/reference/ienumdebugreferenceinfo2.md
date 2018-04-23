---
title: IEnumDebugReferenceInfo2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugReferenceInfo2
helpviewer_keywords:
- IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 18a54ba552886d7dbdd4837c877761c80417b889
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
這個介面會列舉[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumDebugReferenceInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎 (DE) 會實作這個介面做為其支援的物件參考的一部分，在記憶體中。 只有當支援的參考，則必須實作這個介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 Visual Studio 呼叫[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)取得此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IEnumDebugReferenceInfo2`。  
  
|方法|描述|  
|------------|-----------------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|擷取指定的數目的[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)列舉順序中的結構。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|略過指定的數目的[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)列舉順序中的結構。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|列舉序列重設為開頭。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態相同。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|取得數目[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)中查看的列舉值的結構。|  
  
## <a name="remarks"></a>備註  
 參考是基本上型別和位址，而屬性名稱、 類型和地址。 參考仍然存在，只要物件參考存在於記憶體中。 請參閱[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)如需詳細資訊。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)