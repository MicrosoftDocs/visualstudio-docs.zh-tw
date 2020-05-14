---
title: sccrename 函數 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88a917e43729b3049e488264c260f8455ab08fe4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700421"
---
# <a name="sccrename-function"></a>SccRename 函式
此函數重新命名原始碼管理系統中的檔案。

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
 pvContext

[在]原始程式碼管理外掛程式上下文結構。

 hWnd

[在]源控件外掛程式可以用作它提供的任何對話框的父級的IDE視窗句柄。

 lpFile 名稱

[在]要重新命名的檔案的完全限定檔名。

 lp 新名稱

[在]完全限定的新名稱。 如果目錄路徑不同,則檔已從一個子目錄移動到另一個子目錄。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|重新命名操作已成功完成。|
|SCC_E_PROJNOTOPEN|專案在原始程式碼管理下不開放。|
|SCC_E_FILENOTCONTROLLED|該檔不受原始程式碼管理。|
|SCC_E_ACCESSFAILURE|訪問原始程式碼管理系統時出現問題,可能是由於網路或爭用問題。|
|SCC_E_NOTAUTHORIZED|用戶無權完成此操作。|
|SCC_E_COULDNOTCREATEPROJECT|無法作為重命名過程的一部分創建專案。|
|SCC_E_OPNOTPERFORMED|未執行操作。|
|SCC_E_NONSPECIFICERROR|發生未指定或常規錯誤。|

## <a name="remarks"></a>備註
 此功能可用於重新命名檔案或將其從一個位置移到原始碼管理系統中的另一個位置。 原始程式碼管理外掛程式不應嘗試存取磁碟上的檔案。 IDE 負責重新命名本地檔案。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
