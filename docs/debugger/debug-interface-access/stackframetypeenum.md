---
title: StackFrameTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20b0c9dd106e5744a369ddaa6cb870788f7464d3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738558"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
指定堆疊框架類型。

## <a name="syntax"></a>語法

```C++
enum StackFrameTypeEnum {
    FrameTypeFPO,
    FrameTypeTrap,
    FrameTypeTSS,
    FrameTypeStandard,
    FrameTypeFrameData,
    FrameTypeUnknown = -1
};
```

## <a name="elements"></a>項目
省略 `FrameTypeFPO` 框架指標;可用的 FPO 資訊。

`FrameTypeTrap` 核心陷阱框架。

`FrameTypeTSS` 核心陷阱框架。

`FrameTypeStandard` 標準 EBP 堆疊框架。

省略 `FrameTypeFrameData` 框架指標;可用的畫面格資料資訊。

沒有任何偵錯工具資訊的 `FrameTypeUnknown` 框架。

## <a name="remarks"></a>備註
這個列舉中的值是由呼叫[IDiaStackFrame：： get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)方法所傳回。

## <a name="requirements"></a>需求
標頭： cvconst。h

## <a name="see-also"></a>請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
