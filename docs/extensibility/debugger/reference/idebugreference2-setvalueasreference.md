---
title: IDebugReference2::SetValueAsReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd192323407b7558bd05ee12ea95ab5799a35e1e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54967530"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
設定參考，以從另一個參考的值。 保留供未來使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetValueAsReference (   
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```cpp  
int SetValueAsReference (   
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### <a name="parameters"></a>參數  
 `rgpArgs`  
 [in]陣列[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)用來判斷如何設定參考值的物件。  
  
 `dwArgCount`  
 [in]陣列中的參考數目。  
  
 `pValue`  
 [in][IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)從中設定屬性值的物件。  
  
 `dwTimeout`  
 [in]最大時間 （毫秒），這個方法返回之前等候。 使用`INFINITE`無限期等候。  
  
## <a name="return-value"></a>傳回值  
 一律傳回 `E_NOTIMPL`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)