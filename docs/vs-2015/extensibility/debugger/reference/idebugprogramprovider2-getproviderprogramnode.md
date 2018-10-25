---
title: IDebugProgramProvider2::GetProviderProgramNode |Microsoft Docs
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
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 01349617bfb0ad1ecec2a0825831b79752eea049
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921741"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

擷取針對特定程式的 [程式] 節點。  
  
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
|`PFLAG_REMOTE_PORT`|呼叫端在遠端電腦上執行。|  
|`PFLAG_DEBUGGEE`|呼叫端目前正在偵錯 （每個節點會傳回封送處理的其他資訊）。|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|已附加至呼叫端，但不是啟動偵錯工具。|  
  
 `pPort`  
 [in]呼叫處理序的連接埠上執行。  
  
 `processId`  
 [in][AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構包含該程式處理序的識別碼有問題。  
  
 `guidEngine`  
 [in]（如果有的話） 的程式附加到偵錯引擎的 GUID。  
  
 `programId`  
 [in]要取得 [程式] 節點的程式識別碼。  
  
 `ppProgramNode`  
 [out][IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件，表示要求的程式 節點。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

