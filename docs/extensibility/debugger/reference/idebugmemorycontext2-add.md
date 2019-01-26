---
title: IDebugMemoryContext2::Add | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9625bcdc69d4df157f4309ae24d4baafcda1264a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54974340"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
將指定的值加入至目前的內容，並傳回新的內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Add(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int Add(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwCount`  
 [in]要加入至目前內容的值。  
  
 `ppMemCxt`  
 [out]傳回新[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 記憶體內容會是地址，以便將值加入位址會產生新的位址，需要新的內容介面。  
  
 這個方法必須永遠會產生新的內容，即使產生的位址不在此內容相關聯的記憶體空間。 唯一的例外是，如果沒有記憶體可配置給新的內容，或如果`ppMemCxt`為 null 的值 （這是錯誤）。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)