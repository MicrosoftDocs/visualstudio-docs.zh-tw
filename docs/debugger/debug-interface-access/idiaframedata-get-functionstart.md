---
title: IDiaFrameData::get_functionStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionStart method
ms.assetid: 49fd24fb-65c2-4812-8303-56a968353e1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 324cad63a597768dc2c13447c6d2d68756878695
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743604"
---
# <a name="idiaframedataget_functionstart"></a>IDiaFrameData::get_functionStart
抓取旗標，指出區塊是否包含函數的進入點。

## <a name="syntax"></a>語法

```C++
HRESULT get_functionStart ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷如果區塊包含進入點，則傳回 `TRUE`;否則會傳回 `FALSE`。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 如果不支援此屬性，則傳回 `S_FALSE`。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 堆疊框架可以不是函式的開頭，因為框架代表插入函式中的內嵌方法或函數。

## <a name="see-also"></a>請參閱
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)