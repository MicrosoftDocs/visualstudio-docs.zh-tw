---
title: IDiaLineNumber::get_sourceFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_sourceFile method
ms.assetid: 86fc4411-375e-4b99-8f96-4da2c3f68190
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6e8d597682b88e30eefb6a1627ebc3e21a7fe7a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864723"
---
# <a name="idialinenumberget_sourcefile"></a>IDiaLineNumber::get_sourceFile
抓取來源檔案的參考。

## <a name="syntax"></a>語法

```C++
HRESULT get_sourceFile ( 
   IDiaSourceFile** pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回代表來源檔案的 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) 物件。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援這個屬性，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)