---
title: "IDebugPortSupplier2::RemovePort | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2::RemovePort"
helpviewer_keywords: 
  - "IDebugPortSupplier2::RemovePort"
ms.assetid: f5c1fbf2-9084-46f2-a682-7db963928df2
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPortSupplier2::RemovePort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

移除連接埠。  
  
## 語法  
  
```cpp#  
HRESULT RemovePort(   
   IDebugPort2* pPort  
);  
```  
  
```c#  
int RemovePort(   
   IDebugPort2 pPort  
);  
```  
  
#### 參數  
 `pPort`  
 \[in\][IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)物件，表示要移除的連接埠。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法會移除作用中的連接埠的連接埠供應商的內部清單中的連接埠。  
  
## 請參閱  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)