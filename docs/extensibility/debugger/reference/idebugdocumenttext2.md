---
title: IDebugDocumentText2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fa356a41205ecbd51fd22a8396cddae2d7e4728b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54963420"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
此介面代表文字文件。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 以文字形式提供需要的原始程式碼時，偵錯引擎 (DE) 會實作此介面。 由於這是最常見的情況下，如果實作 DE [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面，它也應該實作`IDebugDocumentText2`介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 使用`QueryInterface`方法，以取得從這個介面`IDebugDocument2`介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 上的方法除了`IDebugDocument2`介面，這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|擷取文件中的這個位置的文字的大小。|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|從指定之位置的文件中擷取的文字。|  
  
## <a name="remarks"></a>備註  
 實作此介面的物件，也必須實作<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>介面，其提供<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>介面[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)物件。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)