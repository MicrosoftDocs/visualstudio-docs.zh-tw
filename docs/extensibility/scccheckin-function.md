---
title: SccCheckin 功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5ba512642e1a63d9d39856f96194d717583d44f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701189"
---
# <a name="scccheckin-function"></a>SccCheckin 功能
此函數將以前簽出的檔簽入到原始程式碼管理系統,儲存更改並創建新版本。 此函數使用要簽入的檔的計數和名稱陣列進行調用。

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
 pvContext

[在]原始程式碼管理外掛程式上下文結構。

 hWnd

[在]SCC 外掛程式可以用作它提供的任何對話框的父級的IDE視窗句柄。

 n 檔案

[在]選擇要簽入的檔案數。

 lpFile 名稱

[在]要簽入的檔完全限定的本地路徑名稱的陣列。

 lpComment

[在]要應用於要簽入的每個選定檔的註解。 此參數是`NULL`源控件外掛程式應提示發表評論。

 fOptions

[在]命令旗標,0`SCC_KEEP_CHECKEDOUT`或 。

 pvOptions

[在]SCC 外掛程式特定選項。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功簽入檔。|
|SCC_E_FILENOTCONTROLLED|所選檔不受原始程式碼控制。|
|SCC_E_ACCESSFAILURE|訪問原始程式碼管理系統時出現問題,可能是由於網路或爭用問題。 建議重試。|
|SCC_E_NONSPECIFICERROR|非特異性故障。 檔未簽入。|
|SCC_E_NOTCHECKEDOUT|使用者尚未簽出該檔,因此無法簽入該檔。|
|SCC_E_CHECKINCONFLICT|無法執行簽入,因為:<br /><br /> - 其他使用者已提前簽入,`bAutoReconcile`並且 為 false。<br /><br /> -或-<br /><br /> - 無法執行自動合併(例如,當檔為二進位檔時)。|
|SCC_E_VERIFYMERGE|檔已自動合併,但尚未簽入等待用戶驗證。|
|SCC_E_FIXMERGE|檔已自動合併,但由於合併衝突必須手動解決,因此尚未簽入。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行此操作。|
|SCC_I_OPERATIONCANCELED|操作在完成之前已取消。|
|SCC_I_RELOADFILE|需要重新載入檔或專案。|
|SCC_E_FILENOTEXIST|找不到本地檔案。|

## <a name="remarks"></a>備註
 註釋應用於正在簽入的所有檔。 註釋參數可以是字串`null`,在這種情況下,原始程式碼管理外掛程式可以提示使用者為每個檔輸入註釋字串。

 可以為`fOptions`參數`SCC_KEEP_CHECKEDOUT`提供 標誌的值,以指示使用者打算簽入並再次簽出該檔。

## <a name="see-also"></a>另請參閱
- [原始程式碼管理外掛程式 API 功能](../extensibility/source-control-plug-in-api-functions.md)
