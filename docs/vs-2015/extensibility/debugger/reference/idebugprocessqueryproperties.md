---
title: IDebugProcessQueryProperties | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ad6e7d10b2a6a83aa11a0296f4804704cd12c9d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944356"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個介面是藉由將延伸模組介面[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)實作者。 它可讓實作者，以取得有關偵錯的處理序環境。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 實作這個介面，以取得有關偵錯程序的執行環境。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugProcessQueryProperties`。  
  
|方法|描述|  
|------------|-----------------|  
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|屬性值的查詢。|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|如需屬性值的查詢。|  
  
## <a name="remarks"></a>備註  
 很少會實作這個介面。  
  
## <a name="requirements"></a>需求  
 標頭：Portpriv.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
