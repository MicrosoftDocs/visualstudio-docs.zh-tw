---
title: QUERYCHANGESFUNC |Microsoft Docs
description: QUERYCHANGESFUNC 回呼函式是用來列舉檔案名的集合，並決定每個檔案的狀態。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8abe32abcb79fada541124f50a750fb4c1edde58
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910868"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
這是 [SccQueryChanges](../extensibility/sccquerychanges-function.md) 作業用來列舉檔案名集合，並決定每個檔案狀態的回呼函數。

 函式 `SccQueryChanges` 會提供檔案清單和回呼的指標 `QUERYCHANGESFUNC` 。 原始檔控制外掛程式會列舉指定的清單，並透過此回呼) 為清單中的每個檔案提供狀態 (。

## <a name="signature"></a>簽名

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>參數
 pvCallerData

在 `pvCallerData` 呼叫端傳遞的參數 (IDE) [SccQueryChanges](../extensibility/sccquerychanges-function.md)。 原始檔控制外掛程式不應該對此值的內容進行任何假設。

 pChangesData

在 [QUERYCHANGESDATA 結構](#LinkQUERYCHANGESDATA) 結構的指標，描述檔案的變更。

## <a name="return-value"></a>傳回值
 IDE 會傳回適當的錯誤碼：

|值|描述|
|-----------|-----------------|
|SCC_OK|繼續處理。|
|SCC_I_OPERATIONCANCELED|停止處理。|
|SCC_E_xxx|任何適當的 SCC 錯誤都應該停止處理。|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a> QUERYCHANGESDATA 結構
 傳入的每個檔案結構如下所示：

```cpp
struct QUERYCHANGESDATA_A
{
    DWORD  dwSize;
    LPCSTR lpFileName;
    DWORD  dwChangeType;
    LPCSTR lpLatestName;
};

typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;

struct QUERYCHANGESDATA_W
{
    DWORD   dwSize;
    LPCWSTR lpFileName;
    DWORD   dwChangeType;
    LPCWSTR lpLatestName;
};
```

 此結構的 dwSize 大小 (以位元組為單位) 。

 lpFileName 此專案的原始檔案名稱。

 指出檔案狀態的 dwChangeType 程式碼：

|程式碼|描述|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|無法分辨有哪些變更。|
|`SCC_CHANGE_UNCHANGED`|此檔案沒有任何名稱變更。|
|`SCC_CHANGE_DIFFERENT`|具有不同身分識別的檔案，但資料庫中有相同的名稱。|
|`SCC_CHANGE_NONEXISTENT`|檔案不存在於資料庫或本機中。|
|`SCC_CHANGE_DATABASE_DELETED`|在資料庫中刪除的檔案。|
|`SCC_CHANGE_LOCAL_DELETED`|檔案已在本機刪除，但是檔案仍存在於資料庫中。 如果無法判斷，則傳回 `SCC_CHANGE_DATABASE_ADDED` 。|
|`SCC_CHANGE_DATABASE_ADDED`|檔案已加入至資料庫，但不存在於本機。|
|`SCC_CHANGE_LOCAL_ADDED`|檔案不存在於資料庫中，而且是新的本機檔案。|
|`SCC_CHANGE_RENAMED_TO`|檔案在資料庫中重新命名或移動為 `lpLatestName` 。|
|`SCC_CHANGE_RENAMED_FROM`|檔案已在資料庫中重新命名或移動 `lpLatestName` ; 如果這太昂貴而無法追蹤，則傳回不同的旗標，例如 `SCC_CHANGE_DATABASE_ADDED` 。|

 lpLatestName 這個專案的目前檔案名。

## <a name="see-also"></a>另請參閱
- [IDE 所執行的回呼函數](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [錯誤碼](../extensibility/error-codes.md)
