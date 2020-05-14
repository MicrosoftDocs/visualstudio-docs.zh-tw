---
title: 查詢更改 |微軟文件
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30864cae95672f4026084a94c5474d165b124cba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701638"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
這是[SccQueryChanges](../extensibility/sccquerychanges-function.md)操作用於枚舉檔名集合並確定每個檔狀態的回調函數。

 該`SccQueryChanges`函數被賦予檔清單和指向回調`QUERYCHANGESFUNC`的指標。 原始程式碼管理外掛程式的舉給定清單,並為此清單中的每個檔提供狀態(透過此回調)。

## <a name="signature"></a>簽章

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>參數
 pvCallerData

[在]呼叫`pvCallerData`者 (IDE) 傳遞給[SccQuery 更改](../extensibility/sccquerychanges-function.md)的參數。 原始程式碼管理外掛程式不應對此值的內容進行假設。

 p 變更資料

[在]指向描述對檔的更改的[QUERYCHANGESDATA 結構結構](#LinkQUERYCHANGESDATA)的指標。

## <a name="return-value"></a>傳回值
 IDE 傳回錯誤代碼:

|值|描述|
|-----------|-----------------|
|SCC_OK|繼續處理。|
|SCC_I_OPERATIONCANCELED|停止處理。|
|SCC_E_xxx|任何適當的 SCC 錯誤都應停止處理。|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a>查詢變更資料結構
 為每個檔傳入的結構如下所示:

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

 dwSize 此結構的大小(以位元組為單位)。

 lpFile名稱此專案的原始檔名。

 dwChangeType 代碼指示檔案的狀態:

|程式碼|描述|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|無法判斷發生了什麼變化。|
|`SCC_CHANGE_UNCHANGED`|此檔沒有名稱更改。|
|`SCC_CHANGE_DIFFERENT`|具有不同標識的檔,但資料庫中存在相同的名稱。|
|`SCC_CHANGE_NONEXISTENT`|檔案在資料庫中或本地都不存在。|
|`SCC_CHANGE_DATABASE_DELETED`|在資料庫中刪除的檔。|
|`SCC_CHANGE_LOCAL_DELETED`|檔案在本地刪除,但該檔仍然存在於資料庫中。 如果無法確定這一點,則`SCC_CHANGE_DATABASE_ADDED`傳回 。|
|`SCC_CHANGE_DATABASE_ADDED`|檔案添加到資料庫,但本地不存在。|
|`SCC_CHANGE_LOCAL_ADDED`|檔案在資料庫中不存在,是一個新的本地檔案。|
|`SCC_CHANGE_RENAMED_TO`|檔案重新命名或移至資料庫中為`lpLatestName`。|
|`SCC_CHANGE_RENAMED_FROM`|檔案重新命名或從`lpLatestName`中移至資料庫中。如果跟蹤費用太高,則返回其他標誌,如`SCC_CHANGE_DATABASE_ADDED`。|

 lpLatest名稱此專案的當前檔名。

## <a name="see-also"></a>另請參閱
- [IDE 實作的回檔](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [錯誤碼](../extensibility/error-codes.md)
