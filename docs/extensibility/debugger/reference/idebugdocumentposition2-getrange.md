---
title: IDebugDocumentPosition2::GetRange | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
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
ms.openlocfilehash: 61d0c60f6f7a7e268ad026800e66bd7fee7a9a55
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Gets the range for this document position.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pBegPosition`  
 [in, out] A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) structure that is filled in with the starting position. Set this argument to a null value if this information is not needed.  
  
 `pEndPosition`  
 [in, out] A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) structure that is filled in with the ending position. Set this argument to a null value if this information is not needed.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 The range specified in a document position for a location breakpoint is used by the debug engine (DE) to search ahead for a statement that actually contributes code. For example, consider the following code:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 Line 5 contributes no code to the program being debugged. If the debugger that sets the breakpoint on line 5 wants the DE to search forward a certain amount for the first line that contributes code, the debugger would specify a range that includes additional candidate lines where a breakpoint might be properly placed. The DE would then search forward through those lines until it found a line that could accept a breakpoint.  
  
## <a name="see-also"></a>See Also  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
