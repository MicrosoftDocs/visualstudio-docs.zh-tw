---
description: 此函數會顯示檔案或專案的原始檔控制屬性。
title: SccProperties 函式 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 410febfbbb79cb352b6247139a11b1c49f3cde9c
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220530"
---
# <a name="sccproperties-function"></a>SccProperties 函式
此函數會顯示檔案或專案的原始檔控制屬性。

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

在原始檔控制外掛程式內容結構。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它做為它所提供之任何對話方塊的父代。

 lpFileName

在檔案或專案的完整路徑名稱。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功顯示內容。|
|SCC_I_RELOADFILE|版本控制系統已修改檔案屬性，因此 IDE 應重載此檔案。|
|SCC_E_PROJNOTOPEN|未在原始檔控制中開啟指定的專案。|
|SCC_E_NOTAUTHORIZED|使用者無權查看此檔案或專案的屬性。|
|SCC_E_FILENOTCONTROLLED|指定的檔案或專案不在原始檔控制之下。|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|發生不明或一般錯誤。|

## <a name="remarks"></a>備註
 原始檔控制外掛程式會在它自己的對話方塊中顯示內容。

 這些屬性是由原始檔控制外掛程式所定義，而且可能與外掛程式不同。 如果外掛程式允許使用者變更檔案的原始檔控制屬性，它應該會傳回， `SCC_I_RELOAD` 表示 IDE 必須重載這個檔案或專案。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
