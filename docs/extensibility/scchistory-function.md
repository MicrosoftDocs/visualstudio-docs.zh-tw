---
title: "SccHistory 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccHistory"
helpviewer_keywords: 
  - "SccHistory 函式"
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# SccHistory 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式會顯示指定檔案的歷程記錄。  
  
## 語法  
  
```cpp#  
SCCRTN SccHistory(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### 參數  
 `pvContext`  
 \[\] in原始檔控制外掛程式內容結構。  
  
 `hWnd`  
 \[\] in原始檔控制外掛程式可以使用為父代，它會提供任何對話方塊 IDE 視窗控制代碼。  
  
 `nFiles`  
 \[\] in中指定的檔案數目 `lpFileName` 陣列。  
  
 `lpFileName`  
 \[\] in檔案的完整名稱的陣列。  
  
 `fOptions`  
 \[\] in\(目前未使用\) 的命令旗標。  
  
 `pvOptions`  
 \[\] in原始檔控制外掛程式專屬選項。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|成功取得版本歷程記錄。|  
|SCC\_I\_RELOADFILE|原始檔控制系統實際修改磁碟上的檔案歷程記錄擷取 \(比方說，藉由取得它的舊版本\)，因此 IDE 應重新載入此檔案。|  
|SCC\_E\_FILENOTCONTROLLED|檔案不是原始檔控制下。|  
|SCC\_E\_OPNOTSUPPORTED|原始檔控制系統不支援這項作業。|  
|SCC\_E\_NOTAUTHORIZED|不允許使用者執行這項作業。|  
|SCC\_E\_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC\_E\_PROJNOTOPEN|此專案已開啟。|  
|SCC\_E\_NONSPECIFICERROR|非特定的失敗。 無法取得檔案歷程記錄。|  
  
## 備註  
 原始檔控制外掛程式可以顯示自己的對話方塊，以顯示歷程記錄的每個檔案，請使用 `hWnd` 與父視窗。 或者，選擇性的文字輸出回呼函式提供給 [SccOpenProject](../extensibility/sccopenproject-function.md) 可用，如果受支援。  
  
 請注意，在某些情況下，此呼叫的執行期間可能會變更所檢查的檔案。 例如， [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] 記錄命令可讓使用者有機會取得舊版的檔案。 在這種情況下，原始檔控制外掛程式傳回 `SCC_I_RELOAD` 警告 IDE，需要重新載入檔案。  
  
> [!NOTE]
>  如果原始檔控制外掛程式不支援此函式的檔案陣列，可以顯示只有第一個檔案的檔案歷程記錄。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)