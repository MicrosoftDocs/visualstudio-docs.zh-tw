---
description: 此函式會刪除原始檔控制系統中的檔案。
title: SccRemove 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d80daf83458c9e05ef0a081348080579e7fafef4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073868"
---
# <a name="sccremove-function"></a>SccRemove 函式
此函式會刪除原始檔控制系統中的檔案。

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
 pvCoNtext

在原始檔控制外掛程式內容結構。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它做為它所提供之任何對話方塊的父代。

 nFiles

在陣列中指定的檔案數目 `lpFileNames` 。

 lpFileNames

在要移除之檔案的完整本機路徑名稱陣列。

 lpComment

在要套用至每個要移除之檔案的批註。

 fOptions

在命令旗標 (未使用的) 。

 pvOptions

在原始檔控制外掛程式特定的選項。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|移除成功。|
|SCC_E_FILENOTCONTROLLED|選取的檔案不在原始檔控制之下。|
|SCC_E_OPNOTSUPPORTED|原始檔控制系統不支援這種操作。|
|SCC_E_ISCHECKEDOUT|因為使用者目前已簽出檔案，所以無法將其移除。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或爭用問題。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行這項操作。|
|SCC_E_NONSPECIFICERROR|模糊失敗;檔案未移除。|
|SCC_I_OPERATIONCANCELED|作業已在完成前取消。|

## <a name="remarks"></a>備註
 此函式會從原始檔控制系統中移除檔案，但不會從使用者的本機硬碟中刪除這些檔案。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
