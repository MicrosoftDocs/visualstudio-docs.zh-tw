---
title: IDiaFrameData::get_functionParent | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionParent method
ms.assetid: f00b9ab1-d4da-4818-973a-58f8f0e66769
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 809de8589302ddc35a14e2ea0663248a163176e6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743628"
---
# <a name="idiaframedataget_functionparent"></a>IDiaFrameData::get_functionParent
抓取封閉式函數的框架資料介面。

## <a name="syntax"></a>語法

```C++
HRESULT get_functionParent ( 
   IDiaFrameData** pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回封閉式函數的[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)物件。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)