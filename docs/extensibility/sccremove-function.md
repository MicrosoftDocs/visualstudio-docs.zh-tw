---
title: SccRemove 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ff7299868b96aedb7cc096b4e939a0f8015aeb8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720780"
---
# <a name="sccremove-function"></a>SccRemove 函式
此函式會從原始檔控制系統中刪除檔案。

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

在原始檔控制外掛程式的內容結構。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它所提供之任何對話方塊的父系。

 n

在@No__t_0 陣列中指定的檔案數目。

 lpFileNames

在要移除之檔案的完整本機路徑名稱陣列。

 lpComment

在要套用至要移除之每個檔案的批註。

 fOptions

在命令旗標（未使用）。

 pvOptions

在原始檔控制外掛程式特定選項。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式執行應會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|移除成功。|
|SCC_E_FILENOTCONTROLLED|選取的檔案不在原始檔控制之下。|
|SCC_E_OPNOTSUPPORTED|原始檔控制系統不支援這種作業。|
|SCC_E_ISCHECKEDOUT|無法移除檔案，因為使用者目前已簽出該檔案。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或競爭問題。|
|SCC_E_NOTAUTHORIZED|不允許使用者執行此作業。|
|SCC_E_NONSPECIFICERROR|模糊失敗;檔案未移除。|
|SCC_I_OPERATIONCANCELED|作業已在完成前取消。|

## <a name="remarks"></a>備註
 此函式會將檔案從原始檔控制系統中移除，但不會將它們從使用者的本機硬碟中刪除。

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)