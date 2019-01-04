---
title: IDebugPointerObject::SetBytes |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c6cf8fff235a3148cc53bda40e4b43a52ac75005
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53960679"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
設定從一系列的連續位元組所指向的值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int SetBytes(  
   uint     dwStart,   
   uint     dwCount,   
   byte[]   pBytes,   
   out uint pdwBytes  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwStart`  
 [in]以位元組為單位，從所指向之物件的開始位移。  
  
 `dwCount`  
 [in]若要設定的位元組數目。  
  
 `pBytes`  
 [in]代表新值的位元組陣列。 這個值會儲存成物件，指定位移處開始。  
  
 `pdwBytes`  
 [out]傳回的位元組數目可實際設定。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果使用這個方法的指標，表示這個[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)指向基本型別或簡單基本型別 （也就是可以由簡單的一連串的位元組陣列） 的陣列。 這`IDebugPointerObject`物件不可以是 null 參考 （它必須指向記憶體中的位址）。  
  
## <a name="see-also"></a>另請參閱  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)