---
title: "IDebugProgramProvider2::GetProviderProcessData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2::GetProviderProcessData"
helpviewer_keywords: 
  - "IDebugProgramProvider2::GetProviderProcessData"
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProgramProvider2::GetProviderProcessData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取與指定的處理序中執行程式的清單。  
  
## 語法  
  
```cpp  
HRESULT GetProviderProcessData(  
   PROVIDER_FLAGS         Flags,  
   IDebugDefaultPort2*    pPort,  
   AD_PROCESS_ID          processId,  
   CONST_GUID_ARRAY       EngineFilter,  
   PROVIDER_PROCESS_DATA* pProcess  
);  
```  
  
```c#  
int GetProviderProcessData(  
   enum_PROVIDER_FLAGS     Flags,  
   IDebugDefaultPort2      pPort,  
   AD_PROCESS_ID           ProcessId,  
   CONST_GUID_ARRAY        EngineFilter,  
   PROVIDER_PROCESS_DATA[] pProcess  
);  
```  
  
#### 參數  
 `Flags`  
 \[in\]從的旗標組合[PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)列舉型別。  下列旗標為這個呼叫一般項目：  
  
|旗標|描述|  
|--------|--------|  
|`PFLAG_REMOTE_PORT`|呼叫者正在遠端機器上執行。|  
|`PFLAG_DEBUGGEE`|呼叫端是否目前正在偵錯 \(每個節點會傳回封送處理的其他資訊\)。|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|已附加至呼叫端，但不是啟動偵錯工具。|  
|`PFLAG_GET_PROGRAM_NODES`|要傳回呼叫端要求程式節點的清單。|  
  
 `pPort`  
 \[in\]呼叫的處理程序的連接埠上執行。  
  
 `processId`  
 \[in\][AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構保留包含該程式的處理序 ID 有問題。  
  
 `EngineFilter`  
 \[in\]陣列的 Guid，以便指派給偵錯 \(這些將用來篩選程式，實際上會傳回根據所提供的引擎支援 ； 此程序的偵錯引擎 如果未不指定任何引擎，然後所有程式將會都傳回\)。  
  
 `pProcess`  
 \[\] outA [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md)會被填入所要求的資訊的結構。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 若要取得一份該程序中執行的程式處理程序通常呼叫這個方法。  傳回的資訊是一份[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件。  
  
## 請參閱  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST\_GUID\_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)