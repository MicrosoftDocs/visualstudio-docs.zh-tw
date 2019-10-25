---
title: IDiaSession::get_loadAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::get_loadAddress method
ms.assetid: 5162ae1a-38e3-4571-8995-4ed9be1dec3e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b23aff5cd5d2b94a44e3e9139ff4c97acb2225d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741934"
---
# <a name="idiasessionget_loadaddress"></a>IDiaSession::get_loadAddress
抓取可執行檔的載入位址，此檔案會對應至這個符號存放區中的符號。

## <a name="syntax"></a>語法

```C++
HRESULT get_loadAddress ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回 .exe 檔案或 .dll 檔案載入所在的虛擬位址（VA）。

## <a name="return-value"></a>傳回值
 如果成功，會傳回 `S_OK`;否則，會傳回錯誤碼。

## <a name="remarks"></a>備註
 除非使用[IDiaSession：:P ut_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)方法明確設定，否則傳回的載入位址一律為零。

## <a name="see-also"></a>請參閱
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)