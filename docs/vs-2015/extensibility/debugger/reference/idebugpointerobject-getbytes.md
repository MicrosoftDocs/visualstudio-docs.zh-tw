---
title: IDebugPointerObject::GetBytes |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
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
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3648c180b1bbd96c02c4f00276c0b90d6806b2e9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497089"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugPointerObject::GetBytes](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugpointerobject-getbytes)。  
  
取得指向為一系列的連續位元組的值。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 [in]以位元組為單位，從所指向之物件的開始位移。  
  
 `dwCount`  
 [in]要擷取的位元組數目。  
  
 `pBytes`  
 [in、 out]指向會填入值以一系列的連續的位元組陣列，從物件的指定位移處開始。  
  
 `pdwBytes`  
 [out]傳回實際擷取的位元組的數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;否則，傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 如果使用這個方法的指標，表示這個[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)指向基本型別或簡單基本型別 （也就是可以由簡單的一連串的位元組陣列） 的陣列。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)   
 [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)

