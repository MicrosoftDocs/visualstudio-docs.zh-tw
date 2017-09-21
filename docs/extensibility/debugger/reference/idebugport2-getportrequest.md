---
title: "IDebugPort2::GetPortRequest | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPort2::GetPortRequest"
helpviewer_keywords: 
  - "IDebugPort2::GetPortRequest"
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPort2::GetPortRequest
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得先前用來建立 \(若有\) 的連接埠的連接埠的描述。  
  
## 語法  
  
```cpp#  
HRESULT GetPortRequest(   
   IDebugPortRequest2** ppRequest  
);  
```  
  
```c#  
int GetPortRequest(   
   out IDebugPortRequest2 ppRequest  
);  
```  
  
#### 參數  
 `ppRequest`  
 \[\] out傳回[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)物件，代表用來建立連接埠的要求。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  傳回`E_PORT_NO_REQUEST`如果連接埠未建立使用[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)連接埠要求。  
  
## 請參閱  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [下列](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)