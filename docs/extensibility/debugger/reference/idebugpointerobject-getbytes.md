---
title: IDebugPointerObject::GetBytes |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5e07ab129cb49ffba892ba3b681e6239d4477256
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
取得為一系列的連續的位元組所指向的值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int GetBytes(  
   uint       dwStart,   
   uint       dwCount,   
   out byte[] pBytes,   
   out uint   pdwBytes  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwStart`  
 [in]以位元組為單位，從指向物件的開始位移。  
  
 `dwCount`  
 [in]要擷取的位元組數目。  
  
 `pBytes`  
 [in、 out]指向填入為一系列的連續的位元組值陣列，從物件的指定位移處開始。  
  
 `pdwBytes`  
 [out]傳回實際擷取的位元組的數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果這個方法會使用指標所表示的這[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)指向基本型別或基本型別 （也就是可以由簡單的一連串的位元組陣列） 的簡單陣列。  
  
## <a name="see-also"></a>請參閱  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)   
 [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)