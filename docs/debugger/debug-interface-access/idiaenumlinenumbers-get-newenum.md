---
description: 抓取行號列舉值的 System.runtime.interopservices.outattribute. System.runtime.interopservices.comtypes. IEnumVARIANT 版本。
title: IDiaEnumLineNumbers::get__NewEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::get__NewEnum method
ms.assetid: 8b15f76b-a431-4f60-8bed-3206256b0d10
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fedfce8ac19e2c25bc266612b9f38177a79d861e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148966"
---
# <a name="idiaenumlinenumbersget__newenum"></a>IDiaEnumLineNumbers::get__NewEnum
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
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
