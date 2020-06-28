---
title: IDiaEnumSegments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments interface
ms.assetid: 0c9edd5e-b9ce-43e1-a791-cd4c5d16d923
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd6a0716d0bae5a223cff3439834c87b9650e7a5
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467943"
---
# <a name="idiaenumsegments"></a>IDiaEnumSegments
列舉資料來源中包含的各種區段。

## <a name="syntax"></a>語法

```
IDiaEnumSegments : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示的方法 `IDiaEnumSegments` 。

|方法|描述|
|------------|-----------------|
|[IDiaEnumSegments::get__NewEnum](../../debugger/debug-interface-access/idiaenumsegments-get-newenum.md)|抓取此列舉值的[IEnumVARIANT 介面](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant)版本。|
|[IDiaEnumSegments::get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)|抓取區段的數目。|
|[IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)|透過索引來抓取區段。|
|[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)|抓取列舉序列中指定數目的區段。|
|[IDiaEnumSegments::Skip](../../debugger/debug-interface-access/idiaenumsegments-skip.md)|略過列舉序列中指定數目的區段。|
|[IDiaEnumSegments::Reset](../../debugger/debug-interface-access/idiaenumsegments-reset.md)|將列舉序列重設為開頭。|
|[IDiaEnumSegments::Clone](../../debugger/debug-interface-access/idiaenumsegments-clone.md)|建立枚舉器，其中包含與目前列舉值相同的列舉狀態。|

## <a name="remarks"></a>備註

## <a name="notes-for-callers"></a>呼叫者的注意事項
`QueryInterface`在[IDiaTable](../../debugger/debug-interface-access/idiatable.md)物件上呼叫方法，以取得此介面。 如需詳細資訊，請參閱範例。

## <a name="example"></a>範例
這個範例顯示如何 `IDiaEnumSections` 從資料表取得介面。 如需更完整的區段使用範例，請參閱[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)介面。

```C++
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)
{
    CComPtr<IDiaEnumSegments> pSegments;
    if ( SUCCEEDED( pTable->QueryInterface(
                                __uuidof( IDiaEnumSegments ),
                                (void**)&pSegments )
                  )
       )
    {
        // Do something with this enumeration
    }
}
```

## <a name="requirements"></a>需求
標頭： Dia2。h

程式庫： diaguids

DLL： msdia80.dll

## <a name="see-also"></a>另請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
