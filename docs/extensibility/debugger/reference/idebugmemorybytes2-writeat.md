---
title: "IDebugMemoryBytes2::WriteAt |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 14d5aa4fa026f27f6b083d656cd5df3f8b7d7f41
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
寫入指定的記憶體，指定位址開頭的位元組數目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 [in]要寫入的位元組。 這個陣列會被假設為至少`dwCount`個位元組大小。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`如果並非所有位元組無法寫入或傳回錯誤碼 (通常`E_FAIL`)。  
  
## <a name="remarks"></a>備註  
 如果起始位址不在所表示的 [記憶體] 視窗內[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)物件，不進行任何寫入和錯誤碼的`E_FAIL`傳回 — 即使要寫入的數量重疊的記憶體空間。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
