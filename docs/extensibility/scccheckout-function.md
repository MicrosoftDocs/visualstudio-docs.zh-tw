---
title: SccCheckout 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4112190e145242da591fa3d8e4db7d054bd07466
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943136"
---
# <a name="scccheckout-function"></a>SccCheckout 函式
在指定完整檔案名的清單之後，此函式會將它們簽出至本機磁片磁碟機。 批註會套用至所有簽出的檔案。Comment 引數可以是 `null` 字串。

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
 pvCoNtext

在原始檔控制外掛程式內容結構。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它做為它所提供之任何對話方塊的父代。

 nFiles

在選取要簽出的檔案數目。

 lpFileNames

在要簽出之檔案的完整本機路徑名稱陣列。

 lpComment

在要套用至每個要簽出之所選檔案的批註。

 fOptions

在命令旗標 (查看 [特定命令所使用的位旗標](../extensibility/bitflags-used-by-specific-commands.md)) 。

 pvOptions

在原始檔控制外掛程式特定的選項。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|簽出成功。|
|SCC_E_FILENOTCONTROLLED|選取的檔案不在原始程式碼控制之下。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或爭用問題。 建議您重試。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項操作。|
|SCC_E_NONSPECIFICERROR|模糊失敗。 未簽出檔案。|
|SCC_E_ALREADYCHECKEDOUT|使用者已簽出檔案。|
|SCC_E_FILEISLOCKED|檔案已鎖定，禁止建立新版本。|
|SCC_E_FILEOUTEXCLUSIVE|另一位使用者已完成此檔案的獨佔簽出。|
|SCC_I_OPERATIONCANCELED|作業已在完成前取消。|

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [特定命令所使用的位旗標](../extensibility/bitflags-used-by-specific-commands.md)
