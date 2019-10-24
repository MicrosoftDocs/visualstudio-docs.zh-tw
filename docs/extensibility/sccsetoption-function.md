---
title: SccSetOption 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f48cb84a64c036b373308dfe29bfaf5d2e028b91
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720562"
---
# <a name="sccsetoption-function"></a>SccSetOption 函式
此函式會設定選項，以控制原始檔控制外掛程式的行為。

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

在原始檔控制外掛程式的內容結構。

 nOption

在正在設定的選項。

 dwVal

在選項的設定。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式執行應會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功設定選項。|
|SCC_I_SHARESUBPROJOK|如果已 `SCC_OPT_SHARESUBPROJ` `nOption`，且原始檔控制外掛程式允許 IDE 設定目的地資料夾，則傳回。|
|SCC_E_OPNOTSUPPORTED|未設定此選項，因此不應依賴。|

## <a name="remarks"></a>備註
 IDE 會呼叫這個函式，以控制原始檔控制外掛程式的行為。 第一個參數（`nOption`）表示要設定的值，而第二個是 `dwVal`，表示該如何處理該值。 外掛程式會儲存與 `pvContext``,` 相關聯的這項資訊，因此在呼叫[SccInitialize](../extensibility/sccinitialize-function.md) （但不一定是在每次呼叫[SccOpenProject](../extensibility/sccopenproject-function.md)之後）時，IDE 必須呼叫此函式。

 選項及其值的摘要：

|`nOption`|`dwValue`|描述|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|啟用/停用背景事件佇列。|
|`SCC_OPT_USERDATA`|任意值|指定要傳遞至[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)回呼函數的使用者值。|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|指出 IDE 目前是否支援取消作業。|
|`SCC_OPT_NAMECHANGEPFN`|[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)回呼函式的指標|設定名稱-變更回呼函數的指標。|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|指出 IDE 是否允許手動簽出其檔案（透過原始檔控制使用者介面），或是否必須只透過原始檔控制外掛程式簽出檔案。|
|`SCC_OPT_SHARESUBPROJ`|N/A|如果原始檔控制外掛程式允許 IDE 指定本機專案資料夾，則外掛程式會傳回 `SCC_I_SHARESUBPROJOK`。|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 如果 `SCC_OPT_EVENTQUEUE``nOption`，則 IDE 會停用（或重新啟用）背景處理。 例如，在編譯期間，IDE 可能會指示原始檔控制外掛程式停止任何類型的閒置處理。 編譯之後，它會重新啟用背景處理，讓外掛程式的事件佇列保持在最新狀態。 對應至 `nOption`的 `SCC_OPT_EVENTQUEUE` 值，`dwVal`，亦即 `SCC_OPT_EQ_ENABLE` 和 `SCC_OPT_EQ_DISABLE`有兩個可能的值。

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 如果 `nOption` 的值為 `SCC_OPT_HASCANCELMODE`，則 IDE 可讓使用者取消長時間的作業。 將 `dwVal` 設定為 `SCC_OPT_HCM_NO` （預設值）表示 IDE 沒有 [取消] 模式。 如果原始檔控制外掛程式想要讓使用者能夠取消，就必須提供它自己的 [取消] 按鈕。 `SCC_OPT_HCM_YES` 表示 IDE 提供取消作業的功能，因此 SCC 外掛程式不需要顯示自己的 [取消] 按鈕。 如果 IDE 將 `dwVal` 設定為 `SCC_OPT_HCM_YES`，則會準備回應 `SCC_MSG_STATUS` 和傳送至 `lpTextOutProc` 回呼函式的 `DOCANCEL` 訊息（請參閱[LPTEXTOUTPROC](../extensibility/lptextoutproc.md)）。 如果 IDE 未設定此變數，則外掛程式不應傳送這兩則訊息。

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 如果 nOption 設定為 `SCC_OPT_NAMECHANGEPFN`，而且原始檔控制外掛程式和 IDE 都允許，則外掛程式實際上可以在原始檔控制作業期間重新命名或移動檔案。 `dwVal` 將設定為[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)類型的函式指標。 在原始檔控制作業期間，外掛程式可以呼叫此函式，並傳遞三個參數。 這些是檔案的舊名稱（具有完整路徑）、該檔案的新名稱（具有完整路徑），以及與 IDE 相關之資訊的指標。 IDE 會在這個最後一個指標中傳送，方法是呼叫 `SccSetOption` 並將 `nOption` 設定為 `SCC_OPT_USERDATA`，並將 `dwVal` 指向資料。 此函式的支援是選擇性的。 使用這項功能的 VSSCI 外掛程式必須將其函式指標和使用者資料變數初始化為 `NULL`，而且除非已指定 rename 函式，否則不能呼叫該函數。 它也應該準備好保留所提供的值，或變更它以回應 `SccSetOption`的新呼叫。 這不會發生在原始檔控制命令作業的中間，但可能會在命令之間發生。

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 如果 nOption 設定為 `SCC_OPT_SCCCHECKOUTONLY`，IDE 會指出目前開啟之專案中的檔案永遠不應透過原始檔控制系統的使用者介面，以手動方式簽出。 相反地，檔案應該只透過 IDE 控制項下的原始檔控制外掛程式來簽出。 如果 `dwValue` 設定為 `SCC_OPT_SCO_NO`，則表示應該由外掛程式正常處理檔案，而且可以透過原始檔控制 UI 來簽出檔案。 如果 `dwValue` 設定為 `SCC_OPT_SCO_YES`，則只允許外掛程式簽出檔案，而不應叫用原始檔控制系統的 UI。 這適用于 IDE 可能會有「虛擬檔案」，只透過 IDE 來檢查的情況。

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 如果`nOption` 設定為 `SCC_OPT_SHARESUBPROJ`，則 IDE 會測試當從原始檔控制加入檔案時，原始檔控制外掛程式是否可以使用指定的本機資料夾。 在此情況下，`dwVal` 參數的值並不重要。 當呼叫[SccAddFromScc](../extensibility/sccaddfromscc-function.md)時，如果外掛程式允許 IDE 指定要從原始檔控制加入檔案的本機目的地資料夾，則外掛程式必須在呼叫 `SccSetOption` 函數時傳回 `SCC_I_SHARESUBPROJOK`。 然後，IDE 會使用 `SccAddFromScc` 函式的 `lplpFileNames` 參數，傳入目的地資料夾。 外掛程式會使用該目的資料夾來放置從原始檔控制新增的檔案。 如果外掛程式不會在設定 `SCC_OPT_SHARESUBPROJ` 選項時傳回 `SCC_I_SHARESUBPROJOK`，則 IDE 會假設外掛程式只能在目前的本機資料夾中新增檔案。

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)