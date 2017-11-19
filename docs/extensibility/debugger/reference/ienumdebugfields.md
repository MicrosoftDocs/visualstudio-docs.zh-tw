---
title: "IEnumDebugFields |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugFields
helpviewer_keywords: IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ed697205a5cd7d866df639e2908e3cc0b4fa2f72
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
此介面代表實作物件的集合[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumDebugFields : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 這個介面由提供實作的物件集的符號提供者實作[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面。 請注意，這不是標準的 COM 列舉的緣故[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)方法。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面由[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)和[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 這個介面會實作下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|擷取下的一組[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)列舉中的物件。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|略過指定的數目的項目。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|將列舉重設第一個項目。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|擷取一份目前的列舉。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|擷取列舉中的項目數目。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)   
 [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)