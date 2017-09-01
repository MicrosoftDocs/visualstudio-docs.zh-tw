---
title: IDebugDocumentContext2::Compare | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: 10
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
ms.openlocfilehash: f9feb2c2d73bb840d28e44ad1d9817136fc7a163
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Compares this document context to a given array of document contexts.  
  
## <a name="syntax"></a>Syntax  
  
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
  
#### <a name="parameters"></a>Parameters  
 `compare`  
 [in] A value from the [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) enumeration that specifies the type of comparison.  
  
 `rgpDocContextSet`  
 [in] An array of [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objects that represent the document contexts being compared to.  
  
 `dwDocContextSetLen`  
 [in] The length of the array of document contexts to compare.  
  
 `pdwDocContext`  
 [out] Returns the index into the `rgpDocContextSet` array of the first document context that satisfies the comparison.  
  
## <a name="return-value"></a>Return Value  
 Returns `S_OK` if a match was found. Returns `S_FALSE` if no match was found. Otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 The [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objects that are passed in the array must be implemented by the same debug engine that implements the `IDebugDocumentContext2` object being called on; otherwise, the comparison is not valid.  
  
## <a name="see-also"></a>See Also  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)
