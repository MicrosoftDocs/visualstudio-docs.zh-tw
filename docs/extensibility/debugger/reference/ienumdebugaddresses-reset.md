---
title: "IEnumDebugAddresses::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugAddresses::Reset"
helpviewer_keywords: 
  - "IEnumDebugAddresses::Reset 方法"
ms.assetid: 3a9d7f20-5bc6-4e13-8e91-5af4092e092f
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IEnumDebugAddresses::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會重新列舉型別設定為第一個項目。  
  
## 語法  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```c#  
int Reset();  
```  
  
#### 參數  
 None  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法呼叫下, 一步呼叫之後[下一步](../Topic/IEnumDebugAddresses::Next.md)傳回列舉型別的第一個項目。  
  
## 請參閱  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)   
 [下一步](../Topic/IEnumDebugAddresses::Next.md)