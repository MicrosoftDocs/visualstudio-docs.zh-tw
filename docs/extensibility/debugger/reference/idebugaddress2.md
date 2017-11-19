---
title: "IDebugAddress2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAddress2
helpviewer_keywords: IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 13161c2be23d2eec6f1d91fd59fc465cbc59a510
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugaddress2"></a>IDebugAddress2
這個介面提供的存取權，擁有物件的位址的處理序的識別碼由這個介面。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugAddress2 : IDebugAddress  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 符號提供者會實作此介面實作在相同物件上[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)介面。 這個介面會提供存取給擁有此位址相關物件的程序的識別碼。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 使用[QueryInterface](/cpp/atl/queryinterface)獲得從這個介面[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)介面。  
  
## <a name="methods-in-vtable-order"></a>依照 vtable 順序的方法  
 除了繼承自[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)介面，這個介面會實作下列方法：  
  
|方法|說明|  
|------------|-----------------|  
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|擷取擁有此介面所表示之物件的處理序識別碼。|  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)