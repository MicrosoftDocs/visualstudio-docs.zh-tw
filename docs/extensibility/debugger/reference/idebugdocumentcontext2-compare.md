---
title: IDebugDocumentContext2::Compare |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 550695aa52f1c913b25fc56975eb5c6e36b4c091
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
比較指定之陣列的文件內容的此文件內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```csharp  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### <a name="parameters"></a>參數  
 `compare`  
 [in]中的值[DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)列舉，指定的比較類型。  
  
 `rgpDocContextSet`  
 [in]陣列[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)表示所比較的文件內容的物件。  
  
 `dwDocContextSetLen`  
 [in]將文件內容進行比較之陣列的長度。  
  
 `pdwDocContext`  
 [out]傳回的索引`rgpDocContextSet`滿足比較的第一個文件內容的陣列。  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`如果找不到相符項目。 傳回`S_FALSE`如果找不到相符項目。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)傳遞陣列中的物件必須實作相同的偵錯引擎，可實作`IDebugDocumentContext2`物件呼叫開啟; 否則比較無效。  
  
## <a name="see-also"></a>請參閱  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)