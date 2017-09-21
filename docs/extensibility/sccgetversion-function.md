---
title: "SccGetVersion 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetVersion"
helpviewer_keywords: 
  - "SccGetVersion 函式"
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccGetVersion 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式取得的版本號碼的原始檔控制外掛程式 API 受到原始檔控制外掛程式。  
  
## 語法  
  
```cpp#  
LONG SccGetVersion(void);  
```  
  
#### 參數  
 無。  
  
## 傳回值  
 A `LONG` 包含支援的原始檔控制外掛程式 API 的版本號碼的資料類型:  
  
|WORD|描述|  
|----------|--------|  
|HIWORD|主要版本|  
|LOWORD|次要版本|  
  
## 備註  
 例如，如果原始檔控制外掛程式支援 1.3 版的原始檔控制外掛程式 API，此函式會傳回 0x0103。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)