---
title: IDebugBinder::GetMemoryContext |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 18049e9f0800cc5c2bc0b53e53915a96eebb1718
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
這個方法會將記憶體內容物件位置或記憶體位址。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMemoryContext(   
   IDebugField*           pField,  
   DWORD                  dwConstant,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int GetMemoryContext(  
   IDebugField              pField,   
   uint                     dwConstant,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pField`  
 [in][IDebugField](../../../extensibility/debugger/reference/idebugfield.md)描述要尋找的物件。 如果`NULL`，然後使用`dwConstant`改為。  
  
 `dwConstant`  
 [in]常數的記憶體位址，例如 0x5000。  
  
 `ppMemCxt`  
 [out]傳回[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)代表物件的位址或記憶體中的位址的介面。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)