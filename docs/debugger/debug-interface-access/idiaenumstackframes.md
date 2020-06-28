---
title: IDiaEnumStackFrames | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames interface
ms.assetid: 3d1e8403-c9fc-42ff-ae35-0ab9a5ed2ad7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9322af6bf04e21430ed49be8e631f3a7dc63643
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467824"
---
# <a name="idiaenumstackframes"></a>IDiaEnumStackFrames
列舉可用的各種堆疊框架。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法

|方法|描述|
|------------|-----------------|
|[IDiaEnumStackFrames::Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md)|從列舉序列中抓取指定的堆疊框架元素數目。|
|[IDiaEnumStackFrames::Reset](../../debugger/debug-interface-access/idiaenumstackframes-reset.md)|將列舉序列重設為開頭。|

## <a name="remarks"></a>備註

## <a name="notes-for-callers"></a>呼叫者的注意事項
藉由呼叫[IDiaStackWalker：： getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)或[IDiaStackWalker：： getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)方法來取得此介面。

## <a name="example"></a>範例
這個範例會示範如何取得和使用 `IDiaEnumStackFrames` 介面。 如需函數的執行，請參閱[IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)介面 `PrintStackFrame` 。

```C++
void DumpStackFrames(IDiaStackWalker*     pStackWalker,
                     IDiaStackWalkHelper* pStackWalkHelper,
                     CV_CPU_TYPE_e        cpuType)
{
    if (pStackWalker != NULL && pStackWalkHelper != NULL)
    {
        CComPtr<IDiaEnumStackFrames> pEnumsFrames;
        HRESULT hr;
        hr = pStackWalker->getEnumFrames2(cpuType, pStackWalkHelper, &pEnumFrames);
        if (SUCCEEDED(hr) && pEnumFrames != NULL)
        {
            CComPtr<IDiaStackFrame> pStackFrame;
            DWORD celt = 0;

            while (pEnumFrames->Next(1, &pStackFrame, &celt) == S_OK)
            {
                PrintStackFrame(pStackFrame);
            }
            pStackFrame = NULL;
        }
    }
}
```

## <a name="requirements"></a>需求
標頭： Dia2。h

程式庫： diaguids

DLL： msdia80.dll

## <a name="see-also"></a>另請參閱
- [介面 (偵錯介面存取 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
