---
title: SccOpenProject 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6aa4a715f8d1b87aa831f6a315f07a19e5d4f46
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721047"
---
# <a name="sccopenproject-function"></a>SccOpenProject 函式
此函式會開啟現有的原始檔控制專案，或建立一個新的。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccOpenProject (
   LPVOID        pvContext,
   HWND          hWnd,
   LPSTR         lpUser,
   LPCSTR        lpProjName,
   LPCSTR        lpLocalProjPath,
   LPSTR         lpAuxProjPath,
   LPCSTR        lpComment,
   LPTEXTOUTPROC lpTextOutProc,
   LONG          dwFlags
);
```

#### <a name="parameters"></a>參數
 pvCoNtext

在原始檔控制外掛程式的內容結構。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它所提供之任何對話方塊的父系。

 lpUser

[in、out]使用者的名稱（不超過 SCC_USER_SIZE，包括 Null 結束字元）。

 lpProjName

在識別專案名稱的字串。

 lpLocalProjPath

在專案工作資料夾的路徑。

 lpAuxProjPath

[in、out]識別專案的選擇性輔助字串（不超過 SCC_AUXPATH_SIZE，包括 Null 結束字元）。

 lpComment

在批註至正在建立的新專案。

 lpTextOutProc

在選擇性的回呼函數，可顯示原始檔控制外掛程式的文字輸出。

 dwFlags

在表示當原始檔控制外掛程式的專案不明時，是否需要建立新的專案。 值可以是 `SCC_OP_CREATEIFNEW` 和 `SCC_OP_SILENTOPEN.` 的組合

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式執行應會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|成功開啟專案。|
|SCC_E_INITIALIZEFAILED|無法初始化專案。|
|SCC_E_INVALIDUSER|使用者無法登入原始檔控制系統。|
|SCC_E_COULDNOTCREATEPROJECT|專案在呼叫之前不存在; 已設定 `SCC_OPT_CREATEIFNEW` 旗標，但無法建立專案。|
|SCC_E_PROJSYNTAXERR|不正確專案語法。|
|SCC_E_UNKNOWNPROJECT|原始檔控制外掛程式的專案不明，而且未設定 `SCC_OPT_CREATEIFNEW` 旗標。|
|SCC_E_INVALIDFILEPATH|檔案路徑無效或無法使用。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行此作業。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或競爭問題。 建議使用重試。|
|SCC_E_NONSPECFICERROR|模糊失敗;原始檔控制系統尚未初始化。|

## <a name="remarks"></a>備註
 IDE 可能會傳入使用者名稱（`lpUser`），或只會將指標傳入空字串。 如果有使用者名稱，原始檔控制外掛程式應該使用它做為預設值。 不過，如果未傳遞任何名稱，或登入失敗並具有指定的名稱，外掛程式應該會提示使用者登入，並在收到有效的登入時，傳回 `lpUser` 中的有效名稱 `.` 因為外掛程式可能會變更使用者名稱字串，IDE 一律會配置大小的緩衝區（`SCC_USER_LEN` + 1 或 SCC_USER_SIZE，其中包含 null 結束字元的空格）。

> [!NOTE]
> IDE 可能需要執行的第一個動作可能是呼叫 `SccOpenProject` 函數或[SccGetProjPath](../extensibility/sccgetprojpath-function.md)。 基於這個理由，兩者都有相同的 `lpUser` 參數。

 `lpAuxProjPath` 和 `lpProjName` 會從方案檔讀取，或從對 `SccGetProjPath` 函數的呼叫傳回。 這些參數包含原始檔控制外掛程式與專案相關聯的字串，而且只有外掛程式才有意義。 如果方案檔中沒有這類字串，而且未提示使用者流覽（這會透過 `SccGetProjPath` 函式傳回字串），則 IDE 會傳遞 `lpAuxProjPath` 和 `lpProjName` 的空字串，並預期外掛程式會在第一次時更新這些值。is 函數傳回。

 `lpTextOutProc` 是 IDE 提供給原始檔控制外掛程式的回呼函式指標，用於顯示命令結果輸出。 此回呼函式會在[LPTEXTOUTPROC](../extensibility/lptextoutproc.md)中詳細說明。

> [!NOTE]
> 如果原始檔控制外掛程式打算利用這項功能，就必須在[SccInitialize](../extensibility/sccinitialize-function.md)中設定 `SCC_CAP_TEXTOUT` 旗標。 如果未設定該旗標，或 IDE 不支援這項功能，將會 `NULL` `lpTextOutProc`。

 如果目前開啟的專案不存在，則 `dwFlags` 參數會控制結果。 其中包含兩個位旗標，`SCC_OP_CREATEIFNEW` 和 `SCC_OP_SILENTOPEN`。 如果要開啟的專案已經存在，此函式只會開啟專案並傳回 `SCC_OK`。 如果專案不存在，而且 `SCC_OP_CREATEIFNEW` 旗標為開啟，則原始檔控制外掛程式可以在原始檔控制系統中建立專案、將其開啟，然後傳回 `SCC_OK`。 如果專案不存在，而且 `SCC_OP_CREATEIFNEW` 旗標已關閉，則外掛程式應該檢查是否有 `SCC_OP_SILENTOPEN` 旗標。 如果該旗標不是 on，外掛程式可能會提示使用者輸入專案名稱。 如果該旗標為開啟，則外掛程式應該只傳回 `SCC_E_UNKNOWNPROJECT`。

## <a name="calling-order"></a>呼叫順序
 在正常的事件程序中，會先呼叫[SccInitialize](../extensibility/sccinitialize-function.md)以開啟原始檔控制會話。 會話可能包含呼叫 `SccOpenProject`，後面接著其他原始檔控制外掛程式 API 函式呼叫，並會在呼叫[SccCloseProject](../extensibility/scccloseproject-function.md)時終止。 這類會話可能會在呼叫[SccUninitialize](../extensibility/sccuninitialize-function.md)之前重複數次。

 如果原始檔控制外掛程式在 `SccInitialize` 中設定 `SCC_CAP_REENTRANT` 位，則上述會話順序可能會以平行方式重複多次。 不同的 `pvContext` 結構會追蹤不同的會話，其中每個 `pvContext` 會一次與一個開啟的專案相關聯。 根據 `pvContext` 參數，外掛程式可以判斷在任何特定呼叫中所參考的專案。 如果未設定功能位 `SCC_CAP_REENTRANT`，nonreentrant 原始檔控制外掛程式會受到限制，可使用多個專案。

> [!NOTE]
> 在原始檔控制外掛程式 API 的1.1 版中引進了 `SCC_CAP_REENTRANT` 位。 它不會在1.0 版中設定或忽略，而且所有版本1.0 的原始檔控制外掛程式都會假設為 nonreentrant。

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [字串長度限制](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)