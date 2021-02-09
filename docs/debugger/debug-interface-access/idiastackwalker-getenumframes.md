---
title: IDiaStackWalker：： getEnumFrames |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames method
ms.assetid: f9f09729-4c34-441c-989c-e0b7339ee32c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 55d4a30b9f4b37274872141c6e9ac18a9aab9206
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863848"
---
# <a name="idiastackwalkergetenumframes"></a>IDiaStackWalker::getEnumFrames
捕獲 x86 平臺的堆疊框架列舉值。

## <a name="syntax"></a>語法

```C++
HRESULT getEnumFrames( 
   IDiaStackWalkHelper*   pHelper,
   IDiaEnumStackFrames**  ppEnum
);
```

#### <a name="parameters"></a>參數
 `pHelper`

在Helper [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) 物件。

 `ppEnum`

擴展傳回 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) 物件，其中包含 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) 物件的清單。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 若要取得任何其他平臺上的堆疊框架清單，請呼叫 [IDiaStackWalker：： getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) 方法。

## <a name="see-also"></a>另請參閱
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)