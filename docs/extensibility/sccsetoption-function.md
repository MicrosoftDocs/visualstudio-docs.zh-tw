---
title: SccSetOption 功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1adcbb47e9fce7037fe8942326e8836ade51e3eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700316"
---
# <a name="sccsetoption-function"></a>SccSetOption 函式
此函數設置控制原始程式碼管理外掛程式行為的選項。

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

[在]原始程式碼管理外掛程式上下文結構。

 nOption

[在]正在設置的選項。

 德瓦爾

[在]選項的設置。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功設置該選項。|
|SCC_I_SHARESUBPROJOK|傳回`nOption`(`SCC_OPT_SHARESUBPROJ`如果是 )和原始碼管理外掛程式允許 IDE 設定目標資料夾。|
|SCC_E_OPNOTSUPPORTED|該選項未設置,不應依賴。|

## <a name="remarks"></a>備註
 IDE 呼叫此函數以控制原始程式碼管理外掛程式的行為。 第一個參數`nOption`, 指示要設定的值, 而`dwVal`第二個 參數 指示如何處理該值。 外掛程式儲存與的此資訊相關聯`pvContext``,`, 因此 IDE 必須在呼叫 Scc 初始化後呼叫此函數(但不一定在每次呼叫[SccOpenProject](../extensibility/sccopenproject-function.md)後)。 [SccInitialize](../extensibility/sccinitialize-function.md)

 選項及其值的摘要:

|`nOption`|`dwValue`|描述|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|啟用/禁用後台事件佇列。|
|`SCC_OPT_USERDATA`|任何值|指定要傳遞給[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)回檔功能的使用者值。|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|指示 IDE 當前是否支援取消操作。|
|`SCC_OPT_NAMECHANGEPFN`|指向[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)回檔函式指標|設置指向名稱更改回調函數的指標。|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|指示 IDE 是否允許手動簽出其檔(透過原始碼管理使用者介面),或者是否必須透過原始程式碼管理外掛程式簽出這些檔。|
|`SCC_OPT_SHARESUBPROJ`|N/A|如果原始碼管理外掛程式允許 IDE 指定本地端項目資料夾,則`SCC_I_SHARESUBPROJOK`外掛程式將傳回 。|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 如果是`nOption``SCC_OPT_EVENTQUEUE`,IDE 正在禁用(或重新啟用)後台處理。 例如,在編譯期間,IDE可能會指示原始程式碼管理外掛程式停止任何類型的空閒處理。 編譯後,它將重新啟用後台處理,以使外掛程式的事件佇列保持最新。 `SCC_OPT_EVENTQUEUE`對應於`nOption`的值 , 有兩個可能`dwVal`的值`SCC_OPT_EQ_ENABLE` `SCC_OPT_EQ_DISABLE` , 與 。

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 如果值`nOption``SCC_OPT_HASCANCELMODE`為 ,IDE 允許使用者取消長操作。 設置為`dwVal``SCC_OPT_HCM_NO`(預設值)表示 IDE 沒有取消模式。 源代碼管理外掛程式必須提供自己的"取消"按鈕,如果使用者希望用戶能夠取消。 `SCC_OPT_HCM_YES`指示 IDE 提供了取消操作的功能,因此 SCC 外掛程式不需要顯示其自己的"取消"按鈕。 如果`dwVal`IDE`SCC_OPT_HCM_YES`將 設定到`SCC_MSG_STATUS`,`DOCANCEL`則它準備 回應回`lpTextOutProc`檔函數併發送消息 (請參閱[LPTEXTOUTPROC)。](../extensibility/lptextoutproc.md) 如果 IDE 未設定此變數,外掛程式不應發送這兩條消息。

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 如果 nOption`SCC_OPT_NAMECHANGEPFN`設定為 ,並且原始程式碼管理外掛程式和 IDE 都允許它,則外掛程式實際上可以在原始程式碼管理操作期間重新命名或行動檔案。 `dwVal`將設置為[OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)類型的函數指標。 在原始程式碼管理操作期間,外掛程式可以調用此函數,傳遞三個參數。 這些是檔的舊名稱(具有完全限定的路徑),該檔的新名稱(具有完全限定的路徑),以及指向與 IDE 相關的資訊的指標。 IDE`SccSetOption`通過調用`nOption``SCC_OPT_USERDATA`設置為 ()`dwVal`傳送此最後一個指標,並指向數據。 支援此功能是可選的。 使用此功能的 VSSCI 外掛程式必須將其函數指標和用戶數據變數初始化`NULL`到 ,除非已授予它,否則不得呼叫重命名函數。 它還應準備保留所給出的值,或更改該值以回應對`SccSetOption`的新調用。 這在原始程式碼管理命令操作中不會發生,但可能在命令之間發生。

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 如果 nOption`SCC_OPT_SCCCHECKOUTONLY`設置為 ,IDE 表示不應透過原始碼管理系統的使用者介面手動簽出當前打開專案中的檔。 相反,檔應僅通過 IDE 控制下的原始程式碼管理外掛程式簽出。 如果`dwValue`設置`SCC_OPT_SCO_NO`為 ,則意味著外掛程式應正常處理檔,並且可以通過原始程式碼管理 UI 簽出檔。 如果`dwValue`設定`SCC_OPT_SCO_YES`為 ,則只允許外掛程式簽出檔,並且不應呼叫原始程式碼管理系統的 UI。 這是針對 IDE 可能具有「偽檔」的情況,這些「偽檔」僅通過 IDE 簽出才有意義。

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 如果`nOption`設定`SCC_OPT_SHARESUBPROJ`為 ,IDE 正在測試原始程式碼管理外掛程式在從原始碼管理添加檔時是否可以使用指定的本地資料夾。 在這種情況下,`dwVal`參數的值並不重要。 如果外掛程式允許 IDE 指定在調用[SccAddFromScc](../extensibility/sccaddfromscc-function.md)時從原始程式碼管理中添加檔案的本地目標資料夾,則該`SCC_I_SHARESUBPROJOK``SccSetOption`外掛程式必須在調用 該函數時返回。 然後,IDE`lplpFileNames`使用函數`SccAddFromScc`的參數在目標資料夾中傳遞。 該外掛程式使用該目標資料夾來放置從原始程式碼管理添加的檔案。 如果設置`SCC_OPT_SHARESUBPROJ`該選項時外掛程式`SCC_I_SHARESUBPROJOK`未返回 ,IDE 假定該外掛程式只能在當前本地資料夾中添加檔。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)
