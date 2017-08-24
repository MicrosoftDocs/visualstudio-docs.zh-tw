---
title: IEnumDebugThreads2::Skip | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugThreads2::Skip
helpviewer_keywords:
- IEnumDebugThreads2::Skip
ms.assetid: eab068d4-1f8d-44cd-bc54-92a10fe23de6
caps.latest.revision: 9
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
ms.sourcegitcommit: ff8ecec19f8cab04ac2190f9a4a995766f1750bf
ms.openlocfilehash: 17caa5435c825a1a603bae815dba4772bef69a86
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="ienumdebugthreads2skip"></a>IEnumDebugThreads2::Skip
Skips over the specified number of elements.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```cs  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `celt`  
 [in] Number of elements to skip.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`. Returns `S_FALSE` if `celt` is greater than the number of remaining elements; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 If `celt` specifies a value greater than the number of remaining elements, the enumeration is set to the end and `S_FALSE` is returned.  
  
## <a name="see-also"></a>See Also  
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
