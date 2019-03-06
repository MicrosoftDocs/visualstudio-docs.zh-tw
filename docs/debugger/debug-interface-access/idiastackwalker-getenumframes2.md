---
title: IDiaStackWalker::getEnumFrames2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames2 method
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35886ea0456426c30c44d5fd8e90399d4a2143ef
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56642751"
---
# <a name="idiastackwalkergetenumframes2"></a>IDiaStackWalker::getEnumFrames2
擷取特定平台類型的堆疊框架的列舉值。

## <a name="syntax"></a>語法

```C++

      HRESULT getEnumFrames2( 
   enum  CV_CPU_TYPE_e    cpuid,
   IDiaStackWalkHelper*   pHelper,
   IDiaEnumStackFrames**  ppEnum
);
```

#### <a name="parameters"></a>參數
 `cpuid`

[in]值，以從[CV_CPU_TYPE_e 列舉](../../debugger/debug-interface-access/cv-cpu-type-e.md)指定平台類型的列舉。

 `pHelper`

[in]協助專家[IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)物件。

 `ppEnum`

[out]傳回[IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)物件，其中包含一份[IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 若要取得堆疊框架清單只是 x86 平台，請呼叫[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)方法。

## <a name="see-also"></a>請參閱
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [CV_CPU_TYPE_e 列舉](../../debugger/debug-interface-access/cv-cpu-type-e.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)