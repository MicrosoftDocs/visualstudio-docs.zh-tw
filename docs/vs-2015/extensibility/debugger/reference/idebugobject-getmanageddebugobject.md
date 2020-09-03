---
title: IDebugObject：： GetManagedDebugObject |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4f2917135f5e25648cf08cd9030e3fdf31aedb52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162478"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

在 debug 引擎的位址空間中建立 managed 物件的複本。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```csharp  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppObject`  
 擴展傳回代表新建立之 managed 物件的 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) 物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回 S_OK;否則，會傳回錯誤碼。 如果這個 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 不代表 managed 值類別實例，則傳回 E_FAIL。  
  
## <a name="remarks"></a>備註  
 這個 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 物件必須代表 managed 實值類別實例（例如實例） `System.Decimal` 。 藉由使用本機複本，將會排除呼叫 [評估](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) 的額外負荷。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
