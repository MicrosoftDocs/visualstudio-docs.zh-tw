---
title: SccQuery 更改功能 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec335d808c287decb75bf759d5a3795d98962579
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700489"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges 函式
此函數枚舉給定的檔案清單,提供有關通過回調函數更改每個檔的名稱的資訊。

## <a name="syntax"></a>語法

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>參數
 pContext

[在]源代碼管理外掛程式上下文指標。

 n 檔案

[在]陣列中`lpFileNames`的檔案數。

 lpFile 名稱

[在]要獲取有關資訊的檔名陣列。

 pfnCallback

[在]回檔函數用於調用清單中的每個檔名(有關詳細資訊,請參閱[查詢更改FUNC)。](../extensibility/querychangesfunc.md)

 pvCallerData

[在]將傳遞給回調函數的值保持不變。

## <a name="return-value"></a>傳回值
 此函數的源碼管理外掛程式實現應返回以下值之一:

|值|描述|
|-----------|-----------------|
|SCC_OK|查詢過程已成功完成。|
|SCC_E_PROJNOTOPEN|專案尚未在原始程式碼管理中打開。|
|SCC_E_ACCESSFAILURE|訪問原始程式碼管理系統時出現問題,可能是由於網路或爭用問題。|
|SCC_E_NONSPECIFICERROR|發生未指定或常規錯誤。|

## <a name="remarks"></a>備註
 查詢的更改是命名空間:特別是重新命名、添加和刪除檔。

## <a name="see-also"></a>另請參閱
- [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [錯誤代碼](../extensibility/error-codes.md)
