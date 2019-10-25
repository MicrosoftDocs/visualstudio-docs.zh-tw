---
title: IDiaEnumSectionContribs | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs interface
ms.assetid: 0d6c0632-310f-4a99-8921-58149a1817e3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e332bacdeaeca00d4e43d80807ee5f95c51c7e93
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744241"
---
# <a name="idiaenumsectioncontribs"></a>IDiaEnumSectionContribs
列舉資料來源中包含的各種區段貢獻。

## <a name="syntax"></a>語法

```
IDiaEnumSectionContribs : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示 `IDiaEnumSectionContribs`的方法。

|方法|描述|
|------------|-----------------|
|[IDiaEnumSectionContribs::get__NewEnum](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-newenum.md)|抓取此列舉值的[IEnumVARIANT 介面](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant)版本。|
|[IDiaEnumSectionContribs::get_Count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)|抓取區段貢獻的數目。|
|[IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)|透過索引來抓取區段投稿。|
|[IDiaEnumSectionContribs::Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md)|抓取列舉序列中指定數目的區段貢獻。|
|[IDiaEnumSectionContribs::Skip](../../debugger/debug-interface-access/idiaenumsectioncontribs-skip.md)|略過列舉序列中指定數目的區段貢獻。|
|[IDiaEnumSectionContribs::Reset](../../debugger/debug-interface-access/idiaenumsectioncontribs-reset.md)|將列舉序列重設為開頭。|
|[IDiaEnumSectionContribs::Clone](../../debugger/debug-interface-access/idiaenumsectioncontribs-clone.md)|建立枚舉器，其中包含與目前列舉值相同的列舉狀態。|

## <a name="remarks"></a>備註

## <a name="note-for-callers"></a>呼叫者的注意事項
從[IDiaSession：： getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)方法取得此介面。 如需詳細資訊，請參閱範例。

## <a name="example"></a>範例
這個範例會示範如何取得（`GetEnumSectionContribs` 函式），並使用（`ShowSectionContribs` 函式） `IDiaEnumSectionContribs` 介面。 如需使用區段投稿的更完整範例，請參閱[IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)介面。

```C++

IDiaEnumSectionContribs* GetEnumSectionContribs(IDiaSession *pSession)
{
    IDiaEnumSectionContribs* pUnknown    = NULL;
    REFIID                   iid         = __uuidof(IDiaEnumSectionContribs);
    IDiaEnumTables*          pEnumTables = NULL;
    IDiaTable*               pTable      = NULL;
    ULONG                    celt        = 0;

    if (pSession->getEnumTables(&pEnumTables) != S_OK)
    {
        wprintf(L"ERROR - GetTable() getEnumTables\n");
        return NULL;
    }
    while (pEnumTables->Next(1, &pTable, &celt) == S_OK && celt == 1)
    {
        // There is only one table that matches the given iid
        HRESULT hr = pTable->QueryInterface(iid, (void**)&pUnknown);
        pTable->Release();
        if (hr == S_OK)
        {
            break;
        }
    }
    pEnumTables->Release();
    return pUnknown;
}

void ShowSectionContribs(IDiaSession *pSession)
{
    IDiaEnumSectionContribs* pEnumSectionContribs;

    pEnumSectionContribs = GetEnumSectionContribs(pSession);
    if (pSectionContrib != NULL)
    {
        IDiaSectionContrib* pSectionContrib;
        ULONG celt = 0;

        while(pEnumSectionContribs->Next(1, &pSectionContrib, &celt) == S_OK &&
              celt == 1)
        {
            PrintSectionContrib(pSectionContrib, pSession);
            pSectionContrib->Release();
        }
        pSectionContrib->Release();
    }
}
```

## <a name="requirements"></a>需求
標頭： Dia2。h

程式庫： diaguids

DLL： msdia80

## <a name="see-also"></a>請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
