---
title: IDiaSession::findInjectedSource | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findInjectedSource method
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e2145c90c25c448880e51b9b394c7085e0d49b7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742263"
---
# <a name="idiasessionfindinjectedsource"></a>IDiaSession::findInjectedSource
抓取屬性提供者或編譯進程的其他元件已放入符號存放區中的來源清單。

## <a name="syntax"></a>語法

```C++
HRESULT findInjectedSource ( 
   LPCOLESTR                 srcFile,
   IDiaEnumInjectedSources** ppResult
);
```

#### <a name="parameters"></a>參數
 srcFile

在要搜尋之來源檔案的名稱。

 ppResult

脫銷傳回[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)物件，其中包含所有插入來源的清單。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="see-also"></a>請參閱
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)