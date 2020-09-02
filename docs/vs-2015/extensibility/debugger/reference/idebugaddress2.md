---
title: IDebugAddress2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ca14e6236fc7e12ea259b97f7f2ddb69fe052f55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65692832"
---
# <a name="idebugaddress2"></a>IDebugAddress2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個介面可讓您存取擁有物件之進程的識別碼，該物件的位址由這個介面表示。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugAddress2 : IDebugAddress  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 符號提供者會在執行 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 介面的相同物件上，執行這個介面。 這個介面可讓您存取擁有與此位址相關之物件的進程識別碼。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 使用 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 從 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 介面取得這個介面。  
  
## <a name="methods-in-vtable-order"></a>採用 vtable 順序的方法  
 除了繼承自 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 介面的方法之外，這個介面也會執行下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|抓取擁有這個介面所表示之物件的進程識別碼。|  
  
## <a name="requirements"></a>需求  
 標頭： sh. h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
