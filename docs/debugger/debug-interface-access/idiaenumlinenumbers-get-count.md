---
description: 抓取行號的數目。
title: IDiaEnumLineNumbers::get_Count | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::get_Count method
ms.assetid: dbb55936-b754-4a27-8b82-9537a7adb664
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 33b87762d1112d1f84e3e49bdbc1d2d555d723fd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148973"
---
# <a name="idiaenumlinenumbersget_count"></a>IDiaEnumLineNumbers::get_Count
抓取行號的數目。

## <a name="syntax"></a>語法

```C++
HRESULT get_Count ( 
   LONG* pRetVal
);
```

#### <a name="parameters"></a>參數
 pRetVal

擴展傳回行號的數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaEnumLineNumbers::Item](../../debugger/debug-interface-access/idiaenumlinenumbers-item.md)
