---
title: IDebugDocument2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 36ac127e6cd6e25fd42c4859e723c883ecaffa82
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocument2"></a>IDebugDocument2
此介面代表來源文件。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 通常會實作這個介面。 它必須提供來源的程式碼，而且磁碟上不存在來源時，偵錯引擎 (DE) 也可以實作這個介面。  在這種情況下，DE 也會實作[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)和[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)介面，以及一些額外的方法上[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)和[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 上的方法`IDebugDocumentContext2`， `IDebugDisassemblyStream2`， `IDebugDocumentPosition2`，和`IDebugActivateDocumentEvent2`介面傳回此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugDocument2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|取得其中一種數種形式的文件的名稱。|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|取得文件的類別識別項。|  
  
## <a name="remarks"></a>備註  
 DE 提供的原始程式碼時，才會實作這個介面。 比方說，當您正在偵錯 HTML 網頁上的指令碼，DE 提供原始碼因為下載來源或動態產生，並不是磁碟檔案。 當偵錯傳統的語言，例如 c + +，這個介面不需要實作。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)