---
title: IDebugProperty2::GetDerivedMostProperty |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ca1a90cff0ee96524b13067f32eadd176ad590ee
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55030349"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
取得屬性的最具衍生性屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDerivedMostProperty (   
   IDebugProperty2** ppDerivedMost  
);  
```  
  
```csharp  
int GetDerivedMostProperty (   
   out IDebugProperty2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppDerivedMost`  
 [out]傳回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件，表示最具衍生性的屬性。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則會傳回錯誤碼。 傳回`S_GETDERIVEDMOST_NO_DERIVED_MOST`若未最具衍生性的屬性來擷取。  
  
## <a name="remarks"></a>備註  
 例如，如果這個屬性會描述該物件會實作`ClassRoot`這是實際的具現化，但`ClassDerived`衍生自`ClassRoot`，則這個方法會傳回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件描述`ClassDerived`物件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)