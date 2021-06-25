---
description: 此函數會重新命名原始檔控制系統中的檔案。
title: SccRename 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fb3fa392cd4ed31d907fe5913f8d7965a20df05b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900456"
---
# <a name="sccrename-function"></a>SccRename 函式
此函數會重新命名原始檔控制系統中的檔案。

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

在原始檔控制外掛程式內容結構。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它做為它所提供之任何對話方塊的父代。

 lpFileName

在要重新命名之檔案的完整檔案名。

 lpNewName

在完整的新名稱。 如果目錄路徑不同，則檔案已從一個子目錄移至另一個子目錄。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|重新命名作業已順利完成。|
|SCC_E_PROJNOTOPEN|專案未在原始檔控制中開啟。|
|SCC_E_FILENOTCONTROLLED|檔案不在原始檔控制之下。|
|SCC_E_ACCESSFAILURE|存取原始檔控制系統時發生問題，可能是因為網路或爭用問題。|
|SCC_E_NOTAUTHORIZED|使用者未獲授權，無法完成此操作。|
|SCC_E_COULDNOTCREATEPROJECT|無法在重新命名進程中建立專案。|
|SCC_E_OPNOTPERFORMED|未執行操作。|
|SCC_E_NONSPECIFICERROR|發生未指定或一般的錯誤。|

## <a name="remarks"></a>備註
 您可以使用此函式來重新命名檔案，或將檔案從一個位置移至原始檔控制系統中的另一個位置。 原始檔控制外掛程式不應該嘗試存取磁片上的檔案。 IDE 會負責重新命名本機檔案。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
