---
title: "IDebugCoreServer2::GetPort | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer2::GetPort"
helpviewer_keywords: 
  - "IDebugCoreServer2::GetPort"
ms.assetid: 3f5ea4a8-6085-4600-980a-9e48f8b5be56
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugCoreServer2::GetPort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取特定的連接埠。  
  
## 語法  
  
```cpp#  
HRESULT GetPort(   
   REFGUID       guidPort,  
   IDebugPort2** ppPort  
);  
```  
  
```c#  
int GetPort(   
   ref Guid        guidPort,  
   out IDebugPort2 ppPort  
);  
```  
  
#### 參數  
 `guidPort`  
 \[in\]要擷取之連接埠的 GUID。  
  
 `ppPort`  
 \[\] out傳回[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)物件，代表您想要的連接埠。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  傳回`E_PORTSUPPLIER_NO_PORT`如果沒有指定的識別項與連接埠。  
  
## 請參閱  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)