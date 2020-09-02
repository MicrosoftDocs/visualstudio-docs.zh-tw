---
title: IEnumDebugPrograms2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d9d1030616fa8d7f3a1bfc6b533c4ed8433ea89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703895"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個介面會列舉在目前的 debug 會話中執行的程式。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 Debug engine (DE) 會執行這個介面，以提供由 DE 進行調試的程式清單。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 Visual Studio 會呼叫 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) 來取得這個介面。 Visual Studio 不會使用[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) 。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法 `IEnumDebugPrograms2` 。  
  
|方法|描述|  
|------------|-----------------|  
|[下一個](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|以列舉順序抓取指定的程式數目。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|略過列舉序列中指定的程式數目。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|將列舉順序重設為開頭。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|建立包含與目前列舉值相同列舉狀態的列舉值。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|取得列舉值中的程式數目。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 使用此介面來：  
  
- 藉由呼叫[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) ，然後在每個程式) 上呼叫[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) ，來填入 [**模組**] 視窗 (。  
  
- 藉由**Attach to Process**呼叫 `IDebugProcess2::EnumPrograms` ，然後呼叫每個[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面上的[QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)來取得[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)介面) ，以填入附加至進程清單 (。  
  
- 產生可在程式 (使用 [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)) 來偵測每個程式的 DEs 清單。  
  
- 藉由呼叫 IDebugProcess2：： EnumPrograms，然後呼叫 [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)) ，對每個程式 (套用 [編輯後繼續] (ENC) 更新。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
