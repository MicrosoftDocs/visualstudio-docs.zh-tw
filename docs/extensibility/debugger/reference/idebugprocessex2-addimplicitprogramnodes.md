---
title: IDebugProcessEx2::AddImplicitProgramNodes |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 22f6cadaa88d6cc87ec70451d9da850cd49b7753
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31117016"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
這個方法會將每個偵錯引擎 (DE) 指定程式節點。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```csharp  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### <a name="parameters"></a>參數  
 `guidLaunchingEngine`  
 [in]`GUID`的 DE 是用來啟動程式 （並假設加入自己的程式節點）。  
  
 `rgguidSpecificEngines`  
 [in]陣列`GUID`之 DEs 節點將會加入的程式。  
  
 `celtSpecificEngines`  
 [in]數目`GUID`中`rgguidSpecificEngines`陣列。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 [程式節點](../../../extensibility/debugger/program-nodes.md)將會加入每個 DE 列於`rgguidSpecificEngines`— 排除啟動引擎 (中所指定`guidLaunchingEngine`)，它會假設它會啟動程式時，將其本身的程式節點。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [程式節點](../../../extensibility/debugger/program-nodes.md)