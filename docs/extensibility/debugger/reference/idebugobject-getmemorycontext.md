---
title: "IDebugObject::GetMemoryContext |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject::GetMemoryContext
helpviewer_keywords: IDebugObject::GetMemoryContext method
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 93f6d82b88be23b160effe1c8162648132f461c5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugobjectgetmemorycontext"></a>IDebugObject::GetMemoryContext
取得代表值的物件位址的記憶體內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMemoryContext(   
   IDebugMemoryContext2** pContext  
);  
```  
  
```csharp  
int GetMemoryContext(  
   ref IDebugMemoryContext2 pContext  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pContext`  
 [out]傳回[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)物件，代表物件的值的位址。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 傳回的記憶體內容會指定的位址值所表示的這[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)物件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)