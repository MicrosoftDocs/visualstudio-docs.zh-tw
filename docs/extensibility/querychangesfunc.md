---
title: "QUERYCHANGESFUNC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "QUERYCHANGESFUNC"
helpviewer_keywords: 
  - "QUERYCHANGESFUNC 回呼函式"
  - "QUERYCHANGESDATA 結構"
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# QUERYCHANGESFUNC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

這是所使用的回呼函式 [SccQueryChanges](../extensibility/sccquerychanges-function.md) 操作列舉的檔案名稱的集合，並判斷每個檔案的狀態。  
  
 `SccQueryChanges` 函式會指定清單的指標 `QUERYCHANGESFUNC` 回呼。 原始檔控制外掛程式列舉指定的清單，並提供每個清單中的檔案狀態 \(透過此回呼\)。  
  
## 簽章  
  
```cpp#  
typedef BOOL (*QUERYCHANGESFUNC)( LPVOID pvCallerData, QUERYCHANGESDATA * pChangesData );  
```  
  
## 參數  
 pvCallerData  
 \[\] in `pvCallerData` 參數傳遞至呼叫端 \(IDE\) [SccQueryChanges](../extensibility/sccquerychanges-function.md)。 原始檔控制外掛程式，請不要假設內容的這個值。  
  
 pChangesData  
 \[\] in指標 [QUERYCHANGESDATA 結構](#LinkQUERYCHANGESDATA) 結構描述檔案的變更。  
  
## 傳回值  
 IDE 會傳回適當的錯誤程式碼:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|繼續處理。|  
|SCC\_I\_OPERATIONCANCELED|停止處理。|  
|SCC\_E\_xxx|任何適當的 SCC 錯誤應該停止處理。|  
  
##  <a name="LinkQUERYCHANGESDATA"></a> QUERYCHANGESDATA 結構  
 傳入的每個檔案的結構如下所示:  
  
```cpp#  
struct QUERYCHANGESDATA_A { DWORD  dwSize; LPCSTR lpFileName; DWORD  dwChangeType; LPCSTR lpLatestName; }; typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA; struct QUERYCHANGESDATA_W { DWORD   dwSize; LPCWSTR lpFileName; DWORD   dwChangeType; LPCWSTR lpLatestName; };  
```  
  
 dwSize  
 此結構 \(以位元組為單位\) 的大小。  
  
 lpFileName  
 此項目的原始的檔案名稱。  
  
 dwChangeType  
 指出檔案的狀態碼:  
  
|程式碼|描述|  
|---------|--------|  
|`SCC_CHANGE_UNKNOWN`|不知道有哪些改變。|  
|`SCC_CHANGE_UNCHANGED`|此檔案的名稱並無任何變更。|  
|`SCC_CHANGE_DIFFERENT`|檔案使用不同的身分識別，但資料庫中有相同的名稱。|  
|`SCC_CHANGE_NONEXISTENT`|檔案不存在資料庫中或在本機。|  
|`SCC_CHANGE_DATABASE_DELETED`|從資料庫中刪除的檔案。|  
|`SCC_CHANGE_LOCAL_DELETED`|在本機刪除的檔案，但該檔案仍存在於資料庫中。 如果無法判斷，傳回 `SCC_CHANGE_DATABASE_ADDED`。|  
|`SCC_CHANGE_DATABASE_ADDED`|檔案加入至資料庫，但不在本機上。|  
|`SCC_CHANGE_LOCAL_ADDED`|檔案不存在資料庫中，且新的本機檔案。|  
|`SCC_CHANGE_RENAMED_TO`|檔案重新命名或移動資料庫做為 `lpLatestName`。|  
|`SCC_CHANGE_RENAMED_FROM`|檔案重新命名或從資料庫中移動 `lpLatestName`; 如果這是過於昂貴追蹤，傳回不同的旗標，例如 `SCC_CHANGE_DATABASE_ADDED`。|  
  
 lpLatestName  
 此項目目前的檔案名稱。  
  
## 請參閱  
 [IDE 所實作的回呼函式](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [錯誤代碼](../extensibility/error-codes.md)