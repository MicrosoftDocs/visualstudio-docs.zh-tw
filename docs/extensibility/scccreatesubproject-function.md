---
title: Scccreate 子專案功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74354e05b16830f599dd706fbe48aadd75b11a18
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701044"
---
# <a name="scccreatesubproject-function"></a>SccCreate 子專案功能
此函數在參數指定的現有父專案下創建具有給定名稱的`lpParentProjPath`子專案。

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

[在]源代碼管理外掛程式上下文指標。

 hWnd

[在]源控件外掛程式可以用作它提供的任何對話框的父級的IDE視窗句柄。

 lpUser

[進出]使用者名(最多SCC_USER_SIZE,包括 NULL 終止符)。

 lpParentProjPath

[在]標識父項目的路徑的字串(最多SCC_PRJPATH_SIZE,包括 NULL 終止符)。

 lpSubProj 名稱

[在]建議的子專案名稱(最多SCC_PRJPATH_SIZE,包括 NULL 終止符)。

 lpAuxProjPath

[進出]標識項目的輔助字串(最多SCC_PRJPATH_SIZE,包括 NULL 終止字)。

 lpSubProjPath

[進出]標識子項目的路徑的輸出字串(最多SCC_PRJPATH_SIZE,包括 NULL 終止符)。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功創建子專案。|
|SCC_E_INITIALIZEFAILED|無法初始化父專案。|
|SCC_E_INVALIDUSER|使用者無法登錄到原始程式碼管理系統。|
|SCC_E_COULDNOTCREATEPROJECT|無法建立子專案。|
|SCC_E_PROJSYNTAXERR|無效的專案語法。|
|SCC_E_UNKNOWNPROJECT|源控件外掛程式未知父專案。|
|SCC_E_INVALIDFILEPATH|無效或無法使用的檔案路徑。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行此操作。|
|SCC_E_ACCESSFAILURE|訪問原始程式碼管理系統時出現問題,可能是由於網路或爭用問題。 建議重試。|
|SCC_E_CONNECTIONFAILURE|存在原始程式碼管理外掛程式連接問題。|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|非特異性故障。|

## <a name="remarks"></a>備註
 如果已存在名稱的子專案,則函數可以更改預設名稱以創建唯一名稱,例如向其中添加"#\<數位>"。 調用方必須準備好接受`lpUser`對`lpSubProjPath`的`lpAuxProjPath`更改。 然後`lpSubProjPath`,`lpAuxProjPath`在調用[SccOpenProject](../extensibility/sccopenproject-function.md)中使用 和 參數。 調用方不應在返回時修改它們。 這些字串為原始程式碼管理外掛程式提供了一種追蹤它需要與專案關聯的資訊的方法。 呼叫者 IDE 在傳回時不會顯示這兩個參數,因為外掛程式可以使用可能不適合查看的格式化字串。 函數返回成功或失敗代碼,如果成功,則用新專案的完整專案路徑填充`lpSubProjPath`變數。

 此函數類似於[SccGetProjPath,](../extensibility/sccgetprojpath-function.md)只不過它默默地創建一個專案,而不是提示用戶選擇一個專案。 呼叫函數`SccCreateSubProject`時`lpParentProjName``lpAuxProjPath`, 不會為空,並且將對應於有效的專案。 這些字串通常由IDE從以前對`SccGetProjPath`函數的調用或[SccGet父專案路徑](../extensibility/sccgetparentprojectpath-function.md)接收。

 參數`lpUser`是使用者名。 IDE 將傳遞以前從`SccGetProjPath`接收的相同使用者名,原始程式碼管理外掛程式應使用該名稱作為預設值。 如果使用者已與外掛程式建立了打開的連接,則外掛程式應嘗試消除任何提示,以確保該函數靜默工作。 但是,如果登錄失敗,外掛程式應提示使用者登錄,並在收到有效的登錄時,將名稱轉`lpUser`回 。 由於外掛程式可能會更改此字串,因此IDE將始終分配大小緩衝區(SCC_USER_LEN+1或SCC_USER_SIZE,其中包括空終止符的空間)。 如果更改了字串,則新字串必須是有效的登錄名(至少與舊字串一樣有效)。

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>SccCreate 子專案和 SccGet 父項目路徑的技術說明
 在 Visual Studio 中,將解決方案和專案添加到原始碼管理中已簡化,以最大程度地減少提示使用者選擇原始程式碼管理系統中位置的次數。 如果原始程式資料管理外掛程式同時支援新`SccCreateSubProject``SccGetParentProjectPath`功能和,則 Visual Studio 將啟動這些更改。 但是,以下註冊表項可用於禁用這些更改並恢復到以前的 Visual Studio(原始程式碼管理外掛程式 API 版本 1.1)行為:

 **[HKEY_CURRENT_USER_軟體\微軟[VisualStudio]8.0\源控制]"不創建解決方案 RootfolderinSourceControl"=dword:0000001**

 如果這個註冊表項不存在或設定為 dword:00000000,Visual Studio 將試著`SccCreateSubProject``SccGetParentProjectPath`使用新功能和 。

 如果註冊表項設置為 dword:00000001,Visual Studio 不會嘗試使用這些新功能,並且添加到原始碼管理的操作將像在 Visual Studio 的早期版本中那樣工作。

## <a name="see-also"></a>另請參閱
- [原始程式碼管理外掛程式 API 功能](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
