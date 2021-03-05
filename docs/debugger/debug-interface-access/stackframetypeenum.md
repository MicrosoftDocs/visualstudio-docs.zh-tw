---
description: 指定堆疊框架類型。
title: StackFrameTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b84ad19ec31cd1fae65913827b8ee381711f6534
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155303"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
指定堆疊框架類型。

## <a name="syntax"></a>Syntax

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

## <a name="elements"></a>元素
`FrameTypeFPO` 已省略框架指標;可用的 FPO 資訊。

`FrameTypeTrap` 核心陷阱框架。

`FrameTypeTSS` 核心陷阱框架。

`FrameTypeStandard` 標準 EBP 堆疊框架。

`FrameTypeFrameData` 已省略框架指標;可用的畫面格資料資訊。

`FrameTypeUnknown` 沒有任何偵錯工具資訊的框架。

## <a name="remarks"></a>備註
呼叫 [IDiaStackFrame：： get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) 方法時，會傳回此列舉中的值。

## <a name="requirements"></a>規格需求
標頭： cvconst。h

## <a name="see-also"></a>另請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
