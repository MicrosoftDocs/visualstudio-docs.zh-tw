---
title: IDebugProgramPublisher2::UnpublishProgram | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
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
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 85f0287aace939e3d552a6d2c0289cc457c6a3fd
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
Makes a program unavailable to be debugged.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT UnpublishProgram(  
   IUnknown* pDebuggeeInterface  
);  
```  
  
```csharp  
int UnpublishProgram(  
   object pDebuggeeInterface  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `pDebuggeeInterface`  
 [in] An `IUnknown` interface to the program. This is the same value supplied to the [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) method and uniquely identifies the program being removed (that is, it is used as a cookie).  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 To make a program available to the debug engines and session debug manager, use the [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) method.  
  
## <a name="see-also"></a>See Also  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
