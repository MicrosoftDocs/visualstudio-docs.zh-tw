---
title: IDebugAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09c0ce6f8b641830b76fffd0d201b430ddf00b41
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962244"
---
# <a name="idebugaddress"></a>IDebugAddress
這個介面來表示項目的位址。 它會傳回符號處理常式。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugAddress : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 符號提供者會實作這個介面來代表物件的位址。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 在許多介面的許多方法會傳回此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|擷取[DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)結構描述的物件和其位置。|  
  
## <a name="remarks"></a>備註  
 符號提供者會傳回這個介面來代表物件和它的位置 （例如，函式、 方法或類別） 在特定範圍內。 會傳回此介面，並將其傳遞給各種方法的符號提供者和運算式評估工具。 一般來說，符號提供者是實體，必須將此介面的內容。  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)