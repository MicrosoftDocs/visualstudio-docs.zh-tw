---
title: IDebugCodeContext2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f4c744e5dc79c5e704e2cec6d83e39a4170bcd68
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922964"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
這個介面表示的程式碼指示的開始位置。 適用於大部分的執行階段架構現在，程式碼內容可以視為該應用程式的執行資料流中的位址。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 偵錯引擎會實作這個介面來與相關的文件位置的程式碼指示的位置。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 在許多介面的方法會傳回這個介面，通常， [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)。 它也可搭配廣泛[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)也如同中斷點解析資訊的介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 上的方法除了[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|取得對應至使用中的程式碼內容的文件內容。|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|取得此程式碼內容的語言資訊。|  
  
## <a name="remarks"></a>備註  
 主要差別`IDebugCodeContext2`介面和[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)介面是`IDebugCodeContext2`永遠指令對齊。 這表示`IDebugCodeContext2`一律指向指令開頭而`IDebugMemoryContext2`可能指向記憶體中的執行階段架構的任何位元組。 `IDebugCodeContext2` 就會遞增的指示，而不是基本的儲存體大小 （通常為位元組）。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)   
 [下一步](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)