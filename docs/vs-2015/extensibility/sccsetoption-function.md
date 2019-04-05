---
title: SccSetOption 函式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7f2660ca99d8704f5dd8e7b9aa66c9c8fc5bdbb6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940311"
---
# <a name="sccsetoption-function"></a>SccSetOption 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

此函式會設定控制行為的原始檔控制外掛程式的選項。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功設定的選項。|  
|SCC_I_SHARESUBPROJOK|時所傳回`nOption`已`SCC_OPT_SHARESUBPROJ`和原始檔控制外掛程式可讓 IDE 設定目的地資料夾。|  
|SCC_E_OPNOTSUPPORTED|選擇不設定，且不能指望。|  
  
## <a name="remarks"></a>備註  
 IDE 會呼叫此函式可控制原始檔控制外掛程式的行為。 第一個參數， `nOption`，表示正在設定值，第二個， `dwVal`，指出如何處理該值。 外掛程式會儲存這項資訊與相關聯`pvContext``,`讓 IDE 必須呼叫此函式之後呼叫[SccInitialize](../extensibility/sccinitialize-function.md) (但不是一定在每次呼叫之後[SccOpenProject](../extensibility/sccopenproject-function.md))。  
  
 選項及其值的摘要：  
  
|`nOption`|`dwValue`|描述|  
|---------------|---------------|-----------------|  
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|啟用/停用背景事件佇列。|  
|`SCC_OPT_USERDATA`|任意值|指定的使用者值，要傳遞給[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)回呼函式。|  
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|指出是否在 IDE 目前支援取消作業。|  
|`SCC_OPT_NAMECHANGEPFN`|指標[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)回呼函式|設定的名稱變更的回呼函式的指標。|  
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|表示 IDE 允許從它的檔案，以手動方式 （透過原始檔控制使用者介面） 檢查，或是否他們必須先簽出只能透過原始檔控制外掛程式。|  
|`SCC_OPT_SHARESUBPROJ`|N/A|如果原始檔控制外掛程式可讓在 IDE，以指定的本機專案資料夾，外掛程式會傳回`SCC_I_SHARESUBPROJOK`。|  
  
## <a name="sccopteventqueue"></a>SCC_OPT_EVENTQUEUE  
 如果`nOption`是`SCC_OPT_EVENTQUEUE`，IDE 會停用 （或重新啟用） 背景處理。 比方說，在編譯時，IDE 可能會指示原始檔控制外掛程式，以停止在閒置處理任何類型。 之後在編譯中，它會重新啟用背景處理，將隨插即用中的事件佇列中最新狀態。 對應至`SCC_OPT_EVENTQUEUE`的值`nOption`，有兩個可能的值，如`dwVal`，亦即`SCC_OPT_EQ_ENABLE`和`SCC_OPT_EQ_DISABLE`。  
  
## <a name="sccopthascancelmode"></a>SCC_OPT_HASCANCELMODE  
 如果值`nOption`是`SCC_OPT_HASCANCELMODE`，IDE 可讓使用者取消長時間作業。 設定`dwVal`至`SCC_OPT_HCM_NO`（預設值） 會指示 IDE 有無取消模式。 原始檔控制外掛程式在想要能夠取消使用者必須提供它自己的 [取消] 按鈕。 `SCC_OPT_HCM_YES` 表示 IDE 提供取消作業，因此不需要外掛程式 SCC，這是它自己的 [取消] 按鈕，顯示的功能。 如果 IDE 設定`dwVal`要`SCC_OPT_HCM_YES`，則已準備好回應`SCC_MSG_STATUS`並`DOCANCEL`訊息傳送至`lpTextOutProc`回呼函式 (請參閱[LPTEXTOUTPROC](../extensibility/lptextoutproc.md))。 如果 IDE 不會設定這個變數，外掛程式應該傳送這兩個訊息。  
  
## <a name="sccoptnamechangepfn"></a>SCC_OPT_NAMECHANGEPFN  
 如果 nOption 設`SCC_OPT_NAMECHANGEPFN`，和原始檔控制外掛程式和 IDE 可讓它、 外掛程式可以實際重新命名或移動檔案在原始檔控制作業期間。 `dwVal`將會設定為型別的函式指標[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)。 在原始檔控制作業時，外掛程式可以呼叫此函式，在三個參數中傳遞。 這些是檔案的舊名稱 （具有完整路徑），該檔案，以及具有 ide 的相關資訊的指標 （含有完整路徑） 的新名稱。 IDE 中這個最後一個指標傳送藉由呼叫`SccSetOption`具有`nOption`設為`SCC_OPT_USERDATA`，使用`dwVal`指向的資料。 此函式的支援是選擇性的。 VSSCI 隨插即用-，會使用這項功能必須初始化其函式指標和使用者資料的變數至`NULL`，而且它必須呼叫重新命名函式，除非已獲得其中一個。 它應該也準備好為它所提供的值，或變更以回應新的呼叫`SccSetOption`。 這不會進行來源控制命令的作業，但它可能會發生命令之間。  
  
## <a name="sccoptscccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY  
 如果設定為 nOption `SCC_OPT_SCCCHECKOUTONLY`，IDE 會指出，目前開啟的專案中的檔案應該永遠不會被簽出以手動方式透過原始檔控制系統的使用者介面。 相反地，檔案應該只能透過外掛程式 IDE 控制下的原始檔控制簽出。 如果`dwValue`設為`SCC_OPT_SCO_NO`，這表示該檔案通常外掛程式中處理，並可以透過 UI 原始檔控制簽出。 如果`dwValue`設為`SCC_OPT_SCO_YES`，然後只外掛程式允許簽出檔案，而原始檔控制系統的 UI 應該不會叫用。 這是 IDE 的可能具有 「 虛擬檔案 」 只能透過 IDE 簽出有意義的情況下。  
  
## <a name="sccoptsharesubproj"></a>SCC_OPT_SHARESUBPROJ  
 如果`nOption`設為`SCC_OPT_SHARESUBPROJ`，IDE 會測試是否從原始檔控制新增檔案時，原始檔控制外掛程式可以使用指定的本機資料夾。 值`dwVal`在此情況下並不重要參數。 如果外掛程式允許 IDE，以指定的本機目的地資料夾，其中的檔案會新增從來源控制何時[SccAddFromScc](../extensibility/sccaddfromscc-function.md)呼叫，則必須傳回外掛程式`SCC_I_SHARESUBPROJOK`當`SccSetOption`函式呼叫。 接著會使用 IDE`lplpFileNames`參數的`SccAddFromScc`傳遞目的地資料夾中的函式。 外掛程式會使用該目的地資料夾將加入從原始檔控制的檔案。 如果外掛程式不會傳回`SCC_I_SHARESUBPROJOK`當`SCC_OPT_SHARESUBPROJ`設定選項時，IDE 會假設外掛程式是能夠將檔案新增只能在目前的本機資料夾中。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccAddFromScc](../extensibility/sccaddfromscc-function.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)   
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
