---
title: IDiaInjectedSource::get_filename | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_filename method
ms.assetid: 20f4fc68-335a-4971-b3a6-76501f0e8b19
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5dbc521686004873ef508506031a867ac0c601cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855813"
---
# <a name="idiainjectedsourceget_filename"></a>IDiaInjectedSource::get_filename
抓取來源的檔案名。

## <a name="syntax"></a>語法

```C++
HRESULT get_filename ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>參數
 pRetVal

擴展傳回來源的檔案名。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援這個屬性，則傳回。 否則會傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)