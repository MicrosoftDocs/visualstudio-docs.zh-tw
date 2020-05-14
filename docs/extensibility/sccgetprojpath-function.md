---
title: SccGetProjPath 功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 281787da3499c081fbbe6f59b7b8175a4dbf24d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700696"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath 功能
此函數提示使用者輸入項目路徑,這是一個僅對原始程式碼管理外掛程式有意義的字串。 當使用者為:

- 建立新的專案

- 將現有專案加入版本控制

- 嘗試尋找現有版本控制項目

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
 pvContext

[在]原始程式碼管理外掛程式上下文結構。

 hWnd

[在]源控件外掛程式可以用作它提供的任何對話框的父級的IDE視窗句柄。

 lpUser

[進出]使用者名稱(不超過SCC_USER_SIZE,包括 NULL 終止符)

 lpProjName

[進出]IDE 專案、專案工作區或 makefile 的名稱(不超過SCC_PRJPATH_SIZE,包括 NULL 終止符)。

 lp 本地路徑

[進出]專案的工作路徑。 如果是`bAllowChangePath``TRUE`,原始程式碼管理外掛程式可以修改此字串(不超過_MAX_PATH,包括空終止符)。

 lpAuxProjPath

[進出]返回的項目路徑的緩衝區(不超過SCC_PRJPATH_SIZE,包括 NULL 終止符)。

 bAllow 改變路徑

[在]如果是`TRUE`,原始程式碼管理外掛程式可以`lpLocalPath`提示和修改 字串。

 pb 新

[進出]中的值表示是否創建新專案。 傳回的值表示建立項目的成功:

|傳入|解譯|
|--------------|--------------------|
|TRUE|用戶可以創建新專案。|
|FALSE|使用者可能無法創建新專案。|

|傳出|解譯|
|--------------|--------------------|
|TRUE|創建了一個新專案。|
|FALSE|已選擇現有專案。|

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功創建或檢索專案。|
|SCC_I_OPERATIONCANCELED|已取消作業。|
|SCC_E_ACCESSFAILURE|訪問原始程式碼管理系統時出現問題,可能是由於網路或爭用問題。|
|SCC_E_CONNECTIONFAILURE|嘗試連接到原始程式碼管理系統時出現問題。|
|SCC_E_NONSPECIFICERROR|發生未指定的錯誤。|

## <a name="remarks"></a>備註
 此函數的目的是使 IDE`lpProjName`取得`lpAuxProjPath`參數與 。 在原始程式碼管理外掛程式提示使用者獲取此資訊後,它將這兩個字串傳回 IDE。 IDE 將這些字串保留在其解決方案檔中,並在使用者打開此專案時將其傳遞到[SccOpenProject。](../extensibility/sccopenproject-function.md) 這些字串使外掛程式能夠追蹤與專案關聯的資訊。

 初調用函數時,`lpAuxProjPath`將設定為空字串。 `lProjName`也可能為空,或者可能包含 IDE 專案名稱,原始程式碼管理外掛程式可能使用或忽略該名稱。 當函數成功返回時,外掛程式將返回兩個相應的字串。 IDE 不對這些字串進行假設,不會使用它們,也不會允許使用者修改它們。 如果使用者想要更改設置,IDE 將再次調`SccGetProjPath`用 ,傳遞與上次接收的相同值。 這使外掛程式能夠完全控制這兩個字串。

 對於`lpUser`,IDE 可能會傳遞使用者名,也可以簡單地將指標傳遞到空字串。 如果存在使用者名,原始程式碼管理外掛程式應將其用作預設值。 但是,如果未傳遞任何名稱,或者登入失敗與給定的名稱,外掛程式應提示使用者登入,並在收到有效的登錄時將`lpUser`名稱傳回 。 由於外掛程式可能會更改此字串,因此IDE將始終分配大小緩衝區 (+1)。`SCC_USER_LEN`

> [!NOTE]
> IDE 執行的第一個操作可能是`SccOpenProject`對函數或函數`SccGetProjPath`的調用。 因此,它們都有相同的`lpUser`參數,這使得原始程式碼管理外掛程式可以在任一時間登錄使用者。 即使從函數返回指示失敗,外掛程式也必須用有效的登錄名填充此字串。

 `lpLocalPath`是使用者保存專案的目錄。 它可能是一個空字串。 如果目前沒有定義目錄(例如,使用者嘗試從原始碼管理系統下載專案),如果是`bAllowChangePath``TRUE`,原始程式碼管理外掛程式可以提示使用者輸入或使用其他方法將其自己的字串放入`lpLocalPath`。 如果是`bAllowChangePath``FALSE`,外掛程式不應更改字串,因為使用者已在指定的目錄中工作。

 如果用戶創建新專案以置於原始程式碼管理之下,則在調用原始`SccGetProjPath`程式碼管理系統中,原始程式碼管理外掛程式實際上可能不會創建它。 相反,它將字串與的非`pbNew`零值一起傳遞,指示將在原始程式碼管理系統中創建專案。

 例如,如果 Visual Studio 中的 **「新專案**」精靈中的使用者將專案添加到原始碼管理中,Visual Studio 將呼叫此函數,該外掛程式確定是否可以在原始程式碼管理系統中創建新專案以包含 Visual Studio 專案。 如果使用者在完成嚮導之前按**下 「取消」 的,** 則永遠不會建立專案。 如果用戶按下 **「確定**」,則此時將調`SccOpenProject`用 Visual `SCC_OPT_CREATEIFNEW`Studio 傳入 ,並創建源控制的專案。

## <a name="see-also"></a>另請參閱
- [原始程式碼管理外掛程式 API 功能](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
