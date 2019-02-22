---
title: IDebugDocumentContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f648888e41557e7debe460d99c07cd1017150c0e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992291"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
此介面代表來源檔案的文件中的位置。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugDocumentContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 偵錯引擎 (DE) 會實作這個介面做為其對層級來源的程式碼的偵錯的支援的一部分。 除了在原始程式碼中的位置，此介面會提供方法來比較內容，並瀏覽原始程式碼文件。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 方法上數個介面，最常[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)並[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)介面，傳回這個介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugDocumentContext2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|取得包含這個文件內容的文件。|  
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|取得包含這個文件內容的文件可顯示名稱。|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|擷取與此文件內容相關聯的所有程式碼內容的清單。|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|取得與此文件內容相關聯的語言。|  
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|取得此文件內容的檔案陳述式範圍。|  
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|取得此文件內容的檔案來源範圍。|  
|[Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|比較此文件內容，給定文件內容的陣列。|  
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|以指定數目的陳述式或字行中移動的文件內容。|  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)