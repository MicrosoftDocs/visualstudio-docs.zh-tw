---
description: 此函式會判斷指定專案的父專案路徑。
title: SccGetParentProjectPath 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 305f226117bbb9cf906231a0b9bbaa24c1d87a8e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063977"
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath 函式
此函式會判斷指定專案的父專案路徑。 當使用者將 Visual Studio 專案加入至原始檔控制時，會呼叫這個函式。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccGetParentProjectPath(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpProjPath,
   LPSTR  lpAuxProjPath,
   LPSTR  lpParentProjPath
);
```

### <a name="parameters"></a>參數
 pContext

在原始檔控制外掛程式內容指標。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它做為它所提供之任何對話方塊的父代。

 lpUser

[in，out]使用者名稱最多 (SCC_USER_SIZE，包括 Null 結束字元) 。

 lpProjPath

在識別專案路徑 (的字串，最多可 SCC_PRJPATH_SIZE，包括 Null 結束字元) 。

 lpAuxProjPath

[in，out]識別專案 (的輔助字串，最多可 SCC_PRJPATH_SIZE，包括 Null 結束字元) 。

 lpParentProjPath

[in，out]識別父專案路徑 (的輸出字串，最多可 SCC_PRJPATH_SIZE，包括 Null 結束字元) 。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功取得父專案路徑。|
|SCC_E_INITIALIZEFAILED|無法初始化專案。|
|SCC_E_INVALIDUSER|使用者無法登入原始檔控制外掛程式。|
|SCC_E_UNKNOWNPROJECT|專案對於原始檔控制外掛程式而言是未知的。|
|SCC_E_INVALIDFILEPATH|檔案路徑無效或無法使用。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項操作。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或爭用問題。 建議您重試。|
|SCC_E_PROJSYNTAXERR|不正確專案語法。|
|SCC_E_CONNECTIONFAILURE|儲存連接問題。|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|模糊失敗。|

## <a name="remarks"></a>備註
 此函式會傳回成功或失敗的程式碼，如果成功，則會 `lpParentProjPath` 使用指定專案的完整專案路徑來填滿變數。

 此函數會傳回現有專案的父專案路徑。 針對根專案，函式會傳回在 (中傳遞的專案路徑，也就是相同的根專案路徑) 。 請注意，專案路徑是僅對原始檔控制外掛程式有意義的字串。

 IDE 已準備好接受和參數的變更 `lpUser` `lpAuxProjPath` 。 當使用者在日後開啟此專案時，IDE 會保存這些字串，並將它們傳遞至 [SccOpenProject](../extensibility/sccopenproject-function.md) 。 因此，這些字串可讓原始檔控制外掛程式追蹤與專案相關聯的資訊。

 此函式類似于 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)，不同之處在于它不會提示使用者選取專案。 它也永遠不會建立新的專案，但只適用于現有的專案。

 當 `SccGetParentProjectPath` 呼叫時， `lpProjPath` 而且 `lpAuxProjPath` 將不會是空的，而且會對應至有效的專案。 IDE 通常會從先前的函式呼叫接收這些字串 `SccGetProjPath` 。

 `lpUser`引數是使用者名稱。 IDE 會傳入先前從函式收到的相同使用者名稱 `SccGetProjPath` ，而原始檔控制外掛程式應使用此名稱做為預設值。 如果使用者已經有與外掛程式的開啟連接，則外掛程式應嘗試排除任何提示，以確保函式可無訊息地運作。 但是，如果登入失敗，外掛程式應該會提示使用者輸入登入，並在收到有效的登入時，將名稱傳遞回 `lpUser` 。 由於外掛程式可能會變更這個字串，因此 IDE 一律會配置大小 (`SCC_USER_LEN` + 1) 的緩衝區。 如果字串已變更，則新的字串必須是有效的登入名稱， (至少與舊的字串) 一樣有效。

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>SccCreateSubProject 和 SccGetParentProjectPath 的技術注意事項
 將方案和專案加入至原始檔控制已經過簡化，Visual Studio 將提示使用者在原始檔控制系統中選取位置的次數降到最低。 如果原始檔控制外掛程式同時支援這兩個新函式、 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) 和函式，則會 Visual Studio 啟用這些變更 `SccGetParentProjectPath` 。 不過，您可以使用下列登錄專案來停用這些變更，並還原為先前的 Visual Studio (原始檔控制外掛程式 API 1.1 版) 行為：

 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]"DoNotCreateSolutionRootFolderInSourceControl" = dword：00000001**

 如果這個登錄專案不存在或設定為 dword：00000000，Visual Studio 會嘗試使用新的函式 `SccCreateSubProject` 和 `SccGetParentProjectPath` 。

 如果登錄專案設定為 dword：00000001，Visual Studio 不會嘗試使用這些新的函式，而新增至原始檔控制的作業會像在舊版 Visual Studio 中一樣運作。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
