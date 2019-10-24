---
title: SccRename 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30b2928653507b670160c72ca3ce09a0227a4170
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720760"
---
# <a name="sccrename-function"></a>SccRename 函式
此函式會重新命名原始檔控制系統中的檔案。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccRename(
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName,
   LPCSTR lpNewName
);
```

#### <a name="parameters"></a>參數
 pvCoNtext

在原始檔控制外掛程式的內容結構。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它所提供之任何對話方塊的父系。

 lpFileName

在要重新命名之檔案的完整檔案名。

 lpNewName

在完整的新名稱。 如果目錄路徑不同，則檔案已從一個子目錄移到另一個。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式執行應會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|重新命名作業已成功完成。|
|SCC_E_PROJNOTOPEN|專案未在原始檔控制下開啟。|
|SCC_E_FILENOTCONTROLLED|檔案不在原始檔控制之下。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或競爭問題。|
|SCC_E_NOTAUTHORIZED|使用者未獲授權，無法完成此操作。|
|SCC_E_COULDNOTCREATEPROJECT|無法在重新命名過程中建立專案。|
|SCC_E_OPNOTPERFORMED|未執行操作。|
|SCC_E_NONSPECIFICERROR|發生未指定或一般的錯誤。|

## <a name="remarks"></a>備註
 此函式可以用來重新命名檔案，或在原始檔控制系統中將檔案移到另一個位置。 原始檔控制外掛程式不應嘗試存取磁片上的檔案。 IDE 會負責重新命名本機檔案。

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)