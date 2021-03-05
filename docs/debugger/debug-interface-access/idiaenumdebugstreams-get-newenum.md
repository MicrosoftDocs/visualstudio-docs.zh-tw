---
description: 抓取 debug stream 列舉值的 System.runtime.interopservices.outattribute. System.runtime.interopservices.comtypes. IEnumVARIANT 版本。
title: IDiaEnumDebugStreams::get__NewEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::get__NewEnum method
ms.assetid: 972372ff-abfc-4987-a302-7788fab90348
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b50c3c56d94c508b2f7158bee083060fc57ba81a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149043"
---
# <a name="idiaenumdebugstreamsget__newenum"></a>IDiaEnumDebugStreams::get__NewEnum
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
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)
