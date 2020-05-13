---
title: 歷史函數 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 734afefd97e61867076d487acbcf67f10f54e672
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700655"
---
# <a name="scchistory-function"></a>SccHistory 函式
此函數顯示指定檔的歷史記錄。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccHistory(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>參數
 `pvContext`

[在]原始程式碼管理外掛程式上下文結構。

 `hWnd`

[在]源控件外掛程式可以用作它提供的任何對話框的父級的IDE視窗句柄。

 `nFiles`

[在]`lpFileName`陣列中指定的檔案數。

 `lpFileName`

[在]檔完全限定名稱的陣列。

 `fOptions`

[在]命令標誌(目前未使用)。

 `pvOptions`

[在]原始程式碼管理外掛程式特定選項。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功獲取版本歷史記錄。|
|SCC_I_RELOADFILE|原始程式碼管理系統實際上在獲取歷史記錄時修改了磁碟上的檔(例如,通過獲取其舊版本),因此 IDE 應重新載入此檔。|
|SCC_E_FILENOTCONTROLLED|該檔不受原始程式碼管理。|
|SCC_E_OPNOTSUPPORTED|原始程式碼管理系統不支援此操作。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行此操作。|
|SCC_E_ACCESSFAILURE|訪問原始程式碼管理系統時出現問題,可能是由於網路或爭用問題。 建議重試。|
|SCC_E_PROJNOTOPEN|專案尚未打開。|
|SCC_E_NONSPECIFICERROR|非特異性故障。 無法獲取文件歷史記錄。|

## <a name="remarks"></a>備註
 原始程式碼管理外掛程式可以顯示自己的對話框,以顯示每個檔的歷史記錄,用`hWnd`作父視窗。 或者,如果支援,可以使用提供給[SccOpenProject](../extensibility/sccopenproject-function.md)的可選文本輸出回調功能。

 請注意,在某些情況下,正在檢查的檔可能會在執行此調用期間更改。 例如,[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]歷史記錄命令為使用者提供了獲取檔舊版本的機會。 在這種情況下,原始程式碼管理外掛程式`SCC_I_RELOAD`將返回 以警告 IDE 需要重新載入檔。

> [!NOTE]
> 如果原始程式管理外掛程式不支援該檔陣列的此功能,則只能顯示第一個檔案的檔歷史記錄。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
