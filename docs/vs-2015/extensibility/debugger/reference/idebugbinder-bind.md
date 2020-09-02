---
title: IDebugBinder：： Bind |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 547f94cb4534bcb281cce0fdc2ff7db5fefe3593
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423539"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個方法會取得包含符號目前值的記憶體內容或物件。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT Bind(   
   IDebugObject*  pContainer,  
   IDebugField*   pField,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Bind(  
   IDebugObject     pContainer,  
   IDebugField      pField,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pContainer`  
 在包含[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)所參考之子系的 IDebugObject `pField` 。  
  
 `pField`  
 在代表符號的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 。  
  
 `ppObject`  
 擴展傳回 `IDebugObject` 表示符號實例的。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
