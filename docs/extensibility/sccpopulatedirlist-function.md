---
title: 放大縮小字型功能 放大縮小字型功能微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ac1c51ac694acadd2efb0cd7d1c5a3f1d66ebc1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700560"
---
# <a name="sccpopulatedirlist-function"></a>SccPopulateDirList 函式
此函數確定哪些目錄和(可選)檔案存儲在原始程式碼管理中,給定要檢查的目錄清單。

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
 pContext

[在]源代碼管理外掛程式上下文指標。

 nDirs

[在]`lpDirPaths`陣列中的目錄路徑數。

 lpDirPath

[在]要檢查的目錄路徑陣列。

 pfn 填充

[在]回檔函數用於調用`lpDirPaths`中 每個目錄路徑和(可選)檔名(有關詳細資訊,請參閱[POPDIRLISTFUNC)。](../extensibility/popdirlistfunc.md)

 pvCallerData

[在]要傳遞給回調函數的值保持不變。

 fOptions

[在]控制目錄處理方式的值的組合(請參閱[特定命令為可能的值使用的位標誌的"](../extensibility/bitflags-used-by-specific-commands.md)填充 DirList 標誌"部分)。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|成功完成操作。|
|SCC_E_UNKNOWNERROR|發生錯誤。|

## <a name="remarks"></a>備註
 只有實際上位於原始程式碼管理儲存庫中的目錄和(可選)檔名才會傳遞到回調函數。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [特定命令所使用的位元旗標](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [錯誤代碼](../extensibility/error-codes.md)
