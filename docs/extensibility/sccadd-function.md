---
description: 此函式會將新檔案新增至原始檔控制系統。
title: SccAdd 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7c577bd865a7534a5c4e13253e921ef188e7f0ac
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085685"
---
# <a name="sccadd-function"></a>SccAdd 函式
此函式會將新檔案新增至原始檔控制系統。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccAdd(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG*     pfOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>參數
 pvCoNtext

在原始檔控制外掛程式內容結構。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它做為它所提供之任何對話方塊的父代。

 nFiles

在選取要加入目前專案中的檔案數目（如陣列中所指定） `lpFileNames` 。

 lpFileNames

在要加入之檔案的完整本機名稱陣列。

 lpComment

在要套用至所有要加入之檔案的批註。

 pfOptions

在命令旗標的陣列，以每個檔案為基礎來提供。

 pvOptions

在原始檔控制外掛程式特定的選項。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|新增作業已成功。|
|SCC_E_FILEALREADYEXISTS|選取的檔案已在原始檔控制之下。|
|SCC_E_TYPENOTSUPPORTED|原始檔控制系統不支援檔案類型 (例如，二進位) 。|
|SCC_E_OPNOTSUPPORTED|原始檔控制系統不支援這種操作。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或爭用問題。 建議您重試。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項操作。|
|SCC_E_NONSPECIFICERROR|模糊失敗;未執行新增。|
|SCC_I_OPERATIONCANCELED|作業已在完成前取消。|
|SCC_I_RELOADFILE|需要重載檔案或專案。|
|SCC_E_FILENOTEXIST|找不到本機檔案。|

## <a name="remarks"></a>備註
 `fOptions`陣列會在此取代一般， `pfOptions` 且每個檔案都有一個 `LONG` 選項規格。 這是因為檔案類型可能會因檔案而有所不同。

> [!NOTE]
> 同時指定相同檔案的和選項是不正確 `SCC_FILETYPE_TEXT` `SCC_FILETYPE_BINARY` ，但指定兩者都是有效的。 設定兩者都與設定相同 `SCC_FILETYPE_AUTO` ，在這種情況下，原始檔控制外掛程式會自動偵測 dll 檔案類型。

 以下是陣列中使用的旗標清單 `pfOptions` ：

|選項|值|意義|
|------------|-----------|-------------|
|SCC_FILETYPE_AUTO|0x00|原始檔控制外掛程式應該會偵測檔案類型。|
|SCC_FILETYPE_TEXT|0x01|表示 ASCII 文字檔。|
|SCC_FILETYPE_BINARY|0x02|表示 ASCII 文字以外的檔案類型。|
|SCC_ADD_STORELATEST|0x04|只儲存檔案的最新複本，無差異。|
|SCC_FILETYPE_TEXT_ANSI|0x08|將檔案視為 ANSI 文字。|
|SCC_FILETYPE_UTF8|0x10|將檔案視為 UTF8 格式的 Unicode 文字。|
|SCC_FILETYPE_UTF16LE|0x20|將檔案視為採用 UTF16 位元組由小到大格式的 Unicode 文字。|
|SCC_FILETYPE_UTF16BE|0x40|將檔案視為採用 UTF16 Big Endian 格式的 Unicode 文字。|

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
