---
title: "SccDirQueryInfo 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccDirQueryInfo"
helpviewer_keywords: 
  - "SccDirQueryInfo 函式"
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccDirQueryInfo 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式會檢查其目前狀態的完整目錄的清單。  
  
## 語法  
  
```cpp#  
SCCRTN SccDirQueryInfo(  
LPVOID  pContext,  
LONG    nDirs,  
LPCSTR* lpDirNames,  
LPLONG  lpStatus  
);  
```  
  
#### 參數  
 pContext  
 \[\] in原始檔控制外掛程式內容結構。  
  
 nDirs  
 \[\] in選取要查詢的目錄數目。  
  
 lpDirNames  
 \[\] in查詢目錄的完整路徑的陣列。  
  
 lpStatus  
 \[in、 out\]原始檔控制外掛程式，以便在傳回的狀態旗標的陣列結構 \(請參閱 [目錄狀態碼](../extensibility/directory-status-code-enumerator.md) 如需詳細資訊\)。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|查詢已成功。|  
|SCC\_E\_OPNOTSUPPORTED|原始程式碼控制系統不支援這項作業。|  
|SCC\_E\_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|非特定的失敗。|  
  
## 備註  
 函式會傳回陣列所使用的位元遮罩的位元，以填滿 `SCC_DIRSTATUS` 系列 \(請參閱 [目錄狀態碼](../extensibility/directory-status-code-enumerator.md)\)，指定每個目錄項目。 狀態陣列是由呼叫端所配置的。  
  
 目錄已重新命名為檢查目錄是否在原始檔控制中，藉由查詢是否有對應的專案之前，IDE 會使用此函式。 如果目錄不是原始檔控制下，IDE 可以提供適當的警告給使用者。  
  
> [!NOTE]
>  如果原始檔控制外掛程式選擇實作一個或多個狀態的值，未實作的 bits 應設定為零。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [目錄狀態碼](../extensibility/directory-status-code-enumerator.md)