---
title: IDebugAddress2 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 988e53c53b83658a2ca4338659a5f805f3bcf0e1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497523"
---
# <a name="idebugaddress2"></a>IDebugAddress2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugAddress2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugaddress2)。  
  
這個介面會提供給擁有之物件的位址的處理序識別碼的存取由這個介面。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugAddress2 : IDebugAddress  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 符號提供者所實作的相同物件上實作這個介面[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)介面。 這個介面會提供存取擁有的物件，這個地址相關的處理序的識別碼。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 使用[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)若要取得從這個介面[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)介面。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序中的方法  
 除了繼承自方法[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|擷取擁有此介面所表示之物件的處理序識別碼。|  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)

