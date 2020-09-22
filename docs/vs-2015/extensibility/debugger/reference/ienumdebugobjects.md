---
title: IEnumDebugObjects |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugObjects
helpviewer_keywords:
- IEnumDebugObjects interface
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d01e6340be0cb710d9173850e66fc18d543347d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839133"
---
# <a name="ienumdebugobjects"></a>IEnumDebugObjects
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面代表執行 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 介面的物件集合。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumDebugObjects : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 運算式評估工具會執行這個介面，以提供可實 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 介面的物件集合。 請注意，這不是標準的 COM 列舉，因為 [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) 方法是否存在。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) 會傳回這個介面。  
  
## <a name="methods-in-vtable-order"></a>採用 Vtable 順序的方法  
 這個介面會實作為下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[下一個](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|從列舉中抓取下一組 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 物件。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|略過指定數目的專案。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|將列舉重設為第一個專案。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|抓取目前列舉的複本。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|捕獲列舉中的專案數。|  
  
## <a name="remarks"></a>備註  
 這個介面可讓 debug engine 列舉陣列中的一組物件。  
  
## <a name="requirements"></a>需求  
 標頭： ee. h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)
