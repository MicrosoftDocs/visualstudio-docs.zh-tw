---
title: IDebugDisassemblyStream2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 63426abcc059da3278569f433907d9f073e510b3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
此介面代表資料流的指示。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎會實作這個介面以支援反組譯碼的程式碼。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)方法會傳回此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugDisassemblyStream2`。  
  
|方法|描述|  
|------------|-----------------|  
|[讀取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|讀取從反組譯碼資料流中目前位置開始的指示。|  
|[搜尋](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|讀取的指標在中移動反組譯碼資料流給定的指示，相對於指定的位置數目。|  
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|傳回特定的程式碼內容的程式碼位置識別項。|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|傳回指定的程式碼位置識別碼相對應的程式碼內容物件。|  
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|傳回表示目前的程式碼位置的程式碼位置識別項。|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|取得與此反組譯碼資料流相關聯的來源文件。|  
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|取得此反組譯碼資料流的範圍。|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|取得此反組譯碼資料流的大小。|  
  
## <a name="remarks"></a>備註  
 反組譯碼資料流可以建立可代表在整個位址空間或只函式或模組內的空間。 每個指示由[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)呼叫所傳回的結構[讀取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)