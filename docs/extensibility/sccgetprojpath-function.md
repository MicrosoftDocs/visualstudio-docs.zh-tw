---
description: 此函式會提示使用者輸入專案路徑，這是僅對原始檔控制外掛程式有意義的字串。
title: SccGetProjPath 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 93266464249b8de037a618bab55ede31988384cb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901067"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath 函式
此函式會提示使用者輸入專案路徑，這是僅對原始檔控制外掛程式有意義的字串。 當使用者為時，就會呼叫它：

- 建立新的專案

- 將現有的專案加入至版本控制

- 嘗試尋找現有的版本控制專案

## <a name="syntax"></a>語法

```cpp
SCCRTN SccGetProjPath (
   LPVOID pvContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPSTR  lpProjName,
   LPSTR  lpLocalPath,
   LPSTR  lpAuxProjPath,
   BOOL   bAllowChangePath,
   LPBOOL pbNew
);
```

### <a name="parameters"></a>參數
 pvCoNtext

在原始檔控制外掛程式內容結構。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它做為它所提供之任何對話方塊的父代。

 lpUser

[in，out]使用者名稱 (不會超過 SCC_USER_SIZE，包括 Null 結束字元) 

 lpProjName

[in，out]IDE 專案、專案工作區或 makefile 的名稱 (不會超過 SCC_PRJPATH_SIZE，包括 Null 結束字元) 。

 lpLocalPath

[in，out]專案的工作路徑。 如果 `bAllowChangePath` 為 `TRUE` ，則原始檔控制外掛程式可以修改此字串 (不要超過 _MAX_PATH，包括 null 結束字元) 。

 lpAuxProjPath

[in，out]傳回之專案路徑的緩衝區 (不會超過 SCC_PRJPATH_SIZE，包括 Null 結束字元) 。

 bAllowChangePath

在如果是 `TRUE` ，原始檔控制外掛程式可以提示您輸入和修改 `lpLocalPath` 字串。

 pbNew

[in，out]傳入的值會指出是否要建立新的專案。 傳回的值表示建立專案的成功：

|正在傳入|解讀|
|--------------|--------------------|
|true|使用者可以建立新專案。|
|FALSE|使用者可能不會建立新專案。|

|傳出|解讀|
|--------------|--------------------|
|true|已建立新專案。|
|FALSE|已選取現有的專案。|

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功建立或抓取專案。|
|SCC_I_OPERATIONCANCELED|已取消作業。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或爭用問題。|
|SCC_E_CONNECTIONFAILURE|嘗試連接到原始檔控制系統時發生問題。|
|SCC_E_NONSPECIFICERROR|發生未指定的錯誤。|

## <a name="remarks"></a>備註
 此函數的目的是要讓 IDE 取得參數 `lpProjName` 和 `lpAuxProjPath` 。 當原始檔控制外掛程式提示使用者提供此資訊之後，它會將這兩個字串傳遞回 IDE。 IDE 會將這些字串保存在其方案檔中，並在使用者開啟此專案時，將這些字串傳遞至 [SccOpenProject](../extensibility/sccopenproject-function.md) 。 這些字串可讓外掛程式追蹤與專案相關聯的資訊。

 第一次呼叫函式時， `lpAuxProjPath` 會設為空字串。 `lProjName` 也可以是空的，或可能包含原始檔控制外掛程式可能使用或忽略的 IDE 專案名稱。 當函數成功傳回時，外掛程式會傳回兩個對應的字串。 IDE 對這些字串沒有任何假設，將不會使用它們，也不會讓使用者修改它們。 如果使用者想要變更設定，IDE 將會 `SccGetProjPath` 再次呼叫，並傳入先前所收到的相同值。 這會讓外掛程式完整控制這兩個字串。

 `lpUser`若為，IDE 可以傳入使用者名稱，也可以直接傳入空字串的指標。 如果有使用者名稱，原始檔控制外掛程式應該使用它做為預設值。 但是，如果未傳遞任何名稱，或登入以指定的名稱失敗，則外掛程式應該會提示使用者輸入登入，並在 `lpUser` 收到有效的登入時，將該名稱傳遞回。 由於外掛程式可能會變更這個字串，因此 IDE 一律會配置大小 (`SCC_USER_LEN` + 1) 的緩衝區。

> [!NOTE]
> IDE 執行的第一個動作可能是呼叫函式 `SccOpenProject` 或 `SccGetProjPath` 函數。 因此，兩者都有完全相同的 `lpUser` 參數，可讓原始檔控制外掛程式在任一時間登入使用者。 即使函式的傳回指出失敗，外掛程式也必須使用有效的登入名稱來填滿這個字串。

 `lpLocalPath` 是使用者用來保存專案的目錄。 它可能是空字串。 如果目前未定義任何目錄 (當使用者嘗試從原始檔控制系統下載專案時) 如果 `bAllowChangePath` 是 `TRUE` ，則原始檔控制外掛程式可以提示使用者輸入，或使用其他方法來將自己的字串放入 `lpLocalPath` 。 如果 `bAllowChangePath` 是 `FALSE` ，外掛程式不應變更字串，因為使用者已在指定的目錄中工作。

 如果使用者建立要放在原始檔控制下的新專案，原始檔控制外掛程式在呼叫時，可能不會實際在原始檔控制系統中建立它 `SccGetProjPath` 。 相反地，它會傳回字串以及的非零值 `pbNew` ，表示將在原始檔控制系統中建立專案。

 例如，如果 Visual Studio 的 [ **新增專案** ] 中的使用者將其專案加入至原始檔控制，Visual Studio 會呼叫這個函式，而外掛程式會判斷是否可以在原始檔控制系統中建立新的專案，以包含 Visual Studio 專案。 如果使用者在完成嚮導之前按一下 [ **取消** ]，則永遠不會建立專案。 如果使用者按一下 **[確定]**，則 `SccOpenProject` `SCC_OPT_CREATEIFNEW` 會在該時間建立 Visual Studio 呼叫、傳入，以及原始檔控制的專案。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
