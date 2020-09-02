---
title: IDebugProperty3 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 479827cc83486d6bb9c68d0749b8870cd6c41861
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694768"
---
# <a name="idebugproperty3"></a>IDebugProperty3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面提供下列支援：  
  
- 正在抓取與屬性相關聯的任意長字串。  
  
- 將唯一識別碼與屬性產生關聯。  
  
- 正在抓取屬性的自訂檢視器清單。  
  
- 設定屬性的值，使其能夠報告任何產生的錯誤  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 Debug engine (DE) 會在執行 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 的相同物件上執行這個介面，以提供長字串、屬性識別碼和自訂檢視器的支援。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 呼叫介面上的 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) `IDebugProperty2` 來取得這個介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了繼承自的方法之外 `IDebugProperty2` ，介面也會 `IDebugProperty3` 公開下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|傳回與屬性相關聯之字串的長度。|  
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|傳回使用者提供的緩衝區中的字串。|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|建立這個屬性的唯一識別碼。|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|終結這個屬性的唯一識別碼。|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|傳回可以用來查看此屬性的自訂檢視器數目。|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|傳回可以用來查看此屬性的自訂檢視器清單。|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|設定這個屬性的值，如果發生任何錯誤，則傳回錯誤訊息。|  
  
## <a name="remarks"></a>備註  
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) 是會話 debug MANAGER (SDM) 設定屬性值的慣用方式。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
