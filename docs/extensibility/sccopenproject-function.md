---
title: "SccOpenProject 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccOpenProject"
helpviewer_keywords: 
  - "SccOpenProject 函式"
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# SccOpenProject 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式開啟現有的原始檔控制專案，或建立一個新。  
  
## 語法  
  
```cpp#  
SCCRTN SccOpenProject (  
   LPVOID        pvContext,  
   HWND          hWnd,  
   LPSTR         lpUser,  
   LPCSTR        lpProjName,  
   LPCSTR        lpLocalProjPath,  
   LPSTR         lpAuxProjPath,  
   LPCSTR        lpComment,  
   LPTEXTOUTPROC lpTextOutProc,  
   LONG          dwFlags  
);  
```  
  
#### 參數  
 pvContext  
 \[\] in原始檔控制外掛程式內容結構。  
  
 hWnd  
 \[\] in原始檔控制外掛程式可以使用為父代，它會提供任何對話方塊 IDE 視窗控制代碼。  
  
 lpUser  
 \[in、 out\]使用者 \(不超過 SCC\_USER\_SIZE，包括 NULL 結束字元\) 的名稱。  
  
 lpProjName  
 \[\] in識別專案名稱的字串。  
  
 lpLocalProjPath  
 \[\] in專案的工作資料夾路徑。  
  
 lpAuxProjPath  
 \[in、 out\]選擇性的輔助字串，用來識別專案 \(不超過 SCC\_AUXPATH\_SIZE，包括 NULL 結束字元\)。  
  
 lpComment  
 \[\] in新的專案所建立的註解。  
  
 lpTextOutProc  
 \[\] in若要顯示文字輸出從原始檔控制外掛程式選用的回呼函數。  
  
 dwFlags  
 \[\] in表示是否需要專案是未知來源建立新的專案控制外掛程式。 值可以是項目的組合 `SCC_OP_CREATEIFNEW` 和 `SCC_OP_SILENTOPEN.`  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|在 \[開啟專案的成功。|  
|SCC\_E\_INITIALIZEFAILED|無法初始化專案。|  
|SCC\_E\_INVALIDUSER|使用者可能無法登入原始檔控制系統。|  
|SCC\_E\_COULDNOTCREATEPROJECT|專案不存在之前呼叫。 `SCC_OPT_CREATEIFNEW` 旗標已設定，但無法建立專案。|  
|SCC\_E\_PROJSYNTAXERR|無效的專案的語法。|  
|SCC\_E\_UNKNOWNPROJECT|專案是未知的原始檔控制外掛程式，和 `SCC_OPT_CREATEIFNEW` 未設定旗標。|  
|SCC\_E\_INVALIDFILEPATH|無效或無法使用的檔案路徑。|  
|SCC\_E\_NOTAUTHORIZED|不允許使用者執行這項作業。|  
|SCC\_E\_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC\_E\_NONSPECFICERROR|非特定的失敗。原始檔控制系統尚未初始化。|  
  
## 備註  
 IDE 可能會傳送使用者名稱 \(`lpUser`\)，或它可能會直接傳遞指標為空字串。 如果沒有使用者名稱，原始檔控制外掛程式應該使用它做為預設值。 不過，如果未將名稱傳遞，或具有指定名稱的登入失敗，外掛程式應該會提示使用者登入，會傳回有效的名稱，在 `lpUser` 當它收到有效的登入`.` 因為外掛程式可能會變更使用者名稱字串，IDE 一律會配置大小的緩衝區 \(`SCC_USER_LEN`\+ 1 或 SCC\_USER\_SIZE，其中包括 null 結束字元的空間\)。  
  
> [!NOTE]
>  第一個 IDE 可能需要執行的動作可能會呼叫 `SccOpenProject` 函式或 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)。 基於這個理由，這兩者有相同 `lpUser` 參數。  
  
 `lpAuxProjPath` 和`lpProjName` 會讀取方案檔，或從呼叫傳回 `SccGetProjPath` 函式。 這些參數會包含原始檔控制外掛程式將與專案相關聯的字串，並有意義只有外掛程式。 如果沒有這類字串位於方案檔，而且不瀏覽提示使用者 \(這會傳回字串，以透過 `SccGetProjPath` 函式\)，IDE 會將空字串傳遞兩個 `lpAuxProjPath` 和 `lpProjName`, ，並預期這些值時，此函數會傳回更新的外掛程式。  
  
 `lpTextOutProc` 為原始檔控制外掛程式用來顯示命令的結果輸出至 IDE 所提供的回呼函式的指標。 此回呼函式中有詳細說明在 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)。  
  
> [!NOTE]
>  如果原始檔控制外掛程式是要利用這一點，它必須已經設定 `SCC_CAP_TEXTOUT` 加上旗標 [SccInitialize](../extensibility/sccinitialize-function.md)。 如果未設定該旗標，或如果 IDE 不支援這項功能， `lpTextOutProc` 會 `NULL`。  
  
 `dwFlags` 參數可控制結果，在開啟的專案目前不存在。 它包含兩位元旗標， `SCC_OP_CREATEIFNEW` 和 `SCC_OP_SILENTOPEN`。 如果已開啟的專案存在，函數只是開啟的專案，並傳回 `SCC_OK`。 如果專案不存在，而且如果 `SCC_OP_CREATEIFNEW` 旗標為開啟、 原始檔控制外掛程式在原始檔控制系統中建立專案、 開啟它，並傳回 `SCC_OK`。 如果專案不存在，而且如果 `SCC_OP_CREATEIFNEW` 旗標為關閉，外掛程式應該再檢查 `SCC_OP_SILENTOPEN` 旗標。 如果該旗標不在外掛程式可能會提示使用者輸入專案名稱。 如果該旗標會位於，外掛程式應該只會傳回 `SCC_E_UNKNOWNPROJECT`。  
  
## 呼叫順序  
 在正常的事件， [SccInitialize](../extensibility/sccinitialize-function.md) 會先呼叫，以開啟原始檔控制工作階段。 工作階段會由呼叫 `SccOpenProject`, 、 其他原始檔控制外掛程式 API 函式呼叫，接著程式會終止，且呼叫 [SccCloseProject](../extensibility/scccloseproject-function.md)。 這類工作階段可能會重複多次之前 [SccUninitialize](../extensibility/sccuninitialize-function.md) 呼叫。  
  
 如果原始檔控制外掛程式設定 `SCC_CAP_REENTRANT` 位元 `SccInitialize`, ，則上述的工作階段順序可能會重複許多次以平行方式。 不同 `pvContext` 結構追蹤不同的工作階段，其中每個 `pvContext` 一次是一個開啟的專案相關聯。 根據`pvContext` 參數時，外掛程式可以判斷哪個專案參考的任何特定的呼叫。 如果位元能力 `SCC_CAP_REENTRANT` 未設定，nonreentrant 原始檔控制外掛程式僅限於使用多個專案的能力。  
  
> [!NOTE]
>  `SCC_CAP_REENTRANT` 位元的原始檔控制外掛程式 API 1.1 版中導入。 未設定，或是在 1.0 版中，會忽略，且所有 1.0 版原始檔控制外掛程式會假設為 nonreentrant。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCloseProject](../extensibility/scccloseproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [字串長度限制](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)