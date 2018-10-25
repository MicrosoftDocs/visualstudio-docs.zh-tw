---
title: PROVIDER_PROCESS_DATA |Microsoft Docs
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
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fa72a59725bcfc425b6d5cb63b2d373c7b183edd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866359"
---
# <a name="providerprocessdata"></a>PROVIDER_PROCESS_DATA
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此結構會提供在電腦上執行的處理序的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 非零值 (`TRUE`) 如果[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]偵錯工具正在執行，零 (`FALSE`) 如果不是。  
  
## <a name="remarks"></a>備註  
 此結構會傳遞至[GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)填滿其中的方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)   
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)

