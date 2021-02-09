---
title: IDiaFrameData::get_functionStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionStart method
ms.assetid: 49fd24fb-65c2-4812-8303-56a968353e1b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bae370c5a279edf86bd3fabd9ba710436ae63ed7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855925"
---
# <a name="idiaframedataget_functionstart"></a>IDiaFrameData::get_functionStart
抓取指出區塊是否包含函式進入點的旗標。

## <a name="syntax"></a>語法

```C++
HRESULT get_functionStart ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展 `TRUE` 如果區塊包含進入點，則傳回，否則傳回 `FALSE` 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援這個屬性，則傳回。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 堆疊框架可能不會成為函式的開頭，因為框架代表插入函式的內嵌方法或函式。

## <a name="see-also"></a>另請參閱
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)