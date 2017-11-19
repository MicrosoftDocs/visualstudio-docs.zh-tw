---
title: "IDebugProgramProvider2::GetProviderProcessData |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords: IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ae46cd5e90b4cdd23b0c7fafa147c43805974283
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
擷取從指定的處理序中執行程式的清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetProviderProcessData(  
   PROVIDER_FLAGS         Flags,  
   IDebugDefaultPort2*    pPort,  
   AD_PROCESS_ID          processId,  
   CONST_GUID_ARRAY       EngineFilter,  
   PROVIDER_PROCESS_DATA* pProcess  
);  
```  
  
```csharp  
int GetProviderProcessData(  
   enum_PROVIDER_FLAGS     Flags,  
   IDebugDefaultPort2      pPort,  
   AD_PROCESS_ID           ProcessId,  
   CONST_GUID_ARRAY        EngineFilter,  
   PROVIDER_PROCESS_DATA[] pProcess  
);  
```  
  
#### <a name="parameters"></a>參數  
 `Flags`  
 [in]從旗標的組合[PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)列舉型別。 此呼叫一般會在下列旗標：  
  
|旗標|說明|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|呼叫端遠端電腦上執行。|  
|`PFLAG_DEBUGGEE`|呼叫端目前所偵錯 （封送處理的其他資訊將會傳回每個節點）。|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|已附加至呼叫端，但不是會啟動偵錯工具。|  
|`PFLAG_GET_PROGRAM_NODES`|要傳回呼叫端要求程式節點的清單。|  
  
 `pPort`  
 [in]呼叫處理序的連接埠上執行。  
  
 `processId`  
 [in][AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構包含該程式處理序的識別碼有問題。  
  
 `EngineFilter`  
 [in]對於指派給偵錯此處理序 （這些會用來篩選實際傳回根據提供的引擎的支援; 如果未不指定任何引擎，則會傳回所有程式的程式） 的偵錯引擎的 Guid 陣列。  
  
 `pProcess`  
 [out]A [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)會填入所要求的資訊的結構。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法通常會呼叫處理程序來取得該處理序中執行的程式清單。 傳回的資訊是一份[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)