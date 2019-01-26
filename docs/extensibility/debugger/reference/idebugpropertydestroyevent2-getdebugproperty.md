---
title: IDebugPropertyDestroyEvent2::GetDebugProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPropertyDestroyEvent2::GetDebugProperty
helpviewer_keywords:
- IDebugPropertyDestroyEvent2::GetDebugProperty
ms.assetid: c96ae785-0ac8-4df4-8df3-15a8d7e13687
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 963a3d204841cf92423fa893413d375cfb62cfd8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54960018"
---
# <a name="idebugpropertydestroyevent2getdebugproperty"></a>IDebugPropertyDestroyEvent2::GetDebugProperty
取得要終結的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDebugProperty (   
   IDebugProperty2** ppProperty  
);  
```  
  
```csharp  
int GetDebugProperty (   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppProperty`  
 [out]傳回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件，表示要終結的屬性。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)