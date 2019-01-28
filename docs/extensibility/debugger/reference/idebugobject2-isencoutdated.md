---
title: IDebugObject2::IsEncOutdated |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c5facc3b8efed46817e99624e6b019d1498ec622
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55016131"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
這個方法會決定 編輯後繼續狀態，這個物件或父容器是否已過期。 自訂運算式評估工具不會實作這個方法，一律會傳回`E_NOTIMPL`。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsEncOutdated(  
   BOOL* pfEncOutdated  
);  
```  
  
```csharp  
int IsEncOutdated(  
   out int pfEncOutdated  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pfEncOutdated`  
 [out]非零值 (`TRUE`) 是否過期的編輯後繼續 」 狀態，零 (`FALSE`) 如果不是。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
> [!NOTE]
>  自訂運算式評估工具應該一律傳回`E_NOTIMPL`。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)