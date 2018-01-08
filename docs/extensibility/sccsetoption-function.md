---
title: "SccSetOption 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccSetOption
helpviewer_keywords: SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 70fe624984adce58191ee7d354185eac0bb527ed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="sccsetoption-function"></a>SccSetOption 函式
此函式設定選項可控制行為的原始檔控制外掛程式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccSetOption(  
   LPVOID pvContext,  
   LONG   nOption,  
   LONG   dwVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 pvContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 nOption  
 [in]正在設定選項。  
  
 dwVal  
 [in]選項的設定。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功設定選項。|  
|SCC_I_SHARESUBPROJOK|時所傳回`nOption`已`SCC_OPT_SHARESUBPROJ`和原始檔控制外掛程式可讓 IDE 來設定目的地資料夾。|  
|SCC_E_OPNOTSUPPORTED|此選項未設定，不應依賴在。|  
  
## <a name="remarks"></a>備註  
 IDE 會呼叫此函式可控制行為的原始檔控制外掛程式。 第一個參數， `nOption`，表示正在設定值，第二個， `dwVal`，表示要如何處理該值。 外掛程式會儲存這項資訊與相關聯`pvContext``,`讓 IDE 必須呼叫此函式之後呼叫[SccInitialize](../extensibility/sccinitialize-function.md) (但是不一定在每次呼叫之後[SccOpenProject](../extensibility/sccopenproject-function.md))。  
  
 選項及其值的摘要：  
  
|`nOption`|`dwValue`|描述|  
|---------------|---------------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|啟用/停用背景事件佇列。|  
|`SCC_OPT_USERDATA`|任意值|指定要傳遞給使用者值[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)回呼函式。|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|指出是否在 IDE 目前支援取消作業。|  
|`SCC_OPT_NAMECHANGEPFN`|指標[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)回呼函式|設定名稱變更回撥函式的指標。|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|指出是否要檢查超出其檔，以手動方式 （透過原始檔控制使用者介面），或是否他們必須先簽出原始檔控制外掛程式只能透過允許 IDE。|  
|`SCC_OPT_SHARESUBPROJ`|N/A|如果原始檔控制外掛程式可讓在 IDE 以指定的局部的專案資料夾，此外掛程式就會傳回`SCC_I_SHARESUBPROJOK`。|  
  
## <a name="sccopteventqueue"></a>SCC_OPT_EVENTQUEUE  
 如果`nOption`是`SCC_OPT_EVENTQUEUE`，IDE 會停用 （或重新啟用） 背景處理。 比方說，期間編譯，IDE 可能會指示原始檔控制外掛程式，以停止在閒置處理的任何類型。 之後在編譯中，它會重新啟用背景處理來保持最新的隨插即用中的事件佇列中。 對應至`SCC_OPT_EVENTQUEUE`值`nOption`，有兩個可能的值為`dwVal`，也就是`SCC_OPT_EQ_ENABLE`和`SCC_OPT_EQ_DISABLE`。  
  
## <a name="sccopthascancelmode"></a>SCC_OPT_HASCANCELMODE  
 如果值`nOption`是`SCC_OPT_HASCANCELMODE`，IDE，可讓使用者取消長時間作業。 設定`dwVal`至`SCC_OPT_HCM_NO`（預設值） 表示 IDE 有無取消 5d; 模式。 如果想要能夠取消使用者原始檔控制外掛程式必須提供自己的 [取消] 按鈕。 `SCC_OPT_HCM_YES`指出 IDE 提供取消作業，因此 SCC 外掛程式不需要它自己的 [取消] 按鈕，顯示的能力。 如果在 IDE 設定`dwVal`至`SCC_OPT_HCM_YES`，則已準備好回應`SCC_MSG_STATUS`和`DOCANCEL`訊息傳送至`lpTextOutProc`回呼函式 (請參閱[LPTEXTOUTPROC](../extensibility/lptextoutproc.md))。 如果在 IDE 未設定這個變數，外掛程式不應該傳送這兩則訊息。  
  
## <a name="sccoptnamechangepfn"></a>SCC_OPT_NAMECHANGEPFN  
 如果 nOption 設`SCC_OPT_NAMECHANGEPFN`，和原始檔控制外掛程式及 IDE 讓它，外掛程式可以實際重新命名或移動檔案在原始檔控制作業期間。 `dwVal`會設定為型別的函式指標[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)。 在原始檔控制作業時，外掛程式可以呼叫此函式，在三個參數中傳遞。 這些是舊名稱 （以完整路徑） 的檔案，該檔案，以及一個指向具有 ide 的相關資訊的新名稱 （以完整路徑）。 在 IDE 中這個最後一個指標會傳送藉由呼叫`SccSetOption`與`nOption`設`SCC_OPT_USERDATA`，與`dwVal`指向資料。 此函式的支援是選擇性的。 VSSCI 隨-使用這項功能必須初始化的至其函式指標和使用者資料變數`NULL`，而且它必須呼叫重新命名函式，除非它具有其中一個。 它應該也準備，無法保留已授與它的值，或變更至新的呼叫，以回應`SccSetOption`。 這將不會進行原始檔控制命令的作業，但它可能會發生命令之間。  
  
## <a name="sccoptscccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY  
 如果設為 nOption `SCC_OPT_SCCCHECKOUTONLY`，IDE 會指出，目前開啟的專案中的檔案應該永遠不會先檢查手動透過原始檔控制系統的使用者介面。 相反地，檔案應該只能透過外掛程式 IDE 控制下的原始檔控制簽出。 如果`dwValue`設`SCC_OPT_SCO_NO`，這表示檔案要視為正常外掛程式，並且可以透過 UI 原始檔控制簽出。 如果`dwValue`設`SCC_OPT_SCO_YES`，然後只外掛程式可以簽出檔案，而且應該不會叫用原始檔控制系統的 UI。 這是的情況下 IDE 可能會需要有 「 虛擬檔案 」 只能透過 IDE 簽出有意義。  
  
## <a name="sccoptsharesubproj"></a>SCC_OPT_SHARESUBPROJ  
 如果`nOption`設`SCC_OPT_SHARESUBPROJ`，IDE 會測試是否從原始檔控制新增檔案時，原始檔控制外掛程式可以使用指定的本機資料夾。 值`dwVal`在此情況下並不重要參數。 如果使用這個外掛程式來指定檔案來源中的加入其中的本機目的資料夾 IDE 負責控制何時[SccAddFromScc](../extensibility/sccaddfromscc-function.md)呼叫時，則必須傳回外掛程式`SCC_I_SHARESUBPROJOK`時`SccSetOption`函式呼叫。 接著會使用 IDE`lplpFileNames`參數`SccAddFromScc`傳遞目的地資料夾中的函式。 外掛程式會使用該目的地資料夾將加入從原始檔控制的檔案。 如果外掛程式不會傳回`SCC_I_SHARESUBPROJOK`時`SCC_OPT_SHARESUBPROJ`設定選項時，IDE 會假設外掛程式無法將檔案加入只在目前的本機資料夾。  
  
## <a name="see-also"></a>請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)