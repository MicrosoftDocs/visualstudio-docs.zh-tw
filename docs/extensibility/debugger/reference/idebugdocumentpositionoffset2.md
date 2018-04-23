---
title: IDebugDocumentPositionOffset2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f08b278d75068351d6d65511f74209c7208024cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
表示原始程式檔中的字元位移位置。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 IDE 所實作，且由偵錯引擎。  
  
## <a name="methods"></a>方法  
 下表顯示的方法`IDebugDocumentPositionOffset2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|擷取目前的文件位置的範圍。|  
  
## <a name="remarks"></a>備註  
 這會傳回相同的資訊[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)但在`char`文件開頭位移。 它會存在於磁碟上，也就是字元，而不是通常傳回行和資料行資訊的一維陣列一樣，這會呈現文件。  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)