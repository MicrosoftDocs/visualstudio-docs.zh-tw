---
title: "IEnumDebugAddresses |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugAddresses
helpviewer_keywords: IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: db531c35ea3bbb6176095f19897404d192096e22
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
此介面代表實作物件的集合[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)介面。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 這個介面由提供實作的物件集的符號提供者實作[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)介面。 請注意，這不是標準的 COM 列舉的緣故[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)方法。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面由[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)和[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 這個介面會實作下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|擷取下的一組[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)列舉中的物件。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|略過指定的數目的項目。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|將列舉重設第一個項目。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|擷取一份目前的列舉。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|擷取列舉中的項目數目。|  
  
## <a name="remarks"></a>備註  
 偵錯引擎通常會使用此介面來協助判斷運算式評估工具提供適當的位址。  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)