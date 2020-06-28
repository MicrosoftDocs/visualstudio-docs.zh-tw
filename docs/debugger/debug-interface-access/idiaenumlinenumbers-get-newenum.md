---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 873df8938417da0efe7cd8b6499e4a4b6bfbbe04
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468221"
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

脫銷傳回 `IUnknown` 表示 <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> 此列舉值版本的介面。

## <a name="return-value"></a>傳回值
 如果成功，會傳回，否則會傳回 `S_OK` 錯誤碼。

## <a name="see-also"></a>另請參閱
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)