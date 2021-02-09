---
title: IDiaEnumDebugStreamData::get_name | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::get_Name method
ms.assetid: e6cf2bed-ee2b-4122-886d-c20d93df7ff2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e2dcec8380ebdc869c093a840d76347cd31c244b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857094"
---
# <a name="idiaenumdebugstreamdataget_name"></a>IDiaEnumDebugStreamData::get_name
抓取 debug 資料流程的名稱。

## <a name="syntax"></a>語法

```C++
HRESULT get_Name ( 
   BSTR * pRetVal
)
```

#### <a name="parameters"></a>參數
 pRetVal

擴展傳回 debug 資料流程的名稱。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)