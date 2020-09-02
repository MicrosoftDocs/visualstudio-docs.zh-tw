---
title: IEEDataStorage |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad398380c7c951b99e7d84283355ee9d31955173
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704737"
---
# <a name="ieedatastorage"></a>IEEDataStorage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面代表位元組陣列。  
  
## <a name="syntax"></a>語法  
  
```  
IEEDataStorage : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 運算式評估工具 (EE) 會將此介面實作為型別視覺化程式所使用的 (位元組陣列，以透過 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 介面) 來取得和變更資料。 EE 通常會實作為此介面來支援外部型別視覺化檢視。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 介面上的方法 `IPropertyProxyEESide` 都會傳回這個介面。 呼叫 [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) 以取得 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 介面。 呼叫[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面上的[QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)來取得[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)介面。  
  
## <a name="methods-in-vtable-order"></a>採用 Vtable 順序的方法  
 `IEEDataStorage`介面會執行下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|抓取指定的資料位元組數目至提供的緩衝區。|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|抓取可用的資料位元組數目。|  
  
## <a name="remarks"></a>備註  
 型別視覺化程式會使用這個介面來存取特定物件所持有的資料。 資料會被視為位元組陣列，讓型別視覺化程式以將它呈現給使用者所需的任何方式來操作它。  
  
 如果有需要，自訂檢視器也可以使用此介面，但更常見的情況是，自訂檢視器會使用自訂介面、 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) 或 [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (用於字串導向的資料) 。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [類型視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
