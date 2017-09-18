---
title: "SccInitialize 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccInitialize"
helpviewer_keywords: 
  - "SccInitialize 函式"
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccInitialize 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式初始化原始檔控制外掛程式，並提供功能和整合式的開發環境 \(IDE\) 的限制。  
  
## 語法  
  
```cpp#  
SCCRTN SccInitialize (  
   LPVOID* ppvContext,  
   HWND    hWnd,  
   LPCSTR  lpCallerName,  
   LPSTR   lpSccName,  
   LPLONG  lpSccCaps,  
   LPSTR   lpAuxPathLabel,  
   LPLONG  pnCheckoutCommentLen,  
   LPLONG  pnCommentLen  
);  
```  
  
#### 參數  
 `ppvContext`  
 \[\] in原始檔控制外掛程式可以在此放置其內容結構的指標。  
  
 `hWnd`  
 \[\] in原始檔控制外掛程式可以使用為父代，它會提供任何對話方塊 IDE 視窗控制代碼。  
  
 `lpCallerName`  
 \[\] in程式呼叫的原始檔控制外掛程式的名稱。  
  
 `lpSccName`  
 \[in、 out\]緩衝區的原始檔控制外掛程式放置其本身名稱的位置 \(不要將超過 `SCC_NAME_LEN`\)。  
  
 `lpSccCaps`  
 \[\] out傳回的原始檔控制外掛程式功能旗標。  
  
 `lpAuxPathLabel`  
 \[in、 out\]原始檔控制外掛程式放置位置描述的字串緩衝區 `lpAuxProjPath` 參數所傳回 [SccOpenProject](../extensibility/sccopenproject-function.md) 和 [SccGetProjPath](../extensibility/sccgetprojpath-function.md) \(不要將超過 `SCC_AUXLABEL_LEN`\)。  
  
 `pnCheckoutCommentLen`  
 \[\] out傳回的簽出註解的最大允許長度。  
  
 `pnCommentLen`  
 \[\] out傳回其他註解的最大允許長度。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|來源控制項初始化成功。|  
|SCC\_E\_INITIALIZEFAILED|系統無法初始化。|  
|SCC\_E\_NOTAUTHORIZED|不允許使用者執行指定的作業。|  
|SCC\_E\_NONSPECFICERROR|非特定的失敗。原始檔控制系統尚未初始化。|  
  
## 備註  
 第一次載入原始檔控制外掛程式時，IDE 會呼叫這個函式。 它可讓 IDE 傳遞特定資訊，例如，呼叫者的名稱、 給外掛程式。 IDE 也會取得回特定資訊，例如註解和隨插即用中的功能最大容許長度。  
  
 `ppvContext` 指向 `NULL` 指標。 原始檔控制外掛程式可以配置供本身使用的結構，並儲存在該結構的指標 `ppvContext`。 IDE 會將這個指標傳遞給每個其他 VSSCI API 函式允許外掛程式有可用的內容資訊，而不必透過全域儲存體，並支援多個外掛程式執行個體。 此結構應該被解除配置時 [SccUninitialize](../extensibility/sccuninitialize-function.md) 呼叫。  
  
 `lpCallerName` 和 `lpSccName` 參數可讓 IDE 以及原始檔控制外掛程式交換名稱。 這些名稱可能使用只是為了區分多個執行個體，或它們可能會實際顯示在功能表或對話方塊。  
  
 `lpAuxPathLabel` 參數是字串，做為識別輔助專案路徑儲存在方案檔並傳遞至原始檔控制外掛程式的呼叫中的 \[註解 [SccOpenProject](../extensibility/sccopenproject-function.md)。[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] 會使用字串"SourceSafe 專案:";其他原始檔控制外掛程式應該避免使用這個特定的字串。  
  
 `lpSccCaps` 參數指定的原始檔控制外掛程式的位置來儲存位元旗標，指出隨插即用中的功能。 \(如功能位元旗標的完整清單，請參閱 [功能旗標](../extensibility/capability-flags.md)\)。 比方說，如果要寫入至呼叫端提供的回呼函式結果，外掛程式會設定功能的外掛程式計劃位元 SCC\_CAP\_TEXTOUT。 這會發出信號 IDE 建立版本控制結果視窗。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [功能旗標](../extensibility/capability-flags.md)