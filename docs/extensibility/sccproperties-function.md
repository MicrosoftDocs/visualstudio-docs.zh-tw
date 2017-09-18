---
title: "SccProperties 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccProperties"
helpviewer_keywords: 
  - "SccProperties 函式"
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccProperties 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式會顯示檔案或專案的原始檔控制屬性。  
  
## 語法  
  
```cpp#  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### 參數  
 pvContext  
 \[\] in原始檔控制外掛程式內容結構。  
  
 hWnd  
 \[\] in原始檔控制外掛程式可以使用為父代，它會提供任何對話方塊 IDE 視窗控制代碼。  
  
 lpFileName  
 \[\] in檔案或專案的完整的路徑名稱。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|已成功地顯示屬性。|  
|SCC\_I\_RELOADFILE|版本控制系統已修改的檔案內容，因此 IDE 應重新載入此檔案。|  
|SCC\_E\_PROJNOTOPEN|尚未在原始檔控制開啟指定的專案。|  
|SCC\_E\_NOTAUTHORIZED|使用者未獲授權檢視此檔案或專案的屬性。|  
|SCC\_E\_FILENOTCONTROLLED|指定的檔案或專案不是原始檔控制下。|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|發生未知或一般錯誤。|  
  
## 備註  
 原始檔控制外掛程式在它自己的對話方塊中顯示的屬性。  
  
 屬性會由原始檔控制外掛程式和外掛程式的外掛程式可能不同。 如果外掛程式可讓使用者變更檔案的原始檔控制屬性，它應該傳回 `SCC_I_RELOAD` 發出信號，此檔案或專案需要重新載入的 IDE。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)