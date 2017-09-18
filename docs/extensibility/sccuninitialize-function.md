---
title: "SccUninitialize 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccUninitialize"
helpviewer_keywords: 
  - "SccUninitialize 函式"
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccUninitialize 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式會清除任何先前呼叫所建立的開啟連接或配置 [SccInitialize](../extensibility/sccinitialize-function.md) 以準備關閉原始檔控制外掛程式。  
  
## 語法  
  
```cpp#  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### 參數  
 pvContext  
 \[\] in在建立原始檔控制外掛程式內容結構的指標， [SccInitialize](../extensibility/sccinitialize-function.md)。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|清除工作順利完成。|  
  
## 備註  
 原始檔控制外掛程式會負責準備即將關閉並釋放外掛程式配置內容結構的記憶體。 每個外掛程式的特定執行個體一次呼叫函式。 呼叫 [SccInitialize](../extensibility/sccinitialize-function.md) 之前呼叫。 沒有專案仍然可以開啟時呼叫的 `SccUninitialize`。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)