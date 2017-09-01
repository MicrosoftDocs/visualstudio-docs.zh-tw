---
title: IEnumDebugFields::GetCount | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugFields::GetCount
helpviewer_keywords:
- IEnumDebugFields::GetCount method
ms.assetid: 3f471b40-4db3-49f7-b504-58b2476eef74
caps.latest.revision: 7
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
ms.openlocfilehash: ce93932b56d13afc7ea5bb5c3b16cd42a1219470
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="ienumdebugfieldsgetcount"></a>IEnumDebugFields::GetCount
This method returns the number of elements in the enumeration.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetCount(  
   [out] ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pcelt`  
 [out] Returns the number of elements in the enumeration.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 This method is not part of the customary COM enumeration interface which specifies that only Next, Clone, Skip, and Reset need to be implemented.  
  
## <a name="see-also"></a>See Also  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
