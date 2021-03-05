---
description: 此函式會指定要檢查的目錄清單，以判斷哪些目錄和 (選擇性地) 檔案儲存在原始檔控制中。
title: SccPopulateDirList 函式 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 991803511e48e72012c868eaa4b0afbd889b2380
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221505"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList 函式
此函式會指定要檢查的目錄清單，以判斷哪些目錄和 (選擇性地) 檔案儲存在原始檔控制中。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccPopulateDirList(
   LPVOID        pContext,
   LONG          nDirs,
   LPCSTR*       lpDirPaths,
   POPDIRLISTFUNCpfnPopulate,
   LPVOID        pvCallerData,
   LONG          fOptions
);
```

#### <a name="parameters"></a>參數
 pContext

在原始檔控制外掛程式內容指標。

 nDirs

在陣列中的目錄路徑數目 `lpDirPaths` 。

 lpDirPaths

在要檢查的目錄路徑陣列。

 pfnPopulate

在要針對每個目錄路徑呼叫的回呼函式，並 (選擇性地) `lpDirPaths` (如需詳細資料) ，請參閱 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) 。

 pvCallerData

在要原封不動地傳遞給回呼函式的值。

 fOptions

在控制目錄處理方式的值組合 (請參閱 [特定命令所使用之位旗標](../extensibility/bitflags-used-by-specific-commands.md) 的「PopulateDirList 旗標」一節，以取得可能值) 。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式實作為預期會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功完成操作。|
|SCC_E_UNKNOWNERROR|發生錯誤。|

## <a name="remarks"></a>備註
 只有那些目錄和 (可選擇性地) 實際在原始檔控制存放庫中的檔案名會傳遞至回呼函數。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [錯誤碼](../extensibility/error-codes.md)
