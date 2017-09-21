---
title: "IDebugThread2::EnumFrameInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::EnumFrameInfo"
helpviewer_keywords: 
  - "IDebugThread2::EnumFrameInfo"
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThread2::EnumFrameInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取此執行緒的堆疊框架的清單。  
  
## 語法  
  
```cpp#  
HRESULT EnumFrameInfo (   
   FRAMEINFO_FLAGS        dwFieldSpec,  
   UINT                   nRadix,  
   IEnumDebugFrameInfo2** ppEnum  
);  
```  
  
```c#  
int EnumFrameInfo (   
   enum_FRAMEINFO_FLAGS     dwFieldSpec,  
   uint                     nRadix,  
   out IEnumDebugFrameInfo2 ppEnum  
);  
```  
  
#### 參數  
 `dwFieldSpec`  
 \[in\]從的旗標組合[FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)指定的那一個欄位的列舉型別[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構是在填寫。  指定`FIF_FUNCNAME_FORMAT`成單一字串格式化的函式名稱的旗標。  
  
 `nRadix`  
 \[in\]格式化數字的資訊，列舉值中使用的基數。  
  
 `ppEnum`  
 \[\] out傳回[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)物件，其中包含一份[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構描述的堆疊框架。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 在執行緒框架列舉順序的情況下，先列舉 「 目前的框架與最後一個列舉最舊的框架。  
  
## 請參閱  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)