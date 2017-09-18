---
title: "SccRemove 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccRemove"
helpviewer_keywords: 
  - "SccRemove 函式"
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccRemove 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式會從原始檔控制系統刪除檔案。  
  
## 語法  
  
```cpp#  
SCCRTN SccRemove(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### 參數  
 pvContext  
 \[\] in原始檔控制外掛程式內容結構。  
  
 hWnd  
 \[\] in原始檔控制外掛程式可以使用為父代，它會提供任何對話方塊 IDE 視窗控制代碼。  
  
 nFiles  
 \[\] in中指定的檔案數目 `lpFileNames` 陣列。  
  
 lpFileNames  
 \[\] in要移除的檔案的完整格式的本機路徑名稱的陣列。  
  
 lpComment  
 \[\] in要套用至每個檔案遭到移除註解。  
  
 Stored  
 \[\] in命令的旗標 \(未使用\)。  
  
 pvOptions  
 \[\] in原始檔控制外掛程式專屬選項。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|已成功移除。|  
|SCC\_E\_FILENOTCONTROLLED|選取的檔案不是原始檔控制下。|  
|SCC\_E\_OPNOTSUPPORTED|原始檔控制系統不支援這項作業。|  
|SCC\_E\_ISCHECKEDOUT|無法移除檔案，因為使用者目前已取出。|  
|SCC\_E\_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。|  
|SCC\_E\_NOTAUTHORIZED|不允許使用者執行這項作業。|  
|SCC\_E\_NONSPECIFICERROR|非特定的失敗。不移除檔案。|  
|SCC\_I\_OPERATIONCANCELED|在完成之前已取消作業。|  
  
## 備註  
 此函式會從原始檔控制系統中移除的檔案，但不會刪除它們從使用者的本機硬碟。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)