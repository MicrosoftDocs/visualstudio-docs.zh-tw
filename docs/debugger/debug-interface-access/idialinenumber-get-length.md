---
title: IDiaLineNumber：： get_length |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_length method
ms.assetid: 2c55a6f7-4ef5-45fb-9fd1-d72deaaa2829
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3804d018569a0b2e0ee5a11a3bb5edc8363cfffc
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466886"
---
# <a name="idialinenumberget_length"></a>IDiaLineNumber::get_length
抓取區塊中的位元組數目。

## <a name="syntax"></a>語法

```C++
HRESULT get_length ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>參數
 `pRetVal`

脫銷傳回區塊中的位元組數目。

## <a name="return-value"></a>傳回值
 如果成功，則傳回 `S_OK`。 `S_FALSE`如果不支援此屬性，則傳回。 否則會傳回錯誤碼。

## <a name="remarks"></a>備註
 區塊是[IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)物件所代表之行上的原始程式碼長度。

## <a name="see-also"></a>另請參閱
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)