---
description: 此函式會在 lpParentProjPath 引數所指定的現有父專案下，建立具有指定名稱的子專案。
title: SccCreateSubProject 函式 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 38fb6a18954b0a2f976fad4b24819a08ed868ab6
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221609"
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject 函式
此函式會在引數所指定的現有父專案下，建立具有指定名稱的子專案 `lpParentProjPath` 。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccCreateSubProject(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpParentProjPath,
   LPCSTR lpSubProjName,
   LPSTR  lpAuxProjPath,
   LPSTR  lpSubProjPath
);
```

### <a name="parameters"></a>參數
 pContext

在原始檔控制外掛程式內容指標。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它做為它所提供之任何對話方塊的父代。

 lpUser

[in，out]使用者名稱 (SCC_USER_SIZE，包括 Null 結束字元) 。

 lpParentProjPath

在識別父專案 (路徑的字串，最多可 SCC_PRJPATH_SIZE，包括 Null 結束字元) 。

 lpSubProjName

在建議的子專案名稱最多 (SCC_PRJPATH_SIZE，包括 Null 結束字元) 。

 lpAuxProjPath

[in，out]識別專案 (的輔助字串，最多可 SCC_PRJPATH_SIZE，包括 Null 結束字元) 。

 lpSubProjPath

[in，out]識別子專案 (路徑的輸出字串，最多可 SCC_PRJPATH_SIZE，包括 Null 結束字元) 。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功建立子專案。|
|SCC_E_INITIALIZEFAILED|無法初始化父專案。|
|SCC_E_INVALIDUSER|使用者無法登入原始檔控制系統。|
|SCC_E_COULDNOTCREATEPROJECT|無法建立子專案。|
|SCC_E_PROJSYNTAXERR|不正確專案語法。|
|SCC_E_UNKNOWNPROJECT|父專案對原始檔控制外掛程式而言是未知的。|
|SCC_E_INVALIDFILEPATH|檔案路徑無效或無法使用。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項操作。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或爭用問題。 建議您重試。|
|SCC_E_CONNECTIONFAILURE|發生原始檔控制外掛程式連接問題。|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|模糊失敗。|

## <a name="remarks"></a>備註
 如果已有名稱相同的子專案，則此函式可以變更預設名稱，以建立唯一的名稱，例如，將 "_ \<number> " 新增至其中。 呼叫端必須準備好接受 `lpUser` 、和的變更 `lpSubProjPath` `lpAuxProjPath` 。 `lpSubProjPath`然後， `lpAuxProjPath` 會使用和引數來呼叫[SccOpenProject](../extensibility/sccopenproject-function.md)。 傳回時，呼叫端不應該修改它們。 這些字串提供一個方法，讓原始檔控制外掛程式追蹤需要與專案產生關聯的資訊。 呼叫端 IDE 不會在傳回時顯示這兩個參數，因為外掛程式可以使用可能不適合用于觀看的格式化字串。 函數會傳回成功或失敗的程式碼，如果成功，則會 `lpSubProjPath` 使用新專案的完整專案路徑填入變數。

 此函式類似于 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)，不同之處在于它會以無訊息模式建立專案，而不是提示使用者選取一個專案。 當呼叫函式時 `SccCreateSubProject` ， `lpParentProjName` 而且 `lpAuxProjPath` 將不會是空的，而且會對應至有效的專案。 IDE 通常會從先前呼叫函式 `SccGetProjPath` 或 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)接收這些字串。

 `lpUser`引數是使用者名稱。 IDE 會傳入先前從中接收的相同使用者名稱 `SccGetProjPath` ，而原始檔控制外掛程式應使用此名稱做為預設值。 如果使用者已經有與外掛程式的開啟連接，則外掛程式應嘗試排除任何提示，以確保函式可無訊息地運作。 但是，如果登入失敗，外掛程式應該會提示使用者輸入登入，並在收到有效的登入時，將名稱傳遞回 `lpUser` 。 由於外掛程式可能會變更這個字串，因此 IDE 一律會配置大小 (SCC_USER_LEN + 1 或 SCC_USER_SIZE 的緩衝區，其中包含 null 結束字元) 的空間。 如果字串已變更，則新的字串必須是有效的登入名稱， (至少與舊的字串) 一樣有效。

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>SccCreateSubProject 和 SccGetParentProjectPath 的技術注意事項
 Visual Studio 已簡化將方案和專案加入原始檔控制中的功能，可讓使用者在原始檔控制系統中選取位置的次數降到最低。 如果原始檔控制外掛程式同時支援這兩個新函數和，則 Visual Studio 會啟用這些變更 `SccCreateSubProject` `SccGetParentProjectPath` 。 不過，您可以使用下列登錄專案來停用這些變更，並還原為先前的 Visual Studio (原始檔控制外掛程式 API 1.1 版) 行為：

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]"DoNotCreateSolutionRootFolderInSourceControl" = dword：00000001**

 如果這個登錄專案不存在或設定為 dword：00000000，則 Visual Studio 會嘗試使用新的函式 `SccCreateSubProject` 和 `SccGetParentProjectPath` 。

 如果登錄專案設定為 dword：00000001，Visual Studio 就不會嘗試使用這些新的函式，而新增至原始檔控制的作業會像在舊版 Visual Studio 中一樣運作。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
