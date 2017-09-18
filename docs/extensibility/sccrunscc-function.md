---
title: "SccRunScc 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccRunScc"
helpviewer_keywords: 
  - "SccRunScc 函式"
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccRunScc 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式會叫用的原始檔控制系統管理工具。  
  
## 語法  
  
```cpp#  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
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
 \[\] in選取的檔案名稱的陣列。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|已成功叫用原始檔控制系統管理工具。|  
|SCC\_I\_OPERATIONCANCELED|作業已取消。|  
|SCC\_E\_INITIALIZEFAILED|無法初始化原始檔控制系統。|  
|SCC\_E\_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。|  
|SCC\_E\_CONNECTIONFAILURE|無法連線至原始檔控制系統。|  
|SCC\_E\_FILENOTCONTROLLED|選取的檔案不是原始檔控制下。|  
|SCC\_E\_NONSPECIFICERROR|非特定的失敗。|  
  
## 備註  
 此函式可讓呼叫者必須透過外部管理工具存取的原始檔控制系統功能的完整範圍。 如果原始檔控制系統沒有使用者介面，原始檔控制外掛程式可以實作介面，以執行必要的系統管理功能。  
  
 以計數和目前所選檔案的檔案名稱的陣列，會呼叫此函數。 檔案清單中的系統管理工具支援時，可用來預先選取的檔案中的管理介面。否則，可略過清單。  
  
 此函式通常叫用使用者選取時 **啟動 \< 原始檔控制伺服器 \>** 從 **檔案** \]\-\> \[ **原始檔控制** 功能表。 這 **啟動** 可以一律停用或甚至是藉由設定登錄項目隱藏功能表選項。 如需詳細資訊，請參閱[如何: 安裝原始檔控制外掛程式](../extensibility/internals/how-to-install-a-source-control-plug-in.md)。 只有當呼叫此函式 [SccInitialize](../extensibility/sccinitialize-function.md) 傳回 `SCC_CAP_RUNSCC` 功能位元 \(請參閱 [功能旗標](../extensibility/capability-flags.md) 如需詳細資訊，此裝置和其他功能位元為單位\)。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [如何: 安裝原始檔控制外掛程式](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [功能旗標](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)