---
title: IDebugMemoryBytes2::WriteAt | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2479ac3948f81769ba2e73c746fd1811652aa239
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180564"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

寫入指定的記憶體，並指定位址開頭的位元組數目。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT WriteAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory  
);  
```  
  
```csharp  
int WriteAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pStartContext`  
 [in][IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)物件，指定要從何處開始寫入位元組。  
  
 `dwCount`  
 [in]要寫入的位元組數目。  
  
 `rgbMemory`  
 [in]要寫入的位元組。 這個陣列會假設為至少`dwCount`個位元組大小。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回`S_FALSE`如果並非所有位元組無法寫入，或傳回錯誤碼 (通常`E_FAIL`)。  
  
## <a name="remarks"></a>備註  
 如果起始位址不在所表示的 [記憶體] 視窗內[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)物件，就會發生任何寫入和錯誤碼的`E_FAIL`傳回 — 即使要寫入的數量與記憶體空間重疊。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
