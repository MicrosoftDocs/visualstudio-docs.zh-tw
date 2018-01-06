---
title: "IDebugAddress |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAddress
helpviewer_keywords: IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ea03ec205a4bc28f025b8539bc0abf3abc59ceaa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugaddress"></a>IDebugAddress
此介面代表項目的位址。 它會傳回符號處理常式。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugAddress : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 符號提供者會實作這個介面來代表物件的位址。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 在許多介面上的許多方法會傳回此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|擷取[DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)結構描述物件和其位置。|  
  
## <a name="remarks"></a>備註  
 符號提供者會傳回此介面，以便代表物件和其位置 （例如，函式、 方法或類別） 在特定範圍內。 這個介面是從傳回，而且傳遞給各種方法的符號提供者和運算式評估工具。 一般來說，符號提供者是需要將此介面的內容之唯一實體。  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)