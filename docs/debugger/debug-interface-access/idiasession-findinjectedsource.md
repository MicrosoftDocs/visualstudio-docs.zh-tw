---
description: 抓取屬性提供者或編譯器的其他元件已放入符號存放區中的來源清單。
title: IDiaSession::findInjectedSource | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findInjectedSource method
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e1604bf91f70f2973dcd394f81569b5ee04e9a99
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147846"
---
# <a name="idiasessionfindinjectedsource"></a>IDiaSession::findInjectedSource
抓取屬性提供者或編譯器的其他元件已放入符號存放區中的來源清單。

## <a name="syntax"></a>語法

```C++
HRESULT findInjectedSource ( 
   LPCOLESTR                 srcFile,
   IDiaEnumInjectedSources** ppResult
);
```

#### <a name="parameters"></a>參數
 srcFile

在要搜尋的原始程式檔名稱。

 ppResult

擴展傳回 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) 物件，其中包含所有插入來源的清單。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
