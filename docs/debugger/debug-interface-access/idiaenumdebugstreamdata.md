---
description: 提供對 debug 資料流程中記錄的存取。
title: IDiaEnumDebugStreamData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData interface
ms.assetid: e2023c32-4c05-4d0c-a0be-f016a230c788
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f94fbc365ddd913494bb0fb04f81615c0945955b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149120"
---
# <a name="idiaenumdebugstreamdata"></a>IDiaEnumDebugStreamData
提供對 debug 資料流程中記錄的存取。

## <a name="syntax"></a>Syntax

```
IDiaEnumDebugStreamData : IUnknown
```

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示的方法 `IDiaEnumDebugStreamData` 。

|方法|描述|
|------------|-----------------|
|[IDiaEnumDebugStreamData::get__NewEnum](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-newenum.md)|抓取此列舉值的 [IEnumVARIANT 介面](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) 版本。|
|[IDiaEnumDebugStreamData::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)|抓取偵錯工具資料流程中的記錄數目。|
|[IDiaEnumDebugStreamData::get_name](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-name.md)|抓取 debug 資料流程的名稱。|
|[IDiaEnumDebugStreamData::Item](../../debugger/debug-interface-access/idiaenumdebugstreamdata-item.md)|抓取指定的記錄。|
|[IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)|從列舉序列抓取指定的記錄數目。|
|[IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)|略過列舉序列中指定數目的記錄。|
|[IDiaEnumDebugStreamData::Reset](../../debugger/debug-interface-access/idiaenumdebugstreamdata-reset.md)|將列舉序列重設為開頭。|
|[IDiaEnumDebugStreamData::Clone](../../debugger/debug-interface-access/idiaenumdebugstreamdata-clone.md)|建立包含與目前列舉值相同列舉順序的列舉值。|

## <a name="remarks"></a>備註
此介面代表 debug 資料流程中的記錄資料流程。 每一筆記錄的大小和轉譯相依于記錄來源的資料流程。 這個介面可有效地存取符號檔中的原始資料位元組。

## <a name="notes-for-callers"></a>呼叫者注意事項
呼叫 [IDiaEnumDebugStreams：： Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md) 或 [IDiaEnumDebugStreams：： Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md) 方法以取得 `IDiaEnumDebugStreamData` 物件。

## <a name="example"></a>範例
 這個範例會示範如何存取單一資料流程及其記錄。

```C++
void PrintStreamData(IDiaEnumDebugStreamData* pStream)
{
    BSTR  wszName;
    LONG  dwElem;
    ULONG celt    = 0;
    DWORD cbData;
    DWORD cbTotal = 0;
    BYTE  data[1024];

    if(pStream->get_name(&wszName) != S_OK)
    {
        wprintf_s(L"ERROR - PrintStreamData() get_name\n");
    }
    else
    {
        wprintf_s(L"Stream: %s", wszName);
        SysFreeString(wszName);
    }
    if(pStream->get_Count(&dwElem) != S_OK)
    {
        wprintf(L"ERROR - PrintStreamData() get_Count\n");
    }
    else
    {
        wprintf(L"(%d)\n", dwElem);
    }
    while(pStream->Next(1, sizeof(data), &cbData, (BYTE *)&data, &celt) == S_OK)
    {
        DWORD i;
        for (i = 0; i < cbData; i++)
        {
            wprintf(L"%02X ", data[i]);
            if(i && i % 8 == 7 && i+1 < cbData)
            {
                wprintf(L"- ");
            }
        }
        wprintf(L"| ");
        for(i = 0; i < cbData; i++)
        {
            wprintf(L"%c", iswprint(data[i]) ? data[i] : '.');
        }
        wprintf(L"\n");
        cbTotal += cbData;
    }
    wprintf(L"Summary :\n\tSizeof(Elem) = %d\n\tNo of Elems = %d\n\n",
            cbTotal/dwElem, dwElem);
}
```

## <a name="requirements"></a>規格需求
標頭： Dia2。h

程式庫： diaguids .lib

DLL： msdia80.dll

## <a name="see-also"></a>另請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)
- [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)
