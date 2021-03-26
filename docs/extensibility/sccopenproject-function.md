---
description: 此函式會開啟現有的原始檔控制專案或建立新專案。
title: SccOpenProject 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: baada63e84e95fd466e0e5640c592dfe303d8e1a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063756"
---
# <a name="sccopenproject-function"></a>SccOpenProject 函式
此函式會開啟現有的原始檔控制專案或建立新專案。

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

在原始檔控制外掛程式內容結構。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它做為它所提供之任何對話方塊的父代。

 lpUser

[in，out]使用者的名稱 (不會超過 SCC_USER_SIZE，包括 Null 結束字元) 。

 lpProjName

在識別專案名稱的字串。

 lpLocalProjPath

在專案工作資料夾的路徑。

 lpAuxProjPath

[in，out]識別專案的選擇性輔助字串 (不會超過 SCC_AUXPATH_SIZE，包括 Null 結束字元) 。

 lpComment

在批註至所建立的新專案。

 lpTextOutProc

在選擇性的回呼函式，可顯示原始檔控制外掛程式的文字輸出。

 dwFlags

在指出如果專案對原始檔控制外掛程式而言是未知的，是否需要建立新專案。 值可以是和的組合 `SCC_OP_CREATEIFNEW``SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|開啟專案的成功。|
|SCC_E_INITIALIZEFAILED|無法初始化專案。|
|SCC_E_INVALIDUSER|使用者無法登入原始檔控制系統。|
|SCC_E_COULDNOTCREATEPROJECT|專案不存在於呼叫之前; `SCC_OPT_CREATEIFNEW` 已設定旗標，但無法建立專案。|
|SCC_E_PROJSYNTAXERR|不正確專案語法。|
|SCC_E_UNKNOWNPROJECT|專案對於原始檔控制外掛程式而言是未知的，且 `SCC_OPT_CREATEIFNEW` 未設定旗標。|
|SCC_E_INVALIDFILEPATH|檔案路徑無效或無法使用。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項操作。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或爭用問題。 建議您重試。|
|SCC_E_NONSPECFICERROR|模糊的失敗;原始檔控制系統未初始化。|

## <a name="remarks"></a>備註
 IDE 可能會傳入 () 的使用者名稱 `lpUser` ，也可能只是將指標傳入空字串。 如果有使用者名稱，原始檔控制外掛程式應該使用它做為預設值。 但是，如果未傳遞任何名稱，或登入以指定的名稱失敗，則外掛程式應該會提示使用者登入，並在收到有效登入時傳回有效的名稱， `lpUser` `.` 因為外掛程式可能會變更使用者名稱字串，所以 IDE 一律會配置大小 (`SCC_USER_LEN` + 1 或 SCC_USER_SIZE 的緩衝區，其中包含 null 結束字元) 的空間。

> [!NOTE]
> IDE 可能需要執行的第一個動作可能是對 `SccOpenProject` 函數或 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)的呼叫。 基於這個理由，兩者都有相同的 `lpUser` 參數。

 `lpAuxProjPath` 和 `lpProjName` 會從方案檔中讀取，或從函式的呼叫傳回 `SccGetProjPath` 。 這些參數包含原始檔控制外掛程式與專案相關聯，而且只對外掛程式有意義的字串。 如果方案檔中沒有這類字串，且未提示使用者流覽 (這會透過函式 `SccGetProjPath`) 傳回字串，IDE 會為和傳遞空字串， `lpAuxProjPath` `lpProjName` 並預期外掛程式會在此函式傳回時，更新這些值。

 `lpTextOutProc` 這是 IDE 為原始檔控制外掛程式提供的回呼函式的指標，目的是要顯示命令結果輸出。 這個回呼函式在 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)中有詳細的說明。

> [!NOTE]
> 如果原始檔控制外掛程式打算利用這項功能，就必須在 `SCC_CAP_TEXTOUT` [SccInitialize](../extensibility/sccinitialize-function.md)中設定旗標。 如果未設定該旗標，或如果 IDE 不支援這項功能， `lpTextOutProc` 將會是 `NULL` 。

 `dwFlags`參數會控制目前開啟的專案目前不存在的事件結果。 它包含兩個位旗標 `SCC_OP_CREATEIFNEW` 和 `SCC_OP_SILENTOPEN` 。 如果開啟的專案已經存在，則函式只會開啟專案並傳回 `SCC_OK` 。 如果專案不存在，且 `SCC_OP_CREATEIFNEW` 旗標是開啟的，則原始檔控制外掛程式可以在原始檔控制系統中建立專案、將專案開啟，然後再返回 `SCC_OK` 。 如果專案不存在，且 `SCC_OP_CREATEIFNEW` 旗標為 off，則該外掛程式應檢查 `SCC_OP_SILENTOPEN` 旗標。 如果該旗標不是開啟的，外掛程式可能會提示使用者輸入專案名稱。 如果該旗標是開啟的，則外掛程式應該只傳回 `SCC_E_UNKNOWNPROJECT` 。

## <a name="calling-order"></a>呼叫順序
 在正常的事件程序中，會先呼叫 [SccInitialize](../extensibility/sccinitialize-function.md) 來開啟原始檔控制會話。 會話可能包含的呼叫 `SccOpenProject` ，後面接著其他原始檔控制外掛程式 API 函式呼叫，並且會在呼叫 [SccCloseProject](../extensibility/scccloseproject-function.md)時終止。 這類會話可能會在呼叫 [SccUninitialize](../extensibility/sccuninitialize-function.md) 之前重複數次。

 如果原始檔控制外掛程式設定 `SCC_CAP_REENTRANT` 中的位 `SccInitialize` ，則上述會話順序可能會以平行方式重複許多次。 不同的 `pvContext` 結構會追蹤不同的會話，其中每個會話 `pvContext` 一次都與一個開啟的專案相關聯。 根據 `pvContext` 參數，外掛程式可以決定任何特定呼叫中所參考的專案。 如果未設定此功能位 `SCC_CAP_REENTRANT` ，nonreentrant 原始檔控制外掛程式的運作方式就會限制在使用多個專案的能力。

> [!NOTE]
> 此 `SCC_CAP_REENTRANT` 位是在原始檔控制外掛程式 API 的1.1 版中引進。 它未設定或在1.0 版中被忽略，而且所有版本1.0 原始檔控制外掛程式都會被視為 nonreentrant。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [字串長度限制](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
