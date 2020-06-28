---
title: IDiaSession::getEnumTables | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getEnumTables method
ms.assetid: 66e0fba2-ca63-4e24-a46a-c99c7fb61dd1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b9b229de3818b00379d95a5c19e35c7e83c845e
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465423"
---
# <a name="idiasessiongetenumtables"></a>IDiaSession::getEnumTables
抓取符號存放區中包含的所有資料表的列舉值。

## <a name="syntax"></a>語法

```C++
HRESULT getEnumTables (
    IDiaEnumTables** ppEnumTables
);
```

#### <a name="parameters"></a>參數
`ppEnumTables`

脫銷傳回[IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)物件。 使用此介面來列舉符號存放區中的資料表。

## <a name="return-value"></a>傳回值
如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="example"></a>範例
這個範例會呈現一般函式，該函式會使用 `getEnumTables` 方法來取得特定的列舉值物件。 如果找到列舉值，函數會傳回可轉換成所需介面的指標。否則，函數會傳回 `NULL` 。

```C++
IUnknown *GetTable(IDiaSession *pSession, REFIID iid)
{
    IUnknown *pUnknown = NULL;
    if (pSession != NULL)
    {
        CComPtr<IDiaEnumTables> pEnumTables;
        if (pSession->getEnumTables(&pEnumTables) == S_OK)
        {
            CComPtr<IDiaTable> pTable;
            DWORD celt = 0;
            while(pEnumTables->Next(1,&pTable,&celt) == S_OK &&
                  celt == 1)
            {
                if (pTable->QueryInterface(iid, (void **)pUnknown) == S_OK)
                {
                    break;
                }
                pTable = NULL;
            }
        }
    }
    return(pUnknown);
}
```

## <a name="see-also"></a>另請參閱
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
