---
title: IDebugDocumentCoNtext2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b6d040597f48d4514a58027df3335c080d6305a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144955"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個介面代表來源檔案檔中的位置。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugDocumentContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 在原始程式碼層級的偵錯工具支援中，debug engine (DE) 實作為此介面的一部分。 除了原始程式碼中的位置之外，此介面還提供比較內容和流覽原始程式碼檔的方法。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 多個介面上的方法（通常是 [GetDocumentCoNtext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) 和 [GetDocumentCoNtext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) 介面）會傳回這個介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法 `IDebugDocumentContext2` 。  
  
|方法|描述|  
|------------|-----------------|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|取得包含此檔內容的檔。|  
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|取得包含此檔內容之檔的可顯示名稱。|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|抓取與此檔內容相關聯的所有程式碼內容清單。|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|取得與此檔內容相關聯的語言。|  
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|取得此檔內容的 file 語句範圍。|  
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|取得此檔內容的檔案來源範圍。|  
|[比較](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|將此檔內容與指定的檔內容陣列進行比較。|  
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|依指定的語句或行數移動檔內容。|  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [GetDocumentCoNtext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)   
 [GetDocumentCoNtext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)   
 [GetDocumentCoNtext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)
