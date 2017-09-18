---
title: "SccEndBatch 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccEndBatch"
helpviewer_keywords: 
  - "SccEndBatch 函式"
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccEndBatch 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式結束時的原始檔控制作業批次。 這些批次可能不是巢狀。  
  
## 語法  
  
```cpp#  
SCCRTN SccEndBatch(void);  
```  
  
#### 參數  
 無。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|作業順利完成的批次。|  
|SCC\_E\_UNKNOWNERROR|非特定的失敗。|  
  
## 備註  
 原始檔控制批次用來執行相同的原始檔控制作業，跨多個專案或多個內容。 批次可以用於批次作業期間排除多餘的對話方塊，從使用者體驗。[SccBeginBatch](../extensibility/sccbeginbatch-function.md) 和 `SccEndBatch` 函式做為一組可用來表示的開頭和結尾的作業。 它們不能巢狀結構。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)