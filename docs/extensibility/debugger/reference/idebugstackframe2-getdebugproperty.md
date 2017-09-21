---
title: "IDebugStackFrame2::GetDebugProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetDebugProperty"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetDebugProperty"
ms.assetid: 02c2fa04-1424-4bca-9936-feaecd2afab6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetDebugProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得堆疊框架的屬性描述。  
  
## 語法  
  
```cpp#  
HRESULT GetDebugProperty (   
   IDebugProperty2** ppDebugProp  
);  
```  
  
```c#  
int GetDebugProperty (   
   out IDebugProperty2 ppDebugProp  
);  
```  
  
#### 參數  
 `ppDebugProp`  
 \[\] out傳回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件，描述此堆疊框架的內容。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 呼叫[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)與適當的篩選器的方法可以擷取區域變數、 方法參數、 暫存器和堆疊框架相關聯"this"指標。  
  
## 請參閱  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)