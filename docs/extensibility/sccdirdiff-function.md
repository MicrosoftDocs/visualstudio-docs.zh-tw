---
title: SccDirDiff 功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1bb592a1174a91480ed76ef818733c288c5273c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701007"
---
# <a name="sccdirdiff-function"></a>SccDirDiff 函數
此功能顯示用戶端磁碟上的當前本地目錄與原始程式碼管理下的相應專案之間的差異。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccDirDiff(
   LPVOID    pContext,
   HWND      hWnd,
   LPCSTR    lpDirName,
   LONG      dwFlags,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>參數
 pContext

[在]原始程式碼管理外掛程式上下文結構。

 hWnd

[在]源控件外掛程式可以用作它提供的任何對話框的父級的IDE視窗句柄。

 lpDirname

[在]本地目錄的完全限定路徑,用於顯示視覺差異。

 dwFlags

[在]命令標誌(請參閱備註部分)。

 pvOptions

[在]原始程式碼管理外掛程式特定選項。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|磁碟上的目錄與原始程式碼管理中的專案相同。|
|SCC_I_FILESDIFFER|磁碟上的目錄與原始程式碼管理中的專案不同。|
|SCC_I_RELOADFILE|需要重新載入檔或專案。|
|SCC_E_FILENOTCONTROLLED|目錄不受原始程式碼控制。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行此操作。|
|SCC_E_ACCESSFAILURE|訪問原始程式碼管理系統時出現問題,可能是由於網路或爭用問題。 建議重試。|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|非特異性故障。|
|SCC_E_FILENOTEXIST|找不到本地目錄。|

## <a name="remarks"></a>備註
 此功能用於指示原始程式碼管理外掛程式向使用者顯示對指定目錄的更改清單。 該外掛程式以其選擇的格式打開自己的視窗,以顯示使用者在磁碟上的目錄與版本控制下的相應項目之間的差異。

 如果外掛程式根本不支援目錄的比較,則即使不支援"快速差異"選項,它也必須支援基於檔名對目錄進行比較。

|`dwFlags`|解譯|
|---------------|--------------------|
|SCC_DIFF_IGNORECASE|區分大小寫的比較(可用於快速差異或視覺)。|
|SCC_DIFF_IGNORESPACE|忽略空白(可用於快速差異或視覺)。|
|SCC_DIFF_QD_CONTENTS|如果原始程式碼管理外掛程式支援,請靜默地比較目錄,位元組。|
|SCC_DIFF_QD_CHECKSUM|如果外掛程式支援,則通過校驗和靜靜比較目錄,或者,如果不支援,則回落到SCC_DIFF_QD_CONTENTS。|
|SCC_DIFF_QD_TIME|如果外掛程式支援,請通過其時間戳靜靜比較目錄,或者,如果不支援,則落在SCC_DIFF_QD_CHECKSUM或SCC_DIFF_QD_CONTENTS。|

> [!NOTE]
> 此函數使用與[SccDiff](../extensibility/sccdiff-function.md)相同的命令標誌。 但是,原始程式碼管理外掛程式可以選擇不支援目錄的「快速差異」。

## <a name="see-also"></a>另請參閱
- [原始程式碼管理外掛程式 API 功能](../extensibility/source-control-plug-in-api-functions.md)
