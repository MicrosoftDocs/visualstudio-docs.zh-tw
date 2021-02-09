---
title: IDiaEnumInjectedSources::get__NewEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::get__NewEnum method
ms.assetid: f56cdcdb-dc71-43c7-82fe-e2500986f5bc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2233c625fe1b27ffb749b8d29eb734ecddcb3700
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856730"
---
# <a name="idiaenuminjectedsourcesget__newenum"></a>IDiaEnumInjectedSources::get__NewEnum
抓取 <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> 此列舉值的版本。

## <a name="syntax"></a>語法

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>參數
 pRetVal
- [out，retval]傳回 `IUnknown` 表示 <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> 這個列舉值版本的介面。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)