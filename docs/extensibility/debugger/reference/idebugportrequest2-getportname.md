---
title: "IDebugPortRequest2::GetPortName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortRequest2::GetPortName"
helpviewer_keywords: 
  - "IDebugPortRequest2::GetPortName"
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortRequest2::GetPortName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得連接埠的名稱。  
  
## 語法  
  
```cpp#  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```c#  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### 參數  
 `pbstrPortName`  
 \[\] out傳回連接埠的名稱。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)介面通常是從傳遞偵錯封裝 \(用戶端\) 以取得連線的連接埠提供者 \(伺服器\) 至連接埠。  偵錯封裝和連接埠提供者都能清楚掌握連接埠可能的選項。  如果簡單的字串可以描述為連接埠，然後在`IDebugPortRequest2::GetPortName`方法不會有足夠的資訊，來建立連線。  否則，提供額外的介面，用戶端，可由伺服器使用`IDebugPortRequest2::QueryInterface`。  
  
## 請參閱  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)