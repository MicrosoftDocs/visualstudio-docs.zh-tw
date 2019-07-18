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
ms.openlocfilehash: 44f715c4f74d9b120b324e2d68417a24c9b42684
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62854826"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
指定的堆疊框架的類型。

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
`FrameTypeFPO` 框架指標省略;FPO 資訊可用。

`FrameTypeTrap` 核心設陷框架。

`FrameTypeTSS` 核心設陷框架。

`FrameTypeStandard` 標準的 EBP 堆疊框架。

`FrameTypeFrameData` 框架指標省略;畫面格的資料可用的資訊。

`FrameTypeUnknown` 沒有任何偵錯資訊的框架。

## <a name="remarks"></a>備註
這個列舉型別中的值會傳回呼叫[idiastackframe:: Get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)方法。

## <a name="requirements"></a>需求
標頭： cvconst.h

## <a name="see-also"></a>另請參閱
- [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
