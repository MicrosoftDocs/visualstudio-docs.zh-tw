---
title: IEnumDebugFrameInfo2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6cc6a0ff332fd6feac72ce4abf38b5319e63c913
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161018"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面會列舉 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 結構。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 Debug engine (DE) 會執行這個介面，以提供描述目前呼叫堆疊的結構清單。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 Visual Studio 呼叫 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) ，以在所要進行的程式中發生中斷點、例外狀況或終止時取得此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法 `IEnumDebugFrameInfo2` 。  
  
|方法|描述|  
|------------|-----------------|  
|[下一個](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|抓取列舉序列中指定的 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 結構數目。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|略過列舉序列中指定的 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 結構數目。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|將列舉順序重設為開頭。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|建立包含與目前列舉值相同列舉狀態的列舉值。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|取得列舉值中的 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 結構數目。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 會取得這個介面，做為處理中斷點、例外狀況或使用者在所進行之程式上產生之暫停的第一個步驟。 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構的清單代表目前的呼叫堆疊，目前的函式呼叫位於清單的開頭，而最舊的函數呼叫位於清單結尾。 每個都 `FRAMEINFO` 代表一個堆疊框架，也就是可在其中評估運算式的內容，以及查看的本機變數。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
