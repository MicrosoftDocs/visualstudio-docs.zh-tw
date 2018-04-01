---
title: IDebugMemoryContext2::Subtract |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ef3f851b48de363e5d63afad4d993d1e693af6fe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
減去指定的值，從目前的內容，並傳回新的內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Subtract(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int Subtract(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwCount`  
 [in]要遞減的記憶體位元組數目。  
  
 `ppMemCxt`  
 [out]傳回新[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 記憶體內容會是一個位址，因此減去位址的值會產生需要新的內容介面的新位址。  
  
 這個方法必須永遠會產生新的內容，即使產生的位址超出此內容相關聯的記憶體空間。 唯一的例外是，如果沒有記憶體可以配置給新的內容或`ppMemCxt`是空值 （這是錯誤）。  
  
## <a name="see-also"></a>請參閱  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)