---
title: IEnumDebugFields |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5e3c9a43b6903522fe2caf0e329f8e8faa69cd6b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161084"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個介面代表執行 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 介面的物件集合。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumDebugFields : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 這個介面是由符號提供者所執行，以提供可執行 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 介面的物件集合。 請注意，這不是標準的 COM 列舉，因為 [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) 方法是否存在。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)和[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)會傳回這個介面。  
  
## <a name="methods-in-vtable-order"></a>採用 Vtable 順序的方法  
 這個介面會實作為下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[下一個](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|從列舉中抓取下一組 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|略過指定數目的專案。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|將列舉重設為第一個專案。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|抓取目前列舉的複本。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|捕獲列舉中的專案數。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 標頭： sh. h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)   
 [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)
