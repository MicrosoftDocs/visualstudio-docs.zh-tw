---
title: "SccGetEvents 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetEvents"
helpviewer_keywords: 
  - "SccGetEvents 函式"
ms.assetid: 32f8147d-6dcc-465e-b07b-42da5824f9b0
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccGetEvents 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式會擷取已排入佇列的狀態事件。  
  
## 語法  
  
```cpp#  
SCCRTN SccGetEvents (  
   LPVOID pvContext,  
   LPSTR  lpFileName,  
   LPLONG lpStatus,  
   LPLONG pnEventsRemaining  
);  
```  
  
#### 參數  
 pvContext  
 \[\] in原始檔控制外掛程式內容結構。  
  
 lpFileName  
 \[in、 out\]原始檔控制外掛程式傳回的檔名 \(最多 \_MAX\_PATH 字元\) 的放置位置的緩衝區。  
  
 lpStatus  
 \[in、 out\]會傳回狀態碼 \(請參閱 [檔案狀態碼](../extensibility/file-status-code-enumerator.md) 提供可能的值\)。  
  
 pnEventsRemaining  
 \[in、 out\]傳回在這個呼叫之後保留在佇列中的項目數目。 如果這個數字很大，呼叫端可能會決定呼叫 [SccQueryInfo](../extensibility/sccqueryinfo-function.md) 取得的所有資訊一次。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|取得成功的事件。|  
|SCC\_E\_OPNOTSUPPORTED|不支援此函式。|  
|SCC\_E\_NONSPECIFICERROR|非特定的失敗。|  
  
## 備註  
 閒置處理，以查看是否有任何更新原始檔控制下的檔案的狀態時，會呼叫此函數。 原始檔控制外掛程式會維護它所知，所有檔案的狀態和變更的狀態會註明外掛程式，狀態和相關聯的檔案會儲存在佇列中。 當 `SccGetEvents` 呼叫時，最上層項目佇列會擷取並傳回。 此函式限制要傳回唯一先前快取的資訊，而且必須非常快速的作業 \(也就是沒有磁碟的讀取或詢問原始檔控制系統的狀態\)。否則可能會開始 IDE 的效能降低。  
  
 如果沒有報告狀態更新，原始檔控制外掛程式會將空字串儲存在所指向的緩衝區 `lpFileName`。 否則外掛程式儲存檔案的完整路徑名稱的狀態資訊已變更，並傳回適當的狀態碼為 \(其中一個值的詳細說明 [檔案狀態碼](../extensibility/file-status-code-enumerator.md)\)。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [檔案狀態碼](../extensibility/file-status-code-enumerator.md)