---
title: "IDebugProcess2::GetInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::GetInfo"
helpviewer_keywords: 
  - "IDebugProcess2::GetInfo"
ms.assetid: 46021dce-bb97-46c3-b0cc-e5b3b68acc35
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProcess2::GetInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得處理序的描述。  
  
## 語法  
  
```cpp#  
HRESULT GetInfo(  
   PROCESS_INFO_FIELDS  Fields,  
   PROCESS_INFO*        pProcessInfo  
);  
```  
  
```c#  
int GetInfo(  
   enum_PROCESS_INFO_FIELDS  Fields,  
   PROCESS_INFO[]            pProcessInfo  
);  
```  
  
#### 參數  
 `Fields`  
 \[in\]從值的組合[PROCESS\_INFO\_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)指定的那一個欄位的列舉型別`pProcessInfo`參數是要在 \[填滿。  
  
 `pProcessInfo`  
 \[\] outA [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)會被填入的處理程序描述的結構。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [PROCESS\_INFO\_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)