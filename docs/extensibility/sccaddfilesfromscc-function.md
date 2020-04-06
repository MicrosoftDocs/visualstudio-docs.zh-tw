---
title: Sccadd檔從SCC功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d22527644edbf1697112f5cf8b73b8a3f72b774
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701280"
---
# <a name="sccaddfilesfromscc-function"></a>SCC 函式包含檔案
此函數將檔案清單從原始程式碼管理添加到當前打開的專案。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccAddFilesFromSCC(
   LPVOID  pContext,
   HWND    hWnd,
   LPSTR   lpUser,
   LPSTR   lpAuxProjPath,
   LONG    cFiles,
   LPCSTR* lpFilePaths,
   LPCSTR  lpDestination,
   LPCSTR  lpComment,
   LPBOOL  pbResults
);
```

### <a name="parameters"></a>參數
 pContext

[在]源代碼管理外掛程式上下文指標。

 hWnd

[在]源控件外掛程式可以用作它提供的任何對話框的父級的IDE視窗句柄。

 lpUser

[進出]使用者名(最多SCC_USER_SIZE,包括空終止符)。

 lpAuxProjPath

[進出]標識項目的輔助字串(最多`SCC_PRJPATH_`大小,包括空終止字)。

 cFiles

[在]提供`lpFilePaths`的檔數。

 lpFilePath

[進出]要添加到當前項目的檔名陣列。

 lp目標

[在]要寫入檔的目標路徑。

 lpComment

[在]要應用於要添加到的每個檔的註解。

 pb 結果

[進出]設置為指示每個檔成功(非零或 TRUE)或失敗(零或 FALSE)的標誌陣列(陣列的大小`cFiles`必須至少為長)。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|專案未打開。|
|SCC_E_OPNOTPERFORMED|連線與指定的項目不同`lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|用戶無權更新資料庫。|
|SCC_E_NONSPECIFICERROR|未知的錯誤。|
|SCC_I_RELOADFILE|需要重新載入檔或專案。|

## <a name="see-also"></a>另請參閱
- [原始程式碼管理外掛程式 API 功能](../extensibility/source-control-plug-in-api-functions.md)
