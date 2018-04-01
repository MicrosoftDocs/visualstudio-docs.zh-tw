---
title: IDebugObject2::GetICorDebugValue |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugObject2::GetICorDebugValue
helpviewer_keywords:
- IDebugObject2::GetICorDebugValue method
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5b28e0cd6d66479479dbdb51825e0804abab06be
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobject2geticordebugvalue"></a>IDebugObject2::GetICorDebugValue
取得 managed 程式碼物件，代表與此物件相關聯的值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppUnk`  
 [out]`IUnknown`介面，表示此別名。 這個介面可以查詢`ICorDebugValue`介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 `ICorDebugValue`物件是代表值的通用語言執行平台介面。  
  
## <a name="see-also"></a>請參閱  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)