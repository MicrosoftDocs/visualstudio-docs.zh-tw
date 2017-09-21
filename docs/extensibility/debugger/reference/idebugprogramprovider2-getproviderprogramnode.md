---
title: "IDebugProgramProvider2::GetProviderProgramNode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2::GetProviderProgramNode"
helpviewer_keywords: 
  - "IDebugProgramProvider2::GetProviderProgramNode"
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProgramProvider2::GetProviderProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取特定程式的 \[程式\] 節點。  
  
## 語法  
  
```cpp  
HRESULT GetProviderProgramNode(  
   PROVIDER_FLAGS       Flags,  
   IDebugDefaultPort2*  pPort,  
   AD_PROCESS_ID        processId,  
   REFGUID              guidEngine,  
   UINT64               programId,  
   IDebugProgramNode2** ppProgramNode  
);  
```  
  
```c#  
int GetProviderProgramNode(  
   enum_PROVIDER_FLAGS    Flags,  
   IDebugDefaultPort2     pPort,  
   AD_PROCESS_ID          ProcessId,  
   ref Guid               guidEngine,  
   ulong                  programId,  
   out IDebugProgramNode2 ppProgramNode  
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
  
 `pPort`  
 \[in\]呼叫的處理程序的連接埠上執行。  
  
 `processId`  
 \[in\][AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構保留包含該程式的處理序 ID 有問題。  
  
 `guidEngine`  
 \[in\]\(如果有的話\)，程式附加到偵錯引擎的 GUID。  
  
 `programId`  
 \[in\]要取得程式\] 節點的程式識別碼。  
  
 `ppProgramNode`  
 \[\] out[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件，表示所要求的程式\] 節點。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER\_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)