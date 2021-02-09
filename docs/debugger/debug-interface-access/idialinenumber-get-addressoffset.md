---
title: IDiaLineNumber::get_addressOffset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_addressOffset method
ms.assetid: 3bcb5500-b26c-4d3c-9d81-0a389a3715c3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d8593277312a168355cef1db3142feaf5af936a7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864856"
---
# <a name="idialinenumberget_addressoffset"></a>IDiaLineNumber::get_addressOffset
抓取區塊開始之記憶體位址的位移部分。

## <a name="syntax"></a>語法

```C++
HRESULT get_addressOffset ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

擴展傳回區塊開始之記憶體位址的位移部分。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援這個屬性，則傳回。 否則會傳回錯誤碼。

## <a name="example"></a>範例

```C++
CComPtr< IDiaLineNumber > pLine;
DWORD offset;
pLine->get_addressOffset( &offset);
```

## <a name="see-also"></a>另請參閱
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
- [IDiaLineNumber::get_addressSection](../../debugger/debug-interface-access/idialinenumber-get-addresssection.md)