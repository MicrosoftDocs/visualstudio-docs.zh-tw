---
title: "SccAddFromScc 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccAddFromScc"
helpviewer_keywords: 
  - "SccAddFromScc 函式"
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# SccAddFromScc 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函數可讓使用者瀏覽已在原始檔控制系統的檔案，並接著將這些檔案目前的專案。 比方說，此函式可進入常見的標頭檔目前的專案而不複製檔案。 傳回陣列的檔案， `lplpFileNames`, ，包含使用者想要新增至 IDE 專案的檔案清單。  
  
## 語法  
  
```cpp#  
SCCRTN SccAddFromScc (  
   LPVOID   pvContext,  
   HWND     hWnd,  
   LPLONG   lpnFiles,  
   LPCSTR** lplpFileNames  
);  
```  
  
#### 參數  
 pvContext  
 \[\] in原始檔控制外掛程式內容結構。  
  
 hWnd  
 \[\] in原始檔控制外掛程式可以使用為父代，它會提供任何對話方塊 IDE 視窗控制代碼。  
  
 lpnFiles  
 \[in、 out\]緩衝區中新增的檔案數目。 \(這是 `NULL` 如果指向的記憶體 `lplpFileNames` 會釋出。 請參閱 \< 備註 \> 以取得詳細資料\)。  
  
 lplpFileNames  
 \[in、 out\]沒有目錄路徑的所有檔案名稱的指標陣列。 這個陣列是配置和釋出原始檔控制外掛程式。 如果 `lpnFiles` \= 1 和 `lplpFileNames` 不 `NULL`, ，陣列中的第一個名稱所指 `lplpFileNames` 包含目的地資料夾。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|檔案已成功位於並加入至專案。|  
|SCC\_I\_OPERATIONCANCELED|作業已取消，造成任何影響。|  
|SCC\_I\_RELOADFILE|需要重新載入檔案或專案。|  
  
## 備註  
 IDE 會呼叫此函式。 如果原始檔控制外掛程式支援指定的本機目的資料夾，IDE 會將 `lpnFiles` \= 1，並傳遞到本機資料夾名稱 `lplpFileNames`。  
  
 當呼叫 `SccAddFromScc` 函式傳回時，外掛程式已指派值，以 `lpnFiles` 和 `lplpFileNames`, ，為所需的檔案名稱陣列配置記憶體 \(請注意，此配置會取代在指標 `lplpFileNames`\)。 原始檔控制外掛程式負責將所有檔案都放入使用者的目錄或指定的目的地資料夾中。 然後，IDE 會將檔案加入至 IDE 專案。  
  
 最後，IDE 會呼叫此函式第二次，傳入 `NULL` 的 `lpnFiles`。 這會解譯為特殊的訊號，原始檔控制外掛程式中的檔案名稱陣列配置的記憶體釋放 `lplpFileNames``.`  
  
 `lplpFileNames` 是 `char ***` 指標。 原始檔控制外掛程式會將檔案名稱，因此，以標準方式傳遞的清單，此 api 的指標陣列的指標。  
  
> [!NOTE]
>  VSSCI API 的初始版本未提供一個方法來指示加入之檔案的目標專案。 要做到的語意，這一點 `lplpFIleNames` 參數已增強為方便輸入\/輸出參數，而不是輸出參數。 如果只指定單一檔案，也就是指向的值由 `lpnFiles` \= 1，則第一個項目 `lplpFileNames` 包含目標資料夾。 若要使用這些新的語意，IDE 會呼叫 `SccSetOption` 函式與 `nOption`參數設定為 `SCC_OPT_SHARESUBPROJ`。 如果原始檔控制外掛程式不支援語意 \(semantics\)，它會傳回 `SCC_E_OPTNOTSUPPORTED`。 這麼做的話會停用使用 **從原始檔控制的新增** 功能。 如果外掛程式支援 **從原始檔控制的新增** 功能 \(`SCC_CAP_ADDFROMSCC`\)，則它必須支援新的語意 \(semantics\)，並傳回 `SCC_I_SHARESUBPROJOK`。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)