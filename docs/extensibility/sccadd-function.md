---
title: SccAdd 功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 23a6226b0d3cc2441a509c16b2e4672a766f3329
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701306"
---
# <a name="sccadd-function"></a>SccAdd 函數
此功能向原始程式碼管理系統添加新檔。

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
 pvContext

[在]原始程式碼管理外掛程式上下文結構。

 hWnd

[在]源控件外掛程式可以用作它提供的任何對話框的父級的IDE視窗句柄。

 n 檔案

[在]選擇新增到當前專案中的檔案數(如陣列中給出的`lpFileNames`)。

 lpFile 名稱

[在]要添加的檔完全限定的本地名稱的陣列。

 lpComment

[在]要應用於要添加到的所有文件的註釋。

 pfOptions

[在]命令標誌陣列,按檔提供。

 pvOptions

[在]原始程式碼管理外掛程式特定選項。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|添加操作成功。|
|SCC_E_FILEALREADYEXISTS|所選檔已在原始程式碼管理中。|
|SCC_E_TYPENOTSUPPORTED|源代碼管理系統不支援檔的類型(例如二進位檔案)。|
|SCC_E_OPNOTSUPPORTED|原始程式碼管理系統不支援此操作。|
|SCC_E_ACCESSFAILURE|訪問原始程式碼管理系統時出現問題,可能是由於網路或爭用問題。 建議重試。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行此操作。|
|SCC_E_NONSPECIFICERROR|非特異性故障;未執行添加。|
|SCC_I_OPERATIONCANCELED|操作在完成之前已取消。|
|SCC_I_RELOADFILE|需要重新載入檔或專案。|
|SCC_E_FILENOTEXIST|找不到本地檔案。|

## <a name="remarks"></a>備註
 通常`fOptions`在此處取代為陣列`pfOptions`, 每個檔案有一`LONG`個選項 規範。 這是因為檔類型可能因檔而異。

> [!NOTE]
> 為同一檔指定和`SCC_FILETYPE_TEXT``SCC_FILETYPE_BINARY`選項是無效的,但同時指定這兩個檔都無效。 設置兩者與設定`SCC_FILETYPE_AUTO`相同,在這種情況下,原始程式碼管理外掛程式自動檢測檔類型。

 下面是`pfOptions`陣列中使用的標誌清單:

|選項|值|意義|
|------------|-----------|-------------|
|SCC_FILETYPE_AUTO|0x00|源代碼管理外掛程式應檢測檔類型。|
|SCC_FILETYPE_TEXT|0x01|指示 ASCII 文字檔。|
|SCC_FILETYPE_BINARY|0x02|指示 ASCII 本文以外的文件類型。|
|SCC_ADD_STORELATEST|0x04|只存儲檔的最新副本,沒有增量。|
|SCC_FILETYPE_TEXT_ANSI|0x08|將檔案視為 ANSI 文本。|
|SCC_FILETYPE_UTF8|0x10|以 UTF8 格式將檔案視為 Unicode 文字。|
|SCC_FILETYPE_UTF16LE|0x20|將檔案視為 UTF16 小 Endian 格式的 Unicode 文字。|
|SCC_FILETYPE_UTF16BE|0x40|將檔案視為 UTF16 大 Endian 格式的 Unicode 文字。|

## <a name="see-also"></a>另請參閱
- [原始程式碼管理外掛程式 API 功能](../extensibility/source-control-plug-in-api-functions.md)
