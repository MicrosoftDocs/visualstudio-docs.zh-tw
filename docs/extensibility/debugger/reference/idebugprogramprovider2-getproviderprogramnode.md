---
title: IDebugProgramProvider2::GetProviderProgramNode |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
caps.latest.revision: 13
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 150b2bc744329078319a3bf5d36dc0a97201c0c4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
擷取針對特定程式的程式節點。  
  
## <a name="syntax"></a>語法  
  
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
  
#### <a name="parameters"></a>參數  
 `Flags`  
 [in]從旗標的組合[PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)列舉型別。 此呼叫一般會在下列旗標：  
  
|旗標|描述|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|呼叫端遠端電腦上執行。|  
|`PFLAG_DEBUGGEE`|呼叫端目前所偵錯 （封送處理的其他資訊將會傳回每個節點）。|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|已附加至呼叫端，但不是會啟動偵錯工具。|  
  
 `pPort`  
 [in]呼叫處理序的連接埠上執行。  
  
 `processId`  
 [in][AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構包含該程式處理序的識別碼有問題。  
  
 `guidEngine`  
 [in]該程式附加到 （如果有的話） 的偵錯引擎的 GUID。  
  
 `programId`  
 [in]要取得程式節點之程式的識別碼。  
  
 `ppProgramNode`  
 [out][IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件，表示要求的程式節點。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)