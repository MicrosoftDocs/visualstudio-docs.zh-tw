---
title: IDebugModule3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 923bdb2811a1200b7f638fc2f5727e2d1dbe83b8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58943459"
---
# <a name="idebugmodule3"></a>IDebugModule3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個介面會表示支援的符號和 JustMyCode 狀態的替代位置的模組。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 偵錯引擎 (DE) 會實作這個介面，以支援替代位置的符號，並使用 JustMyCode 狀態 (請參閱[Visual Studio 偵錯工具字彙](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md)"JustMyCode 」 的定義)。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)傳回此介面。 DE 傳送[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)介面，可以使用工作階段偵錯管理員 (SDM)[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)方法。 此外，呼叫[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)上[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)介面會傳回此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 上的方法除了[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|傳回一份搜尋符號以及每個路徑中搜尋結果的路徑。|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|載入並初始化目前模組的符號。|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|傳回旗標，指定模組是否代表使用者程式碼。|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|指定是否將模組應視為使用者程式碼或不。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 是典型的取用者，此介面。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
