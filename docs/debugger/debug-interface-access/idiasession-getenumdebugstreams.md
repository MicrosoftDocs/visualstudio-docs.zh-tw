---
title: IDiaSession::getEnumDebugStreams | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getEnumDebugStreams method
ms.assetid: d294954b-80e9-476c-b9f0-5ca6fd575f68
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62088c1ff7dd3dea8016a18d7c41425fdd584661
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465436"
---
# <a name="idiasessiongetenumdebugstreams"></a>IDiaSession::getEnumDebugStreams
抓取 debug 資料流程的列舉序列。

## <a name="syntax"></a>語法

```C++
HRESULT getEnumDebugStreams ( 
   IDiaEnumDebugStreams** ppEnumDebugStreams
)
```

#### <a name="parameters"></a>參數
 `ppEnumDebugStreams`

脫銷傳回[IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)物件，其中包含 debug 資料流程的清單。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)