---
title: IDiaEnumDebugStreamData::get__NewEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::get__NewEnum method
ms.assetid: 023b3e31-0fc9-478d-88e8-af2ce762f322
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 54e4d7e5061130ac88facbe17b934fa91f61df19
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857087"
---
# <a name="idiaenumdebugstreamdataget__newenum"></a>IDiaEnumDebugStreamData::get__NewEnum
抓取 <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> 此列舉值的版本。

## <a name="syntax"></a>語法

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>參數
 pRetVal

擴展傳回 `IUnknown` 表示 <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> 這個列舉值版本的介面。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)