---
title: IDebugMemoryContext2::Compare |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
caps.latest.revision: 14
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f96ac8409a5aff3868f33f7ed987a6cc237ba5ea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
比較每個內容中的比較旗標，傳回的第一個符合之內容的索引所指示的方式在給定陣列中的記憶體內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Compare(   
   CONTEXT_COMPARE        compare,  
   IDebugMemoryContext2** rgpMemoryContextSet,  
   DWORD                  dwMemoryContextSetLen,  
   DWORD*                 pdwMemoryContext  
);  
```  
  
```csharp  
int Compare(  
   enum_CONTEXT_COMPARE   compare,   
   IDebugMemoryContext2[] rgpMemoryContextSet,   
   uint                   dwMemoryContextSetLen,   
   out uint               pdwMemoryContext  
);  
```  
  
#### <a name="parameters"></a>參數  
 `compare`  
 [in]中的值[CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)列舉，可判斷的比較類型。  
  
 `rgpMemoryContextSet`  
 [in]若要參考的陣列[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)要比較的物件。  
  
 `dwMemoryContextSetLen`  
 [in]中的內容數目`rgpMemoryContextSet`陣列。  
  
 `pdwMemoryContext`  
 [out]會傳回滿足比較的第一個記憶體內容索引。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 傳回`E_COMPARE_CANNOT_COMPARE`如果無法比較兩個內容。  
  
## <a name="remarks"></a>備註  
 偵錯引擎 (DE) 並沒有支援所有類型的比較，但必須至少都支援`CONTEXT_EQUAL`， `CONTEXT_LESS_THAN`，`CONTEXT_GREATER_THAN`和`CONTEXT_SAME_SCOPE`。  
  
## <a name="see-also"></a>請參閱  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)