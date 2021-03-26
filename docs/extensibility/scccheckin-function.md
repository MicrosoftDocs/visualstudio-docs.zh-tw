---
description: 此函式會將先前簽出的檔案簽入至原始檔控制系統，並儲存變更並建立新的版本。
title: SccCheckin 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d6864549c6825092b6ad26be199f8c7b5ea6bab6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060428"
---
# <a name="scccheckin-function"></a>SccCheckin 函式
此函式會將先前簽出的檔案簽入至原始檔控制系統，並儲存變更並建立新的版本。 呼叫此函式時，會使用計數和要簽入之檔案的名稱陣列。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccCheckin (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPSTR*    lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>參數
 pvCoNtext

在原始檔控制外掛程式內容結構。

 hWnd

在IDE 視窗的控制碼，SCC 外掛程式可將其做為它所提供之任何對話方塊的父代。

 nFiles

在選取要簽入的檔案數目。

 lpFileNames

在要簽入之檔案的完整本機路徑名稱陣列。

 lpComment

在要套用至每個要簽入之選取檔案的批註。 `NULL`如果原始檔控制外掛程式應該提示輸入批註，此參數為。

 fOptions

在命令旗標，也就是0或 `SCC_KEEP_CHECKEDOUT` 。

 pvOptions

在SCC 外掛程式特定的選項。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功簽入檔案。|
|SCC_E_FILENOTCONTROLLED|選取的檔案不在原始程式碼控制之下。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或爭用問題。 建議您重試。|
|SCC_E_NONSPECIFICERROR|模糊失敗。 未簽入檔案。|
|SCC_E_NOTCHECKEDOUT|使用者尚未簽出檔案，所以無法將它簽入。|
|SCC_E_CHECKINCONFLICT|無法執行簽入，因為：<br /><br /> -另一位使用者已預先簽入，且 `bAutoReconcile` 為 false。<br /><br /> -或-<br /><br /> -無法完成自動合併 (例如，當檔案是二進位) 時。|
|SCC_E_VERIFYMERGE|檔案已自動合併，但尚未簽入擱置的使用者驗證。|
|SCC_E_FIXMERGE|檔案已自動合併，但因為合併衝突必須手動解決，所以尚未簽入。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項操作。|
|SCC_I_OPERATIONCANCELED|作業已在完成前取消。|
|SCC_I_RELOADFILE|需要重載檔案或專案。|
|SCC_E_FILENOTEXIST|找不到本機檔案。|

## <a name="remarks"></a>備註
 批註會套用至所有簽入的檔案。 批註引數可以是 `null` 字串，在此情況下，原始檔控制外掛程式可以提示使用者輸入每個檔案的批註字串。

 您 `fOptions` 可以為引數指定 `SCC_KEEP_CHECKEDOUT` 旗標的值，以指出使用者將簽入檔案的意圖，並再次將其簽出。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
