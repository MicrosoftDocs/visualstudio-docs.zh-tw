---
title: "IDebugPortSupplier2::AddPort | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2::AddPort"
helpviewer_keywords: 
  - "IDebugPortSupplier2::AddPort"
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortSupplier2::AddPort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

新增連接埠。  
  
## 語法  
  
```cpp#  
HRESULT AddPort(   
   IDebugPortRequest2* pRequest,  
   IDebugPort2**       ppPort  
);  
```  
  
```c#  
int AddPort(   
   IDebugPortRequest2 pRequest,  
   out IDebugPort2    ppPort  
);  
```  
  
#### 參數  
 `pRequest`  
 \[in\][IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)物件，描述要加入的連接埠。  
  
 `ppPort`  
 \[\] out傳回[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)物件，表示連接埠。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法實際上會建立要求的連接埠，以及將它新增到使用中的連接埠的連接埠供應商的內部清單。  [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)可以先呼叫方法，以避免可能耗費時間的延遲。  
  
## 請參閱  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)