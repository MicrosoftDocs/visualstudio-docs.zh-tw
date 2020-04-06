---
title: Scc屬性功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf2dd87efbb50346093144db6e069eea30138e37
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700499"
---
# <a name="sccproperties-function"></a>SccProperties 函式
此函數顯示檔或專案的原始程式碼管理屬性。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccProperties (
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName
);
```

#### <a name="parameters"></a>參數
 pvContext

[在]原始程式碼管理外掛程式上下文結構。

 hWnd

[在]源控件外掛程式可以用作它提供的任何對話框的父級的IDE視窗句柄。

 lpFile 名稱

[在]檔或專案的完全限定路徑名稱。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功顯示屬性。|
|SCC_I_RELOADFILE|版本控制系統已修改文件屬性,因此IDE應重新載入此檔。|
|SCC_E_PROJNOTOPEN|未在原始碼管理中打開指定的專案。|
|SCC_E_NOTAUTHORIZED|使用者無權查看此檔或項目的屬性。|
|SCC_E_FILENOTCONTROLLED|指定的檔或專案不受原始程式碼管理。|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|發生未知或常規錯誤。|

## <a name="remarks"></a>備註
 原始程式碼管理外掛程式在其自己的對話框中顯示屬性。

 屬性由原始程式碼管理外掛程式定義,可能因外掛程式而異。 如果外掛程式允許使用者更改檔的原始程式碼管理屬性,則`SCC_I_RELOAD`應返回 以向 IDE 發出訊號,指出需要重新載入此檔或專案。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
