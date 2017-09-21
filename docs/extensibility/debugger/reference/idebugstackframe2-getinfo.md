---
title: "IDebugStackFrame2::GetInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetInfo"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetInfo"
ms.assetid: 19c6870b-b94e-453c-bf19-82ce95b79d26
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得堆疊框架的描述。  
  
## 語法  
  
```cpp#  
HRESULT GetInfo (   
   FRAMEINFO_FLAGS dwFieldSpec,  
   UINT            nRadix,  
   FRAMEINFO*      pFrameInfo  
);  
```  
  
```c#  
int GetInfo (   
   enum_FRAMEINFO_FLAGS dwFieldSpec,  
   uint                 nRadix,  
   FRAMEINFO[]          pFrameInfo  
);  
```  
  
#### 參數  
 `dwFieldSpec`  
 \[in\]從的旗標組合[FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)指定的那一個欄位的列舉型別`pFrameInfo`參數是要在 \[填滿。  
  
 `nRadix`  
 \[in\]要用於格式化數字的任何資訊基數。  
  
 `pFrameInfo`  
 \[\] outA [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)會被填入的堆疊框架的描述的結構。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)