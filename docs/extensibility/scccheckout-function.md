---
title: SccCheckout 功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ed809e33a80bf2903c88550e97b28b1e0178bcd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701099"
---
# <a name="scccheckout-function"></a>SccCheckout 功能
給定完全限定的檔名清單,此函數會將它們簽到本地驅動器。 註釋應用於簽出的所有檔。註解參數可以是字串`null`。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccCheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>參數
 pvContext

[在]原始程式碼管理外掛程式上下文結構。

 hWnd

[在]源控件外掛程式可以用作它提供的任何對話框的父級的IDE視窗句柄。

 n 檔案

[在]選擇要簽出的檔案數。

 lpFile 名稱

[在]要簽出的檔完全限定的本地路徑名稱的陣列。

 lpComment

[在]要應用於要簽出的每個選定檔的註釋。

 fOptions

[在]命令標誌(請參閱[特定命令使用的比特標誌](../extensibility/bitflags-used-by-specific-commands.md))。

 pvOptions

[在]原始程式碼管理外掛程式特定選項。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|退房成功。|
|SCC_E_FILENOTCONTROLLED|所選檔不受原始程式碼控制。|
|SCC_E_ACCESSFAILURE|訪問原始程式碼管理系統時出現問題,可能是由於網路或爭用問題。 建議重試。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行此操作。|
|SCC_E_NONSPECIFICERROR|非特異性故障。 檔未簽出。|
|SCC_E_ALREADYCHECKEDOUT|使用者已簽出該檔。|
|SCC_E_FILEISLOCKED|該檔已鎖定,禁止創建新版本。|
|SCC_E_FILEOUTEXCLUSIVE|其他使用者已對此文件執行獨佔簽出。|
|SCC_I_OPERATIONCANCELED|操作在完成之前已取消。|

## <a name="see-also"></a>另請參閱
- [原始程式碼管理外掛程式 API 功能](../extensibility/source-control-plug-in-api-functions.md)
- [特定指令使用的位元號](../extensibility/bitflags-used-by-specific-commands.md)
