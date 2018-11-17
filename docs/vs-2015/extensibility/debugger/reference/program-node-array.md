---
title: PROGRAM_NODE_ARRAY |Microsoft Docs
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
- PROGRAM_NODE_ARRAY
helpviewer_keywords:
- PROGRAM_NODE_ARRAY structure
ms.assetid: 8eeea600-eda5-4b7c-868a-0b86d177b0a5
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b04e784db657567d1b6d88c1d3a1d7f882d663a4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779212"
---
# <a name="programnodearray"></a>PROGRAM_NODE_ARRAY
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

包含描述感興趣的程式物件的陣列。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct tagPROGRAM_NODE_ARRAY {  
   DWORD                dwCount;  
   IDebugProgramNode2** Members;  
} PROGRAM_NODE_ARRAY;  
```  
  
```csharp  
public struct tagPROGRAM_NODE_ARRAY {  
   public uint                 dwCount;  
   public IDebugProgramNode2[] Members;  
}  
```  
  
## <a name="members"></a>成員  
 dwCount  
 中的物件數目`Members`陣列。  
  
 成員  
 陣列[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件，描述要求的程式。  
  
## <a name="remarks"></a>備註  
 此結構是的一部分[PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)結構會接著會填入呼叫[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)

