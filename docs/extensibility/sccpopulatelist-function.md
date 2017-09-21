---
title: "SccPopulateList 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccPopulateList"
helpviewer_keywords: 
  - "SccPopulateList 函式"
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccPopulateList 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

此函式會更新為特定的原始檔控制命令的檔案清單，並提供給所有指定檔案的原始檔控制狀態。  
  
## 語法  
  
```cpp#  
SCCRTN SccPopulateList (  
   LPVOID          pvContext,  
   enum SCCCOMMAND nCommand,  
   LONG            nFiles,  
   LPCSTR*         lpFileNames,  
   POPLISTFUNC     pfnPopulate,  
   LPVOID          pvCallerData,  
   LPLONG          lpStatus,  
   LONG            fOptions  
);  
```  
  
#### 參數  
 pvContext  
 \[\] in原始檔控制外掛程式內容結構。  
  
 nCommand  
 \[\] in將會套用到所有的檔案，在原始檔控制命令 `lpFileNames` 陣列 \(請參閱 [指令碼](../extensibility/command-code-enumerator.md) 可能命令的清單\)。  
  
 nFiles  
 \[\] in中的檔案數目 `lpFileNames` 陣列。  
  
 lpFileNames  
 \[\] in已知的 ide 的檔案名稱的陣列。  
  
 pfnPopulate  
 \[\] inIDE 回呼函式呼叫來新增和移除檔案 \(請參閱 [POPLISTFUNC](../extensibility/poplistfunc.md) 如需詳細資訊\)。  
  
 pvCallerData  
 \[\] in要傳遞至回呼函式不變的值。  
  
 lpStatus  
 \[in、 out\]原始檔控制外掛程式，以傳回每個檔案的狀態旗標的陣列。  
  
 Stored  
 \[\] in命令旗標 \(請參閱 「 PopulateList 旗標 」 一節 [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md) 如需詳細資訊\)。  
  
## 傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一:  
  
|值|描述|  
|-------|--------|  
|SCC\_OK|成功。|  
|SCC\_E\_NONSPECIFICERROR|非特定的失敗。|  
  
## 備註  
 此函式會檢查目前狀態的檔案清單。 它會使用 `pfnPopulate` 檔案不相符的準則時，通知呼叫端的回呼函式 `nCommand`。 例如，如果命令是 `SCC_COMMAND_CHECKIN` 清單中的檔案未簽出，然後回呼用來通知呼叫端。 有時候，原始檔控制外掛程式可能會發現，可能會在命令中，並將其新增其他檔案。 這可讓，比方說，Visual Basic 使用者簽出.bmp 檔案會使用自己的專案，但不是會出現在 Visual Basic 專案檔案中。 在使用者選擇 **取得** 命令在 IDE 中。 IDE 會顯示它認為使用者可以取得，所有檔案的清單顯示的清單，之前 `SccPopulateList` 呼叫函式以確保清單以顯示最新狀態。  
  
## 範例  
 IDE 會建置它認為使用者可以取得檔案的清單。 它會顯示此清單之前，它會呼叫 `SccPopulateList` 函式，讓原始檔控制外掛程式有機會新增和刪除清單中的檔案。 外掛程式會修改清單所指定的回呼函式 \(請參閱 [POPLISTFUNC](../extensibility/poplistfunc.md) 如需詳細資訊\)。  
  
 外掛程式會繼續呼叫 `pfnPopulate` 函式，可加入及刪除檔案，直到它完成，然後傳回 `SccPopulateList` 函式。 IDE 就可以顯示的清單。`lpStatus` 陣列代表 IDE 所傳送的原始清單中的所有檔案。 這些檔案此外若要讓所有的狀態中外掛程式的填滿使用的回呼函式。  
  
> [!NOTE]
>  原始檔控制外掛程式都可以直接從這個函式，讓清單，因為它是立即傳回。 如果外掛程式實作此函式，它可以指出此項設定 `SCC_CAP_POPULATELIST` 功能位元旗標的第一個呼叫中 [SccInitialize](../extensibility/sccinitialize-function.md)。 根據預設，外掛程式應該永遠假設傳入的所有項目是檔案。 不過，如果在 IDE 設定 `SCC_PL_DIR` 加上旗標 `fOptions` 參數，傳遞的所有項目都視為目錄。 外掛程式應該在目錄中加入所屬的所有檔案。 IDE 永遠不會將傳入檔案和目錄的混合。  
  
## 請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)   
 [指令碼](../extensibility/command-code-enumerator.md)