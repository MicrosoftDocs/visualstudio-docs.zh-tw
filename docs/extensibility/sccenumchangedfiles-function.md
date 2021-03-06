---
description: 指定本機檔案清單之後，此函式會判斷哪些檔案與原始程式碼控制資料庫中的對應版本不同。
title: SccEnumChangedFiles 函式 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9349172ac60f1e02f82327424cdbc3a3b1d4f865
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221531"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles 函式
指定本機檔案清單之後，此函式會判斷哪些檔案與原始程式碼控制資料庫中的對應版本不同。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccEnumChangedFiles(
   LPVOID  pContext,
   HWND    hWnd,
   LONG    cFiles,
   LPCSTR* lpFileNames,
   LONG*   plIsFileDifferent
);
```

### <a name="parameters"></a>參數
 pContext

在原始檔控制外掛程式內容指標。

 hWnd

在IDE 視窗的控制碼，原始檔控制外掛程式可以使用它做為它所提供之任何對話方塊的父代。

 cFiles

在陣列中指定的檔案名 `lpFileNames` 。 也指定陣列的大小 `plIsFileDifferent` 。

 lpFileNames

在要檢查的本機檔案名陣列。

 plIsFileDifferent

[in，out]值的陣列，表示每個檔案 (陣列的差異狀態，至少必須有 `cFiles`) 的專案。 非零表示檔案不同。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|作業順利完成。|
|SCC_UNSPECIFIEDERROR|一般錯誤。|

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
