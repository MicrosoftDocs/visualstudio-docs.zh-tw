---
title: IDiaSession::get_globalScope | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::get_globalScope method
ms.assetid: 75d128a8-3dce-40ed-b392-de3fdda041b7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b78497cee5fea3eb4ab4fda29eacc3d864ce2ea5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864100"
---
# <a name="idiasessionget_globalscope"></a>IDiaSession::get_globalScope
抓取全域範圍的參考。

## <a name="syntax"></a>語法

```C++
HRESULT get_globalScope ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回代表全域範圍的 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [Exe](../../debugger/debug-interface-access/exe.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)