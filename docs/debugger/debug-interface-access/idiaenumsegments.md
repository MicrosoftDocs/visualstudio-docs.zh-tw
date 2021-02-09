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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 92463a892ec9d02fd7c31061aafa81918cfabe3a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856310"
---
# <a name="idiaenumsegments"></a>IDiaEnumSegments
列舉資料來源中包含的各種區段。

## <a name="syntax"></a>Syntax

```
IDiaEnumSegments : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示的方法 `IDiaEnumSegments` 。

|方法|描述|
|------------|-----------------|
|[IDiaEnumSegments::get__NewEnum](../../debugger/debug-interface-access/idiaenumsegments-get-newenum.md)|抓取此列舉值的 [IEnumVARIANT 介面](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) 版本。|
|[IDiaEnumSegments::get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)|捕獲區段的數目。|
|[IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)|藉由索引來抓取區段。|
|[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)|捕獲列舉序列中指定的區段數目。|
|[IDiaEnumSegments::Skip](../../debugger/debug-interface-access/idiaenumsegments-skip.md)|略過列舉序列中指定的區段數目。|
|[IDiaEnumSegments::Reset](../../debugger/debug-interface-access/idiaenumsegments-reset.md)|將列舉順序重設為開頭。|
|[IDiaEnumSegments::Clone](../../debugger/debug-interface-access/idiaenumsegments-clone.md)|建立包含與目前列舉值相同列舉狀態的列舉值。|

## <a name="remarks"></a>備註

## <a name="notes-for-callers"></a>呼叫者注意事項
`QueryInterface`在[IDiaTable](../../debugger/debug-interface-access/idiatable.md)物件上呼叫方法，以取得這個介面。 如需詳細資訊，請參閱範例。

## <a name="example"></a>範例
這個範例會示範如何 `IDiaEnumSections` 從資料表取得介面。 如需使用區段的更完整範例，請參閱 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) 介面。

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

## <a name="requirements"></a>規格需求
標頭： Dia2。h

程式庫： diaguids .lib

DLL： msdia80.dll

## <a name="see-also"></a>另請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
