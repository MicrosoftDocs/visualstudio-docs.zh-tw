---
title: SccPopulateList 函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 03fedd4854103186eb9d6f034d11a8e0f8b11c9c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279561"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此函式會更新特定的原始檔控制命令的檔案清單，並提供對指定的所有檔案的原始檔控制狀態。  
  
## <a name="syntax"></a>語法  
  
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
  
#### <a name="parameters"></a>參數  
 pvContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 nCommand  
 [in]將會套用到所有的檔案，在原始檔控制命令`lpFileNames`陣列 (請參閱 <<c2> [ 的指令碼](../extensibility/command-code-enumerator.md)取得一份可能命令)。  
  
 nFiles  
 [in]中的檔案數目`lpFileNames`陣列。  
  
 lpFileNames  
 [in]Ide 的已知的檔案名稱的陣列。  
  
 pfnPopulate  
 [in]IDE 回呼函式呼叫來新增和移除檔案 (請參閱[POPLISTFUNC](../extensibility/poplistfunc.md)如需詳細資訊)。  
  
 pvCallerData  
 [in]要傳遞的值不變之回呼函式。  
  
 lpStatus  
 [in、 out]原始檔控制外掛程式傳回每個檔案的狀態旗標的陣列。  
  
 Stored  
 [in]命令旗標 (請參閱 「 PopulateList 旗標 」 一節[特定的命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)如需詳細資訊)。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|成功。|  
|SCC_E_NONSPECIFICERROR|不明確的失敗。|  
  
## <a name="remarks"></a>備註  
 此函式會檢查檔案的目前狀態的清單。 它會使用`pfnPopulate`回呼函式的檔案類型不符合的準則時告知呼叫端`nCommand`。 例如，如果命令是`SCC_COMMAND_CHECKIN`和清單中的檔案尚未簽出，則回呼會用來通知呼叫端。 有時候，原始檔控制外掛程式可能會發現其他檔案，可能是命令的一部分，並將其新增。 這可讓，比方說，Visual Basic 使用者簽出.bmp 檔案使用他 / 她的專案，但未出現在 Visual Basic 專案檔。 使用者選擇**取得**命令在 IDE 中。 IDE 會顯示一份它認為可以取得使用者，所有檔案，但之前顯示的清單，`SccPopulateList`呼叫函式可確保是最新的顯示清單。  
  
## <a name="example"></a>範例  
 IDE 會建置它認為使用者可以取得檔案的清單。 它會顯示此清單之前，它會呼叫`SccPopulateList`函式中，讓原始檔控制外掛程式有機會新增並從清單中刪除檔案。 外掛程式會修改清單藉由呼叫指定的回呼函式 (請參閱[POPLISTFUNC](../extensibility/poplistfunc.md)如需詳細資訊)。  
  
 若要呼叫的外掛程式會繼續`pfnPopulate`函式，可新增和刪除檔案，直到它已完成，並接著會傳回從`SccPopulateList`函式。 然後，IDE 可以顯示其清單。 `lpStatus`陣列都表示原始 IDE 所傳入的清單中的所有檔案。 在所有這些檔案除了使狀態中外掛程式的填滿使用的回呼函式。  
  
> [!NOTE]
>  原始檔控制外掛程式一律可以選擇只會立即傳回從此函式，因為它是保留的清單。 如果外掛程式實作此函式，可能表示這藉由設定`SCC_CAP_POPULATELIST`中的第一個呼叫的功能位元旗標[SccInitialize](../extensibility/sccinitialize-function.md)。 根據預設，外掛程式應該永遠假設傳入的所有項目是檔案。 不過，如果設定 IDE`SCC_PL_DIR`加上旗標在`fOptions`參數，傳入的所有項目都視為目錄。 外掛程式應該在目錄中新增所屬的所有檔案。 IDE 永遠不會將傳入檔案和目錄的混合。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)   
 [命令碼](../extensibility/command-code-enumerator.md)

