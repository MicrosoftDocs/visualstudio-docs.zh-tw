---
title: "IDebugPortSupplierEx2::SetServer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugPortSupplierEx2::SetServer"
ms.assetid: 0e8ef194-3a4f-4abf-8382-4607ab3005d1
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugPortSupplierEx2::SetServer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

設定連接埠提供者的核心的伺服器。  
  
## 語法  
  
```cpp#  
HRESULT SetServer(  
   IDebugCoreServer2* pServer  
);  
```  
  
```c#  
int SetServer(  
   IDebugCoreServer2 pServer  
);  
```  
  
#### 參數  
 `pServer`  
 若要設定的連接埠提供者的核心伺服器。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugPortSupplierEx2](../../../extensibility/debugger/reference/idebugportsupplierex2.md)