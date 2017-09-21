---
title: "SccUncheckout 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccUncheckout"
helpviewer_keywords: 
  - "SccUncheckout 函式"
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# SccUncheckout 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式會復原先前的簽出作業，藉此還原為之前簽出狀態的 \[選取的檔案或檔案的內容。 所有的檔案簽出之後所做的變更都會遺失。  
  
## 語法  
  
```cpp#  
SCCRTN SccUncheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
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
 \[\] in這是要復原簽出檔案的完整格式的本機路徑名稱的陣列。  
  
 Stored  
 \[\] in\(未使用\) 的命令旗標。  
  
 pvOptions  
 \[\] in原始檔控制外掛程式專屬選項。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|復原簽出成功。|  
|SCC\_E\_FILENOTCONTROLLED|選取的檔案不是原始程式碼控制之下。|  
|SCC\_E\_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC\_E\_NONSPECIFICERROR|非特定的失敗。 復原簽出失敗。|  
|SCC\_E\_NOTCHECKEDOUT|使用者沒有簽出檔案。|  
|SCC\_E\_NOTAUTHORIZED|不允許使用者執行這項作業。|  
|SCC\_E\_PROJNOTOPEN|無法從原始檔控制開啟專案。|  
|SCC\_I\_OPERATIONCANCELED|在完成之前已取消作業。|  
  
## 備註  
 這個作業之後， `SCC_STATUS_CHECKEDOUT` 和 `SCC_STATUS_MODIFIED` 旗標會同時清除在其上執行復原簽出檔案。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)