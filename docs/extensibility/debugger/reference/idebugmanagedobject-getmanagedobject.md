---
title: IDebugManagedObject::GetManagedObject |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f30c76dfd0c2f9dafa4844f815ce2506e70346f3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917930"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
傳回代表受管理的物件的介面。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetManagedObject(   
   IUnknown** ppManagedObject  
);  
```  
  
```cpp  
int GetManagedObject(  
   out object ppManagedObject  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppManagedObject`  
 [out]傳回代表受管理的物件的介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 從這個方法傳回的介面可以查詢的任何受管理的類別，使其被呼叫的方法所實作的介面。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)