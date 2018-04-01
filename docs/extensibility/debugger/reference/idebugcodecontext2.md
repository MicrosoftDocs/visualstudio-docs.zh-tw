---
title: IDebugCodeContext2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 75403c0597b2285aa9117f3ffb51acd01c967f3d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
此介面代表程式碼指示的開始位置。 大部分的執行階段架構，程式碼內容可以視為程式的執行資料流中的位址。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎實作這個介面來與相關聯的文件位置將程式碼指示的位置。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 在許多介面上的方法會傳回這個介面，大部分都是， [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)。 它也可用於廣泛以[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)介面也如同中斷點解析資訊。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了上[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|取得對應至使用中程式碼內容的文件內容。|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|取得這個程式碼內容的語言資訊。|  
  
## <a name="remarks"></a>備註  
 主要差別`IDebugCodeContext2`介面和[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)介面是`IDebugCodeContext2`永遠指令對齊。 這表示`IDebugCodeContext2`一律指向開頭的指令，而`IDebugMemoryContext2`可能指向的記憶體，在執行階段架構中任何位元組。 `IDebugCodeContext2`指示而非基本的儲存體大小 （通常為位元組），就會遞增。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)   
 [下一步](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)