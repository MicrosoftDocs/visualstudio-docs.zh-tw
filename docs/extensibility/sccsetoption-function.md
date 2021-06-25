---
description: 此函式會設定控制原始檔控制外掛程式行為的選項。
title: SccSetOption 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 18e33cbb8dbee9b332456826ed33e46e4d2e76de
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904096"
---
# <a name="sccsetoption-function"></a>SccSetOption 函式
此函式會設定控制原始檔控制外掛程式行為的選項。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccSetOption(
   LPVOID pvContext,
   LONG   nOption,
   LONG   dwVal
);
```

#### <a name="parameters"></a>參數
 pvCoNtext

在原始檔控制外掛程式內容結構。

 nOption

在正在設定的選項。

 dwVal

在選項的設定。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功設定此選項。|
|SCC_I_SHARESUBPROJOK|如果 `nOption` was `SCC_OPT_SHARESUBPROJ` 和原始檔控制外掛程式允許 IDE 設定目的資料夾，則會傳回。|
|SCC_E_OPNOTSUPPORTED|未設定此選項，因此不應該依賴此選項。|

## <a name="remarks"></a>備註
 IDE 會呼叫這個函式，以控制原始檔控制外掛程式的行為。 第一個參數（ `nOption` ）表示正在設定的值，而第二個參數則 `dwVal` 表示該值的處理方式。 外掛程式會儲存與相關聯的這項資訊 `pvContext``,` ，因此，IDE 必須在呼叫 [SccInitialize](../extensibility/sccinitialize-function.md) (之後呼叫這個函式，但不一定要在每次呼叫 [SccOpenProject](../extensibility/sccopenproject-function.md)) 之後呼叫這個函數。

 選項及其值的摘要：

|`nOption`|`dwValue`|描述|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|啟用/停用背景事件佇列。|
|`SCC_OPT_USERDATA`|任意值|指定要傳遞至 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) 回呼函數的使用者值。|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|指出 IDE 目前是否支援取消作業。|
|`SCC_OPT_NAMECHANGEPFN`|[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)回呼函式的指標|設定名稱變更回呼函數的指標。|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|指出 IDE 是否允許透過原始檔控制使用者介面，以手動方式簽出其檔案 () 或是否必須透過原始檔控制外掛程式簽出它們。|
|`SCC_OPT_SHARESUBPROJ`|N/A|如果原始檔控制外掛程式允許 IDE 指定本機專案資料夾，外掛程式就會傳回 `SCC_I_SHARESUBPROJOK` 。|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 如果 `nOption` 為 `SCC_OPT_EVENTQUEUE` ，則會停用 IDE (或重新啟用) 背景處理。 例如，在編譯期間，IDE 可能會指示原始檔控制外掛程式停止任何種類的閒置處理。 編譯之後，它會重新啟用背景處理，讓外掛程式的事件佇列保持在最新狀態。 對應到的 `SCC_OPT_EVENTQUEUE` 值 `nOption` ，有兩個可能的值 `dwVal` ，亦即 `SCC_OPT_EQ_ENABLE` 和 `SCC_OPT_EQ_DISABLE` 。

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 如果的值 `nOption` 為 `SCC_OPT_HASCANCELMODE` ，則 IDE 可讓使用者取消長時間的作業。 將設定 `dwVal` 為 `SCC_OPT_HCM_NO` (預設) 表示 IDE 沒有取消模式。 如果原始檔控制外掛程式希望使用者能夠取消，則必須提供自己的 [取消] 按鈕。 `SCC_OPT_HCM_YES` 指出 IDE 提供取消作業的功能，因此 SCC 外掛程式不需要顯示自己的 [取消] 按鈕。 如果 IDE 將設定 `dwVal` 為 `SCC_OPT_HCM_YES` ，則已準備好回應 `SCC_MSG_STATUS` 和 `DOCANCEL` 傳送至回呼函式的訊息 `lpTextOutProc` (查看 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)) 。 如果 IDE 未設定此變數，則外掛程式不應傳送這兩個訊息。

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 如果 nOption 設定為 `SCC_OPT_NAMECHANGEPFN` ，而且原始檔控制外掛程式和 IDE 都允許，則外掛程式在原始檔控制作業期間可以實際重新命名或移動檔案。 `dwVal`將會設定為[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)類型的函式指標。 在原始檔控制作業期間，外掛程式可以呼叫這個函式，並傳入三個參數。 這些是舊名稱 (具有檔案的完整路徑) 、新名稱 (具有該檔案的完整路徑) ，以及與 IDE 相關之資訊的指標。 IDE 會使用 `SccSetOption` `nOption` 將設定為的來呼叫 `SCC_OPT_USERDATA` ，並 `dwVal` 指向資料，以在最後一個指標中傳送。 這項功能的支援是選擇性的。 使用這項功能的 VSSCI 外掛程式，必須將其函式指標和使用者資料變數初始化為 `NULL` ，而且除非已提供命名函式，否則它不能呼叫重新命名函數。 您也應該準備保存所提供的值，或將它變更為回應的新呼叫 `SccSetOption` 。 這不會發生在原始檔控制命令作業的中間，但是命令之間可能會發生這種情況。

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 如果 nOption 設為 `SCC_OPT_SCCCHECKOUTONLY` ，則 IDE 會指出永遠不應該透過原始檔控制系統的使用者介面，手動簽出目前開啟之專案中的檔案。 相反地，應該只透過 IDE 控制項下的原始檔控制外掛程式簽出檔案。 如果 `dwValue` 設定為 `SCC_OPT_SCO_NO` ，則表示檔案應該由外掛程式正常處理，並可透過原始檔控制 UI 簽出。 如果 `dwValue` 設定為 `SCC_OPT_SCO_YES` ，則只允許外掛程式簽出檔案，而且不應該叫用原始檔控制系統的 UI。 這是在 IDE 可能具有「虛擬檔案」的情況下，只在 IDE 中簽出有意義的情況。

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 如果 `nOption` 設定為 `SCC_OPT_SHARESUBPROJ` ，則 IDE 會測試當您從原始檔控制加入檔案時，原始檔控制外掛程式是否可以使用指定的本機資料夾。 `dwVal`在此情況下，參數的值並不重要。 如果外掛程式可讓 IDE 指定在呼叫 [SccAddFromScc](../extensibility/sccaddfromscc-function.md) 時，從原始檔控制加入檔案的本機目的資料夾，則在呼叫函式時，外掛程式必須傳回 `SCC_I_SHARESUBPROJOK` `SccSetOption` 。 然後，IDE 會使用函式的 `lplpFileNames` 參數 `SccAddFromScc` 傳遞至目的資料夾。 外掛程式會使用該目的資料夾來放置從原始檔控制加入的檔案。 如果設定選項時不會傳回外掛程式 `SCC_I_SHARESUBPROJOK` `SCC_OPT_SHARESUBPROJ` ，IDE 會假設外掛程式只能在目前的本機資料夾中新增檔案。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
