---
title: IDebugPortRequest2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fa72ae9d2cfbe399c3507406875e9c692d18b678
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188332"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面描述埠。 此描述可用來將埠新增至埠供應商。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 Visual Studio 通常會在從埠供應商取得 debug 埠的過程中，執行這個介面。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 此介面會傳遞至 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 以建立 debug 埠。 對 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) 的呼叫會傳回這個介面，代表用來在第一個位置建立埠的要求。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法 `IDebugPortRequest2` 。  
  
|方法|描述|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|取得要建立之埠的名稱。|  
  
## <a name="remarks"></a>備註  
 Debug engine 通常不會與埠供應商互動，而且不會使用此介面。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
