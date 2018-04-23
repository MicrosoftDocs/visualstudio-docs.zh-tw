---
title: IDebugPointerObject::SetBytes |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: a8234117d7965c4f2e471855d39ed0c3cee1f88c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
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
 [in]以位元組為單位，從指向物件的開始位移。  
  
 `dwCount`  
 [in]若要設定的位元組數目。  
  
 `pBytes`  
 [in]代表新值的位元組陣列。 這個值會儲存的物件中指定位移處開始。  
  
 `pdwBytes`  
 [out]傳回實際設定的位元組數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果這個方法會使用指標所表示的這[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)指向基本型別或基本型別 （也就是可以由簡單的一連串的位元組陣列） 的簡單陣列。 這`IDebugPointerObject`物件不可為 null 參考 （它必須指向記憶體中的位址）。  
  
## <a name="see-also"></a>另請參閱  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)