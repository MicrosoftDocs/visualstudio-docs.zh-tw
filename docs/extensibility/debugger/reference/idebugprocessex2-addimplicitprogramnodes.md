---
title: IDebugProcessEx2::AddImplicitProgramNodes | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
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
ms.sourcegitcommit: ff8ecec19f8cab04ac2190f9a4a995766f1750bf
ms.openlocfilehash: 43855b6131194f2f84d18c005f7cf5688257121e
ms.contentlocale: zh-tw
ms.lasthandoff: 08/24/2017

---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
This method adds a program node for each debug engine (DE) specified.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```cs  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `guidLaunchingEngine`  
 [in] The `GUID` of a DE that is to be used to launch programs (and is assumed to add its own program nodes).  
  
 `rgguidSpecificEngines`  
 [in] Array of `GUID`s of DEs for which program nodes will be added.  
  
 `celtSpecificEngines`  
 [in] The number of `GUID`s in the `rgguidSpecificEngines` array.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="remarks"></a>Remarks  
 [Program Nodes](../../../extensibility/debugger/program-nodes.md) will be added for each DE listed in `rgguidSpecificEngines`—excluding the launching engine (as given in `guidLaunchingEngine`), which is assumed to add its own program node when it launches a program.  
  
## <a name="see-also"></a>See Also  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Program Nodes](../../../extensibility/debugger/program-nodes.md)
