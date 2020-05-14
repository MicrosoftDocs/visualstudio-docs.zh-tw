---
title: 放大縮小字型功能 放大縮小字型功能微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17889d50dbdcf68dd4cca161d6703b8b6d69ad47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700447"
---
# <a name="sccremove-function"></a>SccRemove 函式
此功能從原始程式碼管理系統中刪除檔案。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccRemove(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
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

[在]要刪除的檔案完全限定的本地路徑名稱的陣列。

 lpComment

[在]要應用於要刪除的每個檔的註釋。

 fOptions

[在]命令標誌(未使用)。

 pvOptions

[在]原始程式碼管理外掛程式特定選項。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|刪除成功。|
|SCC_E_FILENOTCONTROLLED|所選檔不受原始程式碼管理。|
|SCC_E_OPNOTSUPPORTED|原始程式碼管理系統不支援此操作。|
|SCC_E_ISCHECKEDOUT|無法刪除檔案,因為使用者當前已簽出該檔。|
|SCC_E_ACCESSFAILURE|訪問原始程式碼管理系統時出現問題,可能是由於網路或爭用問題。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行此操作。|
|SCC_E_NONSPECIFICERROR|非特異性故障;檔案未被刪除。|
|SCC_I_OPERATIONCANCELED|操作在完成之前已取消。|

## <a name="remarks"></a>備註
 此功能從原始程式碼管理系統中刪除檔,但不會從使用者的本地硬碟驅動器中刪除這些檔。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
