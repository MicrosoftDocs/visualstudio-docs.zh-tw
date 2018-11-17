---
title: IDebugMemoryContext2::Subtract |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 70ed92b6098a736baf3bfa927a368f38a9ba01a7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721613"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

減去指定的值，從目前的內容，並傳回新的內容。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 記憶體內容會是地址，因此減去值的位址會產生新的位址，需要新的內容介面。  
  
 這個方法必須永遠會產生新的內容，即使產生的位址不在此內容相關聯的記憶體空間。 唯一的例外是，如果沒有記憶體可配置給新的內容，或如果`ppMemCxt`為 null 的值 （這是錯誤）。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

