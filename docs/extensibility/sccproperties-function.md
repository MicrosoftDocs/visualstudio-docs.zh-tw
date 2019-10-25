---
title: SccProperties 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e269727441eebc93cd78b70f11fdb571f111ee8b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720840"
---
# <a name="sccproperties-function"></a>SccProperties 函式
此函式會顯示檔案或專案的原始檔控制屬性。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccProperties (
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName
);
```

#### <a name="parameters"></a>參數
 pvCoNtext

在原始檔控制外掛程式的內容結構。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它所提供之任何對話方塊的父系。

 lpFileName

在檔案或專案的完整路徑名稱。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式執行應會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功顯示內容。|
|SCC_I_RELOADFILE|版本控制系統已修改檔案屬性，因此 IDE 應該重載此檔案。|
|SCC_E_PROJNOTOPEN|未在原始檔控制中開啟指定的專案。|
|SCC_E_NOTAUTHORIZED|使用者未獲授權，無法查看此檔案或專案的屬性。|
|SCC_E_FILENOTCONTROLLED|指定的檔案或專案不在原始檔控制之下。|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|發生不明或一般錯誤。|

## <a name="remarks"></a>備註
 原始檔控制外掛程式會在其本身的對話方塊中顯示內容。

 這些屬性是由原始檔控制外掛程式所定義，而且可能會與外掛程式的外掛程式不同。 如果外掛程式允許使用者變更檔案的原始檔控制屬性，它應該會傳回 `SCC_I_RELOAD`，以通知 IDE 此檔案或專案必須重載。

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)