---
title: IDebugEngine3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e43da0b05062c6c7b1c4d3cfe771ff0b93f83a9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195790"
---
# <a name="idebugengine3"></a>IDebugEngine3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

表示單一的偵錯引擎 (DE)，以控制一個或多個模組的偵錯。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugEngine3 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 此介面是由實作自訂 DE （如果它支援符號） 來啟用 JustMyCode 狀態。 DE 必須實作這個介面，如果它支援符號和 JustMyCode。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面是由工作階段的偵錯管理員 (SDM)，將使用者的選項，針對要從中載入符號的位置上呼叫。 也稱為具現化時，設定引擎的 GUID （此 GUID 根據計量引擎註冊時）。 在 SDM 也會呼叫這個介面設定的 JustMyCode 狀態，並設定所指定的狀態偵錯工具已知的所有例外狀況。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了繼承自方法[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)，則`IDebugEngine3`介面會公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|設定裝置將會用來搜尋偵錯符號的路徑。|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|載入尚未有載入其符號的所有模組的符號。|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|告知 DE JustMyCode 資訊。|  
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|從度量設定 DE GUID。|  
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|設定指定的狀態目前未處理的所有例外狀況。|  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
