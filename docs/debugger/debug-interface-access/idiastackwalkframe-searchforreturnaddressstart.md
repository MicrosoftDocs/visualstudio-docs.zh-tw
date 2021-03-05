---
description: 在指定的堆疊框架中搜尋指定位址或附近的傳回位址。
title: IDiaStackWalkFrame：： searchForReturnAddressStart |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::searchForReturnAddressStart method
ms.assetid: 47660b9b-6e4f-4dfa-88ab-63dce28f7412
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 49beac1d7f7c998b5ad3a73222903830a934bc9c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158905"
---
# <a name="idiastackwalkframesearchforreturnaddressstart"></a>IDiaStackWalkFrame::searchForReturnAddressStart
在指定的堆疊框架中搜尋指定位址或附近的傳回位址。

## <a name="syntax"></a>語法

```C++
HRESULT searchForReturnAddressStart ( 
   IDiaFrameData* frame,
   ULONGLONG      startAddress,
   ULONGLONG*     returnAddress
);
```

#### <a name="parameters"></a>參數
 `frame`

在 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) 物件，表示目前的堆疊框架。

 `startAddress`

在要開始搜尋的虛擬記憶體位址。

 `returnAddress`

擴展傳回最接近的函數傳回位址 `startAddress` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
