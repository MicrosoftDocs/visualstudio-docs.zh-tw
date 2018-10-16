---
title: IDebugManagedObject::SetFromManagedObject |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1f1e4b0aa60cdf20a154305238de74ccdd72cd26
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49280744"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

從提供做為參數的實值類別的執行個體中設定之值的類別物件的執行個體的值。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT SetFromManagedObject(   
   IUnknown* pManagedObject  
);  
```  
  
```csharp  
int SetFromManagedObject(  
   object pManagedObject  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pManagedObject`  
 [in]表示包含新值的 managed 的物件的介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法用來變更受管理的物件，表示的[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)物件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)

