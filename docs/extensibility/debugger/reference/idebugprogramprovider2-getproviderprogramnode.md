---
title: IDebugProgramProvider2::GetProviderProgramNode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
caps.latest.revision: 13
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
ms.openlocfilehash: 21543a7b9d6a26998045cf4f42354085f622fb56
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
Retrieves the program node for a specific program.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetProviderProgramNode(  
   PROVIDER_FLAGS       Flags,  
   IDebugDefaultPort2*  pPort,  
   AD_PROCESS_ID        processId,  
   REFGUID              guidEngine,  
   UINT64               programId,  
   IDebugProgramNode2** ppProgramNode  
);  
```  
  
```csharp  
int GetProviderProgramNode(  
   enum_PROVIDER_FLAGS    Flags,  
   IDebugDefaultPort2     pPort,  
   AD_PROCESS_ID          ProcessId,  
   ref Guid               guidEngine,  
   ulong                  programId,  
   out IDebugProgramNode2 ppProgramNode  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `Flags`  
 [in] A combination of flags from the [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) enumeration. The following flags are typical for this call:  
  
|Flag|Description|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|Caller is running on remote machine.|  
|`PFLAG_DEBUGGEE`|Caller is currently being debugged (additional information about marshalling will be returned for each node).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Caller was attached to but not launched by the debugger.|  
  
 `pPort`  
 [in] The port the calling process is running on.  
  
 `processId`  
 [in] An [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) structure holding the ID of the process that contains the program in question.  
  
 `guidEngine`  
 [in] GUID of the debug engine that the program is attached to (if any).  
  
 `programId`  
 [in] ID of the program for which to get the program node.  
  
 `ppProgramNode`  
 [out] An [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) object representing the requested program node.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## <a name="see-also"></a>See Also  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
