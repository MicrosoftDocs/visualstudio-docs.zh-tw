---
title: IDebugModule3 |Microsoft Docs
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
ms.openlocfilehash: 326efe27ae35de1550ebc8230ab3c94229589640
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690947"
---
# <a name="idebugmodule3"></a>IDebugModule3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面表示支援符號和 JustMyCode 狀態之替代位置的模組。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 Debug engine (DE) 會執行這個介面，以支援符號的替代位置，以及使用 JustMyCode 狀態 (請參閱 [Visual Studio 偵錯工具詞彙](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) 中的 "JustMyCode" ) 定義。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 對 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) 的呼叫會傳回這個介面。 會將 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) 介面傳送至會話 debug MANAGER (SDM) 使用 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 方法。 此外，對[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)介面上的[QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)呼叫會傳回這個介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 介面上的方法，這個介面也會執行下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|傳回搜尋符號的路徑清單，以及搜尋每個路徑的結果。|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|載入並初始化目前模組的符號。|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|傳回旗標，指定模組是否代表使用者程式碼。|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|指定模組是否應視為使用者程式碼。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 是此介面的一般取用者。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
