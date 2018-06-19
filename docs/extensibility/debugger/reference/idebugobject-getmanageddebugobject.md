---
title: IDebugObject::GetManagedDebugObject |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6c7b416ca9af4279e11cabbbf880a73891059df6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31113217"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
偵錯引擎的位址空間中建立受管理物件的複本。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 [out]傳回[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)物件，代表新建立的 managed 的物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。 如果這個傳回 E_FAIL [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)不代表 managed 實值類別的執行個體。  
  
## <a name="remarks"></a>備註  
 這[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)物件必須代表 managed 實值類別的執行個體，例如`System.Decimal`執行個體。 所需的本機複本呼叫的額外負荷[評估](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)也會刪除。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)