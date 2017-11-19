---
title: "IDebugDocumentPositionOffset2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 81c934add7248b7d63854b259957d58aae298401
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
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
  
|方法|說明|  
|------------|-----------------|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|擷取目前的文件位置的範圍。|  
  
## <a name="remarks"></a>備註  
 這會傳回相同的資訊[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)但在`char`文件開頭位移。 它會存在於磁碟上，也就是字元，而不是通常傳回行和資料行資訊的一維陣列一樣，這會呈現文件。  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)