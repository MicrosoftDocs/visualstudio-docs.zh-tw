---
title: "IDebugBinder::GetMemoryContext |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder::GetMemoryContext
helpviewer_keywords: IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f8765bcef2d1c9c97a8180cf75acc1d0581990c7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
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