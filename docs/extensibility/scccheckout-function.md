---
title: "SccCheckout 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccCheckout"
helpviewer_keywords: 
  - "SccCheckout 函式"
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# SccCheckout 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

取得一份完整的檔案名稱，此函式取出它們的本機磁碟機。 註解適用於所有簽出的檔案。 註解引數可以是 `null` 字串。  
  
## 語法  
  
```cpp#  
SCCRTN SccCheckout (  
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
 \[\] in選取要簽出檔案的數目。  
  
 lpFileNames  
 \[\] in要簽出檔案的完整格式的本機路徑名稱的陣列。  
  
 lpComment  
 \[\] in若要套用至每個選取的檔案簽出的註解。  
  
 Stored  
 \[\] in命令旗標 \(請參閱 [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)\)。  
  
 pvOptions  
 \[\] in原始檔控制外掛程式專屬選項。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|簽出成功。|  
|SCC\_E\_FILENOTCONTROLLED|選取的檔案不是原始程式碼控制之下。|  
|SCC\_E\_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC\_E\_NOTAUTHORIZED|不允許使用者執行這項作業。|  
|SCC\_E\_NONSPECIFICERROR|非特定的失敗。 檔案未被簽出。|  
|SCC\_E\_ALREADYCHECKEDOUT|使用者已簽出檔案。|  
|SCC\_E\_FILEISLOCKED|檔案鎖定，因而禁止新版本的建立。|  
|SCC\_E\_FILEOUTEXCLUSIVE|另一位使用者已完成獨佔簽出這個檔案。|  
|SCC\_I\_OPERATIONCANCELED|在完成之前已取消作業。|  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)