---
title: "IDebugProcess2::GetPhysicalProcessId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::GetPhysicalProcessId"
helpviewer_keywords: 
  - "IDebugProcess2::GetPhysicalProcessId"
ms.assetid: 77da6e10-75af-4308-97dd-c44416ca52d7
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::GetPhysicalProcessId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得系統處理序識別項。  
  
## 語法  
  
```cpp#  
HRESULT GetPhysicalProcessId(  
   AD_PROCESS_ID* pdwProcessId  
);  
```  
  
```c#  
int GetPhysicalProcessId(  
   AD_PROCESS_ID[] pdwProcessId  
);  
```  
  
#### 參數  
 `pdwProcessId`  
 \[\] out[AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)會填入這些系統處理序識別元資訊的結構。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)