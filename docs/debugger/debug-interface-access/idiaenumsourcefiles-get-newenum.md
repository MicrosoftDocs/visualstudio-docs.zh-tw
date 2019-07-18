---
title: IDiaEnumSourceFiles::get__NewEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::get__NewEnum method
ms.assetid: 8405966c-64b4-4743-9a83-0e27ca2047c7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2460194426384d574cf2dbd36d89819d38472f14
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829650"
---
# <a name="idiaenumsourcefilesgetnewenum"></a>IDiaEnumSourceFiles::get__NewEnum
擷取<xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT>這個列舉值的版本。

## <a name="syntax"></a>語法

```C++
HRESULT get__NewEnum ( 
   IUnknown** pRetVal
);
```

#### <a name="parameters"></a>參數
 pRetVal

[out]傳回`IUnknown`介面，表示<xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT>這個列舉值的版本。

## <a name="return-value"></a>傳回值
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)