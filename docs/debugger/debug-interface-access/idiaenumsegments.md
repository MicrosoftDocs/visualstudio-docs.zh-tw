---
title: IDiaEnumSegments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 255c55dff0dab0c7b36f5029de9e688db949a1fe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833424"
---
# <a name="idiaenumsegments"></a>IDiaEnumSegments
列舉各種資料來源中包含的區段。

## <a name="syntax"></a>語法

```
IDiaEnumSegments : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示的方法`IDiaEnumSegments`。

|方法|描述|
|------------|-----------------|
|[IDiaEnumSegments::get__NewEnum](../../debugger/debug-interface-access/idiaenumsegments-get-newenum.md)|擷取[IEnumVARIANT 介面](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant)這個列舉值的版本。|
|[IDiaEnumSegments::get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)|擷取區段的數目。|
|[IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)|透過索引中擷取的區段。|
|[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)|擷取指定的數目的列舉型別序列中的區段。|
|[IDiaEnumSegments::Skip](../../debugger/debug-interface-access/idiaenumsegments-skip.md)|略過指定的數目的列舉型別序列中的區段。|
|[IDiaEnumSegments::Reset](../../debugger/debug-interface-access/idiaenumsegments-reset.md)|將列舉型別序列重設到開頭。|
|[IDiaEnumSegments::Clone](../../debugger/debug-interface-access/idiaenumsegments-clone.md)|建立列舉值，包含目前的列舉值相同的列舉型別狀態。|

## <a name="remarks"></a>備註

## <a name="notes-for-callers"></a>呼叫端資訊
取得這個介面，藉由呼叫`QueryInterface`方法[IDiaTable](../../debugger/debug-interface-access/idiatable.md)物件。 請參閱詳細資料的範例。

## <a name="example"></a>範例
此範例示範如何取得`IDiaEnumSections`資料表中的介面。 使用區段的更完整範例，請參閱 < [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)介面。

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
標頭：dia2.h

程式庫： diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>另請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
