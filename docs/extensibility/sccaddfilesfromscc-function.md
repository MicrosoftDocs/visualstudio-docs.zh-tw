---
description: 此函式會將檔案清單從原始檔控制加入目前開啟的專案。
title: SccAddFilesFromSCC 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 056e918642e75bbd74c310499544cb2500428646
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060467"
---
# <a name="sccaddfilesfromscc-function"></a>SccAddFilesFromSCC 函式
此函式會將檔案清單從原始檔控制加入目前開啟的專案。

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

在原始檔控制外掛程式內容指標。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它做為它所提供之任何對話方塊的父代。

 lpUser

[in，out]使用者名稱 (SCC_USER_SIZE，包括 null 結束字元) 。

 lpAuxProjPath

[in，out]識別專案 (的輔助字串，最大的 `SCC_PRJPATH_` 大小，包括 null 結束字元) 。

 cFiles

在提供的檔案數目 `lpFilePaths` 。

 lpFilePaths

[in，out]要加入至目前專案的檔案名陣列。

 lpDestination

在要寫入檔案的目的地路徑。

 lpComment

在要套用至每個要加入之檔案的批註。

 pbResults

[in，out]旗標的陣列，這些旗標會設定為表示成功 (非零或 TRUE) 或失敗 (零或錯誤) 每個檔案的大小上限必須至少為 `cFiles` long (。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_E_PROJNOTOPEN|專案未開啟。|
|SCC_E_OPNOTPERFORMED|連接與指定的專案不同 `lpAuxProjPath.`|
|SCC_E_NOTAUTHORIZED|使用者未經授權，無法更新資料庫。|
|SCC_E_NONSPECIFICERROR|未知的錯誤。|
|SCC_I_RELOADFILE|需要重載檔案或專案。|

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
