---
title: "IDebugCoreServer2::EnumPorts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer2::EnumPorts"
helpviewer_keywords: 
  - "IDebugCoreServer2::EnumPorts"
ms.assetid: 3d98dfd0-614f-4d68-90c6-8a9b9cab66f1
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugCoreServer2::EnumPorts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取一份所有可用的連接埠。  
  
## 語法  
  
```cpp#  
HRESULT EnumPorts(   
   IEnumDebugPorts2** ppEnum  
);  
```  
  
```c#  
int EnumPorts(   
   out IEnumDebugPorts2 ppEnum  
);  
```  
  
#### 參數  
 `ppEnum`  
 \[\] out傳回[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)物件，其中包含一份所有連接埠的供應商提供的所有連接埠。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)