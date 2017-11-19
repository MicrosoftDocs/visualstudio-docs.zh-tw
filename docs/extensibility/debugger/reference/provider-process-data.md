---
title: "PROVIDER_PROCESS_DATA |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PROVIDER_PROCESS_DATA
helpviewer_keywords: PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ce3405a46503af2419006d1d408f405726a03259
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="providerprocessdata"></a>PROVIDER_PROCESS_DATA
此結構提供的電腦上執行的處理序的資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct tagPROVIDER_PROCESS_DATA {  
   PROVIDER_FIELDS    Fields;  
   PROGRAM_NODE_ARRAY ProgramNodes;  
   BOOL               fIsDebuggerPresent;  
} PROVIDER_PROCESS_DATA;  
```  
  
```csharp  
public struct PROVIDER_PROCESS_DATA {  
   public uint               Fields;  
   public PROGRAM_NODE_ARRAY ProgramNodes;  
   public int                fIsDebuggerPresent;  
}  
```  
  
## <a name="members"></a>成員  
 欄位  
 從旗標的組合[PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)列舉，指出哪些欄位會填入。  
  
 ProgramNodes  
 A [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)結構，其中包含程式節點的陣列。  
  
 fIsDebuggerPresent  
 非零 (`TRUE`) 如果[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]偵錯工具正在執行，零 (`FALSE`) 如果不是。  
  
## <a name="remarks"></a>備註  
 此結構會傳遞至[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)填滿其中的方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)   
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)