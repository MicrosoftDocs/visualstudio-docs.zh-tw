---
title: SccUncheck 功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4317133b2f215e0f9af447e5c042785561231f63
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700239"
---
# <a name="sccuncheckout-function"></a>SccUncheckout 函式
此函數撤銷以前的簽出操作,從而在簽出之前將所選檔或文件的內容還原到狀態。 結帳後對檔所做的所有更改都丟失。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccUncheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>參數
 pvContext

[在]原始程式碼管理外掛程式上下文結構。

 hWnd

[在]源控件外掛程式可以用作它提供的任何對話框的父級的IDE視窗句柄。

 n 檔案

[在]`lpFileNames`陣列中指定的檔案數。

 lpFile 名稱

[在]要復原簽出的檔案完全限定的本地路徑名稱的陣列。

 fOptions

[在]命令標誌(未使用)。

 pvOptions

[在]原始程式碼管理外掛程式特定選項。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|撤銷簽出成功。|
|SCC_E_FILENOTCONTROLLED|所選檔不受原始程式碼控制。|
|SCC_E_ACCESSFAILURE|訪問原始程式碼管理系統時出現問題,可能是由於網路或爭用問題。 建議重試。|
|SCC_E_NONSPECIFICERROR|非特異性故障。 撤銷簽出未成功。|
|SCC_E_NOTCHECKEDOUT|使用者未簽出該檔。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行此操作。|
|SCC_E_PROJNOTOPEN|尚未從原始程式碼管理打開該專案。|
|SCC_I_OPERATIONCANCELED|操作在完成之前已取消。|

## <a name="remarks"></a>備註
 此操作後,將清除`SCC_STATUS_CHECKEDOUT``SCC_STATUS_MODIFIED`執行復原簽出的檔案的和標誌。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
