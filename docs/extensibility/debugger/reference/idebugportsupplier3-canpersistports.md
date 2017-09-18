---
title: "IDebugPortSupplier3::CanPersistPorts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier3::CanPersistPorts"
helpviewer_keywords: 
  - "IDebugPortSupplier3::CanPersistPorts"
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPortSupplier3::CanPersistPorts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會決定是否連接埠提供者可以保存的連接埠 \(藉由寫入磁碟\) 的偵錯工具的引動過程之間。  
  
## 語法  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```c#  
int CanPersistPorts();  
```  
  
#### 參數  
 無。  
  
## 傳回值  
 `S_OK`如果可以保存的連接埠，或`S_FALSE` ，表示連接埠不會保存。  
  
## 備註  
 如果連接埠提供者可以保存的連接埠，它應該執行這項操作時就會被消滅，然後重新載入檔案時，它會具現化再一次。  
  
## 請參閱  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)