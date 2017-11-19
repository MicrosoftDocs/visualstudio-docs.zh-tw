---
title: "IDebugProperty2::SetValueAsReference |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::SetValueAsReference
helpviewer_keywords: IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d27a087c67401e90e8a3f4629c27d1255d0ade75
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
設定這個屬性的值，指定參考的值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetValueAsReference(  
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```csharp  
int SetValueAsReference(  
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### <a name="parameters"></a>參數  
 `rgpArgs`  
 [in]傳遞至 managed 程式碼屬性 setter 引數的陣列。 如果屬性 setter 不接受引數，或如果此[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件不是指這類屬性 setter`rgpArgs`應為 null 的值。 此參數通常是 null 值。  
  
 `dwArgCount`  
 [in]中的引數數目`rgpArgs`陣列。  
  
 `pValue`  
 [in]中的表單的參考， [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件，用來設定這個屬性的值。  
  
 `dwTimeout`  
 [in]設定值，以毫秒為單位的時間長度。 一般的值是`INFINITE`。 這會影響任何可能評估需要花費的時間的長度。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則會傳回錯誤，程式碼，通常是下列其中之一：  
  
|錯誤|說明|  
|-----------|-----------------|  
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|不支援的值設定的參考。|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|無法設定值，因為這個屬性會參考給方法。|  
|`E_SETVALUE_VALUE_IS_READONLY`|值是唯讀，且無法設定。|  
|`E_NOTIMPL`|未實作方法。|  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)