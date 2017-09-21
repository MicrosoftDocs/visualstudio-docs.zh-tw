---
title: "SccCloseProject 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccCloseProject"
helpviewer_keywords: 
  - "SccCloseProject 函式"
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# SccCloseProject 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式會關閉專案時，結尾的特定工作階段。  
  
## 語法  
  
```cpp#  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### 參數  
 pvContext  
 原始檔控制外掛程式內容結構。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|已成功關閉專案。|  
|SCC\_E\_PROJNOTOPEN|沒有任何專案目前已開啟。|  
|SCC\_E\_NOTAUTHORIZED|不允許使用者執行這項作業。|  
|SCC\_E\_NONSPECIFICERROR|非特定的失敗。|  
  
## 備註  
 [SccOpenProject](../extensibility/sccopenproject-function.md) 一律在呼叫之前呼叫此函式。 此函式的呼叫之後接著呼叫 `SccOpenProject` 函式或 [SccUninitialize](../extensibility/sccuninitialize-function.md), ，這完全結束原始檔控制系統的連線。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)