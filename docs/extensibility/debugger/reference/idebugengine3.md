---
title: "IDebugEngine3 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine3
helpviewer_keywords: IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: df8ea8f5e95cf32f5b1425a4f110c424155b2ef2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine3"></a>IDebugEngine3
表示單一的偵錯引擎 (DE) 可控制偵錯的一個或多個模組。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugEngine3 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 這個介面是由實作自訂 DE （如果它支援符號） 來啟用 JustMyCode 狀態。 DE 必須實作這個介面，如果符號和 JustMyCode 支援。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面是由工作階段的偵錯管理員 (SDM) 傳遞使用者選項以用於載入符號的位置上呼叫。 它也稱為具現化時，設定引擎的 GUID （此 GUID 根據引擎註冊期間的度量資訊）。 SDM 也會呼叫這個介面設定的 JustMyCode 狀態，並設定指定的狀態，偵錯工具已知的所有例外狀況。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了繼承自[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)、`IDebugEngine3`介面會公開下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|設定 DE 將會用來搜尋偵錯符號的路徑。|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|載入尚未有載入其符號的所有模組的符號。|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|告知 DE JustMyCode 資訊。|  
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|設定計量 DE GUID。|  
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|設定指定的狀態目前未處理的所有例外狀況。|  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)