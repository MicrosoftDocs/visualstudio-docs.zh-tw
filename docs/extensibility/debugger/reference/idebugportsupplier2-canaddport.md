---
title: "IDebugPortSupplier2::CanAddPort | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2::CanAddPort"
helpviewer_keywords: 
  - "IDebugPortSupplier2::CanAddPort"
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPortSupplier2::CanAddPort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

請確認連接埠提供者可以新增新的連接埠。  
  
## 語法  
  
```cpp#  
HRESULT CanAddPort(   
   void   
);  
```  
  
```c#  
int CanAddPort();  
```  
  
## 傳回值  
 如果可以加入通訊埠，會傳回`S_OK`。 否則，會傳回`S_FALSE` ，表示沒有連接埠可以新增到此連接埠提供者。  
  
## 備註  
 呼叫這個方法之前呼叫[下列](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)連接埠，以及加入它，可能耗時的作業，會建立第二個方法的方法。  
  
## 請參閱  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [下列](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)