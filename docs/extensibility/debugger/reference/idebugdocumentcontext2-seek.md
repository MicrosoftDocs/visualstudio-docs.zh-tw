---
title: IDebugDocumentContext2::Seek |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::Seek
helpviewer_keywords:
- IDebugDocumentContext2::Seek
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 85ab2a7d81fb2c4b0d9963c57d7c85bdb9d5515c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54974915"
---
# <a name="idebugdocumentcontext2seek"></a>IDebugDocumentContext2::Seek
以指定數目的陳述式或字行中移動的文件內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Seek(   
   int                      nCount,  
   IDebugDocumentContext2** ppDocContext  
);  
```  
  
```cpp  
int Seek(   
   int                        nCount,  
   out IDebugDocumentContext2 ppDocContext  
);  
```  
  
#### <a name="parameters"></a>參數  
 `nCount`  
 [in]陳述式或移動，根據文件內容的程式行數目。  
  
 `ppDocContext`  
 [out]傳回新[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)物件做為新的位置。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)