---
title: "SccRename 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccRename"
helpviewer_keywords: 
  - "SccRename 函式"
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccRename 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式會將檔案重新命名原始檔控制系統中。  
  
## 語法  
  
```cpp#  
SCCRTN SccRename(  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName,  
   LPCSTR lpNewName  
);  
```  
  
#### 參數  
 pvContext  
 \[\] in原始檔控制外掛程式內容結構。  
  
 hWnd  
 \[\] in原始檔控制外掛程式可以使用為父代，它會提供任何對話方塊 IDE 視窗控制代碼。  
  
 lpFileName  
 \[\] in重新命名檔案的完整的檔案名稱。  
  
 lpNewName  
 \[\] in完整的新名稱。 如果不同的目錄路徑，然後移動檔案從一個子目錄到另一個。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|重新命名作業順利完成。|  
|SCC\_E\_PROJNOTOPEN|無法在原始檔控制開啟專案。|  
|SCC\_E\_FILENOTCONTROLLED|檔案不是原始檔控制下。|  
|SCC\_E\_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。|  
|SCC\_E\_NOTAUTHORIZED|若要完成這項作業未授權使用者。|  
|SCC\_E\_COULDNOTCREATEPROJECT|重新命名程序的一部分，無法建立專案。|  
|SCC\_E\_OPNOTPERFORMED|未執行作業。|  
|SCC\_E\_NONSPECIFICERROR|發生未指定或一般錯誤。|  
  
## 備註  
 此函式可用來重新命名檔案或將它從某個位置移到另一個原始檔控制系統中。 原始檔控制外掛程式不應嘗試存取磁碟上的檔案。 是 IDE 的責任，若要重新命名本機檔案。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)