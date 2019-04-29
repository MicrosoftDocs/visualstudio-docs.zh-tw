---
title: IDiaSession::findFileById | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3454ff5ef087b67dda5d48849d4a6c4eceb7e52
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839351"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
依來源檔案識別碼擷取原始程式檔。

## <a name="syntax"></a>語法

```C++
HRESULT findFileById ( 
   DWORD            uniqueId,
   IDiaSourceFile** ppResult
);
```

#### <a name="parameters"></a>參數
 `uniqueId`

[in]指定來源檔案識別碼。

 `ppResult`

[out]傳回[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)擷取代表原始程式檔的物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 DIA sdk 在內部用來進行所有原始程式檔的唯一唯一值的來源檔案識別碼。 這個方法通常是在內部用來 DIA SDK 中。

## <a name="see-also"></a>另請參閱
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)