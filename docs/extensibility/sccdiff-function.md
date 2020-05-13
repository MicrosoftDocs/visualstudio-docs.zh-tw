---
title: SccDiff 功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b68df68ce7fa4ad5cbc98db256204ddf8623d2c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701027"
---
# <a name="sccdiff-function"></a>SccDiff 函數
此函數顯示(或可選地只檢查)當前檔(本地磁碟上)與其在原始程式碼管理系統中的最後簽入版本之間的差異。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccDiff(
   LPVOID    pvContext,
   HWND      hWnd,
   LPCSTR    lpFileName,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>參數
 pvContext

[在]原始程式碼管理外掛程式上下文結構。

 hWnd

[在]源控件外掛程式可以用作它提供的任何對話框的父級的IDE視窗句柄。

 lpFile 名稱

[在]請求差異的檔名。

 fOptions

[在]命令標誌。 有關詳細資訊,請參閱備註。

 pvOptions

[在]原始程式碼管理外掛程式特定選項。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|工作副本和伺服器版本相同。|
|SCC_I_FILESDIFFERS|工作副本與原始程式碼管理下的版本不同。|
|SCC_I_RELOADFILE|需要重新載入檔或專案。|
|SCC_E_FILENOTCONTROLLED|該檔不受原始程式碼管理。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行此操作。|
|SCC_E_ACCESSFAILURE|訪問原始程式碼管理系統時出現問題,可能是由於網路或爭用問題。 建議重試。|
|SCC_E_NONSPECIFICERROR|非特異性故障;未獲取文件差異。|
|SCC_E_FILENOTEXIST|找不到本地檔。|

## <a name="remarks"></a>備註
 此功能具有兩種不同的用途。 預設情況下,它顯示對檔的更改清單。 原始程式碼管理外掛程式以您選擇的任何格式打開自己的視窗,以顯示使用者在磁碟上的檔案與原始程式碼管理下檔案的最新版本之間的差異。

 或者,IDE 可能只需要確定檔是否已更改。 例如,IDE 可能需要確定在未通知用戶的情況下簽出檔是否安全。 在這種情況下,IDE 會傳遞`SCC_DIFF_CONTENTS`標誌 。 原始程式碼管理外掛程式必須對照源代碼管理的檔案檢查磁碟上的檔位元組,並返回一個值,指示兩個檔案是否不同而不向使用者顯示任何內容。

 作為性能優化,原始程式碼管理外掛程式可以使用基於校驗和或時間戳的替代方法,`SCC_DIFF_CONTENTS`而不是: 這些比較形式顯然更快但不太可靠。 並非所有原始程式碼管理系統都支援這些替代比較方法,外掛程式可能必須回到內容比較。 所有原始程式碼管理外掛程式必須至少支援內容比較。

> [!NOTE]
> 快速差異標誌是互斥的。 不傳遞任何標誌是有效的,但同時傳遞多個標誌無效。 `SCC_DIFF_QUICK_DIFF`,這是一個包含所有標誌的掩碼,可用於測試,但絕不應作為參數傳遞。

|`fOption`|意義|
|---------------|-------------|
|SCC_DIFF_IGNORECASE|區分大小寫的比較(可用於快速或視覺差異)。|
|SCC_DIFF_IGNORESPACE|忽略空白(可用於快速或視覺差異)。|
|SCC_DIFF_QD_CONTENTS|靜默比較檔,位元組位元組。|
|SCC_DIFF_QD_CHECKSUM|在支援時,通過校驗和靜靜比較檔。 如果不支援,則回落到內容的比較。|
|SCC_DIFF_QD_TIME|在支援時,通過時間戳悄悄地比較檔。 如果不支援,則回落到內容的比較。|

## <a name="see-also"></a>另請參閱
- [原始程式碼管理外掛程式 API 功能](../extensibility/source-control-plug-in-api-functions.md)
