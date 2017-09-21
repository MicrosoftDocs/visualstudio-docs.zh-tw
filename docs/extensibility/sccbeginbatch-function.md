---
title: "SccBeginBatch 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccBeginBatch"
helpviewer_keywords: 
  - "SccBeginBatch 函式"
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccBeginBatch 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式會啟動批次一連串的原始檔控制作業。[SccEndBatch](../extensibility/sccendbatch-function.md) 將被呼叫來結束批次。 這些批次可能不是巢狀。  
  
## 語法  
  
```cpp#  
SCCRTN SccBeginBatch(void);  
```  
  
#### 參數  
 無。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|批次的作業已成功開始。|  
|SCC\_E\_UNKNOWNERROR|非特定的失敗。|  
  
## 備註  
 原始檔控制批次用來執行相同的作業，跨多個專案或多個內容。 批次可以用於批次作業期間排除重複的每個專案對話方塊中，從使用者體驗。`SccBeginBatch` 函式和 [SccEndBatch](../extensibility/sccendbatch-function.md) 函式組用來指示開始和結束的作業。 它們不能巢狀結構。`SccBeginBatch` 設定旗標，表示批次作業正在進行中。  
  
 批次作業生效時，原始檔控制外掛程式應該對使用者顯示最多一個對話方塊中的任何問題，並在所有後續的作業上套用該對話方塊的回應。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)