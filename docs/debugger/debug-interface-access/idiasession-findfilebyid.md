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
ms.openlocfilehash: aafdd2270606ba6e56713e9166dbae2b8c635b41
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742267"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
依來源檔案識別碼抓取原始程式檔。

## <a name="syntax"></a>語法

```C++
HRESULT findFileById ( 
   DWORD            uniqueId,
   IDiaSourceFile** ppResult
);
```

#### <a name="parameters"></a>參數
 `uniqueId`

在指定來源檔案識別碼。

 `ppResult`

脫銷傳回[IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)物件，代表所抓取的來源檔案。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 來源檔案識別碼是在內部用來進行 DIA SDK 的唯一值，讓所有的來源檔案都是唯一的。 這個方法通常會在內部使用於 DIA SDK。

## <a name="see-also"></a>請參閱
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)