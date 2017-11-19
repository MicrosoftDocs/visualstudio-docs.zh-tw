---
title: "SccPopulateList 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccPopulateList
helpviewer_keywords: SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 60f22174ac217a66f860415de898240d41d9a631
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="sccpopulatelist-function"></a>SccPopulateList 函式
此函式更新的特定來源控制命令的檔案清單，並提供所有指定檔案的原始檔控制狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
#### <a name="parameters"></a>參數  
 pvContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 nCommand  
 [in]將會套用至所有檔案在原始檔控制命令`lpFileNames`陣列 (請參閱[的指令碼](../extensibility/command-code-enumerator.md)取得一份可能的命令)。  
  
 nFiles  
 [in]中的檔案數目`lpFileNames`陣列。  
  
 lpFileNames  
 [in]IDE 已知的檔案名稱陣列。  
  
 pfnPopulate  
 [in]IDE 回呼函式呼叫來新增和移除檔案 (請參閱[POPLISTFUNC](../extensibility/poplistfunc.md)如需詳細資訊)。  
  
 pvCallerData  
 [in]要傳遞的值保持不變，回呼函式。  
  
 lpStatus  
 [in、 out]原始檔控制外掛程式傳回每個檔案的狀態旗標的陣列。  
  
 fOptions  
 [in]命令旗標 (請參閱 「 PopulateList 旗標 」 一節[特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)如需詳細資訊)。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|說明|  
|-----------|-----------------|  
|SCC_OK|成功。|  
|SCC_E_NONSPECIFICERROR|不明確的失敗。|  
  
## <a name="remarks"></a>備註  
 此函式會檢查檔案的目前狀態的清單。 它會使用`pfnPopulate`檔案不相符的準則時，告知呼叫端的回呼函式`nCommand`。 例如，如果命令是`SCC_COMMAND_CHECKIN`，而且在清單中的檔案未簽出，則回呼用來告知呼叫端。 有時候，原始檔控制外掛程式可能會發現可以命令的一部分，並且將它們加入其他檔案。 這可讓，例如 Visual Basic 使用者簽出.bmp 檔案會使用他或她的專案，但不是會出現在 Visual Basic 專案檔中。 使用者選擇**取得**命令在 IDE 中。 IDE 會顯示一份其認定使用者也可以取得的所有檔案之前會顯示清單，但`SccPopulateList`呼叫函式可確定所要顯示清單是最新狀態。  
  
## <a name="example"></a>範例  
 IDE 會建置一份其認定使用者也可以取得的檔案。 它會顯示此清單之前，它會呼叫`SccPopulateList`函式，讓原始檔控制外掛程式有機會新增和刪除清單中的檔案。 外掛程式會修改清單藉由呼叫指定的回呼函式 (請參閱[POPLISTFUNC](../extensibility/poplistfunc.md)如需詳細資訊)。  
  
 呼叫此外掛程式會繼續`pfnPopulate`函式，以新增和刪除的檔案，直到完成，然後再傳回`SccPopulateList`函式。 IDE 可以顯示其清單。 `lpStatus`陣列都代表原始 IDE 所傳入的清單中的所有檔案。 外掛程式的填滿所有這些檔案除了要進行的狀態中使用的回呼函式。  
  
> [!NOTE]
>  原始檔控制外掛程式一律會有選項可只會立即傳回從這個函式，因為它是保留的清單。 如果外掛程式會實作此函式，這可能表示這藉由設定`SCC_CAP_POPULATELIST`功能位元旗標的第一個呼叫中[SccInitialize](../extensibility/sccinitialize-function.md)。 根據預設，外掛程式應該永遠假設傳入的所有項目是檔案。 不過，如果在 IDE 設定`SCC_PL_DIR`加上旗標`fOptions`參數，傳遞的所有項目都被視為目錄。 外掛程式應該在目錄中加入隸屬的所有檔案。 IDE 永遠不會將傳入檔案和目錄的混合。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [特定的命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)   
 [指令碼](../extensibility/command-code-enumerator.md)