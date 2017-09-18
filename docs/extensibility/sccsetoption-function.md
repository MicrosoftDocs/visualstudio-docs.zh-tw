---
title: "SccSetOption 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccSetOption"
helpviewer_keywords: 
  - "SccSetOption 函式"
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccSetOption 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式會將控制的原始檔控制外掛程式行為的選項。  
  
## 語法  
  
```cpp#  
SCCRTN SccSetOption(  
   LPVOID pvContext,  
   LONG   nOption,  
   LONG   dwVal  
);  
```  
  
#### 參數  
 pvContext  
 \[\] in原始檔控制外掛程式內容結構。  
  
 nOption  
 \[\] in正在設定選項。  
  
 dwVal  
 \[\] in選項的設定。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|已成功設定選項。|  
|SCC\_I\_SHARESUBPROJOK|如果傳回 `nOption` 已 `SCC_OPT_SHARESUBPROJ` 和原始檔控制外掛程式可讓 IDE 設定目的地資料夾。|  
|SCC\_E\_OPNOTSUPPORTED|選項未設定，並不能指望。|  
  
## 備註  
 IDE 會呼叫此函式可控制行為的原始檔控制外掛程式。 第一個參數， `nOption`, ，表示正在設定值，第二個， `dwVal`, ，指出如何處理該值。 外掛程式會儲存這項資訊與相關聯 `pvContext``,` 讓 IDE 必須呼叫此函式之後呼叫 [SccInitialize](../extensibility/sccinitialize-function.md) \(但不是一定在每次呼叫之後 [SccOpenProject](../extensibility/sccopenproject-function.md)\)。  
  
 選項及其值的摘要:  
  
|`nOption`|`dwValue`|描述|  
|---------------|---------------|--------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|啟用\/停用背景事件佇列。|  
|`SCC_OPT_USERDATA`|任意值|指定要傳遞給使用者值 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) 回呼函式。|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|指出是否在 IDE 目前支援取消作業。|  
|`SCC_OPT_NAMECHANGEPFN`|指標 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) 回呼函式|設定名稱變更的回呼函式的指標。|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|表示 IDE 允許超出其檔以手動方式 \(透過原始檔控制使用者介面\) 檢查，或是否它們必須先簽出只能透過原始檔控制外掛程式。|  
|`SCC_OPT_SHARESUBPROJ`|N\/A|如果原始檔控制外掛程式可讓 IDE，以指定的本機專案資料夾，此外掛程式會傳回 `SCC_I_SHARESUBPROJOK`。|  
  
## SCC\_OPT\_EVENTQUEUE  
 如果 `nOption` 是 `SCC_OPT_EVENTQUEUE`, ，IDE 會停用 \(或重新啟用\) 背景處理。 比方說，在編譯期間 IDE 可能會指示外掛程式，以停止在閒置處理任何種類的原始檔控制。 之後在編譯時，它會重新啟用背景處理來保持最新的隨插即用中的事件佇列。 對應至 `SCC_OPT_EVENTQUEUE` 值 `nOption`, ，有兩個可能的值，如 `dwVal`, ，也就是 `SCC_OPT_EQ_ENABLE` 和 `SCC_OPT_EQ_DISABLE`。  
  
## SCC\_OPT\_HASCANCELMODE  
 如果值 `nOption` 是 `SCC_OPT_HASCANCELMODE`, ，IDE 會允許使用者取消長時間作業。 設定 `dwVal` 至 `SCC_OPT_HCM_NO` \(預設值\) 表示 IDE 有無取消模式。 原始檔控制外掛程式必須在想要能夠取消使用者提供其 \[取消\] 按鈕。`SCC_OPT_HCM_YES` 表示 IDE 可讓您取消作業，因此 SCC 外掛程式不需要以顯示其 \[取消\] 按鈕。 如果在 IDE 設定 `dwVal` 至 `SCC_OPT_HCM_YES`, ，它已準備好要回應 `SCC_MSG_STATUS` 和 `DOCANCEL` 訊息傳送至 `lpTextOutProc` 回呼函式 \(請參閱 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)\)。 如果在 IDE 不會設定這個變數，外掛程式應該傳送這兩個訊息。  
  
## SCC\_OPT\_NAMECHANGEPFN  
 如果 nOption 設為 `SCC_OPT_NAMECHANGEPFN`, ，和原始檔控制外掛程式和 IDE 可讓它、 外掛程式可以實際重新命名或移動檔案在原始檔控制作業。`dwVal` 將型別的函式指標 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)。 在原始檔控制作業時，外掛程式可以呼叫此函式，在三個參數中傳遞。 這些是舊名稱 \(以完整路徑\) 之檔案的新名稱 \(以完整路徑\) 該檔案，並具有 IDE 的相關資訊的指標。 在 IDE 中這個最後一個指標傳送藉由呼叫 `SccSetOption` 與 `nOption` 設為 `SCC_OPT_USERDATA`, ，與 `dwVal` 指向資料。 此函式的支援是選擇性的。 VSSCI 隨插即用的會使用這項功能必須初始化它函式指標和使用者資料的變數來 `NULL`, ，和它必須呼叫 rename 函式，除非它已被授與其中一個。 它應該也準備好來保留它的值，或變更以回應新的呼叫 `SccSetOption`。 這將不會在原始檔控制命令作業，但是命令之間可能發生的時機。  
  
## SCC\_OPT\_SCCCHECKOUTONLY  
 如果設定為 nOption `SCC_OPT_SCCCHECKOUTONLY`, ，IDE 會指示，目前開啟的專案中的檔案應該永遠不會被簽出以手動方式透過原始檔控制系統的使用者介面。 相反地，檔案應該只能透過外掛程式 IDE 控制下的原始檔控制簽出。 如果 `dwValue` 設為 `SCC_OPT_SCO_NO`, ，這表示檔案通常外掛程式中處理，並且可以透過 UI 原始檔控制簽出。 如果 `dwValue` 設為 `SCC_OPT_SCO_YES`, ，然後只外掛程式允許簽出檔案，而原始檔控制系統 UI 應該不會叫用。 這是針對的 IDE 可能具有 「 虛擬檔案 」 對簽出，只能透過 IDE 的情況。  
  
## SCC\_OPT\_SHARESUBPROJ  
 如果`nOption` 設為 `SCC_OPT_SHARESUBPROJ`, ，IDE 會測試是否從原始檔控制新增檔案時，原始檔控制外掛程式可以使用指定的本機資料夾。 值 `dwVal` 在此情況下並不重要參數。 如果外掛程式可讓 IDE，來指定本機目的地資料夾所在的檔案會新增從來源控制何時 [SccAddFromScc](../extensibility/sccaddfromscc-function.md) 呼叫，則必須傳回外掛程式 `SCC_I_SHARESUBPROJOK` 時 `SccSetOption` 函式呼叫。 接著會使用 IDE `lplpFileNames` 參數 `SccAddFromScc` 傳遞目的地資料夾中的函式。 外掛程式會使用該目的地資料夾將加入從原始檔控制的檔案。 如果外掛程式不會傳回 `SCC_I_SHARESUBPROJOK` 時 `SCC_OPT_SHARESUBPROJ` 設定選項時，IDE 會假設外掛程式是能夠將檔案加入只在目前的本機資料夾中。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)