---
title: IDiaSectionContrib::get_execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_execute method
ms.assetid: 66eb38ce-a5e1-467e-b845-b3dc433eda91
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4fe19ace9d84357b08ab848038283c857d15610
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62828293"
---
# <a name="idiasectioncontribgetexecute"></a>IDiaSectionContrib::get_execute
擷取旗標，指出是否可執行檔當做程式碼區段。

## <a name="syntax"></a>語法

```C++
HRESULT get_excute ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

[out]會傳回`TRUE`一節也可以執行為程式碼; 否則會傳回`FALSE`。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`。 傳回`S_FALSE`不支援這個屬性，則為。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)