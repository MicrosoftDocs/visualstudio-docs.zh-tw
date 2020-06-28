---
title: IDiaFrameData::get_functionParent | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: ef646016433ecfe19106a17dff391c2dd8ce8382
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467383"
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
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)