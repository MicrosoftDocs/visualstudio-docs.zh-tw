---
title: SccPopulateDirList 函式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f13c674e6374e826dc45343e5cd1f7edcc1f8100
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720901"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList 函式
此函式會判斷哪些目錄和（選擇性）檔案會儲存在原始檔控制中，並指定要檢查的目錄清單。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccPopulateDirList(
   LPVOID        pContext,
   LONG          nDirs,
   LPCSTR*       lpDirPaths,
   POPDIRLISTFUNCpfnPopulate,
   LPVOID        pvCallerData,
   LONG          fOptions
);
```

#### <a name="parameters"></a>參數
 pCoNtext

在原始檔控制外掛程式內容指標。

 nDirs

在@No__t_0 陣列中的目錄路徑數目。

 lpDirPaths

在要檢查的目錄路徑陣列。

 pfnPopulate

在要在 `lpDirPaths` 中針對每個目錄路徑和（選擇性） filename 呼叫的回呼函式（如需詳細資訊，請參閱[POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) ）。

 pvCallerData

在要原封不動地傳遞至回呼函式的值。

 fOptions

在值的組合，可控制目錄的處理方式（請參閱位旗標的「PopulateDirList 旗標」一節，以取得可能值的[特定命令所使用](../extensibility/bitflags-used-by-specific-commands.md)的）。

## <a name="return-value"></a>傳回值
 此函式的原始檔控制外掛程式執行應會傳回下列其中一個值：

|值|描述|
|-----------|-----------------|
|SCC_OK|已成功完成作業。|
|SCC_E_UNKNOWNERROR|發生錯誤。|

## <a name="remarks"></a>備註
 只有在原始檔控制存放庫中實際的目錄和（選擇性）檔案名會傳遞至回呼函式。

## <a name="see-also"></a>請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [錯誤碼](../extensibility/error-codes.md)